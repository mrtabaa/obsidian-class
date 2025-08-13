## Features
* Querying
* Change tracking
* Saving
* Concurrency (Race: Default is **last-write-wins**)
* Transactions
* Cashing
* Build-in conventions (e.g. `Id`)
* Configurations (e.g. `MaxLength`)
* Migrations (Schema design)

### Concurrency
Common examples include:
- **Order Status:** Two different systems try to update the status of an order from "Processing" to "Shipped" and "Canceled" at the same time.
- **Inventory Count:** Two customers simultaneously try to purchase the last available item in your stock.
- **User Profile:** Two different sessions try to update a user's email address or profile information simultaneously.

e.g. Prevent update **User Profile** simultaneously.  
```C#
b.Entity<AppUserPostgres>()             // AppUser Model in infra 
    .Property<uint>("xmin")             // shadow property  !!! "xmin" is for PostgreSQL ONLY!
    .IsConcurrencyToken()               // marks as concurrency token  
    .ValueGeneratedOnAddOrUpdate();     // DB-maintained
```
## Setup

Install `dotnet-ef` globally
```bash
dotnet tool install --global dotnet-ef
```

