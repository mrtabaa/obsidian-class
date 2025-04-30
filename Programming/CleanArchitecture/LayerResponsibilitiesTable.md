# Layer Responsibilities Summary

| Layer           | Responsibilities                                 | Depends On         | Avoid                              |
|----------------|--------------------------------------------------|--------------------|-------------------------------------|
| **Domain**      | Entities, Value Objects, Rules, Interfaces       | -                  | Infra, UI, DB, ASP.NET dependencies |
| **Application** | Use cases, DTOs, Orchestration, Validation       | Domain             | Infra, Web                          |
| **Infrastructure** | DB access, External APIs, Identity, Email     | Domain, Application| Business logic                      |
| **Presentation**| Controllers, Authentication, Validation UI       | Application        | Domain, DB access                   |
