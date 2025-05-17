# Contracts Layer

The **Contracts Layer** defines the public-facing API contracts used for communication between the backend and external clients (like your Angular app).

## ✅ Responsibilities
- Request and Response DTOs used in API endpoints
- Enums and shared wrappers meant for frontend
- API-level error models, pagination wrappers
- Used by WebApi (Presentation) and optionally Application

## ❌ Avoid
- Business logic
- Internal use-case orchestration
- Domain rules or persistence details

## 📁 Suggested Structure
```
/Contracts
  ├── /Auth
  │     ├── LoginRequest.cs
  │     └── LoginResponse.cs
  ├── /Users
  ├── /Projects
  └── /Common
```
