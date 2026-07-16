# ☕ Java Mastery Roadmap — Phase 1: Foundations
> Aligned with Phase 1 of the Software Engineering Mastery Roadmap
> **Estimated Duration: 4–6 months**

---

## 🟢 PHASE 1: Foundation & Core Basics
> **Goal:** Understand how Java works and write basic programs.

### 📦 Module 1.1: Introduction to Java
- What is Java & Why Learn It
- History & Evolution of Java
- JDK vs JRE vs JVM
- How Java Code Executes (Compilation & Interpretation)
- Installing JDK & Setting Up IDE (IntelliJ / VS Code)
- Writing Your First "Hello World" Program
- Understanding `main()` method signature

### 📦 Module 1.2: Java Syntax & Basics
- Variables & Data Types (Primitive & Non-Primitive)
- Type Casting (Widening & Narrowing)
- Operators (Arithmetic, Relational, Logical, Bitwise, Ternary)
- String Basics (`String`, `charAt`, `length`, `concat`)
- Taking User Input (`Scanner` class)
- Comments (Single-line, Multi-line, Javadoc)

### 📦 Module 1.3: Control Flow
- `if`, `else if`, `else`
- `switch` statement & Enhanced Switch (Java 14+)
- `for` loop, `while` loop, `do-while` loop
- `break`, `continue`, `return`
- Nested Loops
- Labelled Loops

### 📦 Module 1.4: Arrays
- One-Dimensional Arrays
- Two-Dimensional / Multi-Dimensional Arrays
- Array Traversal & Manipulation
- Common Array Algorithms (Search, Reverse, Sort)
- `Arrays` Utility Class
- Varargs (`int... args`)

### 📦 Module 1.5: Methods (Functions)
- Defining & Calling Methods
- Parameters & Return Types
- Method Overloading
- `static` Methods vs Instance Methods
- Pass-by-Value in Java
- Recursion Basics

> ### 🛠 Phase 1 Milestone Project: **CLI-Based Student Grade Calculator**
> Take student names & marks via console, calculate average, assign grades, and display a formatted report card.

---

## 🔵 PHASE 2: Object-Oriented Programming (OOP)
> **Goal:** Master the four pillars of OOP in Java.

### 📦 Module 2.1: Classes & Objects
- Defining Classes & Creating Objects
- Instance Variables & Methods
- `this` Keyword
- Constructors (Default, Parameterized, Copy)
- Constructor Chaining
- `null` and Object References

### 📦 Module 2.2: Encapsulation
- Access Modifiers (`private`, `default`, `protected`, `public`)
- Getters & Setters
- Data Hiding Principles
- Immutable Classes
- Builder Pattern (Intro)

### 📦 Module 2.3: Inheritance
- `extends` Keyword
- Single, Multilevel, Hierarchical Inheritance
- Why Java Doesn't Support Multiple Inheritance (Classes)
- Method Overriding & `@Override`
- `super` Keyword (Constructor & Method)
- `final` Keyword (Variable, Method, Class)

### 📦 Module 2.4: Polymorphism
- Compile-Time Polymorphism (Method Overloading)
- Runtime Polymorphism (Method Overriding)
- Upcasting & Downcasting
- `instanceof` Operator
- Dynamic Method Dispatch
- Covariant Return Types

### 📦 Module 2.5: Abstraction
- Abstract Classes & Abstract Methods
- Interfaces (Declaration & Implementation)
- `default` & `static` Methods in Interfaces (Java 8+)
- `private` Methods in Interfaces (Java 9+)
- Abstract Class vs Interface — When to Use What
- Multiple Inheritance via Interfaces

### 📦 Module 2.6: Other OOP Concepts
- `Object` Class & Its Methods (`toString`, `equals`, `hashCode`)
- `static` Keyword Deep Dive (Variables, Methods, Blocks, Inner Classes)
- `final` vs `finally` vs `finalize`
- Composition vs Inheritance
- Association, Aggregation, Composition
- Enums & Enum Methods

> ### 🛠 Phase 2 Milestone Project: **Bank Account Management System**
> Create classes for `Account`, `SavingsAccount`, `CurrentAccount` using inheritance, encapsulation, and polymorphism. Support deposit, withdrawal, transfer, and balance inquiry.

