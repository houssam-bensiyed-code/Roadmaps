# ⚡ FastAPI Mastery Roadmap — Phase 2: Architectural Thinking

---

## 🟤 PHASE 0: Python Web Foundations — WSGI, ASGI & Raw HTTP
> **Goal:** Understand how Python handles HTTP at the lowest level — so you know exactly what FastAPI abstracts away.
> **Duration:** ~2–3 weeks (focused)

---

### 📦 Module 0.1: How the Web Works (Python Perspective)
- Client-Server Model Recap
- HTTP Request/Response Lifecycle (from Browser to Python Server and Back)
- What is a Web Server vs Application Server
  - Nginx, Apache (Web Servers — Static Content, Reverse Proxy)
  - Gunicorn, Uvicorn, Hypercorn, Daphne (Application Servers — Run Your Python Code)
  - Web Server vs Application Server vs Framework (Three Distinct Layers)
- Python's Role in Web Development (Historical Context)
  - CGI Scripts → WSGI (PEP 3333) → Frameworks (Django, Flask) → ASGI (Async) → FastAPI
  - Why This Evolution Happened (Pain Points at Each Stage)
- The Python Web Stack
  - Client → Nginx (Reverse Proxy) → Gunicorn/Uvicorn (App Server) → Your Framework → Your Code
  - Why You Need Each Layer in Production

### 📦 Module 0.2: WSGI — The Synchronous Foundation
- What is WSGI (Web Server Gateway Interface — PEP 3333)
- WSGI is Just a Specification (A Callable Convention)
- The WSGI Application Interface
  - A WSGI App is a Callable That Takes `environ` and `start_response`
  - `environ` Dictionary (Everything About the HTTP Request)
    - `REQUEST_METHOD`, `PATH_INFO`, `QUERY_STRING`
    - `CONTENT_TYPE`, `CONTENT_LENGTH`
    - `HTTP_*` Headers (Prefixed with `HTTP_`)
    - `wsgi.input` (Request Body Stream)
  - `start_response` Callable (Status Code + Headers)
  - Return Value (Iterable of Bytes — The Response Body)
- Writing a Bare WSGI Application
  - Hello World WSGI App (A Single Function)
  - Reading Query Parameters from `environ`
  - Reading Request Body from `wsgi.input`
  - Setting Response Headers and Status Codes
  - Returning JSON Responses (Manual Serialization with `json.dumps`)
- WSGI Servers
  - `wsgiref.simple_server` (Built-in — Development Only)
  - Gunicorn (Production WSGI Server)
    - Workers, Threads, Worker Classes
    - Pre-Fork Model (How Gunicorn Handles Concurrency)
    - Configuration (`bind`, `workers`, `timeout`)
- WSGI Middleware
  - A Middleware is a WSGI App That Wraps Another WSGI App
  - Writing a Logging Middleware (Log Every Request/Response)
  - Writing an Auth Middleware (Check API Key Before Reaching App)
  - Middleware Chaining (Onion Model — Each Layer Wraps the Next)
  - **💡 This is exactly how Starlette/FastAPI middleware works**
- Pain Points You'll Feel
  - Manual URL routing (`if environ['PATH_INFO'] == '/users':`)
  - Manual method checking (`if environ['REQUEST_METHOD'] == 'GET':`)
  - Manual request body parsing
  - Manual JSON serialization/deserialization
  - No validation, no dependency injection, no async
  - **These are the exact problems frameworks solve**

### 📦 Module 0.3: ASGI — The Asynchronous Evolution
- Why WSGI Falls Short (No Async, No WebSockets, No HTTP/2)
- What is ASGI (Asynchronous Server Gateway Interface)
- ASGI vs WSGI
  - WSGI: Synchronous Callable → Returns Response
  - ASGI: Async Callable → Receives and Sends Messages
- The ASGI Application Interface
  - An ASGI App is an Async Callable That Takes `scope`, `receive`, `send`
  - `scope` Dictionary (Connection Metadata)
    - `scope['type']` — `'http'`, `'websocket'`, `'lifespan'`
    - `scope['method']`, `scope['path']`, `scope['query_string']`
    - `scope['headers']` (List of Byte Tuples)
  - `receive` Callable (Async — Read Incoming Messages)
    - `{'type': 'http.request', 'body': b'...'}`
  - `send` Callable (Async — Send Outgoing Messages)
    - `{'type': 'http.response.start', 'status': 200, 'headers': [...]}`
    - `{'type': 'http.response.body', 'body': b'...'}`
- Writing a Bare ASGI Application
  - Hello World ASGI App (A Single Async Function)
  - Reading Path and Query Parameters from `scope`
  - Reading Request Body via `receive`
  - Sending JSON Responses via `send` (Two-Step: Start + Body)
  - Handling Different HTTP Methods
- ASGI Servers
  - Uvicorn (Primary ASGI Server)
    - Event Loop (uvloop for Performance)
    - Workers, Configuration
    - `--reload` for Development
  - Hypercorn (HTTP/2, HTTP/3 Support)
  - Daphne (Django Channels — Awareness)
- ASGI Lifespan Events
  - `scope['type'] == 'lifespan'`
  - Startup Events (Initialize DB Pool, Load Config)
  - Shutdown Events (Close Connections, Cleanup)
  - **💡 FastAPI's `lifespan` context manager wraps exactly this**
- ASGI WebSocket Support
  - `scope['type'] == 'websocket'`
  - WebSocket Accept, Receive, Send, Close Messages
  - Full-Duplex Communication
  - **💡 This is how FastAPI WebSocket endpoints work underneath**
- ASGI Middleware
  - Wrapping an ASGI App with Another ASGI App
  - Logging Middleware (Async — Log Request/Response Timing)
  - CORS Middleware (Inject Headers)
  - **💡 Starlette's `CORSMiddleware`, `TrustedHostMiddleware` are ASGI middleware**

### 📦 Module 0.4: Building a REST API with Raw ASGI
- Manual URL Router
  - Parse `scope['path']` and `scope['method']`
  - Route to Handler Functions
  - Path Parameter Extraction (`/users/123` → `user_id = 123`)
- Request Parsing
  - Reading JSON Body via `receive` + `json.loads`
  - Parsing Query Parameters from `scope['query_string']`
  - Header Extraction from `scope['headers']`
- Response Helpers
  - JSON Response Function (Serialize + Set Content-Type)
  - Error Response Function (Status Code + Error Message)
- Building a Simple CRUD API (e.g., Todo List)
  - In-Memory Data Store (Dict)
  - GET, POST, PUT, DELETE Handlers
  - Proper HTTP Status Codes
- Pain Points You'll Feel
  - Verbose routing boilerplate
  - No automatic request validation
  - No automatic serialization/deserialization
  - No dependency injection
  - No automatic API documentation
  - No type safety on request/response
  - **These are exactly what Starlette and FastAPI solve**

### 📦 Module 0.5: Starlette — The Foundation Under FastAPI
- What is Starlette (Lightweight ASGI Framework/Toolkit)
- **FastAPI is Built ON TOP of Starlette** (This is Critical to Understand)
- Starlette Components That FastAPI Inherits
  - `Request` Object (Wraps `scope`, `receive` — Gives You `.json()`, `.query_params`, `.path_params`)
  - `Response` Objects (`JSONResponse`, `HTMLResponse`, `PlainTextResponse`, `StreamingResponse`, `RedirectResponse`)
  - Routing (`Route`, `Router`, `Mount`)
  - Middleware (ASGI Middleware Stack)
  - `WebSocket` Class
  - `BackgroundTask` (Run After Response)
  - `TestClient` (Built on `httpx`)
  - Static Files (`StaticFiles`)
  - Lifespan Management
  - Exception Handlers
- Building a Simple API with Starlette Directly
  - Routes, Request, JSONResponse
  - Middleware Registration
  - Error Handling
- What Starlette Does NOT Have (What FastAPI Adds)
  - No automatic data validation (Pydantic)
  - No automatic serialization (Pydantic)
  - No dependency injection system
  - No automatic OpenAPI/Swagger docs
  - No type-based parameter declaration
  - **FastAPI adds all of these on top of Starlette**

