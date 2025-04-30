# Application Layer

The Application Layer defines **use cases**. It orchestrates domain operations to accomplish goals.

## ✅ Responsibilities
- Use cases (Commands, Queries, Services)
- DTOs (Request, Response)
- Application-level interfaces
- Enums used in filters, predicates
- Mappings (AutoMapper profiles)
- Validation logic (if domain-independent)

## ❌ Avoid
- Business rules
- Data access logic
- ASP.NET Core dependencies

## 📁 Suggested Structure
```
/Application
  ├── /UseCases
  ├── /DTOs
  ├── /Enums
  ├── /Interfaces
  ├── /Mappers
  └── /Validation
```
