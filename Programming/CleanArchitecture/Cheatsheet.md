# Clean Architecture Cheatsheet ✅

- 🔁 **Dependency Rule:** Dependencies point inward
- 🧱 **Domain:** What your app *is*
- ⚙️ **Application:** What your app *does*
- 🌐 **Infrastructure:** How your app connects to the outside world
- 🖥️ **Presentation:** How users interact with the app

## Common Placements

| Item                | Layer          |
|---------------------|----------------|
| Entity (e.g., User) | Domain         |
| Email Service       | Infrastructure |
| LoginRequestDto     | Application    |
| JWT config          | Presentation   |
| Photo.cs            | Domain         |
| MongoPhotoModel.cs  | Infrastructure |
| IUserRepository     | Domain         |
| UserService         | Application    |


## What Goes Where (Cheat Table)

| Type                           | Belongs in       | Why                                          |
|--------------------------------|------------------|-----------------------------------------------|
| DTOs                           | Application      | Used for data transfer, not business rules     |
| Repositories (implementation)  | Infrastructure   | They interact with DBs, not domain logic       |
| ASP.NET attributes or validation | Presentation   | These are UI/framework-specific               |
| Email services, DB connections | Infrastructure   | External dependencies                         |
| Queries, Commands              | Application      | Use cases or orchestrators                    |
| MongoDB/EF Core annotations    | Infrastructure   | ORM-specific concerns                         |