---

## ==🟡 PHASE 3: Core Java Essentials==
> **Goal:** Learn the essential libraries, utilities, and language features.

### 📦 Module 3.1: String Handling In-Depth
- `String` Immutability & String Pool
- `StringBuilder` vs `StringBuffer`
- Important String Methods
- String Comparison (`==` vs `.equals()`)
- String Formatting (`String.format`, `printf`)
- Regular Expressions (`Pattern`, `Matcher`)

### 📦 Module 3.2: Exception Handling
- What Are Exceptions (Checked vs Unchecked)
- `try`, `catch`, `finally`
- `throw` vs `throws`
- Custom Exception Classes
- Try-with-Resources (ARM)
- Best Practices in Exception Handling
- Exception Hierarchy (`Throwable → Error / Exception`)

### 📦 Module 3.3: Wrapper Classes & Autoboxing
- Primitive vs Wrapper (`int` ↔ `Integer`)
- Autoboxing & Unboxing
- Parsing Strings to Numbers
- `Number` Class Methods
- Caching in Wrapper Classes (`Integer.valueOf`)

### 📦 Module 3.4: Java Collections Framework
- **List:** `ArrayList`, `LinkedList`, `Vector`, `Stack`
- **Set:** `HashSet`, `LinkedHashSet`, `TreeSet`
- **Queue:** `PriorityQueue`, `ArrayDeque`
- **Map:** `HashMap`, `LinkedHashMap`, `TreeMap`, `Hashtable`
- `Iterator` & `ListIterator`
- `Comparable` vs `Comparator`
- `Collections` Utility Class (sort, reverse, shuffle, unmodifiable)
- Fail-Fast vs Fail-Safe Iterators

### 📦 Module 3.5: Generics
- Why Generics?
- Generic Classes & Methods
- Bounded Type Parameters (`<T extends Number>`)
- Wildcards (`?`, `? extends T`, `? super T`)
- Type Erasure
- Generic Interfaces

### 📦 Module 3.6: File I/O
- `File` Class Basics
- Byte Streams (`FileInputStream`, `FileOutputStream`)
- Character Streams (`FileReader`, `FileWriter`)
- Buffered Streams (`BufferedReader`, `BufferedWriter`)
- `PrintWriter`
- Serialization & Deserialization (`Serializable`, `ObjectOutputStream`)
- NIO.2 (`Path`, `Files`, `Paths`) — Modern File I/O
- Reading/Writing CSV and Text Files

> ### 🛠 Phase 3 Milestone Project: **File-Based Contact Manager**
> A CLI app that stores contacts in a file (CSV/text). Support add, delete, search, sort, and list contacts using Collections and File I/O. Handle all edge cases with proper exception handling.

---

## ==🟠 PHASE 4: Advanced Java Features==
> **Goal:** Learn modern and powerful Java features including concurrency, functional programming, and JVM internals.

### 📦 Module 4.1: Lambda Expressions & Functional Programming
- What Are Lambdas & Why They Matter
- Functional Interfaces (`@FunctionalInterface`)
- Built-in Functional Interfaces:
  - `Predicate<T>`
  - `Function<T, R>`
  - `Consumer<T>`
  - `Supplier<T>`
  - `BiFunction`, `BiConsumer`, `BiPredicate`
- Method References (`::`)
- Effectively Final Variables in Lambdas
- Immutability and Pure Functions in Java
- Declarative vs Imperative Programming Approaches

### 📦 Module 4.2: Streams API
- Creating Streams (from Collections, Arrays, `Stream.of`)
- Intermediate Ops: `filter`, `map`, `flatMap`, `sorted`, `distinct`, `peek`
- Terminal Ops: `collect`, `forEach`, `reduce`, `count`, `min`, `max`
- `Collectors` Utility (`toList`, `toMap`, `groupingBy`, `joining`, `partitioningBy`)
- Parallel Streams
- `Optional<T>` — Avoiding `NullPointerException`

### 📦 Module 4.3: Date & Time API (Java 8+)
- `LocalDate`, `LocalTime`, `LocalDateTime`
- `ZonedDateTime`, `Instant`, `Duration`, `Period`
- Formatting & Parsing (`DateTimeFormatter`)
- Legacy Date vs Modern API

