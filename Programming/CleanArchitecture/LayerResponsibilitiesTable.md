# Layer Responsibilities Summary

| Layer              | Responsibilities                           | Depends On             | Avoid                               |
| ------------------ | ------------------------------------------ | ---------------------- | ----------------------------------- |
| **Domain**         | Entities, Value Objects, Rules, Interfaces | -                      | Infra, UI, DB, ASP.NET dependencies |
| **Application**    | Use cases, DTOs, Orchestration, Validation | Domain, Shared         | Infra, Web                          |
| **Contracts**      | Request/Response DTOs, Enums               | -                      | Domain, Infra logic, DB annotations |
| **Infrastructure** | DB access, External APIs, Identity, Email  | Domain                 | Business logic                      |
| **Shared**         | Middleware, Auth, Rate limiting, Utilities | -                      | Domain rules, ASP.NET direct access |
| **Presentation**   | Controllers, Auth config, Validation UI    | Application, Contracts | Domain, DB access                   |