### 📦 Module 0.6: Pydantic — The Validation Engine Under FastAPI
- What is Pydantic (Data Validation Using Python Type Hints)
- **FastAPI Uses Pydantic for ALL Request/Response Validation** (Critical to Understand)
- Pydantic V2 (Rust-Powered Core — Major Performance Improvement)
- Core Concepts
  - `BaseModel` (Define a Schema with Type Hints → Automatic Validation)
  - Field Types (str, int, float, bool, datetime, UUID, etc.)
  - Nested Models (Model Within Model)
  - `Optional[T]`, `Union[T1, T2]`, `list[T]`, `dict[str, T]`
  - Default Values and `Field()` (Constraints: `min_length`, `max_length`, `gt`, `lt`, `pattern`)
  - `@field_validator` (Custom Validation Logic on Individual Fields)
  - `@model_validator` (Cross-Field Validation)
  - `model_dump()` / `model_dump_json()` (Serialization)
  - `model_validate()` / `model_validate_json()` (Deserialization)
  - `ConfigDict` (`from_attributes=True` for ORM Mode, `str_strip_whitespace`, etc.)
- Pydantic Settings (`pydantic-settings`)
  - `BaseSettings` (Load Config from Environment Variables)
  - `.env` File Support
  - Nested Settings
  - **💡 This is how you manage configuration in FastAPI apps**
- Why Pydantic Matters
  - Single Source of Truth for Data Shape
  - Automatic Error Messages (Detailed Validation Errors)
  - Automatic JSON Schema Generation (→ OpenAPI Docs)
  - Runtime Type Safety in a Dynamic Language

### 📦 Module 0.7: Understanding What FastAPI Replaces
> **This is the most important module — connecting raw Python web to FastAPI.**

- **Raw ASGI Routing → FastAPI Decorators**
  - `if scope['path'] == '/users':` → `@app.get("/users")`
  - Manual path parsing → `@app.get("/users/{user_id}")`
- **Manual JSON Parsing → Pydantic `@RequestBody`**
  - `json.loads(body)` + manual validation → `def create(user: UserCreate):`
- **Manual Response Building → Automatic Serialization**
  - `JSONResponse(content=...)` → Return a Pydantic model or dict
- **No Validation → Pydantic Validation**
  - `if not data.get('email'):` → `email: EmailStr`
- **ASGI Middleware → FastAPI/Starlette Middleware**
  - Raw ASGI wrapping → `app.add_middleware(CORSMiddleware, ...)`
- **No Documentation → Auto-Generated OpenAPI/Swagger**
  - Nothing → `/docs` and `/redoc` for free
- **No Dependency Injection → FastAPI `Depends()`**
  - Manual instantiation → `def get_db(): yield session` + `Depends(get_db)`
- **WSGI Sync → ASGI Async**
  - `def handler():` → `async def handler():` with native `await` support
- **Mapping Table**

  | Raw WSGI/ASGI | FastAPI Equivalent |
  |---|---|
  | `environ['REQUEST_METHOD']` | `@app.get`, `@app.post`, etc. |
  | `environ['PATH_INFO']` parsing | `@app.get("/items/{item_id}")` |
  | `environ['QUERY_STRING']` parsing | `item_id: int` parameter with type |
  | `wsgi.input` / `receive()` body | `body: ItemCreate` (Pydantic model) |
  | `start_response('200 OK', headers)` | `return item` (auto 200) or `Response(status_code=...)` |
  | Manual `json.dumps()` | Automatic Pydantic serialization |
  | Manual `if not field:` validation | Pydantic validators, `Field()` constraints |
  | WSGI/ASGI middleware wrapping | `app.add_middleware(...)` |
  | Nothing | `/docs` (Swagger), `/redoc` (auto-generated) |
  | Manual instantiation | `Depends()` dependency injection |
  | `scope['type'] == 'websocket'` | `@app.websocket("/ws")` |
  | ASGI lifespan events | `@asynccontextmanager` lifespan |
  | Gunicorn workers | Uvicorn + Gunicorn (`UvicornWorker`) |

> ### 🛠 Phase 0 Milestone Project: **Mini ASGI Framework**
> Build a bare-bones async web framework on top of raw ASGI:
> - Custom ASGI application with async request routing by URL and HTTP method
> - Custom `@route` decorator (your own!) that maps async functions to URL patterns using introspection
> - Path parameter extraction with type coercion (`/users/{user_id:int}`)
> - Automatic JSON request body parsing and response serialization (using Pydantic for validation)
> - Middleware chain with Logging Middleware + Simple Auth Middleware (API key check)
> - WebSocket echo endpoint (raw ASGI WebSocket handling)
> - Starlette `Request`/`Response` wrappers for comparison
> - Implement a small CRUD API (e.g., Todo list) using YOUR framework
> - Run with Uvicorn
> - Then throw it all away and start Phase 1 with FastAPI
>
> **Why:** You will deeply understand ASGI, routing, middleware, Pydantic, dependency injection, and auto-docs — because you built crude versions yourself. When FastAPI does it, it's no longer magic. **You'll never be the developer who can't debug past the decorators.**

---

### ✅ After Phase 0 — You Understand:
- How HTTP requests flow through WSGI/ASGI servers to your Python code
- What Uvicorn and Gunicorn actually do (and why you need both in production)
- How Starlette provides the ASGI toolkit that FastAPI builds on
- How Pydantic powers all validation and serialization in FastAPI
- Why WSGI gave way to ASGI (async, WebSockets, HTTP/2)
- The mapping between raw ASGI and FastAPI decorators
- Why middleware matters (and how FastAPI middleware is just ASGI middleware)
- **You're not learning FastAPI — you're learning what FastAPI automated**

---
---

## 🟢 PHASE 1: FastAPI Core
> **Goal:** Deeply understand FastAPI's architecture and build professional REST APIs.
> **Duration:** ~3–4 weeks

---

### 📦 Module 1.1: FastAPI Fundamentals
- What FastAPI Solves (Speed, Validation, Docs, Async — All in One)
- FastAPI's Architecture Stack (Starlette + Pydantic + Python Type Hints)
- Installation and Project Setup
- Application Instance (`FastAPI()`)
- Running with Uvicorn (Development vs Production)
- Project Structure Best Practices
  - Flat Structure for Small Apps
  - Package Structure for Larger Apps (routers, models, schemas, services, core)
- `APIRouter` (Modular Route Organization — Like Blueprints)
  - Prefixes, Tags, Dependencies per Router
  - Including Routers in the Main App

### 📦 Module 1.2: Path Operations & Parameters
- Path Operation Decorators (`@app.get`, `@app.post`, `@app.put`, `@app.patch`, `@app.delete`)
- Path Parameters (Type-Annotated, Auto-Validated)
  - `Path()` Function (Metadata, Validation Constraints)
- Query Parameters (Optional, Required, Defaults)
  - `Query()` Function (Aliases, Deprecation, Regex Patterns)
- Request Body with Pydantic Models
  - `Body()` Function (Embed, Examples)
  - Multiple Body Parameters
  - Nested Models
- Request Headers (`Header()`)
- Cookie Parameters (`Cookie()`)
- Form Data (`Form()`) and File Uploads (`File()`, `UploadFile`)
- Parameter Declaration Order (How FastAPI Decides: Path vs Query vs Body)
- Mixed Parameters (Path + Query + Body in One Endpoint)

### 📦 Module 1.3: Response Handling
- Return Types and Response Models (`response_model`)
- `response_model_include` / `response_model_exclude`
- Response Status Codes (`status_code`)
- `Response` Class Direct Usage
- `JSONResponse`, `HTMLResponse`, `PlainTextResponse`, `RedirectResponse`
- `StreamingResponse` (Large Files, Server-Sent Events)
- `FileResponse` (File Downloads)
- Response Headers and Cookies
- Custom Response Classes

### 📦 Module 1.4: Pydantic Schemas — Deep Integration
- Request Schemas vs Response Schemas (Create, Read, Update Patterns)
  - `UserCreate`, `UserRead`, `UserUpdate` Separation
