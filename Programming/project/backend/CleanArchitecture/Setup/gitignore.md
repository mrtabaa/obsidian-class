.gitignore
```gitignore
# ============================================
# .gitignore for Hallboard Monorepo
# Includes: Angular CSR, Angular SSR, .NET Backend, Rider, Docker
# ============================================

# ─────────────────────────────
# 🛠 General
# ─────────────────────────────
.DS_Store
Thumbs.db
*.log
*.tmp
*.bak
*.swp
*.swo

# ─────────────────────────────
# 📦 Root-level Node tools (if used)
# ─────────────────────────────
/node_modules/
/dist/
/.env

# ─────────────────────────────
# 🌐 Angular Frontend Apps (CSR + SSR)
# ─────────────────────────────
/apps/client/node_modules/
/apps/client/dist/
/apps/client/.angular/
/apps/client/.env
/apps/client/.idea/

# Angular Universal SSR app
/apps/landing/node_modules/
/apps/landing/dist/
/apps/landing/.angular/
/apps/landing/.env
/apps/landing/server/
/apps/landing/.idea/

# ─────────────────────────────
# 🧱 .NET 9 Backend (Clean Architecture)
# ─────────────────────────────
/backend/bin/
/backend/obj/
/backend/.vs/
/backend/.vscode/
/backend/.idea/
/backend/TestResults/
/backend/*.user
/backend/*.suo
/backend/publish/
/backend/coverage/
/backend/Hallboard.API/
*.db
*.db-shm
*.db-wal

# Build artifacts and cache
*.nupkg
*.snupkg
*.dg
*.user
*.suo
*.userosscache
*.sln.docstates
*.vs/
*.vscode/
.nuget/
project.lock.json
project.assets.json
project.nuget.cache
*.nuget.props
*.nuget.targets
*.csproj.nuget.g.props
*.csproj.nuget.g.targets

# ─────────────────────────────
# ⚙️ Build / CI Scripts
# ─────────────────────────────
/build/**/*.log
/build/**/*.tmp
/build/nginx/
/build/docker/
/build/deploy-prod.sh

# ─────────────────────────────
# 📄 Documentation
# ─────────────────────────────
# (Keep markdown docs)
!/docs/
!/docs/*.md

# ─────────────────────────────
# 🧠 JetBrains Rider IDE Files
# ─────────────────────────────
/.idea/
/.idea.hallboard-web3.iml
/shelf/
/workspace.xml
/contentModel.xml
/modules.xml
/projectSettingsUpdater.xml

# Editor-based HTTP Client requests
/httpRequests/

# Datasource local storage
/dataSources/
/dataSources.local.xml

# ─────────────────────────────
# ✅ Keep these shared folders
# ─────────────────────────────
!/libs/
!/backend/
!/apps/
!/apps/client/
!/apps/landing/
!/build/
```