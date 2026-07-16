# 🦁 NestJS Mastery Roadmap — Phase 2: Architectural Thinking

> Picks up exactly where the TypeScript Foundations Roadmap (Phase 1) ended.
> Aligned with Phase 2 of the Software Engineering Mastery Roadmap.
> **Estimated Duration: 6–9 months**

---

## Prerequisites (Completed in Phase 1)
> ✅ TypeScript Mastery (Advanced types, generics, conditional types, mapped types, decorators)
> ✅ Node.js Internals (V8, event loop, libuv, memory, Worker Threads)
> ✅ Async Programming (Promises, async/await, streams, RxJS basics)
> ✅ OOP + Functional Programming in TypeScript
> ✅ SOLID, Design Patterns, Clean Code
> ✅ SQL, Kysely/Drizzle/Prisma, Redis basics
> ✅ Zod for runtime validation
> ✅ Git, pnpm, Vitest, CI/CD basics
> ✅ Docker, Docker Compose, Linux, Networking essentials
> ✅ Kubernetes concepts (awareness)

---
---

## 🟤 PHASE 0: Node.js Web Foundations — Raw HTTP, Express & Fastify
> **Goal:** Understand how Node.js handles HTTP at the lowest level — so you know exactly what NestJS abstracts away.
> **Duration:** ~2–3 weeks

---

### 📦 Module 0.1: How the Web Works (Node.js Perspective)
- Client-Server Model Recap
- HTTP Request/Response Lifecycle (from Browser to Node.js and Back)
- What is a Web Server vs Application Server
  - Nginx (Reverse Proxy, Static Content, TLS Termination, Load Balancing)
  - Node.js as Both Web Server and Application Runtime
  - Why You Still Put Nginx in Front of Node.js in Production
- Node.js's Role in Web Development (Historical Context)
  - Node.js `http` Module (Raw) → Connect → Express → Koa → Fastify → NestJS
  - Why This Evolution Happened (Pain Points at Each Stage)
  - Express: Minimal, Unopinionated, Middleware-Based
  - Fastify: Performance-First, Schema-Based, Plugin Architecture
  - NestJS: Opinionated, Angular-Inspired, Enterprise-Grade
- The Node.js Production Web Stack
  - Client → Nginx (Reverse Proxy + TLS) → Node.js (Your App) → Database
  - PM2 or Docker for Process Management
  - Why Each Layer Exists

### 📦 Module 0.2: Raw Node.js HTTP Server
- **`http` Module — The Foundation Under Everything**
  - `http.createServer()` (Creates an HTTP Server)
  - `IncomingMessage` (The Request Object)
    - `req.method`, `req.url`, `req.headers`
    - Reading Request Body (Streams — `req.on('data')`, `req.on('end')`)
    - `req.url` Parsing (`new URL()` for Path, Query Parameters)
  - `ServerResponse` (The Response Object)
    - `res.writeHead()` (Status Code + Headers)
    - `res.write()` (Write Body Chunks)
    - `res.end()` (Finalize Response)
    - `res.setHeader()`, `res.statusCode`
  - Content-Type Headers (Setting `application/json`, `text/html`)
- **Building a REST API with Raw `http`**
  - Routing by `req.method` and `req.url` (If/Else Chains)
  - Path Parameter Extraction (`/users/123` → Parse Manually)
  - Reading JSON Request Body (Collect Stream Chunks → `JSON.parse`)
  - Writing JSON Responses (`JSON.stringify` + `Content-Type` Header)
  - Error Responses (Status Codes + Error Body)
  - CRUD Operations (In-Memory Data Store)
- **Pain Points You'll Feel**
  - Manual URL parsing and routing boilerplate
  - Manual request body stream collection and parsing
  - Manual JSON serialization for every response
  - No middleware system
  - No validation
  - No dependency injection
  - No documentation generation
  - **These are the exact problems frameworks solve**

### 📦 Module 0.3: Express.js — The Middleware Foundation
- **Why Express Matters (NestJS Uses Express or Fastify Under the Hood)**
  - NestJS Default Platform Is Express (`@nestjs/platform-express`)
  - Understanding Express = Understanding NestJS's HTTP Layer
- **Express Core Concepts**
  - Application Instance (`express()`)
  - Routing (`app.get()`, `app.post()`, `app.put()`, `app.delete()`)
  - Route Parameters (`/users/:id` → `req.params.id`)
  - Query Parameters (`req.query`)
  - Request Body (`req.body` — Requires `express.json()` Middleware)
  - Response Methods (`res.json()`, `res.status()`, `res.send()`, `res.redirect()`)
- **Middleware (The Core Pattern)**
  - What is Middleware (`(req, res, next) => { ... }`)
  - Middleware Execution Order (Sequential, Top to Bottom)
  - Application-Level Middleware (`app.use()`)
  - Router-Level Middleware
  - Error-Handling Middleware (`(err, req, res, next)` — Four Parameters)
  - Built-in Middleware (`express.json()`, `express.urlencoded()`, `express.static()`)
  - Third-Party Middleware (`cors`, `helmet`, `morgan`, `compression`)
  - **💡 NestJS Middleware is literally Express/Fastify middleware wrapped in a class**
- **Router (Modular Routes)**
  - `express.Router()` (Group Related Routes)
  - Mounting Routers (`app.use('/api/users', userRouter)`)
  - Router-Level Middleware
  - **💡 NestJS Controllers are routers with decorators**
- **Building a Structured API with Express**
  - Route Handlers Separated into Files
  - Middleware for Logging, Auth, CORS
  - Error Handling Middleware (Centralized)
  - Manual Validation (Check Request Body Fields)
  - Type Safety with TypeScript (Type `Request` and `Response`)
- **Pain Points You'll Feel**
  - No structure enforcement (Every Express App Looks Different)
  - No dependency injection (Manual Instantiation)
  - No built-in validation (Manual or Third-Party)
  - No built-in documentation
  - No module system (Just Files and Imports)
  - Middleware-Based Architecture Gets Messy at Scale
  - **NestJS solves all of these**

### 📦 Module 0.4: Fastify — The Performance Alternative
- **Why Fastify Matters (NestJS Alternative Platform)**
  - `@nestjs/platform-fastify` (Swap Express for Fastify in NestJS)
  - When to Choose Fastify Over Express (Performance, Schema Validation)
- **Fastify Core Concepts**
  - Application Instance (`Fastify()`)
  - Route Declaration (`fastify.get()`, `fastify.post()`, etc.)
  - Route Options Object (Schema, Handler, PreHandler)
  - Request and Reply Objects (`request.params`, `request.body`, `reply.send()`)
