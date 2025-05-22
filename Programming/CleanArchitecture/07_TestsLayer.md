# 🧪 Testing Strategy – ca-template

This document outlines the testing layers and folder structure for the `ca-template` project, based on Clean Architecture with modular Web3 support.

---

## 📁 Test Project Structure

```plaintext
Tests/
├── Unit/
│   ├── Domain/
│   └── Application/
├── Integration/
│   ├── Infrastructure/
│   └── Application/
├── E2E/
│   └── WebApi/
```

---

## 🧪 Test Types

### ✅ Unit Tests
- Test **pure logic** in isolation
- No external dependencies (DB, network, HTTP)

#### Examples:
- `Domain`: value objects, aggregates, enums
- `Application`: service logic using mocked interfaces

---

### ✅ Integration Tests
- Test real connections to external systems (Mongo, Postgres, etc.)
- Verifies wiring, data flow, DB mappings

#### Examples:
- Mongo/Postgres repository behavior
- Application services using real implementations

> Consider using [Testcontainers](https://github.com/testcontainers/testcontainers-dotnet) for real DBs in CI

---

### ✅ E2E Tests (End-to-End)
- Simulates actual HTTP requests to your `WebApi`
- Uses `WebApplicationFactory<T>` or `TestServer`

#### Covers:
- Auth endpoints
- Project/escrow flows
- Middleware and filters

---

## 🔖 Test Naming & Convention

| Layer       | Convention               |
|-------------|--------------------------|
| Unit        | `*Tests.cs`              |
| Integration | `[Trait("Category", "Integration")]` |
| E2E         | `[Trait("Category", "E2E")]` or `[Collection("WebApi")]` |

---

## ✅ Commands

```bash
# Run all tests
dotnet test

# Run only E2E
dotnet test --filter "Category=E2E"

# Run only unit tests
dotnet test --filter "FullyQualifiedName~Tests.Unit"
```

---

## 🚀 Future Areas

- `Tests/Web3/` for smart contract services
- `Tests/Redis/` if caching/session gets added
- Load/performance tests (via k6 or Locust)

---

## 🧼 Best Practices

- Keep test logic side-effect-free unless it's intentional (e.g., DB)
- Clean test DBs before/after each run
- Assert business behavior, not just state
- Mirror production code structure in test folders (per module)

---

**Status:** ✅ Structure ready • 🧪 Tests to be added module-by-module  
**Last updated:** {{date:YYYY-MM-DD}}
