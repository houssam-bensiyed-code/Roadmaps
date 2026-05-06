# Most Critical Topics for Software Architect

**CORE FOUNDATIONS**
- Data structures & algorithms (Big-O)
- SOLID principles
- Design Patterns (at minimum: Factory, Strategy, Observer, Adapter, Decorator, Singleton)
- High Cohesion / Low Coupling
- Dependency Inversion
- Relational data modeling (normalization/denormalization)
- RDBMS internals (indexing, transactions, isolation levels)
- CAP theorem

**DISTRIBUTED SYSTEMS (CRITICAL)**
- Fallacies of distributed computing
- Consistency models (strong, eventual)
- Idempotency
- Circuit Breaker pattern
- Retry with backoff
- Horizontal vs vertical scaling
- Caching strategies
- Data partitioning and replication
- Synchronous vs Asynchronous communication

**ARCHITECTURE PATTERNS (CRITICAL)**
- Layered/N-tier architecture
- Microservices decomposition
- Event-Driven Architecture basics
- API Gateway
- CQRS and Event Sourcing (concepts)

**SECURITY (NON-NEGOTIABLE)**
- OWASP Top 10
- OAuth 2.0, JWT
- Encryption at rest/in transit
- SQL injection, XSS, CSRF prevention

**API & INTEGRATION**
- REST principles
- Message brokers vs Event streaming
- Schema evolution

**OPERATIONS**
- CI/CD pipeline fundamentals
- Docker containers
- Kubernetes basics (pods, services, deployments)
- Observability: Logging, Metrics, Tracing
- SLIs, SLOs, SLAs

**CLOUD**
- Cloud compute, storage, databases (AWS/Azure/GCP basics)
- Infrastructure as Code (Terraform)
- Multi-region design

**DOMAIN-DRIVEN DESIGN**
- Bounded Contexts
- Aggregates
- Domain Events

**SOFT SKILLS (CRITICAL)**
- Architecture Decision Records (ADRs)
- Trade-off analysis
- Stakeholder communication
- Conway's Law

**THE TOP 10 ABSOLUTE MUST-HAVES:**
1. SOLID principles + Design Patterns
2. Distributed systems fundamentals (CAP, consistency, idempotency)
3. Microservices + Event-Driven Architecture
4. REST APIs + async messaging
5. RDBMS + NoSQL trade-offs
6. Security (OWASP, OAuth, encryption)
7. Docker + Kubernetes
8. Observability (metrics, logs, traces)
9. Cloud fundamentals
10. Trade-off analysis + ADRs