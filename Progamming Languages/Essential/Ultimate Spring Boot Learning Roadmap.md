# ☘️ Spring Boot Mastery Roadmap — Phase 2: Architectural Thinking
> Picks up exactly where the Java Foundations Roadmap (Phase 1) ended. Starts with Phase 0 to establish Java web foundations before diving into Spring.
> Aligned with Phase 2 of the Software Engineering Mastery Roadmap.
> **Estimated Duration: 7–10 months**

---

## Prerequisites (Completed in Phase 1)
> ✅ Core Java (OOP, Collections, Generics, Streams, Lambdas, Concurrency)
> ✅ DSA fundamentals
> ✅ SOLID, Design Patterns, Clean Code
> ✅ SQL, JDBC, JPA/Hibernate basics
> ✅ Git, Maven/Gradle, JUnit/Mockito, CI/CD basics
> ✅ Docker, Docker Compose, Linux, Networking essentials
> ✅ Kubernetes concepts (awareness)

---

## ==🟤 PHASE 0: Java Web Foundations — Servlets & Jakarta EE Basics==
> **Goal:** Understand how Java handles HTTP at the lowest level — so you know exactly what Spring Boot abstracts away.
> **Duration:** ~2–3 weeks (focused)

---

### 📦 Module 0.1: How the Web Works (Java Perspective)
- Client-Server Model Recap
- HTTP Request/Response Lifecycle (from Browser to Server and Back)
- What is a Web Server vs Application Server
  - Apache Tomcat, Jetty, Undertow — What They Actually Do
  - Web Server (static content) vs Servlet Container (dynamic content)
- Java's Role in Web Development (Historical Context):
  - CGI → Servlets → JSP → Frameworks (Struts, JSF) → Spring MVC → Spring Boot
  - Why This Evolution Happened (Pain Points at Each Stage)
- Jakarta EE vs Java EE vs javax vs jakarta (Naming History)
- WAR Packaging vs Embedded Server (and Why Spring Boot Chose Embedded)

### 📦 Module 0.2: Servlet Fundamentals
- What is a Servlet (A Java Class That Handles HTTP)
- Servlet API (`jakarta.servlet` Package)
- `HttpServlet` Class:
  - `doGet()`, `doPost()`, `doPut()`, `doDelete()`
  - `HttpServletRequest`:
    - `getParameter()`, `getHeader()`, `getMethod()`
    - `getPathInfo()`, `getRequestURI()`, `getQueryString()`
    - `getInputStream()` / `getReader()` (Reading Request Body)
    - `getAttribute()` / `setAttribute()` (Request Scope Data)
    - `getSession()` (Session Access)
  - `HttpServletResponse`:
    - `setStatus()`, `setContentType()`, `setHeader()`
    - `getWriter()` / `getOutputStream()` (Writing Response Body)
    - `sendRedirect()`, `sendError()`
