# Presentation Layer

Handles **user interaction**. Typically an API, web UI, or CLI.

## ✅ Responsibilities
- Controllers (ASP.NET Core)
- Input validation (via annotations or FluentValidation)
- Authentication configuration (JWT, cookies)
- Exposing endpoints to clients

## ❌ Avoid
- Business rules
- Persistence logic
- Direct use of domain or infrastructure logic

## 📁 Suggested Structure
```
/Presentation
  ├── /Controllers
  ├── /Filters
  ├── /Middleware
  ├── /Authentication
  └── /Models (optional for request/response shaping)
```
