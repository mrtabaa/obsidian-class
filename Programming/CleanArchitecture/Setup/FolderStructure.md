```plaintext
/project-name/
├── apps/
│   ├── client/                     # Angular 19 CSR App (Main Dashboard)
│   │   ├── src/
│   │   ├── angular.json
│   │   ├── tsconfig.json
│   │   └── package.json
│   │
│   └── landing/                    # Angular SSR App (Public Landing Page)
│       ├── src/
│       ├── main.server.ts
│       ├── server.ts
│       ├── angular.json
│       ├── tsconfig.server.json
│       └── package.json
│
├── backend/                        # .NET 9 Clean Architecture Backend
│   ├── Directory.Build.props                       # Centralize shared project settings across the solution
|	│   ├── Microsoft.CodeAnalysis.NetAnalyzers     # Install this NuGet to catch code and bug issues early + enforce consistency
│   ├── Directory.Packages.props                    # Centralize NuGet versions / Romve Versions from all projects!
│   ├── WebApi/                     # Entry point with controllers, middleware, filters
│   ├── Application/                # Use cases, DTOs, service contracts
│   ├── Domain/                     # Core entities, value objects, enums
│   ├── Infrastructure/             # MongoDB/PostgreSQL integrations, smart contracts
│   ├── Contracts/                  # Shared API contracts between backend <-> frontend
│   ├── Shared/                     # Middleware, auth, extensions, rate limiting
│   └── Hallboard.sln               # Solution file
│
├── libs/                           # Shared code between apps
│   ├── ui/                         # Angular Material components, shared UI
│   │   ├── components/
│   │   ├── material-theme/
│   │   └── index.ts
│   ├── core/                       # Auth services, guards, interceptors
│   └── env/                        # Environment configs and shared types
│
├── build/                          # CI/CD scripts and deployment configs
│   ├── nginx/                      # Nginx config for SSR + API reverse proxy
│   ├── docker/                     # Dockerfiles, compose files
│   └── deploy-prod.sh              # Optional deployment script
│
├── docs/                           # Markdown documentation
│   ├── architecture.md
│   ├── api-contracts.md
│   └── deployment.md
│
├── .editorconfig
├── .gitignore
├── README.md
└── package.json                    # Optional – for root-level tooling

```