- Schema Inheritance (Base → Create → Read)
- `Optional` Fields for Partial Updates (PATCH)
- Computed Fields (`@computed_field`)
- Pydantic `model_config` with FastAPI
  - `from_attributes = True` (ORM Mode)
  - `json_schema_extra` (OpenAPI Examples)
- Custom Validators in API Context
  - `@field_validator` for Business Rules
  - `@model_validator` for Cross-Field Rules
- Discriminated Unions (Polymorphic Request Bodies)
- Generic Models (`Generic[T]` with Pydantic for Paginated Responses)

### 📦 Module 1.5: Dependency Injection System
- What is Dependency Injection in FastAPI (`Depends()`)
- Function Dependencies (Simple Callables)
- Class Dependencies (Callable Classes)
- Nested Dependencies (Dependencies That Depend on Other Dependencies)
- Shared Dependencies (Same Instance per Request)
- Dependencies with `yield` (Setup + Teardown — Like Context Managers)
  - Database Session Management
  - Resource Cleanup
- Global Dependencies (App-Level, Router-Level)
- Dependencies for Authentication and Authorization
- Overriding Dependencies in Tests
- **💡 FastAPI's DI is simple but powerful — no container, just functions**

### 📦 Module 1.6: Error Handling & Validation
- `HTTPException` (Built-in Error Raising)
- Custom Exception Classes
- Exception Handlers (`@app.exception_handler`)
- Validation Error Handling (Pydantic Validation Errors → 422 Response)
- Custom Validation Error Responses
- Problem Details Format (RFC 7807 / RFC 9457)
- Request Validation Errors vs Application Errors vs Server Errors
- Global Error Handling Strategy

### 📦 Module 1.7: Middleware & Lifecycle
- Middleware Concept in FastAPI (ASGI Middleware Stack)
- Built-in Middleware
  - `CORSMiddleware`
  - `TrustedHostMiddleware`
  - `GZipMiddleware`
  - `HTTPSRedirectMiddleware`
- Custom Middleware (`@app.middleware("http")`)
  - Request/Response Logging
  - Request Timing
  - Custom Headers
