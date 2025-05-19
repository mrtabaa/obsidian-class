# Clean Architecture Cheatsheet ✅

- 🔁 **Dependency Rule:** Dependencies point inward
- 🧱 **Domain:** What your app *is*
- ⚙️ **Application:** What your app *does*
- 🌐 **Infrastructure:** How your app connects to the outside world
- 🖥️ **Presentation:** How users interact with the app
- 📦 **Contracts:** Public DTOs shared with frontend
- 🧰 **Shared:** Cross-cutting utilities (auth, rate limiting)

## Common Placements

| Item                    | Layer          |
|-------------------------|----------------|
| Entity (e.g., User)     | Domain         |
| Email Service           | Infrastructure |
| LoginRequest            | Contracts      |
| JWT config              | Shared         |
| Photo.cs                | Domain         |
| MongoPhotoModel.cs      | Infrastructure |
| IUserRepository         | Domain         |
| UserService             | Application    |
| PaginationParams        | Contracts      |
| RateLimitingMiddleware  | Shared         |
| AuthController          | Presentation   |


## What Goes Where (Cheat Table)

| Type                        | Belongs in     | Why                                      |
| --------------------------- | -------------- | ---------------------------------------- |
| Request/Response DTOs       | Contracts      | Shared with frontend                     |
| Commands / Queries          | Application    | Use cases or orchestrators               |
| Domain entities and rules   | Domain         | Core rules                               |
| Repository interfaces       | Domain         | Abstract DB logic                        |
| Repository implementations  | Infrastructure | DB-specific implementation               |
| ASP.NET attributes          | Presentation   | UI/framework-specific                    |
| Middleware / JWT handling   | Shared         | Cross-cutting concerns, not domain logic |
| MongoDB/EF Core annotations | Infrastructure | ORM-specific concerns                    |
