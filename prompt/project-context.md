---
## S1 — IDENTITY

| Field               | Value                                               |
|---------------------|-----------------------------------------------------|
| Name                |                                                     |
| Codename / Slug     |                                                     |
| Blueprint Version   | YYYY-MM-DD-v1                                       |
| Blueprint Changelog | YYYY-MM-DD: initial setup                           |
| Type                | (Web App / Bot / Mobile / Desktop / CLI / Script)   |
| One-line Goal       |                                                     |
| Core Problem        |                                                     |
| Target Users        |                                                     |
| Business Model      | (SaaS / Freemium / One-time / Internal Tool / OSS)  |
| Stage               | (Idea / Prototype / MVP / Beta / Production)        |
| Priority            | (High / Medium / Low)                               |
| v1.0 Deadline       |                                                     |
| Next Milestone      |                                                     |

**Full Description:**
[2–4 sentences describing what the product does and why it exists.]


---
## S2 — DOMAIN GLOSSARY

| Term  | Exact meaning in THIS project (not the generic meaning) |
|-------|---------------------------------------------------------|
| "..." |                                                         |
| "..." |                                                         |


---
## S3 — TECH STACK

### Languages
- **Primary:**
- **Secondary:**
- **Scripting / Tooling:**

### Frontend
- **Framework + version:**
- **UI Component Library:**
- **Styling:**
- **State Management:**
- **Data Fetching:**
- **Form Handling:**
- **Routing:**
- **Charts / Visualization:**
- **Animation:**

### Backend
- **Framework + version:**
- **Runtime:**
- **API Style:** (REST / GraphQL / tRPC / gRPC / WebSocket)
- **API Versioning:**
- **Realtime:**
- **Background Jobs / Queues:**
- **Caching Layer:**
- **Search Engine:**

### Database
- **Primary DB + version:**
- **Secondary DB:**
- **ORM / Query Builder:**
- **Migration Tool:**
- **Schema Approach:** (Code-first / DB-first / Migration files)

### External Services
- **Auth Provider:**
- **File Storage:**
- **Email Service:**
- **SMS / OTP:**
- **Payment Gateway:**
- **Push Notifications:**
- **Maps / Geo:**
- **Other 3rd Party APIs:**

### AI / ML
- **AI APIs:**
- **ML Framework:**
- **Vector DB:**
- **Embeddings Model:**


---
## S4 — ARCHITECTURE

⚠️  For each field below: choose ONE value, delete the rest.

- **Overall Pattern:**       (Monolith / Microservices / Serverless / Modular Monolith)
- **Design Pattern:**        (MVC / MVVM / Clean Architecture / Hexagonal / Repository)
- **Service Communication:** (REST / Event-Driven / Message Queue / Direct calls)
- **Frontend Architecture:** (CSR / SSR / SSG / ISR / Hybrid)
- **Component Strategy:**    (Atomic Design / Feature-Sliced / Page-Based)
- **Backend Architecture:**  (Layered / Repository / Service Layer / CQRS)
- **Dependency Injection:**  (Yes — tool: [...] / No)
- **Monorepo vs Polyrepo:**


---
## S5 — FILE & FOLDER STRUCTURE

```
project-root/
├── (paste your actual folder tree here)
├── folder-name/  → one-line purpose note
└── ...
```


---
## S6 — CODING STANDARDS

### General Rules

| Rule                  | Value                              |
|-----------------------|------------------------------------|
| Paradigm              | (OOP / Functional / Mixed)         |
| Strict Typing         | (Yes — enforced / Partial / No)    |
| Immutability          | (Enforced / Preferred / No)        |
| Max Function Length   | [N] lines                          |
| Max File Length       | [N] lines                          |
| Single Responsibility | (Strict / Pragmatic)               |
| DRY Policy            | (Strict / Pragmatic)               |

### Naming Conventions

⚠️  Reference conventions below are TypeScript/JavaScript.
    If primary language differs, adapt names and examples accordingly.

| Element           | Convention    | Example               |
|-------------------|---------------|-----------------------|
| Variables         | camelCase     | `userName`            |
| Constants         | UPPER_SNAKE   | `MAX_RETRY_COUNT`     |
| Functions         | camelCase     | `getUserById`         |
| Classes           | PascalCase    | `UserService`         |
| Interfaces/Types  | PascalCase    | `UserProfile`         |
| Files             | kebab-case    | `user-service.ts`     |
| Folders           | kebab-case    | `auth-module/`        |
| DB Tables         | snake_case    | `user_sessions`       |
| DB Columns        | snake_case    | `created_at`          |
| API Endpoints     | kebab-case    | `/api/user-profile`   |
| Components        | PascalCase    | `UserCard.tsx`        |
| CSS Classes       | kebab-case    | `btn-primary`         |
| Enums             | PascalCase    | `UserRole.Admin`      |
| Env Variables     | UPPER_SNAKE   | `DATABASE_URL`        |

