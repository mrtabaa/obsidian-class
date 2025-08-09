## 🧱 Angular 19 Folder Structure – `dashboard` App (Clean Architecture Inspired)

NOTE: 
Each feature has its own dedicated root. See [[Routes Management]]

```plaintext
frontend/
└── src/
    └── app/
        ├── features/                      # Application features (use cases)
        │   ├── auth/                      # e.g., login, register
        │   │   ├── login/
        │   │   │   ├── login.component.ts
        │   │   │   ├── login.component.html
        │   │   │   ├── login.component.scss
        │   │   │   └── login.component.spec.ts
        │   │   ├── auth.service.ts
        │   │   └── routes.ts              # Feature-level routing
        │   │
        │   ├── orders/
        │   │   ├── order-list/
        │   │   ├── order-detail/
        │   │   ├── order.service.ts
        │   │   └── routes.ts
        │   │
        │   └── user-panel/
        │       ├── user-panel.component.ts
        │       ├── user-panel.component.html
        │       └── ...
        │
        ├── shared/                        # Reusable UI elements (non-domain specific)
        │   ├── components/
        │   │   ├── footer/
        │   │   ├── navbar/
        │   │   └── ...
        │   ├── directives/
        │   └── pipes/
        │
        ├── core/                          # App-wide logic & services
        │   ├── services/                  # Global services (e.g., ApiService)
        │   ├── guards/
        │   ├── interceptors/
        │   ├── models/
        │   ├── enums/
        │   └── utils/
        │
        ├── app.config.ts                  # Angular 19 bootstrap configuration
        └── app.routes.ts                      # Root-level app routes
```
