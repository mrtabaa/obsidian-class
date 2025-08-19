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
#### Installation
Install `dotnet-ef` globally
```bash
dotnet tool install --global dotnet-ef
```

#### Factory for design-time migrations
Add `Design-time factory` to be able to migrate from `Infrastructor` independent from `WebApi`. No need to run the app for migrations anymore. 

* With this config structure: 
```json
{  
  "MyPostgresSettings": {  
    "ConnectionString": "Host=localhost;Port=5432;Database=ca-template;Username=postgres;Password=2223;Pooling=true;Minimum Pool Size=5;Maximum Pool Size=100;SSL Mode=Disable"  
  },  
  "MyMongoDbSettings": {  
    "ConnectionString": "mongodb://localhost:27017",  
    "DatabaseName": "ca-template"  
  },
}
```
- Use this code
```C#
using Ca.Infrastructure.Persistence.EFCore.Postgres;  
using Microsoft.EntityFrameworkCore;  
using Microsoft.EntityFrameworkCore.Design;  
using Microsoft.Extensions.Configuration;  
using Microsoft.Extensions.FileProviders;  
  
namespace Ca.Infrastructure.Persistence.EFCore.Common;  
  
/// <summary>  
///     Design-Time (instead of Run-Time)  
///     Enable migrations without running WebApi to make it api independent.  
///     Needs these packages:  
///     <PackageReference Include="Microsoft.Extensions.Configuration" />  
///     <PackageReference Include="Microsoft.Extensions.Configuration.Json" />  
///     <PackageReference Include="Microsoft.Extensions.FileProviders.Physical" />  
///     <PackageReference Include="Microsoft.Extensions.Configuration.EnvironmentVariables" />  
/// </summary>  
public sealed class AppDbContextPostgresFactory : IDesignTimeDbContextFactory<AppDbContextPostgres>  
{  
    public AppDbContextPostgres CreateDbContext(string[] args)  
    {  
        // 0) CI/local override  
        string? fromEnv = Environment.GetEnvironmentVariable("EFCORE_DESIGNTIME_CONN");  
        if (!string.IsNullOrWhiteSpace(fromEnv)) return Build(fromEnv);  
  
        string env = Environment.GetEnvironmentVariable("ASPNETCORE_ENVIRONMENT") ?? "Development";  
        string cwd = Directory.GetCurrentDirectory();  
  
        // 1) Optional infra-local design-time file  
        var cb = new ConfigurationBuilder();  
        string designTime = Path.Combine(cwd, "appsettings.DesignTime.json");  
        if (File.Exists(designTime)) cb.AddJsonFile(designTime, optional: false, reloadOnChange: false);  
  
        // 2) Try to load WebApi appsettings.*  
        string[] candidates = new[]  
        {  
            Path.GetFullPath(  
                Path.Combine(cwd, "../Ca.WebApi")  
            ), // backend/src/Ca.Infrastructure -> backend/src/Ca.WebApi  
            Path.GetFullPath(Path.Combine(cwd, "../../src/Ca.WebApi")),  
            Path.GetFullPath(Path.Combine(cwd, "../../Ca.WebApi"))  
        };  
        string? webApiPath = candidates.FirstOrDefault(Directory.Exists);  
        if (webApiPath is not null)  
        {  
            var fp = new PhysicalFileProvider(webApiPath);  
            cb.AddJsonFile(fp, "appsettings.json", optional: true, reloadOnChange: false).AddJsonFile(  
                fp, $"appsettings.{env}.json", optional: true, reloadOnChange: false  
            );  
        }  
  
        cb.AddEnvironmentVariables();  
        IConfigurationRoot cfg = cb.Build();  
  
        // 3) Read your key first; fall back to common shapes  
        string? cs = cfg["MyPostgresSettings:ConnectionString"] ??  
                     cfg.GetConnectionString("Postgres") ??  
                     cfg["ConnectionStrings:Postgres"];  
  
        if (string.IsNullOrWhiteSpace(cs))  
        {  
            throw new InvalidOperationException(  
                "Postgres connection not found. Expect 'MyPostgresSettings:ConnectionString' (or 'ConnectionStrings:Postgres')."  
            );  
        }  
  
        return Build(cs);  
  
        static AppDbContextPostgres Build(string conn)  
        {  
            DbContextOptions<AppDbContextPostgres> opts = new DbContextOptionsBuilder<AppDbContextPostgres>().  
                UseNpgsql(conn).Options;  
            return new AppDbContextPostgres(opts);  
        }  
    }  
}
```