### Import Order
1. Standard library / built-ins
2. External packages (node_modules / pub.dev / PyPI)
3. Internal absolute imports (via path aliases)
4. Relative imports (`./` or `../`)

- **Path Aliases:** (e.g. `@/` maps to `src/` / None)
- **Barrel Exports:** (Yes — `index.ts` per folder / No)

### Async & Error Handling

| Rule               | Value                                              |
|--------------------|---------------------------------------------------|
| Async Approach     | (async/await / Promises / RxJS / Dart Futures)    |
| Error Strategy     | (try-catch / Result<T,E> pattern / Custom classes)|
| Error Logging      | (tool + levels: error / warn / info / debug)      |
| Silent Errors      | NEVER — always log or rethrow                     |

**Custom Error Classes:**

```
AppError(message, code, statusCode)
├── ValidationError(message, fields[])
├── NotFoundError(message, resource)
├── UnauthorizedError(message)
└── (add yours here)
```

### Comments & Documentation
- **Comment Style:** (JSDoc / Python Docstring / Inline-only)
- **When to Comment:** (Complex logic only / All public methods)
- **TODO Format:** `// TODO(owner): description — TASK-XXX`
- **README:** (Required per service / Top-level only / None)

### Security Rules

| Rule                | Approach                                                 |
|---------------------|----------------------------------------------------------|
| Input Validation    | (Zod / Joi / Pydantic / manual)                          |
| SQL Injection       | (ORM only / Parameterized queries — never string concat) |
| Auth Checks         | (middleware / decorator / manual per route)              |
| Sensitive Data      | Never log. Always hash passwords. Encrypt at rest.       |
| CORS Policy         | (allowed origins list)                                   |
| Rate Limiting       | (tool + default: e.g. 100 req/min per IP)                |
| Secrets             | Always from ENV — never hardcoded, never committed       |
| Raw SQL Permitted   | (Yes — only in: [list specific cases] / No)              |


---
## S7 — DATABASE SCHEMA

- **DB Dialect:** (PostgreSQL 16 / MySQL 8.0 / SQLite 3 / MSSQL / MongoDB)

### Tables

```
TABLE: your_table_name
  column_name  TYPE  CONSTRAINTS

TABLE: (add more here)
  ...
```

### Relationships
- (define your actual relationships here)

### Indexes
- (define your actual indexes here)

### Schema Policies

| Policy        | Value                                                  |
|---------------|--------------------------------------------------------|
| Soft Delete   | (Yes — `deleted_at TIMESTAMPTZ NULL` / No)             |
| Audit Log     | (Yes — `audit_logs` table / No)                        |
| Timestamps    | `created_at` + `updated_at` on every table             |
| Multi-tenancy | (Yes — `tenant_id UUID NOT NULL` on all tables / No)   |
| Primary Keys  | (UUID / BIGSERIAL / CUID)                              |


---
## S8 — API CONTRACT

- **Base URL:** (e.g. `/api/v1`)
- **Auth Header:** `Authorization: Bearer <access_token>`
- **Content-Type:** `application/json`
- **Pagination Style:** (offset / cursor)
- **Max Page Size:** [N]
- **Webhooks:** (Yes — describe payload / No)
- **API Docs Tool:** (Swagger UI at `/api/docs` / Postman / None)

**Success Response:**
```json
{
  "success": true,
  "data": {},
  "message": "OK"
}
```

**Error Response:**
```json
{
  "success": false,
  "error": {
    "code": "ERR_VALIDATION",
    "message": "Human-readable description",
    "details": [
      { "field": "email", "message": "Invalid email format" }
    ]
  }
}
```

**Paginated List — Offset Style** (delete if using cursor):
```json
{
  "success": true,
  "data": {
    "items": [],
    "total": 100,
    "page": 1,
    "limit": 20,
    "hasNext": true,
    "hasPrev": false
  }
}
```

**Paginated List — Cursor Style** (delete if using offset):
⚠️  Delete the pagination format block NOT being used.
    If both blocks remain, AI treats this as EMPTY field.