### 📦 Module 4.4: Multithreading & Concurrency
- Threads: `Thread` Class vs `Runnable` Interface
- Thread Lifecycle & States
- `sleep()`, `join()`, `yield()`
- Synchronization (`synchronized` keyword)
- Inter-Thread Communication (`wait`, `notify`, `notifyAll`)
- `volatile` Keyword
- Thread Safety & Deadlocks
- `ExecutorService` & Thread Pools
- `Callable<V>` & `Future<V>`
- `CompletableFuture` (Async Programming)
- `ReentrantLock`, `ReadWriteLock`
- Concurrent Collections (`ConcurrentHashMap`, `CopyOnWriteArrayList`)
- `CountDownLatch`, `CyclicBarrier`, `Semaphore`

### 📦 Module 4.5: Reactive Programming Basics
- Reactive Programming Concepts (streams, backpressure, event-driven models)
- Java's `Flow` API (Java 9+): `Publisher`, `Subscriber`, `Subscription`, `Processor`
- Reactive Streams Specification
- Backpressure Handling Concepts
- Reactive vs Imperative: When to Use What
- Overview of Libraries (Project Reactor, RxJava — conceptual awareness)

### 📦 Module 4.6: Java Memory Model & JVM Internals
- Stack vs Heap Memory
- Garbage Collection (GC) Basics
- Types of GC (Serial, Parallel, G1, ZGC)
- `finalize()` & Cleaner
- Memory Leaks — Causes & Prevention
- ClassLoader Mechanism
- JIT Compilation

### 📦 Module 4.7: Annotations & Reflection
- Built-in Annotations (`@Override`, `@Deprecated`, `@SuppressWarnings`, `@FunctionalInterface`)
- Custom Annotations
- Meta-Annotations (`@Target`, `@Retention`, `@Inherited`, `@Documented`)
- Reflection API (`Class`, `Method`, `Field`, `Constructor`)
- Accessing Private Members via Reflection
- Use Cases & Dangers of Reflection

### 📦 Module 4.8: Modern Java Features (Java 11–21+)
- Records (Java 16)
- Sealed Classes (Java 17)
- Pattern Matching for `instanceof` (Java 16)
- Switch Expressions (Java 14)
- Text Blocks (Java 15)
- Virtual Threads (Java 21 — Project Loom)
- Structured Concurrency (Preview)
- Helpful NullPointerExceptions (Java 14)

> ### 🛠 Phase 4 Milestone Project: **Multithreaded File Downloader**
> Build a download manager that downloads files concurrently using thread pools, tracks progress with `CompletableFuture`, and uses Streams + Lambdas for processing download metadata. Use Records and modern Java features.

---

## 🔴 PHASE 5: Data Structures & Algorithms in Java
> **Goal:** Strengthen problem-solving skills using Java.

### 📦 Module 5.1: Complexity Analysis
- Time & Space Complexity
- Big O, Big Ω, Big Θ
- Analyzing Loops, Recursion
- Amortized Analysis Basics

### 📦 Module 5.2: Data Structures Implementation
- Linked Lists (Singly, Doubly, Circular)
- Stacks & Queues (Array & LinkedList-based)
- Hash Tables (Custom HashMap)
- Trees (Binary Tree, BST, AVL)
- Heaps (Min-Heap, Max-Heap, Priority Queue)
- Graphs (Adjacency List & Matrix)
- Tries

### 📦 Module 5.3: Algorithms
- Sorting: Bubble, Selection, Insertion, Merge, Quick, Heap, Counting, Radix
- Searching: Linear, Binary, Ternary
- Recursion & Backtracking
- Dynamic Programming (Memoization & Tabulation)
- Greedy Algorithms
- Graph Algorithms (BFS, DFS, Dijkstra, Kruskal, Prim, Topological Sort)
- Sliding Window, Two Pointers

> ### 🛠 Phase 5 Milestone Project: **Custom Collections Library**
> Implement your own `ArrayList`, `LinkedList`, `HashMap`, `BST`, and `Graph` with full CRUD operations, iterators, and unit tests.

---

## ==🟣 PHASE 6: Design Principles, Patterns & Clean Code==
> **Goal:** Write professional, maintainable, and scalable Java code using proven principles and patterns.

