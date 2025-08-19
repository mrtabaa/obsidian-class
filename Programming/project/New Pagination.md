Bake both into your **template** and pick per use case via a **Strategy Pattern**. Default to **offset** for small/admin lists; use **keyset (seek)** for large feeds/infinite scroll or where `Skip` would grow.

Here’s a clean, reusable setup (Angular 19 + .NET 10, Clean Architecture):

### 1) Contracts (Application)

```csharp
public interface IPaginationStrategy<TDoc, TResult>
{
    Task<PagedList<TResult>> PageAsync(
        IMongoCollection<TDoc> collection,
        MongoSpecification<TDoc, TResult> spec,
        PaginationRequest request,
        CancellationToken ct);
}

public sealed record PaginationRequest(int PageNumber = 1, int PageSize = 20, string? Cursor = null);

public sealed record PagedList<T>(IReadOnlyList<T> Items, long? Total, string? NextCursor);

public sealed class MongoSpecification<TDoc, TResult>
{
    public FilterDefinition<TDoc> Filter { get; init; } = Builders<TDoc>.Filter.Empty;
    public SortDefinition<TDoc> Sort { get; init; } = Builders<TDoc>.Sort.Ascending("_id");
    public ProjectionDefinition<TDoc, TResult>? Projection { get; init; }
    public int MaxPageSize { get; init; } = 100;
}
```

### 2) Offset strategy (default-safe)

```csharp
public sealed class OffsetPaginationStrategy<TDoc, TResult> : IPaginationStrategy<TDoc, TResult>
{
    public async Task<PagedList<TResult>> PageAsync(
        IMongoCollection<TDoc> c,
        MongoSpecification<TDoc, TResult> s,
        PaginationRequest r,
        CancellationToken ct)
    {
        var size = Math.Clamp(r.PageSize, 1, s.MaxPageSize);
        var skip = Math.Max(0, (Math.Max(1, r.PageNumber) - 1) * size);

        var find = c.Find(s.Filter).Sort(s.Sort);

        var totalTask = find.CountDocumentsAsync(ct);
        var itemsTask = (s.Projection is null ? find.Limit(size).Skip(skip).ToListAsync(ct)
                                              : find.Limit(size).Skip(skip).Project(s.Projection).ToListAsync(ct));

        await Task.WhenAll(totalTask, itemsTask);
        return new PagedList<TResult>((IReadOnlyList<TResult>)itemsTask.Result, totalTask.Result, NextCursor: null);
    }
}
```

### 3) Keyset strategy (high-scale)

```csharp
public sealed class KeysetPaginationStrategy<TDoc, TResult> : IPaginationStrategy<TDoc, TResult>
{
    public async Task<PagedList<TResult>> PageAsync(
        IMongoCollection<TDoc> c,
        MongoSpecification<TDoc, TResult> s,
        PaginationRequest r,
        CancellationToken ct)
    {
        // Expect primary sort to be a single indexed field, e.g. CreatedAt or _id (asc/desc).
        // Cursor is an opaque Base64 of the last key value.
        var size = Math.Clamp(r.PageSize, 1, s.MaxPageSize);
        var (field, descending) = ResolvePrimarySort(s.Sort); // implement to extract first sort field

        var builder = Builders<TDoc>.Filter;
        var filter = s.Filter;

        if (!string.IsNullOrWhiteSpace(r.Cursor))
        {
            var after = CursorCodec.Decode(r.Cursor); // returns BsonValue
            var cmp = descending ? builder.Lt(field, after) : builder.Gt(field, after);
            filter = builder.And(filter, cmp);
        }

        var query = c.Find(filter).Sort(s.Sort).Limit(size + 1); // +1 to detect hasMore
        var list = s.Projection is null ? await query.ToListAsync(ct)
                                        : await query.Project(s.Projection).ToListAsync(ct);

        var hasMore = list.Count > size;
        if (hasMore) list.RemoveAt(list.Count - 1);

        var nextCursor = hasMore ? CursorCodec.Encode(GetLastKey(list, field)) : null;

        // Total is optional (null) to avoid expensive counts on huge sets.
        return new PagedList<TResult>(list, Total: null, NextCursor: nextCursor);
    }

    // Helpers (sketch): ResolvePrimarySort, GetLastKey, CursorCodec.Encode/Decode …
}
```

### 4) Repository (Infrastructure) using **Specification + Strategy**

```csharp
public sealed class ReadRepository<TDoc>
{
    private readonly IMongoCollection<TDoc> _col;
    public ReadRepository(IMongoDatabase db, string collectionName) => _col = db.GetCollection<TDoc>(collectionName);

    public Task<PagedList<TResult>> PageAsync<TResult>(
        MongoSpecification<TDoc, TResult> spec,
        PaginationRequest request,
        IPaginationStrategy<TDoc, TResult> strategy,
        CancellationToken ct) =>
        strategy.PageAsync(_col, spec, request, ct);
}
```

### 5) Choosing the strategy (Application/UseCase)

- **Default**: `OffsetPaginationStrategy` for admin tables, small datasets, or when you need `Total`.
    
- **High-scale**: `KeysetPaginationStrategy` for feeds, chats, wallets/tx lists, infinite scroll.
    
- Swap via DI or per-query:
    

```csharp
var strategy = useKeyset ? keyset : offset;
return await repo.PageAsync(spec, request, strategy, ct);
```

### Why this template is “safe”

- Avoids LINQ-provider surprises (Mongo’s IQueryable quirks).
    
- Keeps queries **server-side** and **index-aligned** (you decide filter/sort/projection).
    
- Caps page size; prevents unbounded scans.
    
- **Strategy Pattern** lets you optimize per endpoint without changing callers.
    
- **Specification Pattern** keeps query intent explicit and testable.
    

### Practical defaults for your template

- Ship both strategies.
    
- Make **Offset** the default for CRUD screens; expose **Keyset** for lists expected to exceed ~50–100k docs or with infinite scroll.
    
- Provide a `HasMore` variant (fetch `size+1`) when you don’t need `Total`.
    
- Document index requirements: sort key must be indexed; prefer compound `{FilterFields..., SortField}`.
    

If you want, I’ll drop in minimal `CursorCodec`, `ResolvePrimarySort`, and a tiny Angular 19 paginator + infinite scroll adapter to finish the end‑to‑end template.