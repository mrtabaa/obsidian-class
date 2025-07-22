**🐳 Final Docker Setup (Dev + Prod) – Angular SSR/CSR + .NET + MongoDB**

## ✅ Backend – .NET 9 (Multi-stage Production Ready)

`backend/Dockerfile`:

```Dockerfile
# Stage 1: Build
FROM mcr.microsoft.com/dotnet/sdk:9.0 AS build
WORKDIR /src
COPY . .
RUN dotnet publish -c Release -o /app/publish

# Stage 2: Runtime
FROM mcr.microsoft.com/dotnet/aspnet:9.0 AS runtime
WORKDIR /app
COPY --from=build /app/publish .
EXPOSE 80
ENTRYPOINT ["dotnet", "YourApp.dll"]
```

➡️ Replace `"YourApp.dll"` with your actual compiled DLL.

---

## ✅ Angular SSR – `frontend/apps/landing/Dockerfile.ssr`

```Dockerfile
FROM node:20 AS build
WORKDIR /app
COPY . .
RUN npm install && npm run build:ssr

FROM node:20 AS runtime
WORKDIR /app
COPY --from=build /app/dist/landing/browser ./browser
COPY --from=build /app/dist/landing/server ./server
EXPOSE 4000
CMD ["node", "server/main.js"]
```

➡️ Make sure `angular.json` for SSR app outputs to `dist/landing`.

---

## ✅ Angular CSR – `frontend/apps/dashboard/Dockerfile.csr`

```Dockerfile
FROM node:20 AS build
WORKDIR /app
COPY . .
RUN npm install && npm run build

FROM nginx:alpine
COPY --from=build /app/dist/dashboard /usr/share/nginx/html
```

➡️ CSR output should be under `dist/dashboard`.

---

## ✅ Dev Mode – `docker-compose.yml`

```yaml
version: '3.8'

services:
  backend:
    build: ./backend
    ports:
      - "5000:80"
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ConnectionStrings__Mongo=mongodb://mongo:27017/yourdb
    depends_on:
      - mongo

  landing:
    build:
      context: ./frontend/apps/landing
      dockerfile: Dockerfile.ssr
    ports:
      - "4000:4000"
    depends_on:
      - backend

  dashboard:
    build:
      context: ./frontend/apps/dashboard
      dockerfile: Dockerfile.csr
    ports:
      - "4200:80"
    depends_on:
      - backend

  mongo:
    image: mongo:7
    volumes:
      - mongo_data:/data/db

volumes:
  mongo_data:
```

---

## 🚀 Production – `docker-compose.prod.yml`

```yaml
version: '3.8'

services:
  backend:
    build: ./backend
    ports:
      - "5000:80"
    environment:
      - ASPNETCORE_ENVIRONMENT=Production
      - ConnectionStrings__Mongo=mongodb://mongo:27017/yourdb
    depends_on:
      - mongo

  landing:
    build:
      context: ./frontend/apps/landing
      dockerfile: Dockerfile.ssr
    ports:
      - "4000:4000"
    depends_on:
      - backend

  dashboard:
    build:
      context: ./frontend/apps/dashboard
      dockerfile: Dockerfile.csr
    depends_on:
      - backend

  mongo:
    image: mongo:7
    volumes:
      - mongo_data:/data/db

  nginx:
    image: nginx:alpine
    ports:
      - "80:80"
    volumes:
      - ./nginx/default.conf:/etc/nginx/conf.d/default.conf
    depends_on:
      - backend
      - landing
      - dashboard

volumes:
  mongo_data:
```

---

## 🌐 Nginx Reverse Proxy – `nginx/default.conf`

```nginx
server {
  listen 80;

  location / {
    proxy_pass http://landing:4000;
    proxy_http_version 1.1;
    proxy_set_header Host $host;
    proxy_set_header X-Real-IP $remote_addr;
  }

  location /api {
    rewrite ^/api(/.*)$ $1 break;
    proxy_pass http://backend:80;
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

---

## 🧪 Development

```bash
docker compose up --build
```

Access:
- API: http://localhost:5000
- Angular SSR: http://localhost:4000
- Angular CSR: http://localhost:4200/dashboard

---

## 🚀 Production

```bash
docker compose -f docker-compose.prod.yml up -d --build
```

Visit:
- Everything via Nginx: http://your-server-ip

---

## 🧼 Optional `.dockerignore` for backend

Create `backend/.dockerignore`:

```
bin/
obj/
.vscode/
*.user
*.suo
*.csproj.user
Dockerfile*
docker-compose*
```

---

Let me know if you want:
- GitHub Actions workflow for CI/CD
- HTTPS with Let's Encrypt + Nginx
- `Makefile` for simplified build/run commands
