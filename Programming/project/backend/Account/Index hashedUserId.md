### **Why Index the `hashedId` Field?**

1. **Improved Query Performance**: MongoDB uses indexes to locate data efficiently. Without an index on `hashedId`, MongoDB performs a full collection scan, which is slower for large datasets.
    
2. **Reduced Resource Consumption**: Indexes reduce the computational cost of queries, saving CPU and memory resources on your database server.
    
3. **Concurrency**: Indexed queries reduce locking contention in MongoDB, improving performance during concurrent access.
    
4. **Frequent Queries**: If `hashedId` is a field frequently queried, indexed queries will return results significantly faster.

#### How
1. Create the index
```c#
public async Task EnsureHashedIdIndexAsync(IMongoCollection<AppUser> appUserCollection)
{
    var indexKeysBuilder = Builders<AppUser>.IndexKeys;

    // Create an index on the hashedId field
    var hashedIdIndex = new CreateIndexModel<AppUser>(
        indexKeysBuilder.Ascending(u => u.HashedId)
    );

    await appUserCollection.Indexes.CreateOneAsync(hashedIdIndex);
}
```
2. Call it in the `constructor`
```c#
var appUserCollection = _mongoDatabase.GetCollection<AppUser>("appUsers");
await EnsureHashedIdIndexAsync(appUserCollection);

```
###### NOTES: 
* If `hashedId` must be unique, use this:
```c#
var hashedIdIndex = new CreateIndexModel<AppUser>(
    Builders<AppUser>.IndexKeys.Ascending(u => u.HashedId),
    new CreateIndexOptions { Unique = true }
);
```
* If indexing multiple props
```c#
var compoundIndex = Builders<AppUser>.IndexKeys
    .Ascending(u => u.HashedId)
    .Ascending(u => u.Status);

await appUserCollection.Indexes.CreateOneAsync(new CreateIndexModel<AppUser>(compoundIndex));
```
* If indexing an `optional` prop
```c#
var hashedIdIndex = new CreateIndexModel<AppUser>(
    Builders<AppUser>.IndexKeys.Ascending(u => u.HashedId),
    new CreateIndexOptions { Sparse = true }
);
```

#### Confirm the indexed items
In `Mogosh`
```bash
db.appUsers.getIndexes()
```