- Pure ASGI Middleware (When `@app.middleware` Isn't Enough)
- Middleware Ordering (First Added = Outermost Layer)
- Application Lifespan Events
  - `lifespan` Async Context Manager (Modern Approach)
  - Startup Logic (DB Connection Pool, Cache Warmup, Config Loading)
  - Shutdown Logic (Close Connections, Flush Buffers)

### 📦 Module 1.8: Background Tasks & Async
- `BackgroundTasks` (Run After Response is Sent)
- When to Use BackgroundTasks vs Task Queues
- `async def` vs `def` Endpoints (When Each is Appropriate)
- Running Sync Code in Async Context (`run_in_executor`)
- Async Database Drivers vs Sync Drivers
- Concurrency vs Parallelism in FastAPI
- Event Loop Blocking — Common Mistakes

### 📦 Module 1.9: OpenAPI & Documentation
- Auto-Generated OpenAPI Schema (`/openapi.json`)
- Swagger UI (`/docs`) and ReDoc (`/redoc`)
- Customizing OpenAPI Schema
  - Tags and Tag Metadata
  - Operation Descriptions and Summaries
  - Request/Response Examples
  - Deprecated Endpoints
- Custom OpenAPI Schema Generation
- API-First Design with FastAPI (Generate Pydantic Models from OpenAPI Spec)

> ### 🛠 Phase 1 Milestone Project: **Task Management REST API**
> Full CRUD REST API for projects, tasks, and users. Pydantic schemas for create/read/update separation. Dependency injection for shared services. Global error handling with RFC 7807 problem details. Background tasks for notifications. Middleware for request logging and timing. Multiple routers with tags. Full OpenAPI documentation with examples. Profile-based config with `pydantic-settings` (dev/prod). Focus on clean layered architecture.

---

## 🔵 PHASE 2: Data Access & Persistence
> **Goal:** Master async database access with SQLAlchemy, advanced querying, performance tuning, and caching.

---

### 📦 Module 2.1: Async SQLAlchemy with FastAPI
- SQLAlchemy 2.0 Async Engine (`create_async_engine`)
- Async Session (`AsyncSession`, `async_sessionmaker`)
- Session Dependency with `yield` (Per-Request Session Lifecycle)
- Declarative Models with `MappedAsOf` / `DeclarativeBase` (Modern 2.0 Style)
- Mapped Columns (`Mapped[int]`, `mapped_column()`)
- Table Configuration (`__tablename__`, `__table_args__`)
- Column Types and Constraints

### 📦 Module 2.2: Entity Modeling & Relationships
- Entity Lifecycle (Transient, Pending, Persistent, Detached, Deleted)
- Relationships Deep Dive
  - `relationship()` with `Mapped[list["Child"]]`
  - One-to-One (Unique Foreign Key, `uselist=False`)
  - One-to-Many / Many-to-One (Bidirectional, `back_populates`)
  - Many-to-Many (Association Table, Association Object with Extra Data)
- Cascade Types (`save-update`, `merge`, `delete`, `all`, `delete-orphan`)
- Eager vs Lazy Loading
  - Lazy Loading in Async (The `greenlet` Problem — `lazy="raise"` by Default)
  - `selectinload()`, `joinedload()`, `subqueryload()`
  - The N+1 Problem (Detection & Solutions in Async Context)
- Inheritance Strategies (Single Table, Joined, Concrete — Awareness)
- Composite Types (`composite()`)
- Hybrid Properties (`@hybrid_property`)

### 📦 Module 2.3: CRUD Operations & Querying
- Select API (`select()`, `where()`, `filter_by()`)
- Insert, Update, Delete Operations
- Joins (`join()`, `outerjoin()`)
- Aggregations (`func.count()`, `func.sum()`, `func.avg()`)
- Grouping (`group_by()`, `having()`)
- Subqueries and CTEs (`subquery()`, `cte()`)
- `exists()` and `any_()`
- Ordering, Limiting, Offset
- Pagination
  - Offset-Based (`limit`/`offset`)
  - Keyset/Cursor Pagination (Performance for Large Datasets)
  - Generic Paginated Response Schema with Pydantic
- Dynamic Query Building (Conditional Filters)
- Raw SQL When Needed (`text()`)

### 📦 Module 2.4: Transactions & Performance
- Transaction Management
  - `session.begin()`, `session.commit()`, `session.rollback()`
  - Nested Transactions (`session.begin_nested()` — Savepoints)
  - Read-Only Optimization (`execution_options(readonly=True)`)
- Connection Pooling
  - Async Pool Configuration (`pool_size`, `max_overflow`, `pool_timeout`, `pool_recycle`)
  - Pool Events and Monitoring
- Query Performance
  - Indexing Strategies (Align with Phase 1 DB Knowledge)
  - `EXPLAIN ANALYZE` in Practice
  - DTO Projections for Read-Heavy Queries (Select Specific Columns)
  - Batch Operations (`executemany`, Bulk Inserts)
  - Avoiding ORM Overhead for Bulk Reads
  - Pagination Performance (Keyset vs Offset)

### 📦 Module 2.5: Database Migrations — Alembic
- Alembic Setup and Configuration with Async
- Auto-Generating Migrations (`alembic revision --autogenerate`)
- Manual Migration Scripts
- Migration Naming Conventions
- Upgrading and Downgrading
- Data Migrations (Not Just Schema)
- Multiple Heads and Merge Migrations
- Zero-Downtime Migration Strategies (Expand/Contract Pattern)
  - Add Column → Backfill → Switch Code → Drop Old Column
- Running Migrations in CI/CD
- Testing Migrations

### 📦 Module 2.6: Caching with Redis
- `redis.asyncio` (Async Redis Client for Python)
- Redis as Dependency in FastAPI (`Depends()`)
- Spring Cache-Like Patterns in Python
  - Cache-Aside (Application-Level)
  - Write-Through, Write-Behind Concepts
  - Read-Through Concepts
- Building a Caching Decorator/Dependency for FastAPI
- TTL Strategies and Cache Invalidation
- Redis Data Structures in Practice (String, Hash, List, Set, Sorted Set)
- Session Storage with Redis (Awareness)
- Distributed Locking with Redis (Awareness)

### 📦 Module 2.7: Beyond SQL — Other Data Access
- Elasticsearch with Python (`elasticsearch-py`, `elastic-transport`)
  - Async Client
  - Full-Text Search Use Cases
  - Indexing and Querying Documents
  - Integration with FastAPI
- MongoDB with Motor (Async MongoDB Driver)
  - Documents, Collections, CRUD
  - Integration with Pydantic (via Beanie ODM)
- Choosing the Right Storage for Each Use Case

> ### 🛠 Phase 2 Milestone Project: **E-Commerce Product Catalog Service**
> Product catalog with categories, tags, variants, and reviews. Async SQLAlchemy 2.0 with complex relationships and eager loading strategies. Alembic migrations with zero-downtime approach. Redis caching layer for hot products and category listings. Elasticsearch for full-text product search with autocomplete. Keyset and offset pagination. Query performance benchmarks with EXPLAIN ANALYZE. Auditing (created_at, updated_at) with SQLAlchemy events.

---

## 🟡 PHASE 3: Security
> **Goal:** Implement production-grade security — authentication, authorization, OAuth2, and application hardening.

---

### 📦 Module 3.1: FastAPI Security Fundamentals
- FastAPI's Security Utilities (`fastapi.security` Module)
- Security Schemes (How FastAPI Integrates Security into OpenAPI)
  - `OAuth2PasswordBearer` (Token URL, Scopes)
  - `OAuth2PasswordRequestForm`
  - `HTTPBearer`, `HTTPBasic`
  - `APIKeyHeader`, `APIKeyQuery`, `APIKeyCookie`
- Authentication vs Authorization in FastAPI
- Security Dependencies (`Depends()` for Auth)
- Current User Pattern (`get_current_user` Dependency)
- Password Hashing (`passlib` with `bcrypt` / `argon2`)
- User Model and Credential Storage

### 📦 Module 3.2: JWT Authentication (Stateless)
- JWT Structure (Header, Payload, Signature)
- JWT Libraries for Python (`python-jose`, `PyJWT`, `authlib`)
- Token Generation (Access Token + Refresh Token)
- Token Validation and Expiration
- Refresh Token Strategy
  - Token Rotation on Refresh
  - Revocation (Redis Blacklist / Database Allowlist)
- Custom JWT Middleware / Dependency
- Token Claims (Custom Claims, Audience, Issuer)
- JWT Pitfalls and Best Practices
  - Never Store Sensitive Data in JWT Payload
  - Short Access Token TTL + Longer Refresh Token TTL
  - Signing Algorithm Selection (HS256 vs RS256)

### 📦 Module 3.3: OAuth 2.0 & OpenID Connect
- OAuth 2.0 Flows
  - Authorization Code + PKCE (SPAs, Mobile)
  - Client Credentials (Service-to-Service)
  - Resource Owner Password (Legacy — Know Why to Avoid)
- OpenID Connect (ID Token, UserInfo Endpoint)
- FastAPI as OAuth2 Resource Server
  - Validating External JWT Tokens (from Auth Provider)
  - JWKS (JSON Web Key Set) Validation
- FastAPI as OAuth2 Client
  - Social Login (Google, GitHub) with `authlib` / `httpx-oauth`
  - Token Exchange and User Info Retrieval
- SSO (Single Sign-On) Implementation
- Integration with External IdPs
  - Keycloak (Self-Hosted)
  - Auth0 / Okta (Managed)
  - Token Introspection vs Local Validation

### 📦 Module 3.4: Authorization Patterns
- RBAC (Role-Based Access Control)
  - Roles in JWT Claims
  - Permission Dependencies (`Depends(require_role("admin"))`)
- ABAC (Attribute-Based Access Control)
  - Custom Permission Evaluators
  - Policy-Based Authorization
- Resource-Level Authorization (Users Can Only Access Their Own Data)
  - Object-Level Permissions in Endpoints
- Dynamic Permissions (Database-Driven Roles and Permissions)
- Scopes (OAuth2 Scopes for Fine-Grained API Access)
- Multi-Tenancy Security Considerations
- API Key Authentication (for Service-to-Service)

### 📦 Module 3.5: Application Security Hardening
- OWASP Top 10 — FastAPI Mitigations
  - SQL Injection Prevention (Parameterized Queries via SQLAlchemy — Already Safe)
  - XSS Prevention (API Returns JSON, Not HTML — But Be Aware)
  - CSRF Protection (Stateless APIs Don't Need It — When They Do)
  - Mass Assignment Protection (Pydantic Schemas = Explicit Fields = Safe)
  - Insecure Direct Object References (IDOR — Resource-Level Auth)
  - Security Misconfiguration (Disable Debug in Production, Remove Default Docs)
- CORS Configuration (`CORSMiddleware` — Proper Origins, Methods, Headers)
- Security Headers
  - Adding via Middleware (HSTS, X-Frame-Options, X-Content-Type-Options, CSP)
- Rate Limiting
  - `slowapi` (Based on `limits`)
  - Redis-Based Rate Limiting
  - Per-User, Per-IP, Per-Endpoint Strategies
- Input Validation as Security Layer (Pydantic Does Heavy Lifting)
- Secrets Management
  - `pydantic-settings` with Environment Variables
  - `.env` Files (Development Only)
  - HashiCorp Vault, AWS Secrets Manager (Awareness)
- Dependency Vulnerability Scanning (`safety`, `pip-audit`, Snyk)

> ### 🛠 Phase 3 Milestone Project: **Secure Multi-Tenant User Platform**
> User registration and login with JWT access + refresh tokens. OAuth2 social login with Google using `authlib`. RBAC with dynamic database-driven permissions. Resource-level authorization (users only see their own data). API key authentication for service-to-service. Rate limiting with `slowapi` and Redis. CORS configuration. Security headers middleware. OWASP hardening checklist. Full security test suite. Integration with Keycloak for SSO.

---

## 🟠 PHASE 4: Architecture & Domain-Driven Design
> **Goal:** Apply architectural styles, DDD, and modular design within FastAPI applications.

---

### 📦 Module 4.1: Layered & Modular Architecture in FastAPI
- Traditional Layered Architecture (Router → Service → Repository)
  - Pros, Cons, and When It Breaks Down
  - Dependency Flow (Router Depends on Service Depends on Repository)
- Package-by-Feature vs Package-by-Layer
  - Feature-Based Package Structure for FastAPI
- Modular Monolith in FastAPI
  - Vertical Slicing by Business Domain
  - Each Module: Own Routers, Schemas, Models, Services, Repository
  - Module Boundaries with Python Package Visibility (`__init__.py` Public API)
  - Inter-Module Communication via Events (Not Direct Imports)
  - Module Registration Pattern (Auto-Discover and Include Routers)
- Dependency Injection as Architecture Tool
  - Abstract Interfaces (Protocols / ABCs)
  - Concrete Implementations Injected via `Depends()`
  - Swapping Implementations for Testing

### 📦 Module 4.2: Clean Architecture & Hexagonal Architecture in FastAPI
- Hexagonal Architecture (Ports & Adapters)
  - Domain Layer (Entities, Value Objects, Domain Services — No Framework Dependencies)
  - Application Layer (Use Cases, Port Interfaces)
  - Infrastructure Layer (Adapters: SQLAlchemy, FastAPI Routers, Redis, Kafka)
  - Driving Ports (API, CLI) / Driven Ports (Database, External Services)
- Clean Architecture (Uncle Bob)
  - Dependency Rule (Dependencies Point Inward)
  - Entities → Use Cases → Interface Adapters → Frameworks
- Onion Architecture (Comparison)
- Practical Implementation in FastAPI
  - Multi-Package Python Project (Domain, Application, Infrastructure, Presentation)
  - Domain Package has ZERO FastAPI/SQLAlchemy Dependencies
  - Infrastructure Package Provides Adapter Implementations
  - Wiring with FastAPI's `Depends()` System
  - `dependency-injector` Library (When FastAPI's `Depends()` Isn't Enough)
    - Containers, Providers, Wiring
    - Overriding for Tests
- Trade-offs: When Hexagonal is Overkill vs When It Saves You

### 📦 Module 4.3: Strategic DDD
- Ubiquitous Language (Building a Shared Vocabulary)
- Domain Discovery (Big Picture Event Storming)
- Bounded Contexts
  - Identification and Definition
  - Mapping to FastAPI Modules / Services
- Context Mapping Patterns
  - Shared Kernel
  - Customer-Supplier
  - Conformist
  - Anti-Corruption Layer (ACL)
  - Open Host Service / Published Language
  - Partnership
  - Separate Ways
- Subdomain Classification
  - Core Domain (Competitive Advantage — Maximum Investment)
  - Supporting Subdomain (Necessary but Not Differentiating)
  - Generic Subdomain (Buy / Use Off-the-Shelf)
- Event Storming
  - Big Picture Event Storming
  - Design-Level Event Storming
  - Identifying Commands, Events, Aggregates, Policies

### 📦 Module 4.4: Tactical DDD in FastAPI
- Entities (Identity, Lifecycle, Equality by ID)
  - Implementing as Plain Python Classes (Not SQLAlchemy Models)
  - Domain Entity vs Persistence Model Separation
- Value Objects (Immutable, Equality by Value, Self-Validating)
  - Implementing as Frozen Dataclasses or Pydantic Models
  - Value Objects as Embedded Types in SQLAlchemy
- Aggregates and Aggregate Roots
  - Consistency Boundaries
  - Aggregate Design Rules (Small Aggregates, Reference by ID)
  - Transactional Boundaries = Aggregate Boundaries
- Domain Events
  - In-Process Event Bus (Simple List-Based or `blinker` Library)
  - Event Publishing from Aggregates
  - Event Handlers (Subscribers)
  - Event-Driven Between Bounded Contexts
  - Event Naming Conventions (Past Tense: `OrderPlaced`, `PaymentReceived`)
- Repositories (Domain-Oriented, Not CRUD-Oriented)
  - Repository as a Domain Concept (Protocol/ABC Interface)
  - SQLAlchemy Implementation Behind the Interface
  - Mapping Between Domain Entities and ORM Models
- Domain Services (Stateless Business Logic Across Aggregates)
- Application Services (Use Cases — Orchestrate Domain Objects)
  - Transaction Boundaries
  - Schema ↔ Domain Mapping at This Layer
- Factories (Complex Aggregate Creation)
- Specifications Pattern (Business Rules as Objects)
- Domain Model Purity (No Framework in Domain Layer — Ideal vs Pragmatic)

### 📦 Module 4.5: Architecture Decision Records
- ADR Structure (Title, Status, Context, Decision, Consequences)
- When to Write an ADR
- Lightweight ADR Templates (Michael Nygard)
- ADR as Living Documentation
- Connecting ADRs to Code

> ### 🛠 Phase 4 Milestone Project: **Order Management System (DDD + Hexagonal)**
> Model an order domain using DDD: Bounded Contexts (Orders, Inventory, Payments). Aggregates with consistency rules, Value Objects (Money, Address, OrderId), Domain Events published in-process. Hexagonal Architecture with domain package having zero framework dependencies. Repository pattern with SQLAlchemy adapters behind Protocol interfaces. Application services as use cases. Wired together with FastAPI's dependency injection. ADRs for all major decisions. Event Storming artifacts documented.

---

## 🔴 PHASE 5: Microservices & Distributed Systems
> **Goal:** Decompose, communicate, and manage services at scale with distributed systems patterns.

---

### 📦 Module 5.1: Microservices Fundamentals
- Monolith-First Strategy (Why and When to Decompose)
- Service Decomposition Strategies
  - By Business Capability
  - By Subdomain (DDD Bounded Contexts)
- Database-Per-Service Pattern
- Shared Nothing Architecture
- Microservice Size (About Team Ownership, Not Lines of Code)
- Strangler Fig Pattern (Incremental Migration from Monolith)
- Python Microservice Project Template

### 📦 Module 5.2: Synchronous Communication
- Inter-Service Communication with HTTP
  - `httpx.AsyncClient` (Preferred — Async, Connection Pooling)
  - `httpx.AsyncClient` as FastAPI Dependency (Lifecycle via Lifespan)
  - Retry Logic with `tenacity`
  - Timeout Configuration
  - Circuit Breaking (Covered in Module 5.4)
- gRPC with Python
  - Protocol Buffers (`.proto` Files, Code Generation with `grpc_tools`)
  - `grpcio` and `grpcio-tools`
  - Unary, Server-Streaming, Client-Streaming, Bidirectional
  - gRPC with `asyncio` (`grpclib` / `grpcio` async)
  - gRPC vs REST (When to Use What)
- Service Discovery
  - Consul (Service Registration, Health Checks, KV Store)
  - Kubernetes-Native Service Discovery (DNS-Based — Why You May Not Need Consul)
  - Client-Side vs Server-Side Discovery
- API Gateway
  - Kong, Traefik, NGINX as API Gateways
  - Gateway Responsibilities (Routing, Rate Limiting, Auth, TLS Termination)
  - BFF (Backend for Frontend) Pattern
  - Building a Simple Gateway with FastAPI (Reverse Proxy Pattern)

### 📦 Module 5.3: Asynchronous & Event-Driven Communication
- Synchronous vs Asynchronous Trade-offs
- Event-Driven Architecture Concepts
  - Events vs Commands vs Queries
  - Choreography vs Orchestration
- Apache Kafka with Python
  - `aiokafka` (Async Kafka Client — Preferred for FastAPI)
    - Producer (Send Events)
    - Consumer (Receive Events, Consumer Groups)
    - Topics, Partitions, Offsets
    - Serialization (JSON, Avro with Schema Registry via `confluent-kafka`)
  - Error Handling (Dead Letter Topics, Retry Topics)
  - Exactly-Once Semantics (Idempotent Producers)
  - Ordering Guarantees (Partition Keys)
  - Kafka Consumer as FastAPI Background Worker
  - `confluent-kafka` (Alternative — Better Schema Registry Support)
- RabbitMQ with Python
  - `aio-pika` (Async AMQP Client — Preferred for FastAPI)
    - Exchanges (Direct, Topic, Fanout, Headers)
    - Bindings, Queues, Routing Keys
    - Publishing and Consuming Messages
    - Dead Letter Exchanges
    - Message Acknowledgment Modes
  - `pika` (Sync Client — Awareness)
- Celery (Distributed Task Queue)
  - Celery with FastAPI Integration
  - Workers, Brokers (Redis, RabbitMQ), Result Backends
  - Task Routing, Priority Queues
  - Periodic Tasks (Celery Beat)
  - Monitoring (Flower)
  - When Celery vs Direct Kafka/RabbitMQ
- Event Sourcing
  - Event Store Design (Append-Only Log)
  - Projections (Building Read Models from Events)
  - Snapshots (Performance Optimization)
  - Rebuilding State from Events
  - Python Event Sourcing Libraries (`eventsourcing` — Awareness)
- CQRS (Command Query Responsibility Segregation)
  - Separate Write Model (Commands) and Read Model (Queries)
  - Eventual Consistency Between Write and Read Sides
  - CQRS + Event Sourcing Together
  - When CQRS is Overkill
- Saga Pattern
  - Choreography-Based Sagas (Events Trigger Next Steps)
  - Orchestration-Based Sagas (Central Coordinator)
  - Compensating Transactions (Undo Logic)
  - Implementing with State Machine or Custom Orchestrator

### 📦 Module 5.4: Resilience & Fault Tolerance
- Fallacies of Distributed Computing (Peter Deutsch)
- Resilience Patterns in Python
  - `tenacity` (Retry Library)
    - Retry with Exponential Backoff and Jitter
    - Stop Conditions, Wait Strategies
    - Retry on Specific Exceptions
  - Circuit Breaker
    - `pybreaker` (Circuit Breaker Library)
    - States: CLOSED → OPEN → HALF_OPEN
    - Failure Thresholds, Recovery Timeouts
    - Circuit Breaker as FastAPI Dependency
  - Bulkhead
    - `asyncio.Semaphore` (Limit Concurrent Requests to External Services)
    - Thread Pool Isolation for Sync Calls
  - Timeout
    - `asyncio.wait_for()` (Async Timeout)
    - `httpx` Timeout Configuration
  - Combining Patterns (Retry inside Circuit Breaker inside Bulkhead)
- Idempotency
  - Idempotency Keys (UUID in Request Header)
  - Idempotent REST APIs (PUT vs POST)
  - Idempotent Consumers (Deduplication with Redis/DB)
- Graceful Degradation (Fallback Responses, Cached Defaults)
- Failover Strategies (Active-Passive, Active-Active)

### 📦 Module 5.5: Distributed Data Patterns
- Consistency Models (Strong, Eventual, Causal, Read-Your-Writes)
- CAP Theorem and PACELC (Revisited in Practice)
- Distributed Transactions
  - 2PC (Two-Phase Commit) — Why to Avoid in Microservices
  - Sagas (Preferred — Already Covered Above)
- Data Partitioning (Hash, Range, Geographic)
- Replication Strategies (Leader-Follower, Multi-Leader, Leaderless)
- Change Data Capture (CDC)
  - Debezium with Kafka Connect
  - Outbox Pattern (Write Event to Outbox Table → CDC → Kafka)
  - Implementing Outbox Pattern in FastAPI + SQLAlchemy
- Conflict Resolution (Last-Write-Wins, CRDTs — Concepts)

### 📦 Module 5.6: Scalability Patterns
- Horizontal vs Vertical Scaling
- Stateless Service Design (Why and How)
- Caching Strategies (Cache-Aside, Write-Through, Write-Behind, Read-Through)
- Cache Invalidation Strategies
- Rate Limiting and Throttling (Token Bucket, Leaky Bucket, Sliding Window)
- Backpressure Mechanisms
- Connection Pooling and Resource Management
- Database Read Replicas and Query Routing

### 📦 Module 5.7: Configuration & Coordination
- Centralized Configuration
  - Consul KV Store
  - Kubernetes ConfigMaps and Secrets
  - `pydantic-settings` with Multiple Config Sources (Env → File → Defaults)
  - Dynamic Configuration Reload
- Distributed Coordination
  - Leader Election Concepts
  - Distributed Locking (Redis-Based with `redis.asyncio` Lock / Redlock)

> ### 🛠 Phase 5 Milestone Project: **Food Delivery Platform (Microservices)**
> Decompose into services: User (FastAPI + JWT), Restaurant (FastAPI + PostgreSQL), Order (FastAPI + Saga Orchestrator), Delivery (FastAPI + Geo Queries), Payment (FastAPI + Idempotency), Notification (Celery Worker + Email/SMS).
> - Kafka for async events (`OrderPlaced` → `PaymentProcessed` → `DeliveryAssigned`)
> - Saga pattern for order flow (Orchestration-Based)
> - `tenacity` retries + `pybreaker` circuit breakers on all inter-service `httpx` calls
> - CQRS for restaurant search (write to PostgreSQL, read from Elasticsearch)
> - Outbox pattern for reliable event publishing
> - Consul for service discovery and centralized config
> - Each service has its own PostgreSQL database
> - Redis caching for restaurant menus
> - Celery with Redis broker for background notification tasks

---

## 🟣 PHASE 6: API Design & Integration Patterns
> **Goal:** Design excellent APIs and master enterprise integration patterns.

---

### 📦 Module 6.1: REST API Design Excellence
- REST Maturity Model (Richardson's Levels 0–3)
- Resource Naming Conventions (Nouns, Not Verbs)
- Proper HTTP Method Usage (Idempotency Matrix)
- Pagination Patterns (Offset, Cursor/Keyset, Page-Based)
- Filtering, Sorting, Field Selection (Query Parameter Design)
- Bulk Operations API Design
- Partial Updates (PATCH with JSON Merge Patch / JSON Patch)
- Error Response Standards (RFC 7807 Problem Details)
- API Versioning (URI Path vs Header vs Media Type)
- API-First Design Approach
  - OpenAPI Spec First → Generate Pydantic Models (`datamodel-code-generator`)
  - Contract-First vs Code-First Trade-offs
- HATEOAS (When It Adds Value — Rare in Practice)

### 📦 Module 6.2: GraphQL with FastAPI
- GraphQL Concepts (Schema, Types, Queries, Mutations, Subscriptions)
- Strawberry GraphQL with FastAPI
  - Type Definitions with Python Classes and Type Hints
  - `@strawberry.type`, `@strawberry.mutation`, `@strawberry.input`
  - Query and Mutation Resolvers
  - DataLoader Pattern (Solving N+1)
  - Input Validation
  - Error Handling
  - Authentication and Authorization in GraphQL
  - Subscriptions with WebSockets
- GraphQL vs REST — Decision Framework
- GraphQL Federation (Awareness)

### 📦 Module 6.3: gRPC Services with FastAPI
- Coexisting gRPC + REST in One Service
- gRPC for Internal Communication, REST for External
- Protocol Buffers Schema Design
- Streaming Patterns (Server, Client, Bidirectional)
- gRPC Error Handling and Status Codes
- gRPC Health Checking Protocol

### 📦 Module 6.4: Integration Patterns (Enterprise Integration Patterns)
- Core EIP Patterns (Hohpe and Woolf)
  - Message Channel
  - Message Router (Content-Based Router)
  - Message Translator
  - Aggregator, Splitter
  - Dead Letter Channel
  - Wire Tap
- Implementing EIP Patterns in Python
  - Kafka Topic as Message Channel
  - Content-Based Router with Consumer Logic
  - Dead Letter Topics
  - Message Transformation Between Services
- Request-Reply, Publish-Subscribe, Point-to-Point
- Webhooks and Callback Patterns
  - Receiving Webhooks in FastAPI
  - Webhook Signature Verification (HMAC)
  - Retry and Delivery Guarantees
- Polling vs Push Strategies
- Anti-Corruption Layer (Implementation Between Bounded Contexts)
- AsyncAPI for Event-Driven API Documentation
  - AsyncAPI Specification for Kafka/RabbitMQ Contracts
  - Code Generation from AsyncAPI

### 📦 Module 6.5: Contract Testing & API Governance
- Consumer-Driven Contract Testing
  - Pact for Python (`pact-python`)
    - Consumer Tests (Define Expected Interactions)
    - Provider Verification (Verify Against Contracts)
    - Pact Broker (Sharing Contracts)
  - Schema Validation Contracts (OpenAPI Spec as Contract)
- API Linting and Standards Enforcement (`spectral`)
- API Lifecycle Management

> ### 🛠 Phase 6 Milestone Project: **Unified API Platform**
> Build a unified API platform: REST API (OpenAPI-first with generated Pydantic models) + GraphQL API with Strawberry for storefront queries. gRPC service for internal catalog synchronization. Webhook receiver for payment provider callbacks with HMAC verification. Kafka-based message router implementing content-based routing and dead letter topics. Consumer-driven contract tests with Pact. AsyncAPI documentation for event contracts. API versioning strategy demonstrated.

---

## ⚫ PHASE 7: Testing at Scale
> **Goal:** Master every layer of testing for FastAPI — from unit to contract to performance.

---

### 📦 Module 7.1: FastAPI Testing Foundations
- `TestClient` (Starlette — Sync Testing)
- `httpx.AsyncClient` with `ASGITransport` (Async Testing — Preferred)
- `pytest-asyncio` Configuration
- Dependency Overriding (`app.dependency_overrides`)
  - Mocking Database Sessions
  - Mocking External Services
  - Mocking Auth Dependencies
- Testing Middleware
- Testing WebSocket Endpoints
- Testing Background Tasks
- Factory Boy / `polyfactory` (Test Data Factories with Pydantic)

### 📦 Module 7.2: Integration & Persistence Testing
- Testcontainers for Python
  - PostgreSQL, Redis, Kafka, MongoDB, Elasticsearch Containers
  - Async Fixtures with Testcontainers
  - Shared Container Strategy (Session-Scoped Fixtures)
- Database Testing
  - Async Session Fixtures
  - Transaction Rollback Between Tests
  - Alembic Migration Testing (Run Migrations in Test)
  - Seeding Test Data
- External Service Mocking
  - `respx` (Mock `httpx` Requests — Preferred for Async)
  - `aioresponses` (Mock `aiohttp` Requests)
  - WireMock (Docker-Based — Language-Agnostic HTTP Mock)
- Kafka Testing
  - `aiokafka` with Testcontainers Kafka
  - Testing Producers and Consumers

### 📦 Module 7.3: Architecture Testing
- Import Linting (`import-linter`)
  - Layer Dependency Rules (Domain Must Not Import Infrastructure)
  - Module Independence Rules (Orders Module Must Not Import Payment Internals)
  - DDD Pattern Enforcement
- Custom Architecture Tests with `pytest`
  - Scanning for Forbidden Imports
  - Verifying Module Public APIs

### 📦 Module 7.4: Performance & Chaos Testing
- Load Testing
  - Locust (Python-Native Load Testing — Preferred for Python Teams)
    - User Classes, Tasks, Task Sets
    - Custom Load Shapes
    - Distributed Load Testing
  - k6 (JavaScript — Faster, Recommended for Serious Load Testing)
    - Scenarios, Thresholds, Checks
  - Gatling (Awareness)
- Performance Testing Strategy
  - Baseline Establishment
  - Stress Testing, Spike Testing, Soak Testing
  - Performance Budgets
- Chaos Engineering
  - Failure Injection in Python Services
    - Random Latency Injection (Middleware)
    - Random Exception Injection
    - Resource Exhaustion Simulation
  - Chaos Toolkit (`chaostoolkit` — Python-Based Chaos Engineering)
  - GameDay Planning and Execution

### 📦 Module 7.5: Testing Strategy & Best Practices
- Test Pyramid (Unit → Integration → E2E) in Microservices
- Testing Honeycomb (Spotify Model)
- Test Data Management
- Test Isolation Strategies (Database, Event Bus, External Services)
- Flaky Test Management
- Testing in CI/CD Pipelines
  - Parallelization (`pytest-xdist`)
  - Fast Feedback (Unit Tests First, Integration Tests Separate Stage)
- Coverage Strategy (Meaningful Coverage, Not Line Count)

> ### 🛠 Phase 7 Milestone Project: **Comprehensive Test Suite for Food Delivery Platform**
> Retrofit the Phase 5 project with: full unit tests (pytest + mocking with dependency overrides), async integration tests with Testcontainers (PostgreSQL, Kafka, Redis), external service mocks with `respx`, contract tests with Pact, import-linter rules for architecture enforcement, Locust load tests for critical APIs, chaos testing middleware (random latency/failure injection). Greater than 85% meaningful coverage. All tests run in CI/CD with separate stages.

---

## 🔶 PHASE 8: DevOps, Observability & Production Readiness
> **Goal:** Deploy, monitor, and operate FastAPI applications in production with confidence.

---

### 📦 Module 8.1: Production Server Configuration
- Uvicorn Production Configuration
  - Workers (`--workers`)
  - Loop Implementation (`uvloop` for Performance)
  - Access Logging
  - Graceful Shutdown (`--timeout-graceful-shutdown`)
- Gunicorn + Uvicorn Workers (Production Deployment Pattern)
  - `gunicorn -k uvicorn.workers.UvicornWorker`
  - Worker Count (`2 * CPU + 1`)
  - Timeout, Keep-Alive, Graceful Timeout
  - Preloading Application (`--preload`)
- Process Management
  - Running with systemd (Awareness)
  - Running in Docker (Preferred)

### 📦 Module 8.2: Containerization & Kubernetes Deployment
- Docker Best Practices for FastAPI
  - Multi-Stage Dockerfile (Builder Stage → Runtime Stage)
  - Base Image Selection (`python:3.12-slim`)
  - Dependency Installation (Poetry Export → pip install, or pip with requirements.txt)
  - Non-Root User
  - Health Check in Dockerfile
  - `.dockerignore` Optimization
  - Layer Caching for Dependencies
- Kubernetes Deployment for FastAPI
  - Deployment, Service, Ingress YAML Manifests
  - ConfigMaps and Secrets for Configuration
  - Readiness Probes (`/health/ready`)
  - Liveness Probes (`/health/live`)
  - Startup Probes (For Slow-Starting Services)
  - Graceful Shutdown (Signal Handling, `SIGTERM`)
  - Resource Requests and Limits
  - Horizontal Pod Autoscaler (HPA)
  - Pod Disruption Budgets
- Helm Charts for FastAPI Services
- Kubernetes-Native Configuration
  - Config via ConfigMaps → Environment Variables → `pydantic-settings`
  - Secrets via Kubernetes Secrets
  - Service Discovery via Kubernetes DNS

### 📦 Module 8.3: CI/CD Pipeline Design
- CI Pipeline (GitHub Actions)
  - Lint (`ruff`) → Type Check (`mypy`) → Unit Test → Integration Test (Testcontainers) → Security Scan (`bandit`, `safety`) → Contract Test → Docker Build → Push to Registry
  - Dependency Vulnerability Scanning (`pip-audit`, Snyk)
  - Quality Gates (Coverage Threshold, Type Check Pass, Lint Pass)
  - Artifact Promotion Strategy (Dev → Staging → Prod)
- CD Pipeline
  - Blue/Green Deployments
  - Canary Releases (with Kubernetes or API Gateway)
  - Rolling Deployments
  - Feature Flags (Unleash, LaunchDarkly, or Custom Redis-Based)
  - Database Migration in CI/CD (Alembic as Pipeline Step)
- GitOps
  - ArgoCD (Declarative, Git-as-Source-of-Truth)
  - Sync Policies, Health Checks, Rollback
  - Separate App Repo vs Config Repo

### 📦 Module 8.4: Infrastructure as Code
- Terraform for FastAPI Infrastructure
  - AWS/GCP/Azure Resources (RDS, ElastiCache, EKS/GKE, VPC)
  - State Management (Remote Backend, Locking)
  - Modules for Reusability
  - Workspaces for Environment Separation
- Ansible (Configuration Management — Awareness)
- Policy as Code (OPA — Awareness)

### 📦 Module 8.5: Observability — The Three Pillars
- **Structured Logging**
  - `structlog` (Preferred for FastAPI)
    - Processors, Formatters, Bound Loggers
    - JSON Output for Production
    - Key-Value Output for Development
  - Correlation IDs / Trace IDs in Logs
    - Middleware to Generate/Propagate Request IDs
    - `structlog` Context Variables for Request-Scoped Data
  - Log Aggregation
    - ELK Stack (Elasticsearch, Logstash, Kibana)
    - Loki + Grafana (Lightweight Alternative)
  - Logging Best Practices (What to Log, What NOT to Log — No PII)
- **Metrics**
  - Prometheus Client (`prometheus-client` / `prometheus-fastapi-instrumentator`)
    - Auto-Instrumentation (Request Count, Latency Histogram, In-Progress)
    - Custom Metrics (Counters, Gauges, Histograms, Summaries)
    - `/metrics` Endpoint for Prometheus Scraping
  - Grafana Dashboards
    - RED Metrics (Rate, Errors, Duration) per Service
    - USE Metrics (Utilization, Saturation, Errors) for Resources
  - SLIs, SLOs, SLAs, and Error Budgets
  - Business Metrics (Orders per Minute, Revenue, Active Users)
- **Distributed Tracing**
  - OpenTelemetry for Python (`opentelemetry-sdk`)
    - Auto-Instrumentation (`opentelemetry-instrument`)
      - FastAPI, SQLAlchemy, httpx, aiohttp, Kafka Instrumentation
    - Manual Spans (`tracer.start_as_current_span()`)
    - Trace Context Propagation (W3C Trace Context)
    - Baggage Propagation
    - Span Attributes and Events
  - Trace Exporters (Jaeger, Zipkin, OTLP)
  - Trace Visualization (Jaeger UI, Grafana Tempo)
  - Correlating Logs with Traces (Trace ID in Log Entries)
- **Alerting**
  - Alertmanager (Prometheus)
  - Alert Design (Symptom-Based, Not Cause-Based)
  - Runbooks for Each Alert
  - On-Call Rotation and Incident Response Process
- **Dashboarding**
  - Service Health Dashboard
  - Business Metrics Dashboard
  - Infrastructure Dashboard
  - Dashboard-as-Code (Grafana Provisioning with JSON/YAML)

### 📦 Module 8.6: Production Readiness Checklist
- Health Checks (Readiness, Liveness, Startup — FastAPI Endpoints)
- Graceful Shutdown (SIGTERM Handling, Connection Draining)
- Circuit Breakers on All External Calls
- Structured JSON Logging with Trace IDs
- Metrics Exposed and Dashboarded
- Alerts Configured with Runbooks
- Database Migrations Automated (Alembic in CI/CD)
- Secrets Externalized (Not in Code/Config Files)
- Security Headers and OWASP Hardening
- Rate Limiting Configured
- Load Tested to Expected Capacity
- Disaster Recovery Plan Documented
- Rollback Strategy Defined and Tested
- API Documentation Published and Accurate

> ### 🛠 Phase 8 Milestone Project: **Production-Ready Deployment Pipeline**
> Take the Food Delivery Platform and make it production-ready:
> - Dockerized with multi-stage builds, deployed to Kubernetes (Minikube/Kind or cloud)
> - Helm charts for all services
> - Gunicorn + Uvicorn production configuration
> - Full CI/CD pipeline (GitHub Actions → ArgoCD)
> - Terraform for infrastructure (PostgreSQL RDS, ElastiCache Redis, EKS)
> - Full observability stack: `structlog` JSON logs → Loki, `prometheus-fastapi-instrumentator` → Prometheus → Grafana, OpenTelemetry traces → Jaeger
> - Alerting with Prometheus Alertmanager (error rate, latency P99)
> - Grafana dashboards (RED metrics per service, business metrics)
> - Feature flags with Redis-based custom implementation
> - Canary deployment for one service
> - Production readiness checklist verified for all services

---
---

## 🏗️ CAPSTONE PROJECT: Real-Time E-Commerce Platform
> **This is the Phase 2 capstone — it ties everything together.**
>
> Build a distributed e-commerce system with:
>
> - **Modular monolith with clear bounded contexts** (Catalog, Orders, Payments, Notifications) — vertical slices with enforced module boundaries via `import-linter`
> - **Hexagonal Architecture** within each bounded context (domain layer has zero framework dependencies)
> - **DDD tactical patterns** (Aggregates, Value Objects, Domain Events, Repositories behind Protocol interfaces)
> - **Event-driven communication** between modules (Kafka via `aiokafka`)
> - **CQRS** for the product catalog (write to PostgreSQL via SQLAlchemy, read-optimized projections to Elasticsearch)
> - **Saga pattern** for order processing flow (Order → Payment → Inventory → Notification) with compensating transactions
> - **Outbox pattern** for reliable event publishing (SQLAlchemy outbox table → CDC → Kafka)
> - **OAuth 2.0 + JWT** authentication (Keycloak or custom with `python-jose`)
> - **API Gateway** (Traefik or Kong) with rate limiting
> - **GraphQL API** with Strawberry for storefront queries + REST API for admin operations
> - **Async SQLAlchemy 2.0 + Redis + Elasticsearch** (each bounded context owns its data)
> - **Resilience patterns** — `tenacity` retries, `pybreaker` circuit breakers, `asyncio.Semaphore` bulkheads
> - **Full CI/CD pipeline** with canary deployments (GitHub Actions → ArgoCD)
> - **OpenTelemetry** distributed tracing + Prometheus metrics + Grafana dashboards
> - **Terraform** for infrastructure
> - **Comprehensive test suite** — unit (pytest + dependency overrides), integration (Testcontainers), contract (Pact), load (Locust), architecture (import-linter)
> - **Architecture Decision Records (ADRs)** and **C4 diagrams** (Structurizr)
> - **Event Storming artifacts** documented
> - **AsyncAPI specs** for all event contracts
> - **Production readiness** checklist verified for every service
>
> **Why:** Covers DDD, event-driven architecture, distributed systems patterns, security, DevOps, observability, API design, and testing in one cohesive project that demonstrates mastery of Phase 2.

---

## ✅ After Completing This Roadmap — You Can:
- Understand WSGI/ASGI and what FastAPI automates
- Build production-grade FastAPI applications
- Design and implement Hexagonal / Clean Architecture in Python
- Model domains using DDD (strategic + tactical)
- Build and operate microservices with FastAPI
- Implement event-driven systems with Kafka, RabbitMQ, and Celery
- Apply CQRS, Event Sourcing, and Saga patterns
- Secure applications with OAuth 2.0, JWT, and FastAPI security
- Design excellent REST, GraphQL, and gRPC APIs
- Master enterprise integration patterns
- Implement resilience patterns (circuit breakers, retries, bulkheads)
- Deploy to Kubernetes with CI/CD and GitOps
- Build full observability (logging, metrics, tracing, alerting)
- Write comprehensive tests at every layer
- Make and document architectural decisions (ADRs)
- Facilitate Event Storming sessions
- Create C4 architecture diagrams
- Choose and justify architectural styles for given requirements
- **You are ready for Phase 3: Cloud-Native Mastery and Leadership**

---

## 📋 Quick Reference Summary

```
Phase  0  ➜  Python Web Foundations (WSGI/ASGI)   🟤
Phase  1  ➜  FastAPI Core                          🟢
Phase  2  ➜  Data Access & Persistence             🔵
Phase  3  ➜  Security                              🟡
Phase  4  ➜  Architecture & DDD                    🟠
Phase  5  ➜  Microservices & Distributed Systems   🔴
Phase  6  ➜  API Design & Integration              🟣
Phase  7  ➜  Testing at Scale                      ⚫
Phase  8  ➜  DevOps, Observability & Production    🔶
       🏗️  ➜  CAPSTONE: E-Commerce Platform
```

> **⏱ Estimated Timeline:** 6–9 months (with consistent daily practice)
> **💡 Pro Tip:** Don't just learn FastAPI decorators — understand ASGI, Starlette, and Pydantic underneath. When something breaks, you debug through the stack, not around it.
> **⚡ Key Principle:** FastAPI gives you speed. DDD gives you correctness. Architecture gives you longevity. Testing gives you confidence. Observability gives you sleep.
```

---

## How This Maps to the SE Roadmap Phase 2

| SE Roadmap Phase 2 Module | Covered In |
|---|---|
| 2.1 Architectural Styles (Monolith, Microservices, Event-Driven, Hexagonal, Clean, CQRS) | Phase 4 + Phase 5 |
| 2.2 Distributed Systems (Consistency, Resilience, Scalability, Distributed Data) | Phase 5 (Modules 5.4, 5.5, 5.6) |
| 2.3 API Design & Integration (REST, GraphQL, gRPC, EIP, Messaging) | Phase 6 + Phase 5 (Module 5.3) |
| 2.4 Security Architecture (OWASP, OAuth2, JWT, IAM, App Security) | Phase 3 |
| 2.5 DevOps & CI/CD (Pipelines, Deployments, IaC, Observability) | Phase 8 |
| 2.6 Domain-Driven Design (Strategic + Tactical DDD) | Phase 4 (Modules 4.3, 4.4) |
| Phase 2 Project: E-Commerce Platform | Capstone Project |

**Every topic from Phase 2 of the SE Roadmap is covered. Nothing is missing. Nothing is extra.**