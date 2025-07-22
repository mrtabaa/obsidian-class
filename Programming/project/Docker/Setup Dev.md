# 🐳 Docker Dev Setup for Fullstack (.NET + Angular SSR/CSR)

## 📁 Folder Structure

```
project-name/
├── backend/                 # .NET 9 Web API
├── frontend/
|   ├── apps
│      ├── landing/          # Angular Universal (SSR)
│      └── dashboard/        # Angular SPA (CSR)
├── Dockerfile
├── docker-compose.yml
├── .devcontainer/
│   └── devcontainer.json  (optional for VS Code)
```

---

## 🔧 Step-by-Step Setup

### 1. Create `Dockerfile` in root:

```Dockerfile
# Dockerfile
FROM mcr.microsoft.com/dotnet/sdk:9.0 AS dev

# Install Node.js 20.x
RUN curl -fsSL https://deb.nodesource.com/setup_20.x | bash - && \
    apt-get install -y nodejs

# Install Angular CLI globally
RUN npm install -g @angular/cli@19

# Install yarn globally (optional)
RUN npm install -g yarn

# Create working directory
WORKDIR /app

# Default command
CMD [ "bash" ]
```

---

### 2. Create `docker-compose.yml` in root:

```yaml
# docker-compose.yml
version: '3.8'

services:
  dev:
    build:
      context: .
      dockerfile: Dockerfile
    volumes:
      - .:/app
    ports:
      - "4200:4200"     # Angular CSR
      - "4000:4000"     # Angular SSR
      - "5000:5000"     # .NET API
    command: sleep infinity  # Keeps container alive for manual commands
```

---

### 3. (Optional) Create VS Code Dev Container Config

#### Create `.devcontainer/devcontainer.json`:

```json
{
  "name": "Fullstack Dev Container",
  "dockerComposeFile": "../docker-compose.yml",
  "service": "dev",
  "workspaceFolder": "/app",
  "settings": {
    "terminal.integrated.defaultProfile.linux": "bash"
  },
  "extensions": [
    "ms-dotnettools.csharp",
    "dbaeumer.vscode-eslint",
    "angular.ng-template"
  ],
  "forwardPorts": [4200, 4000, 5000]
}
```

✅ Now you can just open the folder in VS Code → "Reopen in Container"

---

## 🚀 Run Your Apps (Inside Container)

First, enter the container:

```bash
docker compose run --service-ports dev bash
```

Then:

### 👉 Angular CSR (dashboard)
```bash
cd frontend/dashboard
npm install
ng serve --host 0.0.0.0
```

### 👉 Angular SSR (landing)
```bash
cd frontend/landing
npm install
npm run dev:ssr  # This should run on port 4000
```

### 👉 .NET 9 Web API
```bash
cd backend
dotnet restore
dotnet run --urls=http://0.0.0.0:5000
```

---

## 🛠 Tips

- Add `.vscode/settings.json` to configure debugging if needed
- Add `.dockerignore` to speed up build
- You can alias commands in a `Makefile` or NPM script later

---

## 🧼 Clean Up

Stop and remove all containers:

```bash
docker compose down
```

---

## 🧠 Summary

| Stack         | Inside Container     |
|---------------|----------------------|
| Node.js       | v20.x                |
| Angular CLI   | v19.x                |
| .NET SDK      | v9.0                 |
| Yarn (opt)    | Installed globally   |
| Port Mappings | 4200 (CSR), 4000 (SSR), 5000 (.NET) |

---

Let me know if you want:
- A `Makefile` for easier dev commands
- Or Nginx setup for SSR in prod
- Or Dockerized Mongo/Postgres services
