# Suggested Clean Architecture Folder Structure

/src
  ├── Domain
  │   ├── Entities
  │   ├── ValueObjects
  │   ├── Services
  │   ├── Interfaces
  │   ├── Enums
  │   └── Events
  ├── Application
  │   ├── UseCases
  │   ├── DTOs
  │   ├── Interfaces
  │   ├── Mappers
  │   └── Enums
  ├── Infrastructure
  │   ├── Mongo
  │   ├── PostgreSql
  │   ├── Email
  │   └── Identity
  └── Presentation
      ├── Controllers
      ├── Filters
      ├── Middleware
      └── Authentication
