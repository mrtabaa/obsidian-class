# 🔗 Layer Reference Order (Clean Architecture)

This file explains **which layers are allowed to reference which** in the project Clean Architecture. Following this order enforces the **Dependency Rule** and maintains a clean separation of concerns.

---

## 🔁 General Rule

> **Dependencies always point inward.**  
> Outer layers can reference inner layers, but **inner layers should never know about outer layers**.

---

## 🧭 Reference Flow Diagram

```
Presentation
   │
   ▼
Application
   │
   ▼
Domain
```

**Plus supporting layers:**
```
       ┌──────────────┐
       │   Contracts  │◄────────┐
       └──────────────┘         │
                                │
       ┌──────────────┐         │
       │    Shared    │◄────┐   │
       └──────────────┘     │   │
                            │   │
┌──────────────┐    ┌──────────────┐
│   WebApi     │────►  Application │
└──────────────┘    └──────────────┘
        │                     ▲
        ▼                     │
┌──────────────┐    ┌──────────────┐
│Infrastructure│────►   Domain     │
└──────────────┘    └──────────────┘

```

---

## ✅ Allowed References

| From Layer         | Allowed to Reference                           |
| ------------------ | ---------------------------------------------- |
| **Presentation**   | Infrastructure, Application, Contracts, Shared |
| **Application**    | Domain, Contracts (DTOs), Shared (optional)    |
| **Contracts**      | (No references — pure DTO layer)               |
| **Infrastructure** | Domain, Shared                                 |
| **Shared**         | (No references — utility only)                 |
| **Domain**         | Shared (optional)                              |

---

## ❌ Disallowed Examples

- ❌ Domain referencing Application or Infrastructure
- ❌ Contracts referencing Domain or Infrastructure
- ❌ Presentation using Infrastructure directly
- ❌ Application using Controllers or ASP.NET-specific types

---

## ✅ Summary

- 📦 **Contracts** = Stable DTOs for APIs. Referenced by outer layers only.
- 🧰 **Shared** = Cross-cutting helpers. Used anywhere, but should not depend on business logic.
- 🧱 **Domain** = The heart. Should remain isolated and framework-agnostic.

---