### 📦 Module 6.1: SOLID Principles (Deep Understanding with Real Examples)
- Single Responsibility Principle (SRP)
- Open/Closed Principle (OCP)
- Liskov Substitution Principle (LSP)
- Interface Segregation Principle (ISP)
- Dependency Inversion Principle (DIP)

### 📦 Module 6.2: Design Principles (Beyond SOLID)
- Separation of Concerns
- High Cohesion / Low Coupling
- Composition over Inheritance
- Dependency Inversion & Inversion of Control
- Law of Demeter (Principle of Least Knowledge)
- Principle of Least Astonishment
- Information Hiding (Parnas)

### 📦 Module 6.3: Creational Patterns
- Singleton Pattern
- Factory Method Pattern
- Abstract Factory Pattern
- Builder Pattern
- Prototype Pattern

### 📦 Module 6.4: Structural Patterns
- Adapter Pattern
- Bridge Pattern
- Composite Pattern
- Decorator Pattern
- Facade Pattern
- Flyweight Pattern
- Proxy Pattern

### 📦 Module 6.5: Behavioral Patterns
- Strategy Pattern
- Observer Pattern
- Command Pattern
- State Pattern
- Template Method Pattern
- Chain of Responsibility Pattern
- Mediator Pattern
- Visitor Pattern
- Iterator Pattern

### 📦 Module 6.6: Concurrency Patterns
- Producer-Consumer Pattern
- Read-Write Lock Pattern
- Thread Pool Pattern
- Future/Promise Pattern

### 📦 Module 6.7: Anti-Patterns & When NOT to Use Patterns
- Common Anti-Patterns (God Class, Spaghetti Code, Golden Hammer, Lava Flow)
- Over-Engineering with Patterns
- Recognizing When a Pattern Adds Unnecessary Complexity
- Pattern Selection Decision Framework