```json
{
  "success": true,
  "data": {
    "items": [],
    "nextCursor": "TOKEN_abc123",
    "prevCursor": null,
    "hasNext": true,
    "limit": 20
  }
}
```


---
## S9 — AUTH & AUTHORIZATION

- **Auth Flow:** (JWT / OAuth2 / Session-based / Passkey)
- **Token Strategy:** (Access + Refresh pair / Single long-lived token)
- **Access Token Expiry:** (e.g. 15 minutes)
- **Refresh Token Expiry:** (e.g. 30 days)
- **Refresh Token Storage:** (HttpOnly cookie / Redis / DB table)
- **Token Rotation on Refresh:** (Yes — invalidate old token / No)

| Role  | Can do                              |
|-------|-------------------------------------|
| admin | Full access to all resources        |
| user  | CRUD on own resources only          |
| guest | Read-only on public resources       |

- **Permission Check:** (Middleware / RBAC decorator / Manual per route)
- **Password Policy:** (min 8 chars, 1 uppercase, 1 number, 1 special)
- **2FA:** (Yes — TOTP / SMS / Email OTP / No)
- **Account Lockout:** (Yes — after N failed attempts / No)


---
## S10 — DEVOPS & DEPLOYMENT

- **Environments:** dev / staging / production
- **Containerization:** (Docker + Docker Compose / Docker only / None)
- **Hosting:**
- **Reverse Proxy:** (Nginx / Caddy / Traefik / None)
- **CI/CD:** (GitHub Actions / GitLab CI / Jenkins / None)
- **Package Manager:** (npm / yarn / pnpm / bun / pip / pub)
- **Git Workflow:** (GitFlow / Trunk-based / Feature branches)
- **Branch Naming:** `type/TASK-N-short-description`
  - Types: `feature/` `bugfix/` `hotfix/` `refactor/` `chore/`
- **Commit Convention:** Conventional Commits
  - Format: `type(scope): description`
  - Types: `feat` `fix` `refactor` `perf` `test` `chore` `docs`
- **PR Requirements:** (reviews needed / CI must pass / linked task ID)

**ENV Variables:**

```
DATABASE_URL
JWT_SECRET
```


---
## S11 — TESTING STRATEGY

- **Philosophy:** (TDD / Test-after / Critical paths only)
- **Unit Test Tool:**
- **Integration Test Tool:**
- **E2E Test Tool:**
- **Coverage Target:** [N]%
- **Test File Location:** (`__tests__/` next to source / `tests/` at root)
- **Mocking Strategy:** (Jest mocks / unittest.mock / MSW for HTTP)
- **CI Enforcement:** (Must pass before merge / Advisory only)

Always test:
- All auth flows (login, refresh, logout)
- All DB write operations
- All external API integrations
- All background jobs


---
## S12 — PERFORMANCE RULES

- **Max Page Size:** same value as defined in API CONTRACT section
- **N+1 Queries:** FORBIDDEN — always use eager loading or JOIN
- **No Full Table Scans:** DB index required before any WHERE/JOIN/ORDER BY
- **Lazy Loading:** (Yes — only in: [...] / No)

Operations that MUST always be background jobs:
- Any outgoing HTTP / API call to an external service
- File read / write / process > 500 KB
- Sending email or SMS
- DB query with no index (full table scan)
- Any operation that touches > 10,000 rows at once
- Report generation or data export of any kind
- Image resizing, video processing, or audio processing
- Webhook delivery with retry logic


---
## S13 — DECISIONS LOG

- **WHY [Tech A] over [Tech B]:**
- **WHY this architecture:**
- **WHY this DB schema approach:**
- **WHY this auth strategy:**

**Rejected Approaches — NEVER suggest these again:**
- ❌ [Approach] — Reason: [why it was rejected]
- ❌ [Approach] — Reason: [why it was rejected]

**Special Constraints / Client Requirements:**


---
## CURRENT STATE

**Last Task ID:** TASK-000
**Last BUG Number:** BUG-000
**Last DEBT Number:** DEBT-000
**Last Updated:** YYYY-MM-DD
**Project Status:** FRESH START — no features implemented yet.

### ✅ COMPLETED
- Nothing completed yet.

### 🔄 IN PROGRESS
- Nothing in progress yet.

### ⏳ BACKLOG
- No backlog items yet.

### 🐛 KNOWN BUGS
- No known bugs yet.

### ⚠️ TECH DEBT
- No tech debt yet.

### 🔒 OFF-LIMITS
- Nothing is off-limits yet.