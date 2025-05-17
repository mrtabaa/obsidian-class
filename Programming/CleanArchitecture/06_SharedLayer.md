# Shared Layer

The **Shared Layer** holds cross-cutting concerns that are reused across Infrastructure, WebApi, and sometimes Application.

## ✅ Responsibilities
- JWT generation utilities
- Middleware (e.g., rate limiting, logging)
- Common helpers and extension methods
- Auth token parsing, security tools

## ❌ Avoid
- Business or domain logic
- UI-specific or DB-specific behavior

## 📁 Suggested Structure
```
/Shared
  ├── /Authentication
  ├── /Middleware
  ├── /Extensions
  └── /RateLimiting
```
