optimistic concurrency by default. 
automatic transaction management
cashing like redis? 
int or guid or else?

* Design a schema based on models
```bash
dotnet ef migrations add Init -o MyDirectory/Migrations
```

 * Create the database based on the migration
```bash
dotnet ef database update
```

* Redesign schema after model change
```bash
dotnet ef migrations add PasswordAdded
```