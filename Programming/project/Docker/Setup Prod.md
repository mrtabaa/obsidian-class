# 🚀 Docker Production Setup for Fullstack (.NET + Angular SSR/CSR)

## 📁 Folder Structure

```
/
├── backend/              # .NET 9 Web API
├── frontend/
|   ├── apps
│      ├── landing/          # Angular Universal (SSR)
│      └── dashboard/        # Angular SPA (CSR - Static)
├── nginx/
│   └── default.conf      # Nginx reverse proxy config
├── Dockerfile.api
├── Dockerfile.ssr
├── Dockerfile.csr
├── docker-compose.prod.yml
```

---

## 🔧 Step-by-Step Setup

### 1. 🐳 `Dockerfile.api` – .NET 9 Web API

```Dockerfile
# Dockerfile.api
FROM mcr.microsoft.com/dotnet/aspnet:9.0 AS base
WORKDIR /app

COPY backend/out ./

ENTRYPOINT ["dotnet", "YourAppName.dll"]
```

➡️ First, publish your API:
```bash
dotnet publish -c Release -o backend/out
```

---

### 2. 🐳 `Dockerfile.ssr` – Angular Universal (SSR)

```Dockerfile
# Dockerfile.ssr
FROM node:20-alpine

WORKDIR /app

COPY frontend/landing/package*.json ./
RUN npm install

COPY frontend/landing ./
RUN npm run build:ssr

CMD ["node", "dist/landing/server/main.js"]
```

> Make sure your SSR port is `4000` in `angular.json` or `main.ts`.

---

### 3. 🐳 `Dockerfile.csr` – Angular CSR (Static Site)

```Dockerfile
# Dockerfile.csr
FROM node:20 as build

WORKDIR /app

COPY frontend/dashboard/package*.json ./
RUN npm install

COPY frontend/dashboard ./
RUN npm run build

# --- Static Serving Stage ---
FROM nginx:alpine
COPY --from=build /app/dist/dashboard /usr/share/nginx/html
```

---

### 4. ⚙️ Nginx Reverse Proxy – `nginx/default.conf`

```nginx
server {
  listen 80;

  location / {
    proxy_pass http://ssr:4000;
    proxy_http_version 1.1;
    proxy_set_header Upgrade $http_upgrade;
    proxy_set_header Connection 'upgrade';
    proxy_set_header Host $host;
    proxy_cache_bypass $http_upgrade;
  }

  location /api {
    rewrite ^/api(/.*)$ $1 break;
    proxy_pass http://api:5000;
    proxy_http_version 1.1;
    proxy_set_header Host $host;
    proxy_set_header X-Real-IP $remote_addr;
  }

  location /dashboard {
    root /usr/share/nginx/html;
    index index.html;
    try_files $uri $uri/ /index.html;
  }
}
```

> SSR is served at `/`, API at `/api`, CSR static at `/dashboard`.

---

### 5. 🧱 `docker-compose.prod.yml`

```yaml
version: '3.8'

services:
  api:
    build:
      context: .
      dockerfile: Dockerfile.api
    ports:
      - "5000:5000"
    restart: always

  ssr:
    build:
      context: .
      dockerfile: Dockerfile.ssr
    ports:
      - "4000:4000"
    restart: always

  csr:
    build:
      context: .
      dockerfile: Dockerfile.csr
    restart: always

  nginx:
    image: nginx:alpine
    ports:
      - "80:80"
    volumes:
      - ./nginx/default.conf:/etc/nginx/conf.d/default.conf
    depends_on:
      - api
      - ssr
      - csr
    restart: always
```

---

## 🚀 Build & Run in Production

```bash
# 1. Publish .NET API
dotnet publish -c Release -o backend/out

# 2. Build and deploy all
docker compose -f docker-compose.prod.yml up -d --build
```

---

## 🛠 Tips for Production

- Use `docker cp` or shared volume to persist logs
- Use HTTPS with Nginx or put behind a reverse proxy like Caddy, Traefik, or Cloudflare Tunnel
- Add health checks in `docker-compose.yml`
- Set up CI/CD to run these steps

---

## ✅ Summary

| App         | Type     | Port | Dockerfile        | Served From |
|-------------|----------|------|--------------------|--------------|
| .NET API    | Backend  | 5000 | Dockerfile.api     | /api         |
| Angular SSR | Frontend | 4000 | Dockerfile.ssr     | /            |
| Angular CSR | Static   | —    | Dockerfile.csr     | /dashboard   |
| Nginx       | Proxy    | 80   | nginx/default.conf | public       |

---

Let me know if you want:
- SSL (HTTPS) config
- Auto-deploy with GitHub Actions
- `.env` injection and secrets handling