- Servlet Lifecycle:
  - `init()` → `service()` → `destroy()`
  - Single Instance, Multiple Threads (Thread Safety Implications)
  - Servlet Container Manages the Lifecycle (You Don't Call `new`)
- Servlet Configuration:
  - `web.xml` (Deployment Descriptor — Traditional)
  - `@WebServlet` Annotation (Modern)
  - URL Mapping Patterns (`/api/*`, `*.do`, `/`)
- `ServletContext` (Application-Wide Shared State)
- `ServletConfig` (Per-Servlet Configuration)

### 📦 Module 0.3: Building a REST API with Raw Servlets
- Setting Up a Servlet Project:
  - Maven Project with `jakarta.servlet-api` Dependency
  - Embedded Tomcat (No External Server — Using `org.apache.catalina.startup.Tomcat`)
  - OR Traditional WAR Deployed to Standalone Tomcat
- Handling Different HTTP Methods in One Servlet
- Parsing Path Parameters Manually (`/users/123` → Extract `123`)
- Reading JSON Request Body (Using Jackson/Gson Manually)
- Writing JSON Responses (Manual Serialization)
- Request Routing:
  - One Servlet Per Resource (Verbose)
  - Front Controller Pattern (Single Entry Point Servlet That Routes)
  - **💡 This is exactly what Spring's `DispatcherServlet` does**
- Error Handling:
  - `sendError()` with Status Codes
  - Error Pages in `web.xml`
  - Custom Error Response Bodies
- Pain Points You'll Feel:
  - Manual routing boilerplate
  - Manual JSON parsing/serialization
  - Manual parameter extraction and validation
  - No dependency injection
  - No declarative configuration
  - **These are the exact problems Spring solves**

### 📦 Module 0.4: Filters & Listeners
- **Filters (`jakarta.servlet.Filter`):**
  - `doFilter()` and `FilterChain`
  - Filter Ordering (Chain of Responsibility Pattern)
  - Use Cases:
    - Logging Filter (Log Every Request/Response)
    - Authentication Filter (Check Auth Header Before Servlet)
    - CORS Filter (Add CORS Headers)
    - Encoding Filter (Set Character Encoding)
  - `@WebFilter` Annotation
  - **💡 Spring Security's `SecurityFilterChain` is built on this exact mechanism**
- **Listeners:**
  - `ServletContextListener` (Application Startup/Shutdown)
  - `HttpSessionListener` (Session Created/Destroyed)
  - `ServletRequestListener` (Request Start/End)
  - `@WebListener` Annotation
  - **💡 Spring's `ApplicationListener` and `@EventListener` evolved from this**

### 📦 Module 0.5: Sessions, Cookies & State Management
- HTTP is Stateless (Recap)
- Cookies:
  - `Cookie` Class (`new Cookie(name, value)`)
  - `response.addCookie()`, `request.getCookies()`
  - Cookie Attributes (Max-Age, Path, Domain, Secure, HttpOnly, SameSite)
- Sessions (`HttpSession`):
  - `request.getSession()` / `request.getSession(false)`
  - `setAttribute()`, `getAttribute()`, `invalidate()`
  - Session ID (JSESSIONID Cookie)
  - Session Timeout Configuration
  - Session in Distributed Systems (Sticky Sessions, Session Replication, External Store)
  - **💡 Why Spring Boot defaults to Stateless for APIs (JWT instead of sessions)**

### 📦 Module 0.6: JSP — Just Enough to Understand (Not to Master)
- What is JSP (Java Server Pages)
- JSP is Compiled to a Servlet (Under the Hood)
- JSP Expressions, Scriptlets, Directives (Brief Overview)
- EL (Expression Language) & JSTL (Tag Libraries)
- MVC Pattern with Servlets + JSP:
  - Servlet as Controller
  - JSP as View
  - JavaBean / POJO as Model
  - `RequestDispatcher.forward()` — Forwarding to JSP
- **Why JSP Died:**
  - Mixing Logic and Presentation
  - Poor Testability
  - Rise of REST APIs + SPA Frontends (React, Angular, Vue)
  - Thymeleaf as Modern Server-Side Alternative (Awareness)
- **💡 You will NOT use JSP in modern development — but knowing it explains Spring MVC's `ViewResolver` and template engines**

### 📦 Module 0.7: Understanding What Spring Replaces
> **This is the most important module — connecting Servlets to Spring.**

- **Front Controller Pattern:**
  - Your manual routing servlet → Spring's `DispatcherServlet`
  - `DispatcherServlet` is literally a Servlet registered in the Servlet container
- **Manual DI → Spring IoC Container:**
  - In Servlets you `new` everything → Spring injects dependencies
- **Manual Routing → `@RequestMapping`:**
  - `if/else` on URL paths → Declarative annotations
- **Manual JSON Parsing → `@RequestBody` + Jackson:**
  - `ObjectMapper` in every servlet → Automatic serialization
- **Manual Validation → `@Valid` + Bean Validation:**
  - `if (name == null)` everywhere → Declarative constraints
- **Servlet Filters → Spring Security `SecurityFilterChain`:**
  - Same `Filter` interface, wrapped in Spring's security framework
- **`web.xml` → Auto-Configuration:**
  - Hundreds of lines of XML → Zero XML
- **WAR + External Tomcat → Embedded Tomcat:**
  - Deploy to server → `java -jar app.jar`
- **Mapping Table:**

  | Raw Servlet | Spring Boot Equivalent |
  |---|---|
  | `HttpServlet.doGet()` | `@GetMapping` |
  | `HttpServletRequest.getParameter()` | `@RequestParam` |
  | URL path parsing | `@PathVariable` |
  | `request.getReader()` + Jackson | `@RequestBody` |
  | `response.getWriter()` + Jackson | `@ResponseBody` / `ResponseEntity` |
  | `Filter.doFilter()` | `SecurityFilterChain` / `OncePerRequestFilter` |
  | `web.xml` URL mapping | `@RequestMapping` |
  | `ServletContextListener` | `@EventListener` / `ApplicationRunner` |
  | `HttpSession` | `SecurityContext` / JWT / Redis |
  | `RequestDispatcher.forward()` | `ViewResolver` + Thymeleaf |
  | Front Controller servlet | `DispatcherServlet` (auto-configured) |

> ### 🛠 Phase 0 Milestone Project: **Mini REST Framework**
> Build a bare-bones REST framework on top of raw Servlets:
> - **Front Controller Servlet** that routes requests by URL and HTTP method
> - **Custom `@Route` annotation** (your own!) that maps methods to URL patterns
>   - Use reflection to scan and register routes at startup (like Spring does)
> - **Automatic JSON serialization/deserialization** (Jackson integration)
> - **Filter chain** with Logging Filter + Simple Auth Filter (API key check)
> - **Session-based simple login** (just to understand sessions)
> - Implement a small CRUD API (e.g., Todo list) using YOUR framework
> - Embedded Tomcat (run with `java -jar`)
> - Then throw it all away and start Phase 1 with Spring Boot
>
> **Why:** You will deeply understand `DispatcherServlet`, `@RequestMapping`, `SecurityFilterChain`, auto-configuration, and DI — because you built crude versions yourself. When Spring does it, it's no longer magic. **You'll never be the developer who can't debug past the annotations.**

---

### ✅ After Phase 0 — You Understand:
- [ ] How HTTP requests flow through a Servlet container
- [ ] What `DispatcherServlet` actually does (because you built one)
- [ ] Why Filters matter (and how Spring Security uses them)
- [ ] Why DI and auto-configuration exist (because you felt the pain without them)
- [ ] The mapping between raw Servlet API and Spring annotations
- [ ] Why sessions gave way to JWTs for stateless APIs
- [ ] Why JSP died and REST APIs won
- [ ] **You're not learning Spring — you're learning what Spring automated**

---

## ==🟢 PHASE 1: Spring Framework & Spring Boot Core==
> **Goal:** Deeply understand Spring's foundation — IoC, DI, AOP — and Spring Boot's conventions.

### 📦 Module 1.1: Spring Framework Core
- What is Spring & Why It Exists
- Inversion of Control (IoC) Container
- Dependency Injection (Constructor, Setter, Field — and why Constructor wins)
- Bean Lifecycle (Instantiation → Populate → Init → Destroy)
- Bean Scopes (`singleton`, `prototype`, `request`, `session`)
- `ApplicationContext` vs `BeanFactory`
- Stereotype Annotations (`@Component`, `@Service`, `@Repository`, `@Controller`)
- Configuration Approaches (`@Configuration`, `@Bean`, `@ComponentScan`)
- `@Qualifier`, `@Primary`, `@Lazy`
- Profiles (`@Profile`) and Conditional Beans (`@Conditional`)
- SpEL (Spring Expression Language) — Basics
- AOP Fundamentals:
  - Cross-cutting concerns
  - Aspects, Pointcuts, Advice (Before, After, Around)
  - `@Aspect`, `@Around`, `@Before`, `@After`, `@AfterReturning`, `@AfterThrowing`
  - Proxy Mechanism (JDK Dynamic Proxy vs CGLIB)
  - Practical uses: Logging, Security, Transactions, Metrics

### 📦 Module 1.2: Spring Boot Fundamentals
- What Spring Boot Solves (Convention over Configuration)
- Spring Initializr & Project Scaffolding
- Auto-Configuration (`@EnableAutoConfiguration`, `spring.factories` / `AutoConfiguration.imports`)
- `@SpringBootApplication` Deconstructed
- Project Structure & Best Practices
- `application.properties` vs `application.yml`
- Configuration Binding (`@ConfigurationProperties`, `@Value`)
- Profiles & Environment-Specific Configuration
- Externalized Configuration (Precedence Order)
- Embedded Servers (Tomcat, Jetty, Undertow)
- Spring Boot DevTools (Live Reload, H2 Console)
- Actuator:
  - Health, Info, Metrics, Environment Endpoints
  - Custom Health Indicators
  - Custom Metrics with Micrometer
  - Securing Actuator Endpoints

### 📦 Module 1.3: Building REST APIs
- `@RestController` vs `@Controller`
- `@RequestMapping`, `@GetMapping`, `@PostMapping`, `@PutMapping`, `@DeleteMapping`, `@PatchMapping`
- `@PathVariable`, `@RequestParam`, `@RequestBody`, `@RequestHeader`
- `ResponseEntity<T>` & HTTP Status Codes
- Content Negotiation (JSON, XML)
- Request Validation (`@Valid`, `@NotNull`, `@NotBlank`, `@Size`, `@Pattern`, `@Email`, Custom Validators)
- Global Exception Handling:
  - `@ControllerAdvice` / `@RestControllerAdvice`
  - `@ExceptionHandler`
  - Problem Details (RFC 7807 / RFC 9457) — Spring Boot 3+
- DTO Pattern (Separating API Layer from Domain)
- Object Mapping (MapStruct vs ModelMapper — MapStruct preferred)
- Pagination & Sorting (`Pageable`, `Page<T>`, `Sort`)
- File Upload & Download
- API Versioning Strategies (URI, Header, Parameter)
- HATEOAS (`spring-hateoas`, Link, EntityModel)
- OpenAPI Documentation (`springdoc-openapi`, Swagger UI)

> ### 🛠 Phase 1 Milestone Project: **Task Management REST API**
> Full CRUD REST API for tasks & users: validation, global error handling (RFC 7807), DTOs with MapStruct, pagination, OpenAPI docs, Actuator health/metrics, profile-based config (dev/prod). Focus on clean layered architecture.

---

## ==🔵 PHASE 2: Data Access & Persistence==
> **Goal:** Master Spring Data JPA, advanced querying, performance tuning, and multi-database strategies.

### 📦 Module 2.1: Spring Data JPA — Deep Dive
- Repository Hierarchy (`Repository`, `CrudRepository`, `JpaRepository`, `PagingAndSortingRepository`)
- Derived Query Methods (naming conventions, limits, existence checks)
- Custom Queries (`@Query` with JPQL and Native SQL)
- Named Queries (`@NamedQuery`, `@NamedNativeQuery`)
- Projections (Interface-Based, Class-Based, Dynamic)
- Specifications (`Specification<T>`, Criteria API for dynamic queries)
- Query by Example (QBE)
- Auditing (`@CreatedDate`, `@LastModifiedDate`, `@CreatedBy`, `@LastModifiedBy`, `AuditorAware`)
- Soft Deletes (Implementation Strategies with `@Where` / `@SQLDelete`)
- Custom Repository Implementations

### 📦 Module 2.2: Entity Modeling & Relationships
- Entity Lifecycle (Transient, Managed, Detached, Removed)
- Relationships Deep Dive:
  - `@OneToOne` (Shared PK, Join Column, Join Table)
  - `@OneToMany` / `@ManyToOne` (Bidirectional pitfalls, `mappedBy`)
  - `@ManyToMany` (Join Table customization)
- Cascade Types (`PERSIST`, `MERGE`, `REMOVE`, `ALL` — and the orphanRemoval trap)
- Fetch Strategies:
  - Lazy vs Eager Loading
  - The N+1 Problem (Detection & Solutions)
  - `@EntityGraph` and `JOIN FETCH`
  - `@BatchSize`
- Inheritance Strategies (`SINGLE_TABLE`, `TABLE_PER_CLASS`, `JOINED`)
- Embeddables (`@Embedded`, `@Embeddable`)
- Value Objects as Embeddables
- Composite Keys (`@EmbeddedId`, `@IdClass`)

### 📦 Module 2.3: Transactions & Performance
- `@Transactional` Deep Dive:
  - Propagation Levels (`REQUIRED`, `REQUIRES_NEW`, `NESTED`, `SUPPORTS`, `MANDATORY`, `NEVER`)
  - Isolation Levels
  - Read-Only Transactions (Performance Benefits)
  - Rollback Rules (`rollbackFor`, `noRollbackFor`)
  - Proxy Pitfalls (Self-Invocation Problem)
- First-Level Cache (Persistence Context) vs Second-Level Cache (Ehcache, Caffeine)
- Query Performance:
  - Indexing Strategies (Aligned with Phase 1 DB knowledge)
  - Batch Insert/Update (`hibernate.jdbc.batch_size`)
  - `EXPLAIN ANALYZE` in Practice
  - DTO Projections for Read-Heavy Queries
  - Pagination Performance (Keyset Pagination vs Offset)
- Connection Pooling Tuning (HikariCP Configuration)
- Database Migration Tools:
  - Flyway (Versioned Migrations, Repeatable Migrations, Callbacks)
  - Liquibase (Changesets, Rollbacks)
  - Zero-Downtime Migration Strategies (Expand/Contract Pattern)

### 📦 Module 2.4: Beyond JPA — Other Data Access
- Spring Data Redis:
  - `RedisTemplate`, `StringRedisTemplate`
  - `@Cacheable`, `@CacheEvict`, `@CachePut` (Spring Cache Abstraction)
  - Cache-Aside, Write-Through, Write-Behind Patterns
  - TTL Strategies and Cache Invalidation
  - Redis Data Structures (String, Hash, List, Set, Sorted Set) in Spring
  - Session Storage with Redis
- Spring Data MongoDB (Awareness):
  - `MongoTemplate`, `MongoRepository`
  - Document Modeling in Spring
- Spring Data Elasticsearch (Awareness):
  - Full-Text Search Use Cases
  - `ElasticsearchRepository`

> ### 🛠 Phase 2 Milestone Project: **E-Commerce Product Catalog Service**
> Product catalog with categories, variants, and search. Spring Data JPA with complex relationships, entity graphs for N+1 resolution, Flyway migrations, Redis caching layer, Elasticsearch for product search, pagination (keyset + offset), auditing, and query performance benchmarks.

---

## ==🟡 PHASE 3: Security==
> **Goal:** Implement production-grade security — authentication, authorization, OAuth2, and application hardening.

### 📦 Module 3.1: Spring Security Fundamentals
- Security Filter Chain Architecture
- `SecurityFilterChain` Bean Configuration (Modern — no `WebSecurityConfigurerAdapter`)
- Authentication vs Authorization
- `UserDetailsService` and `UserDetails`
- Password Encoding (`BCryptPasswordEncoder`, `Argon2PasswordEncoder`)
- In-Memory, JDBC, and Custom Authentication Providers
- Form-Based Login & HTTP Basic Auth
- Session Management (Stateful vs Stateless)
- Security Context & `SecurityContextHolder`
- Method Security (`@PreAuthorize`, `@PostAuthorize`, `@Secured`, `@RolesAllowed`)

### 📦 Module 3.2: JWT Authentication (Stateless)
- JWT Structure (Header, Payload, Signature)
- JWT Generation, Validation, and Expiration
- Refresh Token Strategy (Rotation, Revocation)
- Custom JWT Authentication Filter
- Token Blacklisting (Redis-Based)
- Stateless Session Configuration
- JWT Pitfalls and Best Practices

### 📦 Module 3.3: OAuth 2.0 & OpenID Connect
- OAuth 2.0 Flows:
  - Authorization Code + PKCE (SPAs, Mobile)
  - Client Credentials (Service-to-Service)
  - Resource Owner Password (Legacy — Know Why to Avoid)
- OpenID Connect (ID Token, UserInfo Endpoint)
- Spring Authorization Server (Building Your Own Auth Server)
- Spring OAuth2 Resource Server:
  - JWT Decoder Configuration
  - Opaque Token Introspection
  - Scope/Authority Mapping
- Spring OAuth2 Client:
  - Social Login (Google, GitHub)
  - `OAuth2AuthorizedClientManager`
- SSO (Single Sign-On) Implementation
- Integration with External IdPs (Keycloak, Auth0, Okta)

### 📦 Module 3.4: Authorization Patterns
- RBAC (Role-Based Access Control) Implementation
- ABAC (Attribute-Based Access Control) with Custom `PermissionEvaluator`
- Resource-Level Authorization (Users can only access their own data)
- Dynamic Permissions (Database-Driven Roles and Permissions)
- Multi-Tenancy Security Considerations
- API Key Authentication (for Service-to-Service)

### 📦 Module 3.5: Application Security Hardening
- OWASP Top 10 — Spring Boot Mitigations:
  - SQL Injection Prevention (Parameterized Queries — already via JPA)
  - XSS Prevention (Output Encoding, Content Security Policy)
  - CSRF Protection (When to Enable/Disable)
  - Mass Assignment Protection (DTOs, `@JsonIgnore`)
  - Insecure Direct Object References (IDOR)
- CORS Configuration (`CorsConfigurationSource`)
- Security Headers (HSTS, X-Frame-Options, X-Content-Type-Options)
- Rate Limiting (Bucket4j, Resilience4j RateLimiter)
- Input Validation as a Security Layer
- Secrets Management (Environment Variables, Spring Cloud Config, Vault — Awareness)
- Dependency Vulnerability Scanning (OWASP Dependency-Check, Snyk in CI/CD)

> ### 🛠 Phase 3 Milestone Project: **Secure Multi-Tenant User Platform**
> User registration/login, JWT with refresh tokens, OAuth2 social login (Google), RBAC + resource-level authorization, rate limiting, CORS, security headers, OWASP hardening, Keycloak integration. Full security test suite.

---

## 🟠 PHASE 4: Architecture & Domain-Driven Design
> **Goal:** Apply architectural styles, DDD, and modular design within Spring Boot applications.

### 📦 Module 4.1: Layered & Modular Architecture in Spring Boot
- Traditional Layered Architecture (Controller → Service → Repository)
  - Pros, Cons, and When It Breaks Down
- Package-by-Feature vs Package-by-Layer
- Modular Monolith in Spring Boot:
  - Vertical Slicing by Business Domain
  - Module Boundaries with Package-Private Visibility
  - Spring Modulith:
    - `@ApplicationModule`
    - Module API (Public) vs Internals (Package-Private)
    - Module Dependency Rules and Verification Tests
    - Module Interaction via Events
  - Internal vs Published Events

### 📦 Module 4.2: Clean Architecture & Hexagonal Architecture in Spring
- Hexagonal Architecture (Ports & Adapters):
  - Domain Layer (Entities, Value Objects, Domain Services — No Spring Dependencies)
  - Application Layer (Use Cases, Port Interfaces)
  - Infrastructure Layer (Adapters: JPA, REST, Messaging)
  - Port Interfaces (Driving Ports / Driven Ports)
- Clean Architecture (Uncle Bob):
  - Dependency Rule (Dependencies Point Inward)
  - Entities → Use Cases → Interface Adapters → Frameworks
- Onion Architecture (Comparison)
- Practical Implementation in Spring Boot:
  - Multi-Module Maven/Gradle Project
  - Domain Module has ZERO Spring dependencies
  - Infrastructure Module provides implementations
  - Wiring with Spring DI
- Trade-offs: When Hexagonal is Overkill

### 📦 Module 4.3: Strategic DDD
- Ubiquitous Language (Building a Shared Vocabulary)
- Domain Discovery (Big Picture Event Storming)
- Bounded Contexts:
  - Identification and Definition
  - Mapping to Spring Modules / Services
- Context Mapping Patterns:
  - Shared Kernel
  - Customer-Supplier
  - Conformist
  - Anti-Corruption Layer (ACL)
  - Open Host Service / Published Language
  - Partnership
  - Separate Ways
- Subdomain Classification:
  - Core Domain (Competitive Advantage — Maximum Investment)
  - Supporting Subdomain (Necessary but Not Differentiating)
  - Generic Subdomain (Buy / Use Off-the-Shelf)
- Event Storming:
  - Big Picture Event Storming
  - Design-Level Event Storming
  - Identifying Commands, Events, Aggregates, Policies

### 📦 Module 4.4: Tactical DDD in Spring Boot
- Entities (Identity, Lifecycle, Equality by ID)
- Value Objects (Immutable, Equality by Value, Self-Validating)
  - Implementing as Java Records or `@Embeddable`
- Aggregates & Aggregate Roots:
  - Consistency Boundaries
  - Aggregate Design Rules (Small Aggregates, Reference by ID)
  - Transactional Boundaries = Aggregate Boundaries
- Domain Events:
  - `AbstractAggregateRoot` and `@DomainEvents` in Spring Data
  - `ApplicationEventPublisher`
  - Event-Driven Between Bounded Contexts
  - Event Naming Conventions (Past Tense: `OrderPlaced`, `PaymentReceived`)
- Repositories (Domain-Oriented, Not CRUD-Oriented):
  - Repository as a Domain Concept
  - Implementing with Spring Data JPA
  - Collection-Oriented vs Persistence-Oriented
- Domain Services (Stateless Business Logic Across Aggregates)
- Application Services (Use Cases — Orchestrate Domain Objects):
  - Transaction Boundaries
  - DTO ↔ Domain Mapping at This Layer
- Factories (Complex Aggregate Creation)
- Specifications Pattern (Business Rules as Objects)
- Domain Model Purity (No Framework Annotations in Domain Layer — Ideal vs Pragmatic)

### 📦 Module 4.5: Architecture Decision Records
- ADR Structure (Title, Status, Context, Decision, Consequences)
- When to Write an ADR
- Lightweight ADR Templates (Michael Nygard)
- ADR as Living Documentation
- Connecting ADRs to Code

> ### 🛠 Phase 4 Milestone Project: **Order Management System (DDD + Hexagonal)**
> Model an order domain using DDD: Bounded Contexts (Orders, Inventory, Payments), Aggregates, Value Objects, Domain Events. Implement with Hexagonal Architecture in a multi-module Spring Boot project using Spring Modulith. Event-driven communication between modules. ADRs for all major decisions. Event Storming artifacts documented.

---

## 🔴 PHASE 5: Microservices & Distributed Systems
> **Goal:** Decompose, communicate, and manage services at scale with Spring Cloud and distributed systems patterns.

### 📦 Module 5.1: Microservices Fundamentals
- Monolith-First Strategy (Why and When to Decompose)
- Service Decomposition Strategies:
  - By Business Capability
  - By Subdomain (DDD Bounded Contexts)
- Database-Per-Service Pattern
- Shared Nothing Architecture
- Microservice Size (Not About Lines of Code — About Team Ownership)
- Strangler Fig Pattern (Incremental Migration from Monolith)

### 📦 Module 5.2: Synchronous Communication
- Inter-Service Communication with REST:
  - `RestClient` (Spring Boot 3.2+ — Preferred)
  - `WebClient` (Reactive/Non-Blocking)
  - `RestTemplate` (Legacy — Know Why to Avoid)
  - OpenFeign Declarative Clients (`@FeignClient`)
- gRPC with Spring Boot:
  - Protocol Buffers (`.proto` Files, Code Generation)
  - Unary, Server-Streaming, Client-Streaming, Bidirectional
  - `grpc-spring-boot-starter`
  - gRPC vs REST (When to Use What)
- Service Discovery:
  - Netflix Eureka (Self-Registration, Client-Side Discovery)
  - Consul (Awareness)
  - Kubernetes-Native Service Discovery (Why You May Not Need Eureka)
- API Gateway:
  - Spring Cloud Gateway:
    - Route Predicates and Filters
    - Rate Limiting (Redis-Based)
    - Circuit Breaking at Gateway Level
    - Request/Response Transformation
    - Load Balancing
  - BFF (Backend for Frontend) Pattern

### 📦 Module 5.3: Asynchronous & Event-Driven Communication
- Synchronous vs Asynchronous Trade-offs
- Event-Driven Architecture Concepts:
  - Events vs Commands vs Queries
  - Choreography vs Orchestration
- Apache Kafka with Spring:
  - `spring-kafka`: Producer, Consumer, Topics, Partitions, Consumer Groups
  - `@KafkaListener`, `KafkaTemplate`
  - Serialization (JSON, Avro with Schema Registry)
  - Error Handling (Dead Letter Topics, Retry Topics)
  - Exactly-Once Semantics (Idempotent Producers, Transactions)
  - Ordering Guarantees (Partition Keys)
  - Kafka Streams with Spring (Awareness)
- RabbitMQ with Spring:
  - `spring-amqp`: Exchanges (Direct, Topic, Fanout, Headers)
  - Bindings, Queues, Routing Keys
  - `@RabbitListener`, `RabbitTemplate`
  - Dead Letter Exchanges
  - Message Acknowledgment Modes
- Event Sourcing:
  - Event Store Design
  - Projections (Building Read Models from Events)
  - Snapshots (Performance Optimization)
  - Rebuilding State from Events
- CQRS (Command Query Responsibility Segregation):
  - Separate Write Model (Commands) and Read Model (Queries)
  - Eventual Consistency Between Write and Read Sides
  - CQRS + Event Sourcing Together
  - When CQRS is Overkill
- Saga Pattern:
  - Choreography-Based Sagas (Events)
  - Orchestration-Based Sagas (Saga Orchestrator)
  - Compensating Transactions (Undo Logic)
  - Implementing with Spring State Machine or Custom

### 📦 Module 5.4: Resilience & Fault Tolerance
- Fallacies of Distributed Computing (Peter Deutsch)
- Resilience4j with Spring Boot:
  - Circuit Breaker (`@CircuitBreaker`, States: CLOSED → OPEN → HALF_OPEN)
  - Retry (`@Retry`, Exponential Backoff with Jitter)
  - Rate Limiter (`@RateLimiter`)
  - Bulkhead (`@Bulkhead`, Semaphore vs Thread Pool)
  - Time Limiter (`@TimeLimiter`)
  - Combining Multiple Patterns (Decoration Order Matters)
  - Monitoring with Actuator + Micrometer
- Idempotency:
  - Idempotency Keys
  - Idempotent REST APIs (PUT vs POST)
  - Idempotent Consumers (Deduplication)
- Timeout Strategies
- Graceful Degradation (Fallback Responses, Cached Defaults)
- Failover Strategies (Active-Passive, Active-Active)

### 📦 Module 5.5: Distributed Data Patterns
- Consistency Models (Strong, Eventual, Causal, Read-Your-Writes)
- CAP Theorem & PACELC (Revisited in Practice)
- Distributed Transactions:
  - 2PC (Two-Phase Commit) — Why to Avoid in Microservices
  - Sagas (Preferred — Already Covered Above)
- Data Partitioning (Hash, Range, Geographic)
- Replication Strategies (Leader-Follower, Multi-Leader, Leaderless)
- Change Data Capture (CDC):
  - Debezium with Kafka Connect
  - Outbox Pattern (`TransactionalOutbox` → CDC → Kafka)
- Conflict Resolution (Last-Write-Wins, CRDTs — Concepts)

### 📦 Module 5.6: Scalability Patterns
- Horizontal vs Vertical Scaling
- Stateless Service Design (Why and How)
- Caching Strategies (Cache-Aside, Write-Through, Write-Behind, Read-Through)
- Cache Invalidation Strategies
- Rate Limiting & Throttling (Token Bucket, Leaky Bucket, Sliding Window)
- Backpressure Mechanisms
- Connection Pooling and Resource Management
- Database Read Replicas and Query Routing

### 📦 Module 5.7: Configuration & Coordination
- Centralized Configuration:
  - Spring Cloud Config Server (Git-Backed)
  - Spring Cloud Config Client
  - Refresh Scope (`@RefreshScope`, `/actuator/refresh`)
  - Bus Refresh (Spring Cloud Bus + RabbitMQ/Kafka)
  - Alternatives: Consul KV, Kubernetes ConfigMaps
- Distributed Coordination:
  - Leader Election Concepts
  - Distributed Locking (Redis-Based: Redisson, `spring-integration`)

> ### 🛠 Phase 5 Milestone Project: **Food Delivery Platform (Microservices)**
> Decompose into services: User, Restaurant, Order, Delivery, Payment, Notification.
> - Spring Cloud Gateway + Eureka
> - Kafka for async events (OrderPlaced → PaymentProcessed → DeliveryAssigned)
> - Saga pattern for order flow (Orchestration)
> - Resilience4j circuit breakers on all inter-service calls
> - CQRS for restaurant search (write to PostgreSQL, read from Elasticsearch)
> - Outbox pattern with Debezium for reliable event publishing
> - Spring Cloud Config for centralized configuration
> - Each service has its own database (PostgreSQL)
> - Redis caching for restaurant menus

---

## 🟣 PHASE 6: API Design & Integration Patterns
> **Goal:** Design excellent APIs and master enterprise integration patterns.

### 📦 Module 6.1: REST API Design Excellence
- REST Maturity Model (Richardson's Levels 0–3)
- Resource Naming Conventions (Nouns, Not Verbs)
- Proper HTTP Method Usage (Idempotency Matrix)
- Pagination Patterns (Offset, Cursor/Keyset, Page-Based)
- Filtering, Sorting, Field Selection
- Bulk Operations API Design
- Partial Updates (PATCH with JSON Merge Patch / JSON Patch)
- Error Response Standards (RFC 7807 Problem Details)
- API Versioning (URI Path vs Header vs Media Type)
- API-First Design Approach:
  - OpenAPI Spec First → Generate Code
  - Contract-First vs Code-First Trade-offs
- HATEOAS (When It Adds Value)

### 📦 Module 6.2: GraphQL with Spring
- GraphQL Concepts (Schema, Types, Queries, Mutations, Subscriptions)
- Spring for GraphQL:
  - Schema Definition (SDL)
  - `@QueryMapping`, `@MutationMapping`, `@SchemaMapping`
  - `@BatchMapping` (Solving N+1)
  - DataLoader Pattern
  - Input Validation
  - Error Handling
  - Authentication & Authorization in GraphQL
- GraphQL vs REST — Decision Framework
- GraphQL Federation (Awareness)

### 📦 Module 6.3: Integration Patterns (Enterprise Integration Patterns)
- Core EIP Patterns (Hohpe & Woolf):
  - Message Channel
  - Message Router (Content-Based Router)
  - Message Translator
  - Aggregator, Splitter
  - Dead Letter Channel
  - Wire Tap
- Spring Integration:
  - Channels, Endpoints, Transformers, Routers, Filters
  - Integration Flows (Java DSL)
  - File, HTTP, JMS, Kafka Adapters
- Request-Reply, Publish-Subscribe, Point-to-Point
- Webhooks and Callback Patterns
- Polling vs Push Strategies
- Anti-Corruption Layer (Implementation with Spring)
- AsyncAPI for Event-Driven API Documentation

### 📦 Module 6.4: Contract Testing & API Governance
- Consumer-Driven Contract Testing:
  - Spring Cloud Contract:
    - Contract DSL (Groovy/YAML)
    - Producer-Side Verification (Auto-Generated Tests)
    - Consumer-Side Stubs (WireMock)
  - Pact (Awareness)
- API Linting and Standards Enforcement
- API Lifecycle Management

> ### 🛠 Phase 6 Milestone Project: **API Gateway Platform**
> Build a unified API platform: REST API (OpenAPI-first) + GraphQL API for the same domain, Spring Integration for external system adapters (webhook receiver, file import), consumer-driven contract tests (Spring Cloud Contract), API documentation portal.

---

## ⚫ PHASE 7: Testing at Scale
> **Goal:** Master every layer of testing for Spring Boot — from unit to contract to performance.

### 📦 Module 7.1: Spring Boot Testing Foundations
- `@SpringBootTest` (Full Context, Sliced Context, Web Environment)
- Test Slices:
  - `@WebMvcTest` (Controller Layer)
  - `@DataJpaTest` (Repository Layer)
  - `@JsonTest` (Serialization)
  - `@RestClientTest`
- `@MockBean` and `@SpyBean`
- TestRestTemplate and MockMvc
- `WebTestClient` (WebFlux / Integration)

### 📦 Module 7.2: Integration & Persistence Testing
- Testcontainers:
  - PostgreSQL, Redis, Kafka, MongoDB, Elasticsearch
  - `@Container` and `@Testcontainers`
  - Shared Container Strategy (Performance)
  - Singleton Container Pattern
- Database Testing:
  - `@Sql` and `@SqlGroup`
  - Data Initialization for Tests
  - Transaction Rollback in Tests
- WireMock (Mocking External HTTP Services)
- Embedded Kafka (`@EmbeddedKafka`) for Messaging Tests

### 📦 Module 7.3: Architecture & Contract Testing
- ArchUnit (Architecture Rule Enforcement):
  - Layer Dependency Rules
  - Naming Conventions
  - DDD Pattern Enforcement (Aggregates Don't Depend on Repositories)
  - Spring Modulith Verification Tests
- Spring Cloud Contract (Covered in Module 6.4 — Applied Here)
- Consumer-Driven Contract Testing Workflow

### 📦 Module 7.4: Performance & Chaos Testing
- Load Testing:
  - Gatling (Scala DSL, HTTP Protocol, Simulations)
  - k6 (JavaScript, Scenarios, Thresholds)
  - JMeter (Awareness)
- Performance Testing Strategy:
  - Baseline Establishment
  - Stress Testing, Spike Testing, Soak Testing
  - Performance Budgets
- Chaos Engineering:
  - Chaos Monkey for Spring Boot
  - Failure Injection (Latency, Exceptions, Memory)
  - GameDay Planning and Execution

### 📦 Module 7.5: Testing Strategy & Best Practices
- Test Pyramid (Unit → Integration → E2E) in Microservices
- Testing Honeycomb (Spotify Model)
- Test Data Management
- Test Isolation Strategies
- Flaky Test Management
- Testing in CI/CD Pipelines (Parallelization, Fast Feedback)

> ### 🛠 Phase 7 Milestone Project: **Comprehensive Test Suite for Food Delivery Platform**
> Retrofit the Phase 5 project with: full unit tests (JUnit 5 + Mockito), integration tests with Testcontainers (PostgreSQL, Kafka, Redis), contract tests (Spring Cloud Contract), ArchUnit rules for architecture enforcement, Gatling load tests for critical APIs, Chaos Monkey configuration. >85% meaningful coverage. Tests run in CI/CD.

---

## 🔶 PHASE 8: DevOps, Observability & Production Readiness
> **Goal:** Deploy, monitor, and operate Spring Boot applications in production with confidence.

### 📦 Module 8.1: Containerization & Kubernetes Deployment
- Docker Best Practices for Spring Boot:
  - Multi-Stage Dockerfile
  - JVM Memory Settings in Containers (`-XX:MaxRAMPercentage`)
  - Spring Boot Buildpacks (`spring-boot:build-image`)
  - Jib (Google — Daemonless Container Build)
  - Image Layering for Faster Builds
- Kubernetes Deployment for Spring Boot:
  - Deployment, Service, Ingress YAML Manifests
  - ConfigMaps and Secrets for `application.yml`
  - Readiness and Liveness Probes (Actuator `/health/readiness`, `/health/liveness`)
  - Graceful Shutdown (`server.shutdown=graceful`)
  - Resource Requests and Limits
  - Horizontal Pod Autoscaler (HPA)
- Helm Charts for Spring Boot Services
- Kubernetes-Native Spring (Spring Cloud Kubernetes):
  - Config via ConfigMaps/Secrets
  - Service Discovery via Kubernetes DNS
  - Leader Election via Kubernetes API

### 📦 Module 8.2: CI/CD Pipeline Design
- CI Pipeline (GitHub Actions / GitLab CI):
  - Build → Unit Test → Integration Test → SAST Scan → Contract Test → Docker Build → Push
  - Dependency Vulnerability Scanning (Snyk, OWASP)
  - SonarQube Quality Gate
  - Artifact Promotion Strategy (Dev → Staging → Prod)
- CD Pipeline:
  - Blue/Green Deployments
  - Canary Releases (with Spring Cloud Gateway or Kubernetes)
  - Rolling Deployments
  - Feature Flags (Unleash, LaunchDarkly, Togglz for Spring)
  - Database Migration in CI/CD (Flyway, Zero-Downtime)
- GitOps:
  - ArgoCD (Declarative, Git-as-Source-of-Truth)
  - Sync Policies, Health Checks, Rollback

### 📦 Module 8.3: Infrastructure as Code
- Terraform for Spring Boot Infrastructure:
  - AWS/GCP/Azure Resources (RDS, ElastiCache, EKS, VPC)
  - State Management (Remote Backend, Locking)
  - Modules for Reusability
  - Workspaces for Environment Separation
- Ansible (Configuration Management — Awareness)
- Policy as Code (OPA — Awareness)

### 📦 Module 8.4: Observability — The Three Pillars
- **Structured Logging:**
  - SLF4J + Logback Configuration
  - JSON Structured Logging (Logstash Encoder)
  - Correlation IDs / Trace IDs in Logs
  - Log Aggregation: ELK Stack (Elasticsearch, Logstash, Kibana) or Loki + Grafana
  - MDC (Mapped Diagnostic Context) for Request Context
- **Metrics:**
  - Micrometer (Spring Boot's Metrics Facade)
  - Built-in Metrics (JVM, HTTP, DB, Cache)
  - Custom Metrics (Counters, Gauges, Timers, Distribution Summaries)
  - Prometheus Scraping (`/actuator/prometheus`)
  - Grafana Dashboards (RED Metrics: Rate, Errors, Duration)
  - SLIs, SLOs, SLAs, and Error Budgets
- **Distributed Tracing:**
  - Micrometer Tracing (Spring Boot 3+ — Replaced Sleuth)
  - OpenTelemetry Integration
  - Trace Propagation Across Services (W3C Trace Context)
  - Jaeger / Zipkin as Trace Backend
  - Baggage Propagation
  - Span Customization (`@Observed`, `Observation` API)
- **Alerting:**
  - Alertmanager (Prometheus)
  - Alert Design (Symptom-Based, Not Cause-Based)
  - Runbooks for Each Alert
  - On-Call Rotation and Incident Response Process
- **Dashboarding:**
  - Service Health Dashboard
  - Business Metrics Dashboard
  - Infrastructure Dashboard
  - Dashboard-as-Code (Grafana Provisioning)

### 📦 Module 8.5: Production Readiness Checklist
- Health Checks (Readiness, Liveness, Startup Probes)
- Graceful Shutdown and Connection Draining
- Circuit Breakers on All External Calls
- Structured Logging with Trace IDs
- Metrics Exposed and Dashboarded
- Alerts Configured with Runbooks
- Database Migrations Automated
- Secrets Externalized (Not in Code/Config)
- Security Headers and OWASP Hardening
- Load Tested to Expected Capacity
- Disaster Recovery Plan Documented
- Rollback Strategy Defined

> ### 🛠 Phase 8 Milestone Project: **Production-Ready Deployment Pipeline**
> Take the Food Delivery Platform and make it production-ready:
> - Dockerized with Buildpacks, deployed to Kubernetes (Minikube/Kind or cloud)
> - Helm charts for all services
> - Full CI/CD pipeline (GitHub Actions → ArgoCD)
> - Terraform for infrastructure
> - Full observability: structured JSON logs → Loki, metrics → Prometheus → Grafana, traces → Jaeger
> - Alerting with Prometheus Alertmanager
> - Grafana dashboards (RED metrics per service)
> - Feature flags with Togglz
> - Canary deployment for one service
> - Production readiness checklist verified for all services

---

## 🏗️ CAPSTONE PROJECT: Real-Time E-Commerce Platform
> **This is the Phase 2 capstone — it ties everything together.**
>
> Build a distributed e-commerce system with:
> - **Modular monolith with clear bounded contexts** (Catalog, Orders, Payments, Notifications) — Spring Modulith
> - **Hexagonal Architecture** within each bounded context
> - **DDD tactical patterns** (Aggregates, Value Objects, Domain Events, Repositories)
> - **Event-driven communication** between modules (Kafka)
> - **CQRS** for the product catalog (write to PostgreSQL, read-optimized projections to Elasticsearch)
> - **Saga pattern** for order processing flow (Order → Payment → Inventory → Notification)
> - **OAuth 2.0 + JWT** authentication (Spring Authorization Server or Keycloak)
> - **API Gateway** (Spring Cloud Gateway) with rate limiting
> - **GraphQL API** for storefront queries + REST API for admin
> - **PostgreSQL + Redis + Elasticsearch** (each bounded context owns its data)
> - **Resilience4j** circuit breakers, retries, bulkheads
> - **Full CI/CD pipeline** with canary deployments (GitHub Actions + ArgoCD)
> - **OpenTelemetry** distributed tracing + Prometheus metrics + Grafana dashboards
> - **Terraform** for infrastructure
> - **Comprehensive test suite**: unit, integration (Testcontainers), contract (Spring Cloud Contract), load (Gatling), ArchUnit
> - **Architecture Decision Records (ADRs)** and **C4 diagrams** (Structurizr)
> - **Event Storming artifacts** documented
> - **Production readiness** checklist verified
>
> **Why:** Covers DDD, event-driven architecture, distributed systems patterns, security, DevOps, observability, API design, and testing in one cohesive project that demonstrates mastery of Phase 2.

---

## ✅ After Completing This Roadmap — You Can:
- [ ] Build production-grade Spring Boot applications
- [ ] Design and implement Hexagonal / Clean Architecture
- [ ] Model domains using DDD (strategic + tactical)
- [ ] Build and operate microservices with Spring Cloud
- [ ] Implement event-driven systems with Kafka and RabbitMQ
- [ ] Apply CQRS, Event Sourcing, and Saga patterns
- [ ] Secure applications with OAuth 2.0, JWT, and Spring Security
- [ ] Design excellent REST and GraphQL APIs
- [ ] Master enterprise integration patterns
- [ ] Implement resilience patterns (circuit breakers, retries, bulkheads)
- [ ] Deploy to Kubernetes with CI/CD and GitOps
- [ ] Build full observability (logging, metrics, tracing, alerting)
- [ ] Write comprehensive tests at every layer
- [ ] Make and document architectural decisions (ADRs)
- [ ] Facilitate Event Storming sessions
- [ ] Create C4 architecture diagrams
- [ ] Choose and justify architectural styles for given requirements
- [ ] **You are ready for Phase 3: Cloud-Native Mastery & Leadership**

---


### 📚 Phase-by-Phase Summary

| Phase | Title | Key Technologies & Concepts | Milestone Project |
|:---:|---|---|---|
| **0** | Java Web Foundations | Servlets, `HttpServletRequest/Response`, Filters, Listeners, JSP | Mini REST Framework |
| **1** | Spring Boot Core | IoC, DI, AOP, Auto-Config, REST APIs, Validation, Actuator | Task Management API |
| **2** | Data Access | Spring Data JPA, Entities, `@Transactional`, Redis, Flyway | E-Commerce Catalog |
| **3** | Security | Spring Security, JWT, OAuth2, OIDC, OWASP Top 10 | Multi-Tenant Platform |
| **4** | Architecture & DDD | Hexagonal, Clean Arch, Bounded Contexts, Aggregates, Modulith | Order Management System |
| **5** | Microservices | Spring Cloud Gateway, Kafka, Resilience4j, Sagas, CQRS | Food Delivery Platform |
| **6** | API Design & EIP | REST Maturity, GraphQL, Spring Integration, Contract Testing | API Gateway Platform |
| **7** | Testing | Test Slices, Testcontainers, ArchUnit, Gatling, Chaos Monkey | Full Test Suite Retrofit |
| **8** | DevOps & Prod | Docker, Kubernetes, ArgoCD, Terraform, OpenTelemetry | Prod-Ready Deployment |
| **🎉** | **Capstone** | **All of the above** | **Real-Time E-Commerce Platform** |

### 🛠️ Core Spring Boot Annotation Cheat Sheet
- **Core & DI**: `@SpringBootApplication`, `@Component`, `@Service`, `@Repository`, `@Configuration`, `@Bean`, `@Autowired`, `@Qualifier`, `@Profile`, `@Conditional`
- **Web & API**: `@RestController`, `@RequestMapping`, `@GetMapping`, `@PostMapping`, `@PutMapping`, `@DeleteMapping`, `@PathVariable`, `@RequestParam`, `@RequestBody`, `@ResponseEntity`, `@ExceptionHandler`, `@ControllerAdvice`
- **Data & Persistence**: `@Entity`, `@Table`, `@Id`, `@GeneratedValue`, `@Column`, `@OneToMany`, `@ManyToOne`, `@Transactional`, `@Query`, `@Cacheable`, `@CacheEvict`
- **Security**: `@EnableWebSecurity`, `@EnableMethodSecurity`, `@PreAuthorize`, `@PostAuthorize`, `@Secured`
- **AOP**: `@Aspect`, `@Pointcut`, `@Before`, `@After`, `@Around`, `@AfterReturning`, `@AfterThrowing`
- **Boot & Actuator**: `@ConfigurationProperties`, `@RefreshScope`, `@Scheduled`, `@Async`, `@Observed`
- **Testing**: `@SpringBootTest`, `@WebMvcTest`, `@DataJpaTest`, `@MockBean`, `@SpyBean`, `@Testcontainers`, `@Container`

---
*End of Roadmap. You are now equipped to build, scale, and operate enterprise-grade Java applications.*