# Domain Layer

The **Domain Layer** is the heart of your application. It defines what your app *is*, regardless of how it's delivered or stored.

## ✅ Responsibilities
- Entities
- Value Objects
- Domain Services
- Enums (business-related)
- Interfaces (e.g., IRepository, IValidator)
- Domain Events (optional)

## ❌ Avoid
- DTOs
- Persistence attributes (e.g., `[BsonId]`)
- ASP.NET Core features
- External service dependencies

## 📁 Suggested Structure
```
/Domain
  ├── /Entities
  ├── /ValueObjects
  ├── /Services
  ├── /Interfaces
  ├── /Enums
  └── /Events
```