- **Plugin System (Fastify's Killer Feature)**
  - `fastify.register()` (Encapsulated Plugins)
  - Plugin Encapsulation (Each Plugin Gets Its Own Scope)
  - Decorators (`fastify.decorate()` — Extend Fastify Instance)
  - Hooks (Lifecycle Hooks — `onRequest`, `preHandler`, `onSend`, `onResponse`)
  - **💡 NestJS Modules are conceptually similar to Fastify plugins but more structured**
- **Schema-Based Validation (JSON Schema)**
  - Route Schemas (Body, Params, Query, Headers, Response)
  - Automatic Validation (Fastify Validates Against Schema)
  - Automatic Serialization (Fastify Serializes Response by Schema — Faster Than `JSON.stringify`)
  - **💡 NestJS uses `class-validator` + `class-transformer` or Zod instead**
- **Fastify vs Express**
  - Performance (Fastify Is Significantly Faster)
  - Schema Validation (Fastify Built-In vs Express Manual)
  - Plugin Encapsulation (Fastify) vs Flat Middleware (Express)
  - Ecosystem Size (Express Larger, Fastify Growing)
  - When to Choose Each in NestJS Context

### 📦 Module 0.5: The Patterns NestJS Automates
- **Front Controller Pattern**
  - Your manual routing → NestJS `DispatcherModule` handles routing automatically
  - Decorator-Based Route Declaration
- **Middleware Pattern**
  - Express `(req, res, next)` → NestJS `NestMiddleware` interface
  - But also: Guards, Interceptors, Pipes, Exception Filters (Beyond Middleware)
- **Dependency Injection**
  - Manual `new Service()` in Express → `@Injectable()` + Constructor Injection in NestJS
  - NestJS has a Full IoC Container (Like Spring)
- **Module System**
  - Express: No structure → NestJS: `@Module()` enforces encapsulation
  - Imports, Exports, Providers, Controllers
- **Validation**
  - Manual `if (!body.email)` → NestJS `@Body()` + Validation Pipes + DTOs
- **Error Handling**
  - Express Error Middleware → NestJS Exception Filters (`@Catch()`)
- **Documentation**
  - Nothing → NestJS `@nestjs/swagger` auto-generates OpenAPI
- **Mapping Table**

  | Raw Express / Fastify | NestJS Equivalent |
  |---|---|
  | `app.get('/users', handler)` | `@Get('users')` on Controller Method |
  | `req.params.id` | `@Param('id')` |
  | `req.query.page` | `@Query('page')` |
  | `req.body` + `express.json()` | `@Body()` + DTO Class |
  | `res.json(data)` | `return data` (Auto-Serialized) |
  | `res.status(201).json(data)` | `@HttpCode(201)` or `throw new HttpException()` |
  | `(req, res, next)` middleware | `NestMiddleware.use()` |
  | Auth middleware | `@UseGuards(AuthGuard)` |
  | Validation middleware | `@UsePipes(ValidationPipe)` |
  | Error-handling middleware | `@Catch()` Exception Filters |
  | `express.Router()` | `@Controller('route')` |
  | Manual module files | `@Module({ imports, controllers, providers, exports })` |
  | `new UserService()` | `@Injectable()` + Constructor Injection |
  | Nothing | `@ApiTags()`, `@ApiOperation()` → Swagger UI |
  | `app.use(cors())` | `app.enableCors()` or `CorsMiddleware` |
  | Fastify plugins | NestJS Modules with `@Global()`, Dynamic Modules |
  | Fastify hooks | NestJS Interceptors (`@UseInterceptors()`) |
  | Fastify decorators | NestJS Custom Decorators (`createParamDecorator()`) |

> ### 🛠 Phase 0 Milestone Project: **Mini Express Framework with DI**
> Build a structured Express application that mimics NestJS patterns:
> - Custom decorator system using TypeScript decorators and `reflect-metadata`
>   - `@Controller('/path')`, `@Get()`, `@Post()`, `@Body()`, `@Param()` decorators (your own!)
>   - Scan decorated classes and auto-register routes at startup
> - Simple IoC container (dependency injection)
>   - `@Injectable()` decorator
>   - Constructor-based injection with reflection
>   - Singleton scope
> - Middleware chain with Logging + Auth (API key) middleware
> - Validation layer (Zod schemas on request body)
> - Centralized error handling middleware
> - Implement a CRUD API (e.g., Todo list) using YOUR framework
> - Then throw it all away and start Phase 1 with NestJS
>
> **Why:** You will deeply understand Controllers, Providers, Modules, Guards, Pipes, Interceptors, and Exception Filters — because you built crude versions yourself. When NestJS does it, it's no longer magic. **You'll never be the developer who can't debug past the decorators.**

---

### ✅ After Phase 0 — You Understand:
- How HTTP requests flow through Node.js to your handlers
- What Express middleware actually does (and how NestJS wraps it)
- Why Fastify is faster and when to choose it as NestJS platform
- How dependency injection works at a fundamental level
- The mapping between raw Express/Fastify and NestJS abstractions
- Why NestJS's module system, guards, pipes, and interceptors exist
- **You're not learning NestJS — you're learning what NestJS automated**

---
---

## 🟢 PHASE 1: NestJS Core
> **Goal:** Deeply understand NestJS's architecture — modules, providers, DI, request pipeline — and build professional REST APIs.
> **Duration:** ~4–5 weeks

---

### 📦 Module 1.1: NestJS Fundamentals
- What NestJS Solves (Structure, DI, Modularity, Enterprise-Grade Patterns)
- NestJS Architecture Philosophy (Angular-Inspired, Platform-Agnostic)
- Architecture Stack (NestJS → Platform Adapter → Express/Fastify)
- Installation and Project Scaffolding (`@nestjs/cli`)
  - `nest new project-name`
  - `nest generate` (module, controller, service, guard, pipe, interceptor, filter)
- Project Structure
  - `main.ts` (Bootstrap)
  - `app.module.ts` (Root Module)
  - Feature Modules (Vertical Slices)
- Platform Selection
  - `@nestjs/platform-express` (Default)
  - `@nestjs/platform-fastify` (Performance)
  - Switching Platforms (Minimal Code Changes)
- Running and Debugging
  - `nest start --watch` (Development)
  - `nest build` (Production Build)
  - Debugging with VS Code (Launch Configuration)

### 📦 Module 1.2: Modules - The Building Blocks
- `@Module()` Decorator
  - `imports` (Other Modules This Module Depends On)
  - `controllers` (Controllers Scoped to This Module)
  - `providers` (Services/Providers Scoped to This Module)
  - `exports` (Providers to Make Available to Importing Modules)
- Module Encapsulation (Providers Are Private by Default)
- Feature Modules (One Module Per Business Domain)
- Shared Modules (Common Utilities, Re-Exported)
- `@Global()` Modules (Available Everywhere — Use Sparingly)
- Dynamic Modules (`forRoot()`, `forRootAsync()`, `forFeature()`)
  - Configuration Pattern (Pass Options at Import Time)
  - Async Factory Pattern (Load Config from External Source)
  - `ConfigurableModuleBuilder` (Utility for Building Dynamic Modules)
- Module Re-Exporting (Import + Re-Export for Convenience)
- Circular Dependencies and `forwardRef()`
- Lazy-Loaded Modules (On-Demand Module Loading)

### 📦 Module 1.3: Providers & Dependency Injection
- **`@Injectable()` Decorator**
  - Services (Business Logic Containers)
  - Repositories (Data Access — Custom, Not TypeORM Repos)
  - Factories, Helpers, Any Injectable Class
- **NestJS IoC Container**
  - Constructor-Based Injection (Preferred)
  - Property-Based Injection (`@Inject()` — Rare)
  - Token-Based Injection (String and Symbol Tokens)
  - Custom Providers
    - `useClass` (Class Provider — Default)
    - `useValue` (Value Provider — Constants, Config Objects)
    - `useFactory` (Factory Provider — Dynamic Creation with Dependencies)
    - `useExisting` (Alias Provider — Alias One Token to Another)
  - `@Inject()` with Custom Tokens
  - `@Optional()` (Optional Dependencies)
- **Provider Scopes**
  - `DEFAULT` (Singleton — Shared Across App — Default)
  - `REQUEST` (New Instance Per Request)
  - `TRANSIENT` (New Instance Per Injection)
  - Scope Hierarchy (Request Scope Bubbles Up)
  - Performance Implications of Request/Transient Scopes
- **Injection Contexts**
  - Module Scope (Providers Belong to Modules)
  - Circular Injection and `forwardRef()`
  - `ModuleRef` (Dynamic Provider Resolution at Runtime)
  - `ContextIdFactory` (Request Context Tracking)

### 📦 Module 1.4: Controllers & Request Handling
- `@Controller('route-prefix')` Decorator
- HTTP Method Decorators (`@Get()`, `@Post()`, `@Put()`, `@Patch()`, `@Delete()`, `@Head()`, `@Options()`, `@All()`)
- Route Parameters
  - `@Param('id')` (Path Parameters)
  - `@Query('page')` (Query Parameters)
  - `@Body()` (Request Body)
  - `@Headers('authorization')` (Request Headers)
  - `@Ip()` (Client IP)
  - `@Session()` (Session Object)
  - `@Req()` / `@Res()` (Raw Request/Response — Escape Hatch, Avoid When Possible)
- Response Handling
  - Return Value Auto-Serialization (Return Object → JSON Response)
  - `@HttpCode()` (Override Default Status Code)
  - `@Header()` (Set Response Headers)
  - `@Redirect()` (Redirect Responses)
  - `@Render()` (Template Rendering — Awareness)
  - Platform-Specific Response (`@Res()` — Lose Interceptor/Serialization Support)
- Route Wildcards and Parameterized Paths
- Sub-Domain Routing (`@Controller({ host: ':account.example.com' })`)
- Request Payload Classes (DTOs)
  - Separation of Create, Update, Read DTOs
  - `PartialType()`, `PickType()`, `OmitType()`, `IntersectionType()` (Mapped Types Helpers)

### 📦 Module 1.5: The NestJS Request Lifecycle - Deep Understanding
- **Full Request Pipeline (Order Matters)**
  1. Incoming Request
  2. Globally Bound Middleware
  3. Module-Bound Middleware
  4. Global Guards
  5. Controller Guards
  6. Route Guards
  7. Global Interceptors (Pre-Controller)
  8. Controller Interceptors (Pre-Controller)
  9. Route Interceptors (Pre-Controller)
  10. Global Pipes
  11. Controller Pipes
  12. Route Pipes
  13. Route Parameter Pipes
  14. Controller Method (Handler)
  15. Route Interceptors (Post-Controller)
  16. Controller Interceptors (Post-Controller)
  17. Global Interceptors (Post-Controller)
  18. Exception Filters (Route → Controller → Global)
  19. Response
- **Why Understanding This Order Is Critical**
  - Guards Run Before Pipes (Auth Check Before Validation)
  - Interceptors Wrap the Handler (Can Transform Response)
  - Exception Filters Catch Everything (Last Resort)

### 📦 Module 1.6: Pipes - Validation & Transformation
- What Pipes Do (Transform Input Data, Validate Input Data)
- Built-in Pipes
  - `ValidationPipe` (Class-Validator Integration — Most Important)
  - `ParseIntPipe`, `ParseFloatPipe`, `ParseBoolPipe`, `ParseUUIDPipe`
  - `ParseArrayPipe`, `ParseEnumPipe`
  - `DefaultValuePipe`
- **`ValidationPipe` Deep Dive**
  - `class-validator` Decorators (`@IsString()`, `@IsEmail()`, `@IsNotEmpty()`, `@MinLength()`, `@IsOptional()`, `@IsEnum()`, `@IsArray()`, `@ValidateNested()`, `@IsUUID()`, `@Matches()`)
  - `class-transformer` (`@Transform()`, `@Exclude()`, `@Expose()`, `@Type()`, `plainToInstance`)
  - Whitelist Option (`whitelist: true` — Strip Unrecognized Properties)
  - `forbidNonWhitelisted` (Reject Unrecognized Properties)
  - `transform: true` (Auto-Transform Query Params to Correct Types)
  - Error Message Customization
  - Custom Validation Decorators (`registerDecorator`)
  - Validation Groups
- **Alternative: Zod-Based Validation**
  - `nestjs-zod` or Custom Zod Pipe
  - Zod Schemas as DTOs
  - When Zod vs class-validator
- Custom Pipes (`PipeTransform` Interface)
- Pipe Binding Levels (Parameter, Method, Controller, Global)

### 📦 Module 1.7: Guards - Authentication & Authorization Gateway
- What Guards Do (Allow or Deny Request Processing — Return Boolean)
- `CanActivate` Interface
- Execution Context (`ExecutionContext` — Access Request, Controller, Handler Metadata)
- Accessing Request Object from Guard
- Reflector and Custom Metadata
  - `@SetMetadata()` (Attach Metadata to Handlers)
  - Custom Decorators Wrapping `SetMetadata`
  - `Reflector.get()`, `Reflector.getAllAndOverride()`, `Reflector.getAllAndMerge()`
- Guard Binding Levels (Method, Controller, Global)
- Guards vs Middleware (Guards Have Access to Execution Context, Know What Handler Runs Next)
- Common Guard Patterns
  - Authentication Guard (Is User Logged In?)
  - Role Guard (Does User Have Required Role?)
  - Ownership Guard (Does User Own This Resource?)
  - Feature Flag Guard (Is Feature Enabled?)

### 📦 Module 1.8: Interceptors - Cross-Cutting Concerns
- What Interceptors Do (Transform Response, Add Behavior Before/After Handler)
- `NestInterceptor` Interface
- `CallHandler` and `handle()` (Returns Observable of Response)
- RxJS in Interceptors (`map`, `tap`, `catchError`, `timeout`)
- Common Interceptor Patterns
  - Logging Interceptor (Log Request/Response + Timing)
  - Transform Interceptor (Wrap Response in Standard Envelope `{ data, meta }`)
  - Cache Interceptor (Return Cached Response If Available)
  - Timeout Interceptor (`timeout` RxJS Operator)
  - File Upload Interceptor (`FileInterceptor`, `FilesInterceptor`)
  - Serialization Interceptor (`ClassSerializerInterceptor`)
- Interceptor Binding Levels (Method, Controller, Global)
- Interceptors vs Middleware (Interceptors See Both Request AND Response, Have RxJS Power)

### 📦 Module 1.9: Exception Filters - Error Handling
- NestJS Exception Layer
  - `HttpException` and Built-in HTTP Exceptions (`NotFoundException`, `BadRequestException`, `UnauthorizedException`, `ForbiddenException`, `ConflictException`, etc.)
  - Custom Exception Classes
- Exception Filters (`@Catch()`)
  - `ExceptionFilter` Interface
  - Catching Specific Exceptions
  - Catching All Exceptions (`@Catch()` with No Arguments)
  - Problem Details Format (RFC 7807 / RFC 9457)
  - Custom Error Response Shapes
- Filter Binding Levels (Method, Controller, Global)
- Global Filter with Dependency Injection (`APP_FILTER` Token)
- Separating Business Exceptions from HTTP Exceptions (Domain Exceptions Mapped to HTTP in Filters)

### 📦 Module 1.10: Configuration & Environment
- `@nestjs/config` Module
  - `ConfigModule.forRoot()` (Load `.env` Files)
  - `ConfigService` (Access Config Values)
  - Namespaced Configuration (`registerAs()`)
  - Validation with Joi or Zod (Validate Environment Variables at Startup)
  - Custom Config Files (YAML, TOML)
  - Environment-Specific Config (`.env.development`, `.env.production`)
- Profiles and Environment Separation
- Configuration Best Practices
  - Fail Fast on Missing Config (Validate at Bootstrap)
  - Strongly Typed Config (Type-Safe Access)
  - No Secrets in Code or Config Files

### 📦 Module 1.11: OpenAPI Documentation
- `@nestjs/swagger` Module
- Swagger Setup (`SwaggerModule.createDocument()`, `SwaggerModule.setup()`)
- Decorators for Documentation
  - `@ApiTags()` (Group Endpoints)
  - `@ApiOperation()` (Describe Endpoint)
  - `@ApiResponse()` (Document Responses)
  - `@ApiProperty()` (Document DTO Properties)
  - `@ApiQuery()`, `@ApiParam()`, `@ApiHeader()`, `@ApiBody()`
  - `@ApiBearerAuth()`, `@ApiOAuth2()`, `@ApiSecurity()`
  - `@ApiExtraModels()` (Register Models Not Directly Used in Controllers)
- CLI Plugin (`@nestjs/swagger/plugin` — Auto-Infer from DTOs)
- Multiple Swagger Documents (Separate Docs for Different API Versions/Audiences)
- API Versioning
  - URI Versioning (`/v1/users`, `/v2/users`)
  - Header Versioning
  - Media Type Versioning
  - `@Version('1')` Decorator

> ### 🛠 Phase 1 Milestone Project: **Task Management REST API**
> Full CRUD REST API for projects, tasks, and users. Proper module structure (UserModule, ProjectModule, TaskModule). DTOs with `class-validator` for create/read/update separation. Custom ValidationPipe with whitelist. Auth Guard (stub — API key for now). Logging Interceptor + Response Transform Interceptor. Global Exception Filter with RFC 7807 problem details. `@nestjs/config` for environment management. Full Swagger documentation with examples. API versioning (v1). Focus on understanding the full request lifecycle.

---

## 🔵 PHASE 2: Data Access & Persistence
> **Goal:** Master database access with TypeORM/Prisma/Drizzle in NestJS, advanced querying, performance tuning, and caching.

---

### 📦 Module 2.1: TypeORM with NestJS (Deep Dive)
- `@nestjs/typeorm` Integration
  - `TypeOrmModule.forRoot()` / `TypeOrmModule.forRootAsync()` (Connection Setup)
  - `TypeOrmModule.forFeature([Entity])` (Register Entities Per Module)
- Entity Definition
  - `@Entity()`, `@Column()`, `@PrimaryGeneratedColumn()`
  - Column Types (`varchar`, `int`, `boolean`, `timestamp`, `json`, `enum`, `uuid`)
  - Column Options (`nullable`, `unique`, `default`, `length`)
  - `@CreateDateColumn()`, `@UpdateDateColumn()`, `@DeleteDateColumn()` (Soft Deletes)
  - `@VersionColumn()` (Optimistic Locking)
- Repository Pattern
  - `Repository<Entity>` and `@InjectRepository()`
  - `find()`, `findOne()`, `findOneBy()`, `save()`, `remove()`, `delete()`, `update()`
  - `FindOptions` (`where`, `order`, `relations`, `select`, `skip`, `take`)
  - Custom Repositories (Extending `Repository`)
- Relationships
  - `@OneToOne()`, `@JoinColumn()`
  - `@OneToMany()`, `@ManyToOne()`
  - `@ManyToMany()`, `@JoinTable()`
  - Bidirectional Relations (`inverseSide`)
  - Cascade Options (`insert`, `update`, `remove`, `soft-remove`)
  - Eager vs Lazy Loading
    - `eager: true` (Always Load — Use Carefully)
    - `relations` in `find()` (Explicit Loading)
    - N+1 Problem (Detection and Resolution with `leftJoinAndSelect`)
- QueryBuilder (Complex Queries)
  - `createQueryBuilder()`, `select`, `where`, `andWhere`, `orWhere`
  - Joins (`leftJoinAndSelect`, `innerJoinAndSelect`)
  - Aggregations (`groupBy`, `having`, `getCount`, `getRawMany`)
  - Subqueries
  - Raw SQL (`query()`)
- Inheritance Strategies (`STI`, `TABLE_PER_CLASS`)
- Subscribers and Entity Listeners (`@BeforeInsert()`, `@AfterInsert()`, `@BeforeUpdate()`)

### 📦 Module 2.2: Prisma with NestJS (Alternative ORM)
- Why Prisma (Schema-First, Auto-Generated Client, Excellent TypeScript Support)
- `schema.prisma` (Declarative Schema)
  - Models, Fields, Relations, Enums
  - `@id`, `@unique`, `@default`, `@relation`, `@map`, `@@index`
- `PrismaService` (Extending `PrismaClient`, `OnModuleInit`, `OnModuleDestroy`)
- CRUD Operations (Fully Typed)
  - `create`, `findUnique`, `findFirst`, `findMany`, `update`, `upsert`, `delete`
  - `include` (Eager Loading Relations)
  - `select` (Field Selection)
  - Nested Writes (Create Parent + Children in One Operation)
- Prisma Migrate (`prisma migrate dev`, `prisma migrate deploy`)
- Prisma vs TypeORM (Trade-offs: DX vs Flexibility vs Performance)
- When to Use Prisma vs TypeORM vs Drizzle in NestJS

### 📦 Module 2.3: Drizzle ORM with NestJS (SQL-First Alternative)
- Why Drizzle (SQL-Like, Lightweight, Full Type Safety)
- Schema Definition in TypeScript
- Query API (SQL-Like + Relational)
- Drizzle Kit for Migrations
- Integration with NestJS (Custom Module/Provider)
- Drizzle vs Prisma vs TypeORM (Decision Framework)

### 📦 Module 2.4: Transactions & Performance
- **Transaction Management**
  - TypeORM: `DataSource.transaction()`, `QueryRunner`
  - Prisma: `prisma.$transaction()` (Interactive and Sequential)
  - Nested Transactions (Savepoints)
  - Read-Only Transactions
  - Transaction Isolation Levels
- **Connection Pooling**
  - TypeORM Pool Configuration
  - Prisma Connection Pool (`connection_limit`, `pool_timeout`)
  - Monitoring Pool Usage
- **Query Performance**
  - Indexing Strategies (Aligned with Phase 1 DB Knowledge)
  - `EXPLAIN ANALYZE` in Practice
  - N+1 Detection and Resolution
  - DTO Projections for Read-Heavy Queries (Select Specific Columns)
  - Batch Operations
  - Pagination Performance (Keyset vs Offset)
- **Database Migrations**
  - TypeORM Migrations (`migration:generate`, `migration:run`, `migration:revert`)
  - Prisma Migrate
  - Drizzle Kit
  - Zero-Downtime Migration Strategies (Expand/Contract)
  - Data Migrations
  - Running Migrations in CI/CD

### 📦 Module 2.5: Caching with Redis
- `@nestjs/cache-manager` (Cache Module)
  - `CacheModule.register()` / `CacheModule.registerAsync()`
  - `@CacheKey()`, `@CacheTTL()`
  - `CacheInterceptor` (Auto-Cache GET Responses)
  - `CACHE_MANAGER` Injection (Programmatic Cache Access)
  - `cache.get()`, `cache.set()`, `cache.del()`
- Redis as Cache Store (`cache-manager-redis-yet` or `cache-manager-ioredis-yet`)
- Cache Patterns
  - Cache-Aside (Application-Level)
  - Write-Through, Write-Behind Concepts
  - Read-Through Concepts
- TTL Strategies and Cache Invalidation
- `ioredis` Direct Usage (When `cache-manager` Isn't Enough)
  - Redis Data Structures (String, Hash, List, Set, Sorted Set)
  - Pub/Sub
  - Session Storage
- Custom Cache Decorators

### 📦 Module 2.6: Elasticsearch Integration
- `@nestjs/elasticsearch` Module
- `ElasticsearchService` (Wraps Official Client)
- Indexing Documents
- Full-Text Search Queries
- Index Mapping and Settings
- Keeping Elasticsearch in Sync with Database (Event-Driven)

> ### 🛠 Phase 2 Milestone Project: **E-Commerce Product Catalog Service**
> Product catalog with categories, tags, variants, and reviews. TypeORM (or Prisma/Drizzle) with complex relationships, eager loading strategies, and N+1 resolution. Database migrations with zero-downtime approach. Redis caching with `@nestjs/cache-manager` for hot products and category listings. Elasticsearch for full-text product search with autocomplete. Keyset and offset pagination. Query performance benchmarks with `EXPLAIN ANALYZE`. Auditing (created_at, updated_at) with entity listeners/subscribers.

---

## 🟡 PHASE 3: Security
> **Goal:** Implement production-grade security — authentication, authorization, OAuth2, and application hardening.

---

### 📦 Module 3.1: NestJS Security Fundamentals
- Security Architecture in NestJS (Guards + Passport + JWT + Custom)
- `@nestjs/passport` Module
  - Passport.js Integration (Strategy Pattern for Authentication)
  - Passport Strategies (Local, JWT, OAuth2, API Key)
  - `AuthGuard()` (Built-in Guard Factory)
- Password Hashing (`bcrypt`, `argon2`)
- User Entity with Credentials

### 📦 Module 3.2: Local Authentication (Username/Password)
- Passport Local Strategy (`passport-local`)
  - `LocalStrategy` (Extends `PassportStrategy(Strategy)`)
  - `validate()` Method (Return User or Throw)
  - `AuthGuard('local')` (Trigger Local Strategy)
- Login Endpoint (Accept Credentials, Return Token)
- Registration Endpoint (Hash Password, Create User)

### 📦 Module 3.3: JWT Authentication (Stateless)
- `@nestjs/jwt` Module
  - `JwtModule.register()` / `JwtModule.registerAsync()`
  - `JwtService` (Sign, Verify, Decode)
- JWT Structure (Header, Payload, Signature)
- Passport JWT Strategy (`passport-jwt`)
  - `JwtStrategy` (Extends `PassportStrategy(Strategy)`)
  - Extract JWT from Bearer Header
  - `validate()` Method (Decode Payload → Return User)
  - `AuthGuard('jwt')` (Protect Routes)
- Refresh Token Strategy
  - Access Token (Short TTL — 15min)
  - Refresh Token (Longer TTL — 7 Days)
  - Token Rotation on Refresh
  - Revocation (Redis Blacklist / Database Allowlist)
- JWT Pitfalls and Best Practices
  - Short Access Token TTL
  - Signing Algorithm Selection (HS256 vs RS256)
  - Never Store Sensitive Data in Payload
- Custom JWT Auth Guard (Beyond Passport — For More Control)

### 📦 Module 3.4: OAuth 2.0 & OpenID Connect
- OAuth 2.0 Flows
  - Authorization Code + PKCE (SPAs, Mobile)
  - Client Credentials (Service-to-Service)
  - Resource Owner Password (Legacy — Know Why to Avoid)
- OpenID Connect (ID Token, UserInfo Endpoint)
- Passport OAuth2 Strategies
  - `passport-google-oauth20` (Google Login)
  - `passport-github2` (GitHub Login)
  - Custom OAuth2 Strategy
- NestJS as OAuth2 Resource Server
  - Validating External JWT Tokens
  - JWKS Validation
- SSO Implementation
- Integration with External IdPs
  - Keycloak (Self-Hosted)
  - Auth0 / Okta (Managed)
  - Token Introspection vs Local Validation

### 📦 Module 3.5: Authorization Patterns
- **RBAC (Role-Based Access Control)**
  - `@Roles('admin', 'manager')` Custom Decorator
  - `RolesGuard` (Check User Roles Against Required Roles)
  - Roles in JWT Claims
- **ABAC (Attribute-Based Access Control)**
  - Policy-Based Authorization
  - Custom `PermissionGuard`
  - CASL Integration (`@casl/ability`)
    - Ability Definition (What Can User Do?)
    - Checking Abilities in Guards
    - Subject-Based Permissions
- **Resource-Level Authorization**
  - Ownership Checks (Users Can Only Access Their Own Data)
  - `PoliciesGuard` (Check Against Resource)
- **Dynamic Permissions (Database-Driven)**
  - Roles and Permissions Tables
  - Loading Permissions at Runtime
- **Multi-Tenancy Security Considerations**
  - Tenant Isolation in Guards
  - Tenant Context Propagation
- **API Key Authentication**
  - Custom API Key Strategy
  - API Key Guard for Service-to-Service

### 📦 Module 3.6: Application Security Hardening
- OWASP Top 10 — NestJS Mitigations
  - SQL Injection Prevention (Parameterized Queries via ORM — Already Safe)
  - XSS Prevention (API Returns JSON — Awareness for SSR)
  - CSRF Protection (Stateless APIs Don't Need It — When They Do)
  - Mass Assignment Protection (DTOs + Whitelist Pipe = Safe)
  - Insecure Direct Object References (IDOR — Resource-Level Auth)
  - Security Misconfiguration (Disable Swagger in Production, CORS Config)
- **CORS** (`app.enableCors()` with Proper Origins, Methods, Headers)
- **Helmet** (`@nestjs/helmet` — Security Headers)
  - HSTS, X-Frame-Options, X-Content-Type-Options, CSP
- **Rate Limiting**
  - `@nestjs/throttler` Module
  - `ThrottlerModule.forRoot()` (TTL, Limit)
  - `@Throttle()` (Per-Route Overrides)
  - `@SkipThrottle()` (Exclude Routes)
  - Redis-Based Throttling (Distributed Rate Limiting)
  - Per-User, Per-IP, Per-Endpoint Strategies
- Input Validation as Security Layer (ValidationPipe + DTOs)
- Secrets Management
  - `@nestjs/config` with Environment Variables
  - `.env` Files (Development Only)
  - HashiCorp Vault, AWS Secrets Manager (Awareness)
- Dependency Vulnerability Scanning (`npm audit`, Snyk)

> ### 🛠 Phase 3 Milestone Project: **Secure Multi-Tenant User Platform**
> User registration and login with JWT access + refresh tokens (Passport JWT). OAuth2 social login with Google (Passport Google). RBAC with `@Roles()` decorator and `RolesGuard`. CASL-based ABAC for fine-grained permissions. Resource-level authorization (users only see their own data). API key authentication for service-to-service. Rate limiting with `@nestjs/throttler` (Redis store). Helmet security headers. CORS configuration. OWASP hardening checklist verified. Full security test suite.

---

## 🟠 PHASE 4: Architecture & Domain-Driven Design
> **Goal:** Apply architectural styles, DDD, and modular design within NestJS applications.

---

### 📦 Module 4.1: Layered & Modular Architecture in NestJS
- Traditional Layered Architecture (Controller → Service → Repository)
  - Pros, Cons, and When It Breaks Down
  - NestJS Naturally Encourages This Pattern
- Package-by-Feature vs Package-by-Layer
  - Feature Module Pattern (NestJS Modules = Feature Boundaries)
- Modular Monolith in NestJS
  - Vertical Slicing by Business Domain
  - Each Module: Own Controllers, Services, Entities, DTOs
  - Module Boundaries with Exports (Only Export What Other Modules Need)
  - Inter-Module Communication via Events (Not Direct Service Injection)
    - `@nestjs/event-emitter` Module
    - `EventEmitter2` (`@OnEvent()` Decorator)
    - Sync vs Async Event Handlers
  - Module Independence Verification (Import Rules)
- Dependency Injection as Architecture Tool
  - Abstract Interfaces (TypeScript Abstract Classes or Tokens)
  - Concrete Implementations via Providers
  - Swapping Implementations for Testing

### 📦 Module 4.2: Clean Architecture & Hexagonal Architecture in NestJS
- **Hexagonal Architecture (Ports & Adapters)**
  - Domain Layer (Entities, Value Objects, Domain Services — No NestJS Dependencies)
  - Application Layer (Use Cases, Port Interfaces)
  - Infrastructure Layer (Adapters: TypeORM Repositories, Controllers, Kafka Producers)
  - Driving Ports (REST, GraphQL, gRPC, CLI) / Driven Ports (Database, External APIs, Messaging)
- **Clean Architecture (Uncle Bob)**
  - Dependency Rule (Dependencies Point Inward)
  - Entities → Use Cases → Interface Adapters → Frameworks
- **Onion Architecture (Comparison)**
- **Practical Implementation in NestJS**
  - Multi-Package Monorepo (Nx or Turborepo)
    - `libs/domain` (Zero NestJS Dependencies — Plain TypeScript)
    - `libs/application` (Use Cases, Port Interfaces)
    - `libs/infrastructure` (NestJS Modules, TypeORM, Kafka)
    - `apps/api` (NestJS Application Shell)
  - Domain Package Has ZERO NestJS/TypeORM Decorators
  - Infrastructure Provides Adapter Implementations
  - Wiring with NestJS DI (Custom Providers with Abstract Class Tokens)
  - `useClass` Provider for Binding Interface → Implementation
- **Trade-offs: When Hexagonal Is Overkill**

### 📦 Module 4.3: Strategic DDD
- Ubiquitous Language (Building a Shared Vocabulary)
- Domain Discovery (Big Picture Event Storming)
- Bounded Contexts
  - Identification and Definition
  - Mapping to NestJS Modules / Microservices
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

### 📦 Module 4.4: Tactical DDD in NestJS
- **Entities (Identity, Lifecycle, Equality by ID)**
  - Domain Entity Class (Plain TypeScript — No `@Entity()` Decorator)
  - Persistence Entity (TypeORM `@Entity()` — Separate from Domain)
  - Mapping Between Domain and Persistence Entities
- **Value Objects (Immutable, Equality by Value, Self-Validating)**
  - Implementing as Frozen Classes or Readonly Objects
  - Value Objects as Embedded Types in TypeORM (`@Column(() => Address)`)
- **Aggregates and Aggregate Roots**
  - Consistency Boundaries
  - Aggregate Design Rules (Small Aggregates, Reference by ID)
  - Transactional Boundaries = Aggregate Boundaries
  - Aggregate Root Enforces Invariants
- **Domain Events**
  - `@nestjs/event-emitter` for In-Process Events
  - `EventEmitter2` (`emit`, `@OnEvent()`)
  - Aggregate Collects Events → Application Service Publishes After Commit
  - Event-Driven Between Bounded Contexts
  - Event Naming Conventions (Past Tense: `OrderPlaced`, `PaymentReceived`)
- **Repositories (Domain-Oriented, Not CRUD-Oriented)**
  - Repository Interface in Domain Layer (Abstract Class or Interface)
  - TypeORM/Prisma Implementation in Infrastructure Layer
  - Mapping Between Domain Entities and ORM Entities
  - Injecting via NestJS DI (`useClass` Custom Provider)
- **Domain Services (Stateless Business Logic Across Aggregates)**
- **Application Services (Use Cases — Orchestrate Domain Objects)**
  - Transaction Boundaries
  - DTO ↔ Domain Mapping at This Layer
  - One Public Method Per Use Case Class (Single Responsibility)
- **Factories (Complex Aggregate Creation)**
- **Specifications Pattern (Business Rules as Objects)**
- **Domain Model Purity (No NestJS/TypeORM in Domain Layer)**

### 📦 Module 4.5: CQRS with NestJS
- `@nestjs/cqrs` Module
  - Command Bus (`CommandBus`)
  - Query Bus (`QueryBus`)
  - Event Bus (`EventBus`)
- Commands and Command Handlers
  - `ICommand`, `ICommandHandler`, `@CommandHandler()`
  - Commands as Intent (Imperative: `CreateOrderCommand`)
- Queries and Query Handlers
  - `IQuery`, `IQueryHandler`, `@QueryHandler()`
  - Queries as Questions (Interrogative: `GetOrderByIdQuery`)
- Events and Event Handlers
  - `IEvent`, `IEventHandler`, `@EventsHandler()`
  - Events as Facts (Past Tense: `OrderCreatedEvent`)
- Sagas (`@Saga()` — React to Events, Dispatch Commands)
- When CQRS Adds Value vs Overkill

### 📦 Module 4.6: Architecture Decision Records
- ADR Structure (Title, Status, Context, Decision, Consequences)
- When to Write an ADR
- Lightweight ADR Templates (Michael Nygard)
- ADR as Living Documentation
- Connecting ADRs to Code

> ### 🛠 Phase 4 Milestone Project: **Order Management System (DDD + Hexagonal + CQRS)**
> Model an order domain using DDD: Bounded Contexts (Orders, Inventory, Payments). Aggregates with consistency rules, Value Objects (Money, Address, OrderId), Domain Events via `@nestjs/event-emitter`. CQRS with `@nestjs/cqrs` (Commands for writes, Queries for reads). Hexagonal Architecture with domain package having zero NestJS dependencies (Nx monorepo). Repository pattern with TypeORM adapters behind abstract class interfaces. Application services as use cases. ADRs for all major decisions. Event Storming artifacts documented.

---

## 🔴 PHASE 5: Microservices & Distributed Systems
> **Goal:** Decompose, communicate, and manage services at scale with NestJS microservices and distributed systems patterns.

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

### 📦 Module 5.2: NestJS Microservices Framework
- **`@nestjs/microservices` Module**
  - Hybrid Application (HTTP + Microservice in Same Process)
  - Standalone Microservice (No HTTP — Only Message-Based)
  - `createMicroservice()` and `connectMicroservice()`
- **Transport Layers (Built-In)**
  - TCP Transport (Default — Simple, No Broker)
  - Redis Transport (Pub/Sub Based)
  - NATS Transport (Lightweight Message Broker)
  - MQTT Transport (IoT Focused — Awareness)
  - gRPC Transport (High-Performance — Covered in Detail Below)
  - Kafka Transport (Event Streaming — Covered in Detail Below)
  - RabbitMQ Transport (`@golevelup/nestjs-rabbitmq` or Custom)
- **Message Patterns**
  - Request-Response (`@MessagePattern()`)
    - Client Sends Request → Service Sends Response
    - `ClientProxy.send()` (Returns Observable)
    - Synchronous-Like Communication Over Async Transport
  - Event-Based (`@EventPattern()`)
    - Fire and Forget (No Response Expected)
    - `ClientProxy.emit()` (Returns Observable — Completes When Sent)
- **Client Registration**
  - `ClientsModule.register()` / `ClientsModule.registerAsync()`
  - `@Client()` Decorator (Shorthand)
  - `ClientProxy` (Abstraction Over Transport)
  - Connection Management (Reconnection, Error Handling)

### 📦 Module 5.3: Synchronous Communication
- **gRPC with NestJS**
  - `@nestjs/microservices` gRPC Transport
  - Protocol Buffers (`.proto` Files, Code Generation)
  - `@GrpcMethod()` Decorator (Define gRPC Service Methods)
  - `@GrpcStreamMethod()` (Streaming)
  - gRPC Client (`ClientGrpc`, `getService()`)
  - Unary, Server-Streaming, Client-Streaming, Bidirectional
  - gRPC Error Handling (Status Codes)
  - gRPC vs REST (When to Use What)
  - `ts-proto` or `protobufjs` for Type Generation
- **REST-Based Communication**
  - `HttpModule` (`@nestjs/axios`)
  - `HttpService` (Wraps Axios — Reactive with RxJS)
  - Retry Logic, Timeout Configuration
  - Circuit Breaking (Covered in Module 5.5)
- **Service Discovery**
  - Consul Integration
  - Kubernetes-Native Service Discovery
  - Client-Side vs Server-Side Discovery
- **API Gateway**
  - NestJS as API Gateway (Route Requests to Microservices)
  - Kong, Traefik, NGINX as External Gateways
  - BFF (Backend for Frontend) Pattern

### 📦 Module 5.4: Asynchronous & Event-Driven Communication
- Synchronous vs Asynchronous Trade-offs
- Event-Driven Architecture Concepts
  - Events vs Commands vs Queries
  - Choreography vs Orchestration
- **Apache Kafka with NestJS**
  - Kafka Transport in `@nestjs/microservices`
  - `@MessagePattern()` and `@EventPattern()` with Kafka Topics
  - Producer (`ClientKafka`, `emit()`, `send()`)
  - Consumer (Consumer Groups, Offsets)
  - Serialization (JSON, Avro with Schema Registry)
  - Error Handling (Dead Letter Topics, Retry Topics)
  - Ordering Guarantees (Partition Keys)
  - `kafkajs` Direct Usage (When NestJS Transport Isn't Enough)
- **RabbitMQ with NestJS**
  - `@golevelup/nestjs-rabbitmq` (Preferred — More Feature-Rich)
    - `@RabbitSubscribe()` Decorator
    - Exchanges (Direct, Topic, Fanout, Headers)
    - Queues, Bindings, Routing Keys
    - Dead Letter Exchanges
    - Message Acknowledgment
    - Request-Reply Pattern (RPC Over RabbitMQ)
  - NestJS RMQ Transport (Built-in — Simpler but Less Flexible)
- **Bull / BullMQ (Job Queues)**
  - `@nestjs/bullmq` Module
  - Queue Definition (`@InjectQueue()`)
  - Job Processors (`@Processor()`, `@WorkerHost()`)
  - Job Options (Delay, Retry, Priority, Backoff)
  - Scheduled/Repeatable Jobs
  - Job Events and Lifecycle
  - Bull Board (Queue Dashboard)
  - When Bull vs Kafka vs RabbitMQ
- **Event Sourcing**
  - Event Store Design (Append-Only Log)
  - Projections (Building Read Models from Events)
  - Snapshots (Performance Optimization)
  - Rebuilding State from Events
  - NestJS CQRS Module + Custom Event Store
- **CQRS in Distributed Context**
  - Separate Write Model (Commands) and Read Model (Queries)
  - Eventual Consistency Between Write and Read Sides
  - CQRS + Event Sourcing Together
  - When CQRS is Overkill
- **Saga Pattern**
  - Choreography-Based Sagas (Events Trigger Next Steps)
  - Orchestration-Based Sagas (Central Coordinator)
  - Compensating Transactions (Undo Logic)
  - `@Saga()` in `@nestjs/cqrs` (React to Events, Dispatch Commands)
  - Custom Saga Orchestrator

### 📦 Module 5.5: Resilience & Fault Tolerance
- Fallacies of Distributed Computing (Peter Deutsch)
- **Resilience Patterns in NestJS**
  - `nestjs-resilience` or Custom Implementation
  - Circuit Breaker
    - `opossum` Library (Circuit Breaker for Node.js)
    - States: CLOSED → OPEN → HALF_OPEN
    - Custom Circuit Breaker Interceptor
  - Retry
    - RxJS `retry()` and `retryWhen()` in Interceptors
    - Exponential Backoff with Jitter
    - `p-retry` Library
  - Bulkhead
    - Concurrency Limiting (Semaphore Pattern)
    - `p-limit` Library
  - Timeout
    - RxJS `timeout()` Operator in Interceptors
    - `HttpModule` Timeout Configuration
  - Combining Patterns (Interceptor Pipeline)
- **Idempotency**
  - Idempotency Keys (UUID in Request Header)
  - Idempotent REST APIs (PUT vs POST)
  - Idempotent Consumers (Deduplication with Redis/DB)
  - Custom Idempotency Interceptor
- **Graceful Degradation** (Fallback Responses, Cached Defaults)
- **Failover Strategies** (Active-Passive, Active-Active)

### 📦 Module 5.6: Distributed Data Patterns
- Consistency Models (Strong, Eventual, Causal, Read-Your-Writes)
- CAP Theorem and PACELC (Revisited in Practice)
- Distributed Transactions
  - 2PC (Two-Phase Commit) — Why to Avoid in Microservices
  - Sagas (Preferred — Already Covered)
- Data Partitioning (Hash, Range, Geographic)
- Replication Strategies (Leader-Follower, Multi-Leader, Leaderless)
- Change Data Capture (CDC)
  - Debezium with Kafka Connect
  - Outbox Pattern (Write Event to Outbox Table → CDC → Kafka)
  - Implementing Outbox Pattern in NestJS + TypeORM
- Conflict Resolution (Last-Write-Wins, CRDTs — Concepts)

### 📦 Module 5.7: Scalability Patterns
- Horizontal vs Vertical Scaling
- Stateless Service Design (Why and How)
- Caching Strategies (Cache-Aside, Write-Through, Write-Behind, Read-Through)
- Cache Invalidation Strategies
- Rate Limiting and Throttling (Token Bucket, Leaky Bucket, Sliding Window)
- Backpressure Mechanisms
- Connection Pooling and Resource Management
- Database Read Replicas and Query Routing

### 📦 Module 5.8: Configuration & Coordination
- Centralized Configuration
  - NestJS Config Service + Spring Cloud Config Server (Awareness)
  - Consul KV Store
  - Kubernetes ConfigMaps and Secrets
  - Dynamic Configuration Reload
- Distributed Coordination
  - Leader Election Concepts
  - Distributed Locking (Redis-Based with `ioredis` Lock / Redlock)

> ### 🛠 Phase 5 Milestone Project: **Food Delivery Platform (Microservices)**
> Decompose into NestJS microservices: User Service (JWT Auth), Restaurant Service (CRUD + Search), Order Service (CQRS + Saga Orchestrator), Delivery Service (Real-Time Tracking), Payment Service (Idempotent), Notification Service (BullMQ Worker).
> - gRPC for sync inter-service communication (User ↔ Order, Order ↔ Payment)
> - Kafka for async events (`OrderPlaced` → `PaymentProcessed` → `DeliveryAssigned`)
> - Saga pattern for order flow (Orchestration with `@nestjs/cqrs`)
> - `opossum` circuit breakers on all inter-service calls
> - CQRS for restaurant search (write to PostgreSQL, read from Elasticsearch)
> - Outbox pattern for reliable event publishing
> - Each service has its own PostgreSQL database
> - Redis caching for restaurant menus
> - BullMQ for background notification processing (email, push)
> - Consul or Kubernetes DNS for service discovery

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
- API Versioning in NestJS (URI, Header, Media Type — `@Version()`)
- API-First Design Approach
  - OpenAPI Spec First → Generate DTOs / NestJS Controllers
  - Contract-First vs Code-First Trade-offs
- HATEOAS (When It Adds Value)

### 📦 Module 6.2: GraphQL with NestJS
- `@nestjs/graphql` Module
- **Code-First Approach**
  - `@ObjectType()`, `@Field()`, `@InputType()`, `@ArgsType()`
  - `@Resolver()`, `@Query()`, `@Mutation()`, `@Subscription()`
  - `@ResolveField()` (Resolve Nested Object Fields)
  - Auto-Generated Schema from Decorators
- **Schema-First Approach**
  - Write `.graphql` Schema Files
  - Generate TypeScript Types
  - Resolver Implementations
- **GraphQL Deep Dive**
  - Input Validation (Integrate `class-validator` with GraphQL Inputs)
  - Error Handling (GraphQL Errors, Formatted Errors)
  - DataLoader Pattern (Solving N+1 — `@nestjs/dataloader` or Custom)
  - Complexity and Depth Limiting (Prevent Abusive Queries)
  - Authentication and Authorization in GraphQL (`@UseGuards()` on Resolvers)
  - Subscriptions (WebSocket-Based Real-Time Updates)
    - `graphql-ws` Protocol
    - PubSub Engine (`graphql-subscriptions`)
    - Redis-Based PubSub (For Multi-Instance)
  - Federation (Apollo Federation — Combining Multiple GraphQL Services)
    - `@nestjs/graphql` Federation Support
    - Gateway and Subgraphs
- GraphQL vs REST — Decision Framework

### 📦 Module 6.3: gRPC API Design (Beyond Basic Communication)
- Service Definition Best Practices
- Proto File Organization (Per-Service vs Shared)
- gRPC Error Model (Status Codes, Error Details)
- gRPC Health Checking Protocol
- gRPC Reflection (Service Discovery — Awareness)
- REST ↔ gRPC Transcoding (Awareness)

### 📦 Module 6.4: WebSockets & Real-Time
- `@nestjs/websockets` Module
- `@WebSocketGateway()` Decorator
- `@SubscribeMessage()` (Handle Incoming Messages)
- `@WebSocketServer()` (Access Server Instance)
- Adapters
  - Socket.IO Adapter (Default — Feature-Rich, Rooms, Namespaces)
  - WS Adapter (`ws` Library — Lightweight, Standards-Compliant)
- Rooms and Namespaces (Socket.IO)
- Broadcasting and Targeted Messages
- Authentication in WebSockets (Handshake-Based Auth)
- Redis Adapter for Multi-Instance WebSocket (Scaling Horizontally)
- Server-Sent Events (SSE) as Alternative (`@Sse()`)

### 📦 Module 6.5: Integration Patterns (Enterprise Integration Patterns)
- Core EIP Patterns (Hohpe and Woolf)
  - Message Channel
  - Message Router (Content-Based Router)
  - Message Translator
  - Aggregator, Splitter
  - Dead Letter Channel
  - Wire Tap
- Implementing EIP Patterns in NestJS
  - Kafka/RabbitMQ Topic as Message Channel
  - Content-Based Router with Consumer Logic
  - Dead Letter Topics/Exchanges
  - Message Transformation Between Services (DTOs, Adapters)
- Request-Reply, Publish-Subscribe, Point-to-Point
- Webhooks and Callback Patterns
  - Receiving Webhooks in NestJS
  - Webhook Signature Verification (HMAC)
  - Retry and Delivery Guarantees
- Polling vs Push Strategies
- Anti-Corruption Layer (Implementation Between Bounded Contexts)
- AsyncAPI for Event-Driven API Documentation

### 📦 Module 6.6: Contract Testing & API Governance
- Consumer-Driven Contract Testing
  - Pact for NestJS (`@pact-foundation/pact`)
    - Consumer Tests (Define Expected Interactions)
    - Provider Verification (Verify Against Contracts)
    - Pact Broker (Sharing Contracts)
  - Schema Validation Contracts (OpenAPI/Proto as Contract)
- API Linting and Standards Enforcement
- API Lifecycle Management

> ### 🛠 Phase 6 Milestone Project: **Unified API Platform**
> Build a unified API platform: REST API (OpenAPI-first with Swagger) + GraphQL API with code-first approach for storefront queries (with DataLoader, subscriptions, complexity limiting). gRPC service definitions for internal inter-service communication. WebSocket gateway for real-time order tracking (Socket.IO with Redis adapter). Webhook receiver for payment provider callbacks with HMAC verification. Consumer-driven contract tests with Pact. AsyncAPI documentation for event contracts. API versioning strategy demonstrated.

---

## ⚫ PHASE 7: Testing at Scale
> **Goal:** Master every layer of testing for NestJS — from unit to contract to performance.

---

### 📦 Module 7.1: NestJS Testing Foundations
- **`@nestjs/testing` Module**
  - `Test.createTestingModule()` (Create Test Module)
  - `TestingModule.compile()` (Build Container)
  - Overriding Providers (`.overrideProvider()`, `.useClass()`, `.useValue()`, `.useFactory()`)
  - Overriding Guards, Interceptors, Pipes, Filters
- **Unit Testing Controllers**
  - Mock Services (Inject Mock via Provider Override)
  - Test HTTP Handling (Directly Call Controller Methods)
- **Unit Testing Services**
  - Mock Repositories and External Dependencies
  - Testing Business Logic in Isolation
- **Integration Testing**
  - `supertest` with `app.getHttpServer()` (Full HTTP Integration)
  - Test Full Request Pipeline (Middleware → Guards → Pipes → Handler → Interceptors → Filters)
  - Database Integration (Real Database in Tests)
- **Testing Microservice Handlers**
  - `@MessagePattern()` and `@EventPattern()` Testing
  - ClientProxy Mocking

### 📦 Module 7.2: Integration & Persistence Testing
- **Testcontainers for Node.js**
  - PostgreSQL, Redis, Kafka, MongoDB, Elasticsearch
  - Container Lifecycle in Tests (Start Before All, Stop After All)
  - Shared Container Strategy (Performance)
- **Database Testing**
  - TypeORM/Prisma Test Configuration
  - Migration Before Tests
  - Transaction Rollback Between Tests
  - Seeding Test Data
  - Factory Libraries (`typeorm-seeding`, Custom Factories)
- **External Service Mocking**
  - `nock` (Mock HTTP Requests)
  - WireMock (Docker-Based)
  - Custom Mock Servers for gRPC

### 📦 Module 7.3: Architecture Testing
- **Import Enforcement**
  - `eslint-plugin-boundaries` (Enforce Module Dependency Rules)
  - `dependency-cruiser` (Visualize and Validate Dependencies)
  - Custom ESLint Rules for Architecture
  - DDD Pattern Enforcement (Domain Must Not Import Infrastructure)
  - Module Independence Rules
- **NestJS Module Verification**
  - Verify Module Imports and Exports Are Correct
  - Verify Circular Dependencies Don't Exist

### 📦 Module 7.4: Performance & Chaos Testing
- **Load Testing**
  - k6 (JavaScript-Based — Recommended)
    - Scenarios, Thresholds, Checks
    - Virtual Users, Ramp-Up, Duration
  - Autocannon (Node.js HTTP Benchmarking)
  - Artillery (YAML-Based Load Testing)
  - Gatling (Awareness)
- **Performance Testing Strategy**
  - Baseline Establishment
  - Stress Testing, Spike Testing, Soak Testing
  - Performance Budgets
- **Chaos Engineering**
  - Failure Injection in NestJS
    - Random Latency Injection (Custom Interceptor)
    - Random Exception Injection
    - Resource Exhaustion Simulation
  - Chaos Toolkit (Awareness)
  - GameDay Planning and Execution

### 📦 Module 7.5: Testing Strategy & Best Practices
- Test Pyramid (Unit → Integration → E2E) in Microservices
- Testing Honeycomb (Spotify Model)
- Test Data Management
- Test Isolation Strategies
- Flaky Test Management
- Testing in CI/CD Pipelines (Parallelization, Fast Feedback)
- Coverage Strategy (Meaningful Coverage, Not Line Count)

> ### 🛠 Phase 7 Milestone Project: **Comprehensive Test Suite for Food Delivery Platform**
> Retrofit the Phase 5 project with: full unit tests (Vitest/Jest + provider overrides), integration tests with Testcontainers (PostgreSQL, Kafka, Redis), `supertest` E2E tests for full request pipeline, contract tests with Pact, `dependency-cruiser` rules for architecture enforcement, k6 load tests for critical APIs, chaos testing interceptor (random latency/failure injection). Greater than 85% meaningful coverage. All tests run in CI/CD with separate stages (unit → integration → contract → E2E).

---

## 🔶 PHASE 8: DevOps, Observability & Production Readiness
> **Goal:** Deploy, monitor, and operate NestJS applications in production with confidence.

---

### 📦 Module 8.1: Containerization & Kubernetes Deployment
- **Docker Best Practices for NestJS**
  - Multi-Stage Dockerfile
    - Stage 1: Install Dependencies (`pnpm install --frozen-lockfile`)
    - Stage 2: Build TypeScript (`nest build` or `tsc`)
    - Stage 3: Production Image (Only `dist/` + `node_modules` + `package.json`)
  - Base Image Selection (`node:20-slim` or `node:20-alpine`)
  - Non-Root User (`node`)
  - `NODE_ENV=production` (Skip devDependencies)
  - Health Check in Dockerfile
  - `.dockerignore` Optimization
  - Layer Caching for Dependencies
  - pnpm in Docker (Multi-Stage with `pnpm deploy`)
- **Kubernetes Deployment**
  - Deployment, Service, Ingress YAML Manifests
  - ConfigMaps and Secrets for `process.env`
  - Readiness Probes (`@nestjs/terminus` Health Checks)
  - Liveness Probes
  - Startup Probes (For Slow-Starting Services)
  - Graceful Shutdown
    - `app.enableShutdownHooks()`
    - `OnModuleDestroy`, `BeforeApplicationShutdown` Lifecycle Hooks
    - Connection Draining (Close DB Pools, Finish In-Flight Requests)
  - Resource Requests and Limits
  - Horizontal Pod Autoscaler (HPA)
- **Health Checks with `@nestjs/terminus`**
  - `HealthCheckService`, `@HealthCheck()`
  - Built-in Indicators: `TypeOrmHealthIndicator`, `HttpHealthIndicator`, `DiskHealthIndicator`, `MemoryHealthIndicator`
  - Custom Health Indicators
  - Separate Readiness vs Liveness Endpoints
- **Helm Charts for NestJS Services**
- **Kubernetes-Native NestJS**
  - Config via ConfigMaps → Environment Variables → `@nestjs/config`
  - Service Discovery via Kubernetes DNS

### 📦 Module 8.2: CI/CD Pipeline Design
- **CI Pipeline (GitHub Actions)**
  - Lint (ESLint) → Type Check (`tsc --noEmit`) → Unit Test → Integration Test (Testcontainers) → Security Scan (`npm audit`, Snyk) → Contract Test → Build (`nest build`) → Docker Build → Push to Registry
  - Dependency Vulnerability Scanning
  - Quality Gates (Type Check, Lint, Coverage Threshold)
  - Artifact Promotion Strategy (Dev → Staging → Prod)
- **CD Pipeline**
  - Blue/Green Deployments
  - Canary Releases (with Kubernetes or API Gateway)
  - Rolling Deployments
  - Feature Flags (Unleash, LaunchDarkly, or Custom with Redis + NestJS Guard)
  - Database Migration in CI/CD (TypeORM/Prisma/Drizzle as Pipeline Step)
- **GitOps**
  - ArgoCD (Declarative, Git-as-Source-of-Truth)
  - Sync Policies, Health Checks, Rollback
  - Separate App Repo vs Config Repo

### 📦 Module 8.3: Infrastructure as Code
- Terraform for NestJS Infrastructure
  - AWS/GCP/Azure Resources (RDS, ElastiCache, EKS/GKE, VPC, MSK)
  - State Management (Remote Backend, Locking)
  - Modules for Reusability
  - Workspaces for Environment Separation
- Ansible (Configuration Management — Awareness)
- Policy as Code (OPA — Awareness)

### 📦 Module 8.4: Observability — The Three Pillars
- **Structured Logging**
  - `nestjs-pino` (Pino Integration for NestJS — Preferred)
    - Auto-Log Requests and Responses
    - Correlation IDs (Auto-Generated or Propagated)
    - Child Loggers per Request
    - JSON Output for Production
    - `pino-pretty` for Development
  - NestJS Built-in Logger (`Logger` Class — Basic)
  - Custom Logger (Implement `LoggerService` Interface)
  - Log Aggregation
    - ELK Stack (Elasticsearch, Logstash, Kibana)
    - Loki + Grafana (Lightweight)
  - Logging Best Practices (What to Log, What NOT to Log)
- **Metrics**
  - Prometheus Client (`prom-client`)
    - Custom Metrics (Counters, Gauges, Histograms, Summaries)
    - `/metrics` Endpoint
  - `@willsoto/nestjs-prometheus` (NestJS Prometheus Module)
    - Auto-Instrumentation (Request Count, Duration)
    - Custom Metric Decorators
  - Grafana Dashboards
    - RED Metrics (Rate, Errors, Duration)
    - USE Metrics (Utilization, Saturation, Errors)
  - SLIs, SLOs, SLAs, and Error Budgets
  - Business Metrics
- **Distributed Tracing**
  - OpenTelemetry for Node.js (`@opentelemetry/sdk-node`)
    - Auto-Instrumentation (`@opentelemetry/auto-instrumentations-node`)
      - HTTP, Express/Fastify, gRPC, Database, Redis Instrumentation
    - Manual Spans
    - Trace Context Propagation (W3C Trace Context)
    - Baggage Propagation
  - `nestjs-otel` (NestJS OpenTelemetry Module)
    - `@Span()` Decorator (Custom Spans)
    - `TraceService` (Manual Tracing)
  - Trace Exporters (Jaeger, Zipkin, OTLP)
  - Correlating Logs with Traces (Trace ID in Log Entries via `nestjs-pino`)
- **Alerting**
  - Alertmanager (Prometheus)
  - Alert Design (Symptom-Based, Not Cause-Based)
  - Runbooks for Each Alert
  - On-Call and Incident Response
- **Dashboarding**
  - Service Health, Business Metrics, Infrastructure Dashboards
  - Dashboard-as-Code (Grafana Provisioning)

### 📦 Module 8.5: Production Readiness Checklist
- Health Checks (Readiness, Liveness, Startup — `@nestjs/terminus`)
- Graceful Shutdown (`enableShutdownHooks`, Lifecycle Hooks)
- Circuit Breakers on All External Calls
- Structured JSON Logging with Trace IDs (`nestjs-pino`)
- Metrics Exposed and Dashboarded (`/metrics`)
- Alerts Configured with Runbooks
- Database Migrations Automated
- Secrets Externalized
- Security Headers (Helmet) and OWASP Hardening
- Rate Limiting (`@nestjs/throttler`)
- Load Tested to Expected Capacity
- Disaster Recovery Plan Documented
- Rollback Strategy Defined and Tested
- Swagger Disabled in Production (or Auth-Protected)

> ### 🛠 Phase 8 Milestone Project: **Production-Ready Deployment Pipeline**
> Take the Food Delivery Platform and make it production-ready:
> - Dockerized with multi-stage builds, deployed to Kubernetes (Minikube/Kind or cloud)
> - Helm charts for all services
> - `@nestjs/terminus` health checks (readiness, liveness) for every service
> - Graceful shutdown with `enableShutdownHooks`
> - Full CI/CD pipeline (GitHub Actions → ArgoCD)
> - Terraform for infrastructure (RDS, ElastiCache, EKS)
> - Full observability: `nestjs-pino` JSON logs → Loki, `@willsoto/nestjs-prometheus` → Prometheus → Grafana, OpenTelemetry traces → Jaeger
> - Alerting with Prometheus Alertmanager (error rate, latency P99)
> - Grafana dashboards (RED metrics per service, business metrics)
> - Feature flags with Redis-based Guard
> - Canary deployment for one service
> - Production readiness checklist verified for all services

---
---

## 🏗️ CAPSTONE PROJECT: Real-Time E-Commerce Platform
> **This is the Phase 2 capstone — it ties everything together.**
>
> Build a distributed e-commerce system with:
>
> - **Modular monolith with clear bounded contexts** (Catalog, Orders, Payments, Notifications) — NestJS Modules with strict import/export boundaries, verified by `dependency-cruiser`
> - **Hexagonal Architecture** within each bounded context (domain layer has zero NestJS dependencies, Nx monorepo with `libs/domain`, `libs/application`, `libs/infrastructure`)
> - **DDD tactical patterns** (Aggregates, Value Objects, Domain Events via `@nestjs/event-emitter`, Repositories behind abstract class interfaces wired with `useClass` providers)
> - **CQRS** with `@nestjs/cqrs` — Commands for writes, Queries for reads, Event Handlers for projections
> - **Event-driven communication** between modules (Kafka via `@nestjs/microservices` Kafka transport)
> - **Saga pattern** for order processing flow (Order → Payment → Inventory → Notification) with `@Saga()` and compensating transactions
> - **Outbox pattern** for reliable event publishing (TypeORM outbox table → CDC → Kafka)
> - **OAuth 2.0 + JWT** authentication (Passport JWT + Keycloak integration)
> - **API Gateway** (NestJS Gateway service or Traefik/Kong) with `@nestjs/throttler` rate limiting
> - **GraphQL API** for storefront queries (code-first with `@nestjs/graphql`, DataLoader, subscriptions for real-time inventory) + REST API for admin operations
> - **gRPC** for internal inter-service communication
> - **WebSocket gateway** for real-time order tracking (Socket.IO with Redis adapter)
> - **PostgreSQL + Redis + Elasticsearch** (each bounded context owns its data)
> - **Resilience patterns** — `opossum` circuit breakers, RxJS retry interceptors, bulkhead with `p-limit`
> - **BullMQ** for background jobs (email notifications, report generation)
> - **Full CI/CD pipeline** with canary deployments (GitHub Actions → ArgoCD)
> - **OpenTelemetry** distributed tracing + Prometheus metrics + Grafana dashboards
> - **Terraform** for infrastructure
> - **`@nestjs/terminus`** health checks, graceful shutdown, `nestjs-pino` structured logging
> - **Comprehensive test suite** — unit (provider overrides), integration (Testcontainers + `supertest`), contract (Pact), load (k6), architecture (`dependency-cruiser`)
> - **Architecture Decision Records (ADRs)** and **C4 diagrams** (Structurizr)
> - **Event Storming artifacts** documented
> - **AsyncAPI specs** for all event contracts
> - **Production readiness** checklist verified for every service
>
> **Why:** Covers DDD, event-driven architecture, distributed systems patterns, security, DevOps, observability, API design (REST + GraphQL + gRPC + WebSocket), and testing in one cohesive project that demonstrates mastery of Phase 2 with NestJS.

---

## ✅ After Completing This Roadmap — You Can:
- Understand Express/Fastify internals and what NestJS automates
- Build production-grade NestJS applications with the full request lifecycle mastered
- Leverage NestJS DI, Modules, Guards, Pipes, Interceptors, and Exception Filters expertly
- Design and implement Hexagonal / Clean Architecture in NestJS
- Model domains using DDD (strategic + tactical)
- Implement CQRS with `@nestjs/cqrs` (Commands, Queries, Events, Sagas)
- Build and operate microservices with `@nestjs/microservices` (TCP, gRPC, Kafka, RabbitMQ)
- Implement event-driven systems with Kafka, RabbitMQ, and BullMQ
- Apply Event Sourcing and Saga patterns
- Secure applications with Passport, JWT, OAuth 2.0, RBAC, ABAC, CASL
- Design excellent REST, GraphQL, gRPC, and WebSocket APIs
- Master enterprise integration patterns
- Implement resilience patterns (circuit breakers, retries, bulkheads)
- Deploy to Kubernetes with CI/CD and GitOps
- Build full observability (pino logging, Prometheus metrics, OpenTelemetry tracing, alerting)
- Write comprehensive tests at every layer
- Make and document architectural decisions (ADRs)
- Facilitate Event Storming sessions
- Create C4 architecture diagrams
- Choose and justify architectural styles for given requirements
- **You are ready for Phase 3: Cloud-Native Mastery & Leadership**

---

## 📋 Quick Reference Summary

```
Phase  0  ➜  Node.js Web Foundations (Express/Fastify)   🟤
Phase  1  ➜  NestJS Core                                 🟢
Phase  2  ➜  Data Access & Persistence                   🔵
Phase  3  ➜  Security                                    🟡
Phase  4  ➜  Architecture & DDD                          🟠
Phase  5  ➜  Microservices & Distributed Systems         🔴
Phase  6  ➜  API Design & Integration                    🟣
Phase  7  ➜  Testing at Scale                            ⚫
Phase  8  ➜  DevOps, Observability & Production          🔶
       🏗️  ➜  CAPSTONE: E-Commerce Platform
```

> **⏱ Estimated Timeline:** 6–9 months (with consistent daily practice)
> **💡 Pro Tip:** NestJS gives you structure. Don't fight the structure — understand WHY each building block (Guard, Pipe, Interceptor, Filter) exists and WHEN each one is the right tool. If you understand the request lifecycle, you understand NestJS.
> **⚡ Key Principle:** NestJS is opinionated so you can focus on your domain, not your folder structure. But opinions aren't constraints — know when to deviate and document why (ADRs).

---

## How This Maps to the SE Roadmap Phase 2

| SE Roadmap Phase 2 Module | Covered In |
|---|---|
| 2.1 Architectural Styles (Monolith, Microservices, Event-Driven, Hexagonal, Clean, CQRS) | Phase 4 + Phase 5 |
| 2.2 Distributed Systems (Consistency, Resilience, Scalability, Distributed Data) | Phase 5 (Modules 5.5, 5.6, 5.7) |
| 2.3 API Design & Integration (REST, GraphQL, gRPC, WebSocket, EIP, Messaging) | Phase 6 + Phase 5 (Module 5.4) |
| 2.4 Security Architecture (OWASP, OAuth2, JWT, IAM, App Security) | Phase 3 |
| 2.5 DevOps & CI/CD (Pipelines, Deployments, IaC, Observability) | Phase 8 |
| 2.6 Domain-Driven Design (Strategic + Tactical DDD) | Phase 4 (Modules 4.3, 4.4) |
| Phase 2 Project: E-Commerce Platform | Capstone Project |

**Every topic from Phase 2 of the SE Roadmap is covered. Nothing is missing. Nothing is extra.**