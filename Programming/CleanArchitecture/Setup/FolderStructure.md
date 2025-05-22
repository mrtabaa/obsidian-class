```plaintext
/project-name/
├── apps/
│   ├── client/                             # Angular 19 CSR App (Main Dashboard)
│   │   ├── src/
│   │   ├── angular.json
│   │   ├── tsconfig.json
│   │   └── package.json
│   │
│   └── landing/                            # Angular SSR App (Public Landing Page)
│       ├── src/
│       ├── main.server.ts
│       ├── server.ts
│       ├── angular.json
│       ├── tsconfig.server.json
│       └── package.json
│
├── backend/                                        # .NET 9 Clean Architecture Backend
│   ├── Directory.Build.props                       # Centralized settings
|	│   ├── Microsoft.CodeAnalysis.NetAnalyzers     # Install this NuGet to catch code and bug issues early + enforce consistency
│   ├── Directory.Packages.props                    # Centralized NuGet versioning
│
│   ├── WebApi/                             # Entry point: controllers, filters, middleware
│
│   ├── Application/                        # Use cases, services, commands/queries
│   │   └── Modules/
│   │       ├── Auth/
│   │       ├── Projects/
│   │       └── Payments/
│
│   ├── Domain/                             # Core rules: entities, aggregates, value objects
│   │   └── Modules/
│   │       ├── Shared/
│   │       ├── Auth/
│   │       ├── Project/
│   │       └── Payment/
│
│   ├── Infrastructure/                     # Adapters and integration code
│   │   ├── Persistence/
│   │   │   ├── Mongo/
│   │   │   │   ├── MongoServiceExtensions.cs
│   │   │   │   ├── MongoRepositoryExtensions.cs
│   │   │   │   └── Settings/
│   │   │   └── Postgres/
│   │   │       ├── PostgresServiceExtensions.cs
│   │   │       └── PostgresRepositoryExtensions.cs
│   │   ├── Web3/
│   │   │   ├── EscrowContractService.cs
│   │   │   └── Web3ServiceExtensions.cs
│   │   ├── Redis/
│   │   │   ├── RedisCacheService.cs
│   │   │   └── RedisServiceExtensions.cs
│   │   └── InfrastructureServices.cs       # Composes all infra modules into IServiceCollection
│
│   ├── Contracts/                          # Shared API request/response models
│   │   └── Modules/
│   │       ├── Auth/
│   │       ├── Projects/
│   │       └── Payments/
│
│   ├── Shared/                             # Cross-cutting: OperationResult, errors, time, utils
│
│   ├── Tests/                              # All backend tests live here
│   │   ├── Unit/
│   │   │   ├── Domain/
│   │   │   └── Application/
│   │   ├── Integration/
│   │   │   ├── Infrastructure/
│   │   │   └── Application/
│   │   └── E2E/
│   │       └── WebApi/
│   │
│   └── Hallboard.sln                       # Solution file for the entire backend
│
├── libs/                                   # Shared Angular libraries
│   ├── ui/                                 # Reusable Material components, layouts
│   │   ├── components/
│   │   ├── material-theme/
│   │   └── index.ts
│   ├── core/                               # Auth, guards, services, interceptors
│   └── env/                                # Environment configs, tokens, models
│
├── build/                                  # CI/CD, Docker, Nginx, deployment
│   ├── nginx/
│   ├── docker/
│   └── deploy-prod.sh
│
├── docs/                                   # Obsidian-ready architecture notes
│   ├── architecture.md
│   ├── api-contracts.md
│   ├── deployment.md
│   └── tests.md
│
├── .editorconfig
├── .gitignore
├── README.md
└── package.json                            # Optional: tooling or mono-repo scripts

```