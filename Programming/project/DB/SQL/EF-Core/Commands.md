### Development
1. **Design a schema based on models**
```bash
cd backend/src/Ca.Infrastructure
```
###### Postgres
```bash
dotnet ef migrations add Init \ # Name it Init
  -o Persistence/EFCore/Postgres/Migrations \ # Create Migrations folder
  --context AppDbContextPostgres # Separate migrations per provider with AppDbContextPostgres.cs
```
###### SQL Server
```bash
dotnet ef migrations add Init \
  -o Persistence/EFCore/SqlServer/Migrations \
  --context AppDbContextSqlServer # AppDbContextSqlServer.cs
```

2. **Create the database based on the migration**
```bash
dotnet ef database update
```
<font color="#f79646">Note: It's fine to see this error for the first time. Further updates won't have it. </font>
```bash
Failed executing DbCommand (25ms) [Parameters=[], CommandType='Text', CommandTimeout='30']
SELECT "MigrationId", "ProductVersion"
FROM "__EFMigrationsHistory"
ORDER BY "MigrationId";
```


3. **Redesign schema after model change**
```bash
dotnet ef migrations add PasswordAdded
```

### Production
Production deployments (safer than auto-migrate on startup)
- Generate an idempotent script and run it via CI/CD:
```bash 
dotnet ef migrations script --idempotent -o Persistence/EFCore/Migrations/upgrade.sql
```

### Roll back (if needed):
```bash
dotnet ef migrations list
dotnet ef database update <PreviousMigrationName>
```