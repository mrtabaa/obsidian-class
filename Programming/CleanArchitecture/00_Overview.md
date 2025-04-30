# Clean Architecture Overview

Clean Architecture separates an application into layers to enforce clear boundaries between business logic and technical concerns.

**Layer Order (innermost to outermost):**
1. Domain
2. Application
3. Infrastructure
4. Presentation

**Dependency Rule:** 
- Dependencies point **inward**.
- Outer layers depend on inner ones — never the reverse.
