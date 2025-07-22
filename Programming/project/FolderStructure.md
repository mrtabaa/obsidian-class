dashboard.hallboard.com
www.hallboard.com

```plaintext
/project-name/
│
├── frontend/                                   # ✅ All Angular apps and libraries live here
│   ├── angular.json                            # Angular workspace root config
│   ├── tsconfig.base.json                      # Shared TypeScript config
│   ├── package.json                            # Contains Angular, Material, etc.
│   │
│   ├── apps/                                   # Angular applications
│   │   ├── dashboard/                          # Angular 19 CSR App (Main Dashboard)
│   │   │   ├── src/
│   │   │   ├── main.ts
│   │   │   └── ... (standalone app config)
│   │   │
│   │   └── landing/                            # Angular SSR App (SEO Landing Pages)
│   │       ├── src/
│   │       ├── main.server.ts
│   │       ├── server.ts
│   │       └── ... (Angular Universal setup)
│   │
│   ├── libs/                                   # Shared Angular libraries
│   │   ├── ui/                                 # ✅ Angular Material-based standalone components
│   │   │   ├── components/
│   │   │   ├── material-theme/
│   │   │   └── index.ts
│   │   │
│   │   ├── core/                               # Auth, guards, interceptors, services
│   │   │   ├── auth/
│   │   │   ├── api/
│   │   │   └── utils/
│   │   │
│   │   └── env/                                # Environment tokens, models, configs
│   │
│   └── tools/                                  # Optional: dev tools, schematics, builders
│
│
├── backend/                                    # .NET 9 Clean Architecture Backend
│   ├── Directory.Build.props                   # Centralized project-wide MSBuild settings
│   ├── Directory.Packages.props                # NuGet version pinning (Microsoft.CodeAnalysis.NetAnalyzers, etc.)
│   │
│   ├── WebApi/                                 # ASP.NET Core API entry point — controllers, filters, DI, middleware
			Helpers/
			Filters/
			Middlewares/
		└── Modules/
	│   │       ├── Auth/
	│   │       ├── Project/
	│   │       └── Payment/
		
│   ├── Application/                            # Use cases, CQRS handlers, service interfaces
│   │   └── Modules/
│   │       ├── Auth/
│   │       ├── Projects/
│   │       └── Payments/
│   │
│   ├── Domain/                                 # Domain models, aggregates, value objects
│   │   └── Modules/
│   │       ├── Common/
│   │       ├── Auth/
│   │       ├── Project/
│   │       └── Payment/
│   │
│   ├── Infrastructure/                         # Persistence, Redis, Web3, integration logic
			Features/
			Modules/
			│   ├── Common/
	│   │       ├── Auth/
	│   │       ├── Project/
	│   │       └── Payment/		
	│   │   Persistence/
│   │   │   ├── Mongo/
│   │   │   └── Postgres/
│   │   ├── Web3/
│   │   ├── Redis/
│   │   └── InfrastructureServices.cs
│   │
│   ├── Contracts/                              # Shared DTOs and request/response models
│   │   └── Modules/
│   │       ├── Auth/
│   │       ├── Projects/
│   │       └── Payments/
│   │
│   ├── Shared/                                 # Cross-cutting: OperationResult, time, logging
│   │
│   ├── Tests/                                  # Unit, Integration, E2E tests
│   │   ├── Unit/
│   │   ├── Integration/
│   │   └── E2E/
│   │
│   └── Hallboard.sln                           # Solution file for the backend
│
│
├── build/                                      # CI/CD, Docker, Nginx, deploy configs
│   ├── docker/
│   ├── nginx/
│   └── deploy-prod.sh
│
├── docs/                                       # Obsidian/architecture notes
│   ├── architecture.md
│   ├── api-contracts.md
│   ├── deployment.md
│   └── tests.md
│
├── .editorconfig
├── .gitignore
├── README.md
└── package.json                                # Optional: tooling scripts or root-level mono-repo support

```