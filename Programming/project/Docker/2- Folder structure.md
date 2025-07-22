```
hallboard/
├── backend/                     # .NET 9 API
│   └── Dockerfile
├── frontend/
│   └── apps/
│       ├── dashboard/           # Angular CSR
│       │   └── Dockerfile.csr
│       └── landing/             # Angular SSR
│           └── Dockerfile.ssr
├── docker-compose.yml           # Dev mode
├── docker-compose.prod.yml      # Production
├── nginx/
│   └── default.conf             # Nginx reverse proxy (prod only)
```