### 📦 Module 6.8: Clean Code Practices
- Meaningful Naming Conventions
- Method & Class Design
- DRY, KISS, YAGNI Principles
- Code Smells & Refactoring Techniques (Martin Fowler's Catalog)
- Writing Self-Documenting Code
- Proper Error Handling Design
- Javadoc Best Practices
- Code Reviews Best Practices

> ### 🛠 Phase 6 Milestone Project: **Notification System**
> Design a notification service supporting Email, SMS, and Push notifications using Factory, Observer, Strategy, Builder, and Chain of Responsibility patterns. Apply SOLID and design principles throughout. Include comprehensive code review checklist.

---

## ⚫ PHASE 7: Testing, Build Tools & Version Control
> **Goal:** Master professional Java development practices — testing, building, and collaborating.

### 📦 Module 7.1: Unit Testing
- JUnit 5 (Annotations, Assertions, Lifecycle)
- Parameterized Tests
- Mockito (Mocking, Stubbing, Verification, Faking)
- AAA Pattern (Arrange, Act, Assert)
- Test-Driven Development (TDD) — Red/Green/Refactor
- Code Coverage (JaCoCo): Metrics and Their Limitations

### 📦 Module 7.2: Integration Testing & Advanced Testing
- Integration Testing Strategies
- Behavior-Driven Development (BDD) — Cucumber/JBehave
- Test Pyramids (Unit → Integration → E2E)
- Testing Anti-Patterns
- Testcontainers for Integration Tests
- Writing Testable Code (Dependency Injection for Testability)

### 📦 Module 7.3: Build Tools & Dependency Management
- Maven (POM, Dependencies, Lifecycle, Plugins, Profiles)
- Gradle (Groovy/Kotlin DSL, Tasks, Dependencies)
- Dependency Management and Vulnerability Scanning
- Multi-Module Projects
- Artifact Repositories (Nexus, Artifactory)
- Reproducible Builds
- Semantic Versioning and Release Management

### 📦 Module 7.4: Version Control Mastery
- Git Internals (Objects, Refs, DAG)
- Branching Strategies (GitFlow, Trunk-Based Development, GitHub Flow)
- Monorepo vs Polyrepo Trade-offs
- Advanced Git (Rebase, Cherry-Pick, Bisect, Stash, Hooks)
- GitHub / GitLab Collaboration (PRs, Code Reviews, Protected Branches)
- `.gitignore` for Java Projects

### 📦 Module 7.5: CI/CD Foundations
- Continuous Integration Best Practices
- Pipeline-as-Code (GitHub Actions)
- Pipeline Stages (Build, Test, Scan, Package)
- Automated Testing in CI Pipelines
- Static Analysis Tools (Checkstyle, SpotBugs, SonarQube)
- Dependency Vulnerability Scanning (OWASP Dependency-Check, Snyk)

### 📦 Module 7.6: Logging & Debugging
- `System.out` vs Logging Frameworks
- SLF4J + Logback / Log4j2
- Log Levels (TRACE, DEBUG, INFO, WARN, ERROR)
- Structured Logging
- Debugging with IDE (Breakpoints, Watch, Evaluate)

> ### 🛠 Phase 7 Milestone Project: **Library Management System (Fully Tested)**
> Build a complete library system with Maven/Gradle, write comprehensive JUnit + Mockito tests (TDD), integration tests, implement structured logging, set up CI/CD with GitHub Actions, and host on GitHub with proper branching strategy. Achieve >80% code coverage.

---

## ==🔶 PHASE 8: Databases & Data Modeling==
> **Goal:** Understand data modeling, master SQL, connect Java to databases, and understand database internals.

### 📦 Module 8.1: Data Modeling Fundamentals
- Entity-Relationship Diagrams (ERD)
- Relational Modeling (Normalization: 1NF–5NF)
- Denormalization Trade-offs
- Document Modeling Concepts (NoSQL Patterns)
- Graph Data Modeling Concepts
- Data Modeling for Analytics (Star Schema, Snowflake Schema — Awareness)

### 📦 Module 8.2: SQL Mastery
- DDL, DML, DCL, TCL
- CRUD Operations
- Joins (INNER, LEFT, RIGHT, FULL, CROSS, Self-Joins)
- Subqueries & Common Table Expressions (CTEs)
- Aggregations & Window Functions
- Views, Stored Procedures, Triggers (Awareness)

### 📦 Module 8.3: RDBMS Internals & Advanced Concepts
- Indexing Deep Dive (B-Tree, B+Tree, Hash Index, Composite Index)
- Query Plans & `EXPLAIN` / `EXPLAIN ANALYZE`
- ACID Properties (Atomicity, Consistency, Isolation, Durability)
- Isolation Levels (Read Uncommitted, Read Committed, Repeatable Read, Serializable)
- Transactions & MVCC (Multi-Version Concurrency Control)
- Connection Pooling (HikariCP)
- Replication Basics (Leader-Follower)
- Sharding Basics (Concepts & Trade-offs)

### 📦 Module 8.4: JDBC
- JDBC Architecture & Drivers
- `Connection`, `Statement`, `PreparedStatement`
- `ResultSet` Processing
- CRUD with JDBC
- SQL Injection & Prevention
- Transaction Management (`commit`, `rollback`, `savepoint`)
- Connection Pooling with HikariCP

### 📦 Module 8.5: ORM & JPA / Hibernate (Introduction)
- What is ORM & Why Use It
- JPA Annotations (`@Entity`, `@Table`, `@Id`, `@Column`)
- Hibernate Basics (SessionFactory, Session)
- Entity Relationships (`@OneToMany`, `@ManyToOne`, `@ManyToMany`)
- JPQL & Criteria API Basics
- Lazy vs Eager Loading

### 📦 Module 8.6: NoSQL & Distributed Data Concepts
- NoSQL Categories (Document, Key-Value, Column-Family, Graph, Time-Series)
- When to Use SQL vs NoSQL
- CAP Theorem and PACELC
- Redis Basics (Key-Value Store, Data Structures, Use Cases)
- MongoDB Basics (Documents, Collections, Queries — Awareness)
- Polyglot Persistence Concepts

> ### 🛠 Phase 8 Milestone Project: **Employee Management System with PostgreSQL**
> Full CRUD app using JDBC and JPA with PostgreSQL: proper schema design with normalization, indexing strategies, connection pooling, transactions, query optimization with EXPLAIN, and Redis for simple caching.

---

## 🔷 ==PHASE 9: Networking, Infrastructure & Operations==
> **Goal:** Understand networking, operating systems, containerization, and infrastructure fundamentals.

### 📦 Module 9.1: Networking Essentials
- OSI Model & TCP/IP Stack
- DNS Resolution
- HTTP/HTTPS Protocol Deep Dive (Methods, Headers, Status Codes)
- TLS/SSL Handshakes & Certificates
- Load Balancers (L4 vs L7)
- CDNs and Reverse Proxies
- WebSockets (Concepts)
- gRPC & Protocol Buffers (Concepts)
- HTTP/2 and HTTP/3 (QUIC) — Awareness

### 📦 Module 9.2: Java Networking
- `Socket` & `ServerSocket`
- Building a Simple TCP Client/Server
- `HttpClient` (Java 11+)
- Making HTTP Requests from Java
- REST Principles & HTTP Semantics

### 📦 Module 9.3: Operating Systems & Linux Fundamentals
- Linux Basics (File System, Permissions, Users)
- Essential Commands (navigation, file manipulation, process management)
- Package Management (apt, yum)
- Shell Scripting Basics
- Processes, Signals, and Systemd
- Environment Variables and Configuration
- SSH and Remote Access

### 📦 Module 9.4: Containers & Docker
- Virtual Machines vs Containers
- Docker Fundamentals (Images, Containers, Layers)
- Writing Dockerfiles (for Java Applications)
- Docker Networking (Bridge, Host, Custom Networks)
- Docker Volumes (Persistent Data)
- Docker Compose (Multi-Container Applications)
- Dockerizing a Java Application
- Docker Best Practices (Multi-Stage Builds, Image Optimization)

### 📦 Module 9.5: Container Orchestration Basics
- Why Orchestration? (Problems Docker Alone Doesn't Solve)
- Kubernetes Core Concepts (Pods, Services, Deployments, Namespaces)
- kubectl Basics
- YAML Manifests (Awareness)
- ConfigMaps and Secrets (Awareness)
- Kubernetes vs Docker Compose — When to Use What

> ### 🛠 Phase 9 Milestone Project: **Containerized Java TCP Chat Server**
> Build a multi-client chat server using Java Sockets and threads. Dockerize it with a multi-stage Dockerfile. Create a docker-compose setup with the chat server + Redis (for message persistence) + PostgreSQL (for user accounts). Deploy locally using Docker Compose.

---

## 🏗️ CAPSTONE PROJECT: Production-Grade URL Shortener
> **This is the Phase 1 capstone that ties everything together.**
>
> Build a URL shortener service (like bit.ly) with:
> - **Clean Java code** applying SOLID principles and design patterns
> - **RESTful API** with proper HTTP semantics and error handling (using lightweight server — Javalin or plain `HttpServer`)
> - **PostgreSQL** with proper schema design, normalization, and indexing
> - **Redis** caching layer for hot URLs
> - **Docker** containerization with docker-compose (app + PostgreSQL + Redis)
> - **Comprehensive test suite** (unit + integration tests, TDD approach)
> - **CI/CD pipeline** (GitHub Actions: build → test → scan → docker build)
> - **Structured logging** and health check endpoints
> - **Git** with proper branching strategy and semantic versioning
> - Architecture documented with decision rationale
>
> **Why:** Small enough to finish, complex enough to demonstrate all Phase 1 skills — clean code, design patterns, testing, databases, Docker, CI/CD, networking, and infrastructure.

---

## ✅ After Completing This Roadmap — You Can:
- [ ] Write clean, testable, maintainable Java code
- [ ] Apply appropriate design patterns with justification
- [ ] Understand JVM internals, concurrency, and memory management
- [ ] Solve DSA problems confidently in Java
- [ ] Design normalized/denormalized data models
- [ ] Work fluently with SQL, JDBC, and JPA basics
- [ ] Understand NoSQL concepts and CAP theorem
- [ ] Explain networking and infrastructure fundamentals
- [ ] Containerize applications with Docker and Docker Compose
- [ ] Set up CI/CD pipelines with GitHub Actions
- [ ] Use Git professionally with proper branching strategies
- [ ] Write comprehensive tests (unit, integration, TDD)
- [ ] **You are fully ready for Phase 2: Spring Boot & Architectural Thinking**

---
