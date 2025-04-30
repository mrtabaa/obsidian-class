# Infrastructure Layer

Responsible for **technical concerns**: persistence, APIs, cloud services.

## ✅ Responsibilities
- Implement repository interfaces
- Database access (e.g., Mongo, PostgreSQL)
- External services (e.g., email, file storage)
- Identity management
- Configuration of external SDKs

## ❌ Avoid
- Business logic
- Use cases
- Presentation logic

## 📁 Suggested Structure
```
/Infrastructure
  ├── /Mongo
  │     ├── /Models
  │     └── /Repositories
  ├── /PostgreSql
  │     ├── /Models
  │     └── /Repositories
  ├── /Email
  └── /Identity
```
