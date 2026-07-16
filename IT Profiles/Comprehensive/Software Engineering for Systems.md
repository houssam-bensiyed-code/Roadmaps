# 🔧 Systems Software Engineering Mastery Roadmap (2025+)
## For C++, Rust & Low-Level Systems Programming

> This roadmap replaces the web-focused SWE roadmap for engineers working
> at the systems level — operating systems, databases, game engines, compilers,
> embedded systems, networking stacks, high-frequency trading, and performance-
> critical infrastructure.
>
> Pair this with a C++ or Rust language roadmap for each phase.

---
---

## PHASE 1: FOUNDATIONS (Systems Basics)
*Duration: ~4–6 months*

---

### Module 1.1: Programming Mastery (Systems Perspective)
#### 1.1.1 Core Programming Proficiency
- Master at least one systems language deeply (C++, Rust, or C)
- Understand memory layout (stack, heap, static/global, text segment)
- Manual memory management (allocation, deallocation, ownership, borrowing)
- Pointer arithmetic, references, smart pointers, RAII
- Data structures & algorithms (Big-O, trees, graphs, hash maps, dynamic programming)
- Generics/templates, compile-time computation, metaprogramming
- Understanding undefined behavior and how to avoid it

#### 1.1.2 Multi-Paradigm Programming (Systems Context)
- **Procedural Programming** (functions, control flow, data transformation — the foundation)
- **Object-Oriented Programming** (encapsulation, inheritance, polymorphism, virtual dispatch, vtables)
- **Functional Programming** (immutability, pure functions, higher-order functions, closures, iterators)
- **Generic Programming** (templates/generics, compile-time polymorphism, zero-cost abstractions)
- **Data-Oriented Design** (DOD — structure of arrays vs array of structures, cache-friendly layouts)
- Declarative vs Imperative approaches
- When each paradigm wins in systems code

#### 1.1.3 Clean Code & Craftsmanship (Systems Context)
- SOLID principles adapted for systems programming
- DRY, KISS, YAGNI
- Code smells and refactoring techniques (Martin Fowler's catalog)
- Meaningful naming, function design, error handling
- Resource Acquisition Is Initialization (RAII) as design principle
- Zero-cost abstraction philosophy
- Code reviews best practices
- API design for libraries and frameworks (ABI stability, header design, forward declarations)

---

### Module 1.2: Computer Architecture & Hardware Fundamentals
#### 1.2.1 CPU Architecture
- Von Neumann architecture (fetch-decode-execute cycle)
- Instruction Set Architectures (x86-64, ARM64 — conceptual understanding)
- Registers, ALU, control unit
- Instruction pipelining (hazards: data, control, structural)
- Branch prediction (why it matters for performance)
- Superscalar execution and out-of-order execution (conceptual)
- SIMD / Vectorization (SSE, AVX, NEON — awareness of auto-vectorization)
- Clock cycles, IPC (Instructions Per Cycle), throughput vs latency

#### 1.2.2 Memory Hierarchy
- Registers → L1 Cache → L2 Cache → L3 Cache → RAM → Disk/SSD
- Cache lines (typically 64 bytes), cache associativity
- Temporal locality vs spatial locality
- Cache misses (compulsory, capacity, conflict)
- Cache-friendly data structures and access patterns
- Memory alignment and padding
- False sharing in multi-threaded code
- NUMA (Non-Uniform Memory Access) — awareness
- TLB (Translation Lookaside Buffer) — awareness

#### 1.2.3 Memory Model & Data Representation
- Bits, bytes, words, endianness (little-endian, big-endian)
- Integer representation (two's complement, unsigned, overflow behavior)
- Floating-point representation (IEEE 754 — single, double precision)
  - Precision loss, NaN, infinity, denormals
  - Why `0.1 + 0.2 != 0.3`
- Character encoding (ASCII, UTF-8, UTF-16, UTF-32)
- Struct layout in memory (alignment, padding, `sizeof`, `offsetof`)
- Bit manipulation (flags, masks, shifting, counting bits)

#### 1.2.4 I/O & Storage
- I/O models (polling, interrupts, DMA)
- Storage hierarchy (registers → cache → RAM → SSD → HDD → tape)
- SSD internals (NAND flash, wear leveling, write amplification — awareness)
- I/O scheduling and buffering
- Memory-mapped I/O vs port-mapped I/O (conceptual)
- DMA (Direct Memory Access) — awareness

---

### Module 1.3: Operating Systems Fundamentals
#### 1.3.1 Process Management
- What is a process (address space, PID, state transitions)
- Process creation (`fork`, `exec`, `spawn`)
- Process states (new, ready, running, blocked, terminated)
- CPU scheduling algorithms (FCFS, SJF, Round Robin, Priority, MLFQ)
- Context switching (what it costs, when it happens)
- Inter-Process Communication (IPC)
  - Pipes (anonymous, named/FIFO)
  - Shared memory (`mmap`, `shmget`)
  - Message queues (POSIX, System V)
  - Sockets (Unix domain, TCP/UDP)
  - Signals (`SIGINT`, `SIGTERM`, `SIGKILL`, `SIGUSR1`)

#### 1.3.2 Threading & Synchronization
- Threads vs processes (shared address space, lighter weight)
- User-level threads vs kernel-level threads
- POSIX threads (`pthreads`) — conceptual (C++ `std::thread`, Rust `std::thread`)
- Thread lifecycle (create, join, detach)
- Race conditions (data races, time-of-check-time-of-use)
- Synchronization primitives
  - Mutexes (recursive, timed, try-lock)
  - Read-Write Locks (shared vs exclusive)
  - Condition variables (wait, notify_one, notify_all)
  - Semaphores (counting, binary)
  - Spinlocks (when to use, when not to)
  - Barriers
  - Atomic operations (compare-and-swap, fetch-and-add, memory ordering)
- Deadlock (conditions: mutual exclusion, hold-and-wait, no preemption, circular wait)
  - Deadlock prevention, avoidance, detection, recovery
- Livelock and starvation
- Lock-free and wait-free data structures (conceptual — awareness)
- Memory ordering (sequential consistency, acquire-release, relaxed)
  - C++ memory model (`memory_order_seq_cst`, `memory_order_acquire`, `memory_order_release`, `memory_order_relaxed`)
  - Rust atomics (`Ordering::SeqCst`, `Ordering::Acquire`, `Ordering::Release`, `Ordering::Relaxed`)
- Happens-before relationship

#### 1.3.3 Memory Management (OS Level)
- Virtual memory (virtual address → physical address translation)
- Page tables (single-level, multi-level, inverted)
- TLB (Translation Lookaside Buffer)
- Page faults (minor, major)
- Demand paging and copy-on-write
- Memory allocation strategies (first-fit, best-fit, buddy system, slab allocator)
- `malloc`/`free` internals (free lists, fragmentation, `mmap` for large allocations)
- Memory-mapped files (`mmap`)
- Stack vs heap allocation (stack frames, stack overflow)
- Address Space Layout Randomization (ASLR) — awareness

#### 1.3.4 File Systems
- File system abstractions (files, directories, inodes, file descriptors)
- File operations (open, read, write, close, seek, truncate)
- File system types (ext4, XFS, Btrfs, NTFS, APFS — awareness)
- Journaling (write-ahead logging for crash recovery)
- VFS (Virtual File System) layer
- Buffered vs direct I/O (`O_DIRECT`)
- `fsync`, `fdatasync` (durability guarantees)
- File locking (advisory vs mandatory, `flock`, `fcntl`)
- Sparse files, hard links, symbolic links

#### 1.3.5 Linux Systems Programming
- Linux fundamentals (file system hierarchy, permissions, users, groups)
- Essential commands (navigation, file manipulation, process management)
- Shell scripting basics
- `systemd` (services, units, journal)
- System calls (the interface between user space and kernel)
  - Key syscalls: `read`, `write`, `open`, `close`, `mmap`, `fork`, `exec`, `wait`, `kill`, `socket`, `bind`, `listen`, `accept`, `connect`, `epoll`
  - `strace` (trace system calls — essential debugging tool)
  - `ltrace` (trace library calls)
- `/proc` and `/sys` file systems (runtime kernel information)
- `cgroups` and `namespaces` (container foundations — awareness)
- Package management, development tools (`make`, `cmake`, `pkg-config`)
- `man` pages (learning to read them fluently)

---

### Module 1.4: Software Design Fundamentals (Systems Context)
#### 1.4.1 Design Principles
- Separation of Concerns
- High Cohesion / Low Coupling
- Composition over Inheritance (especially relevant in systems — prefer composition and traits)
- Dependency Inversion & Inversion of Control
- Law of Demeter
- Principle of Least Astonishment
- Information Hiding (Parnas)
- Principle of Least Privilege (security context)
- Fail-fast principle
- Defense in depth

#### 1.4.2 Design Patterns (GoF & Systems-Specific)
- **Creational:** Singleton, Factory Method, Abstract Factory, Builder, Prototype, Object Pool
- **Structural:** Adapter, Bridge, Composite, Decorator, Facade, Proxy, Flyweight
- **Behavioral:** Strategy, Observer, Command, State, Template Method, Chain of Responsibility, Mediator, Visitor, Iterator
- **Concurrency Patterns:** Producer-Consumer, Read-Write Lock, Thread Pool, Future/Promise, Active Object, Monitor Object, Thread-Specific Storage
- **Systems-Specific Patterns:**
  - RAII (Resource Acquisition Is Initialization) — the most important systems pattern
  - Pimpl (Pointer to Implementation) — ABI stability, compilation firewall
  - Type Erasure (Runtime polymorphism without inheritance)
  - CRTP (Curiously Recurring Template Pattern) — static polymorphism
  - ECS (Entity-Component-System) — game engines, simulation
  - Arena/Region-Based Allocation — bulk allocation and deallocation
  - Intrusive vs Non-Intrusive containers
  - Handle/Body (Bridge variant for resource management)
  - Double Buffering (graphics, audio, real-time)
- When NOT to use patterns (anti-pattern awareness)

#### 1.4.3 Data Modeling (Systems Context)
- Relational modeling (normalization: 1NF–5NF, denormalization trade-offs)
- Entity-Relationship Diagrams
- In-memory data modeling (flat buffers, structs, tagged unions, variant types)
- Binary serialization formats (Protocol Buffers, FlatBuffers, Cap'n Proto, MessagePack)
- Schema evolution (forward/backward compatibility)
- Memory-mapped data structures
- Data-oriented design (SoA vs AoS, cache-friendly layouts)

---

### Module 1.5: Development Practices
#### 1.5.1 Version Control Mastery
- Git internals (objects, refs, DAG)
- Branching strategies (GitFlow, trunk-based, GitHub Flow)
- Monorepo vs polyrepo trade-offs (especially for systems projects with libraries)
- Semantic versioning and release management
- Git submodules and subtrees (common in C++ projects)

#### 1.5.2 Testing Foundations
- Unit testing (AAA pattern, mocking, stubbing, faking)
- Integration testing strategies
- Test-Driven Development (TDD) — Red/Green/Refactor
- Behavior-Driven Development (BDD) — awareness
- Test pyramids and testing anti-patterns
- Code coverage: metrics and their limitations
- **Systems-Specific Testing:**
  - Fuzz testing (libFuzzer, AFL, `cargo fuzz`)
  - Property-based testing
  - Sanitizers (AddressSanitizer, MemorySanitizer, ThreadSanitizer, UBSan)
  - Valgrind (memory leak detection, cache profiling)
  - Benchmark testing (micro-benchmarks, statistical rigor)
  - Chaos testing for concurrent code
  - Hardware-in-the-loop testing (embedded — awareness)

#### 1.5.3 Build Systems & Dependency Management
- Build systems
  - Make / Makefile
  - CMake (the C++ standard — `CMakeLists.txt`, targets, packages, presets)
  - Cargo (Rust's build system — `Cargo.toml`, features, workspaces)
  - Bazel (large-scale monorepo builds — awareness)
  - Meson, Ninja (awareness)
- Dependency management
  - C++: vcpkg, Conan, FetchContent (CMake)
  - Rust: crates.io, `Cargo.toml`
  - Vendoring vs registry-based dependencies
  - Vulnerability scanning
- Artifact management
- Reproducible builds
- Cross-compilation (targeting different architectures and OSes)
- Compiler flags and optimization levels (`-O0`, `-O2`, `-O3`, `-Os`, LTO)

---

### Module 1.6: Networking & I/O Fundamentals
#### 1.6.1 Networking Essentials
- OSI model & TCP/IP stack
- Ethernet, IP (IPv4/IPv6), routing basics
- TCP deep dive (three-way handshake, flow control, congestion control, Nagle's algorithm, TCP_NODELAY)
- UDP (connectionless, when to use)
- DNS resolution
- HTTP/HTTPS, TLS/SSL handshakes
- Load balancers (L4 vs L7)
- CDNs, reverse proxies
- WebSockets, gRPC, HTTP/2, HTTP/3 (QUIC)

#### 1.6.2 Systems I/O Models
- Blocking I/O (simplest, thread-per-connection)
- Non-blocking I/O (`O_NONBLOCK`, polling)
- I/O Multiplexing (`select`, `poll`, `epoll` (Linux), `kqueue` (BSD/macOS), `IOCP` (Windows))
- `epoll` deep dive (edge-triggered vs level-triggered, `EPOLLIN`, `EPOLLOUT`, `EPOLLHUP`)
- Async I/O (`io_uring` — Linux 5.1+ — modern high-performance I/O)
- Reactor pattern (single-threaded event loop — libuv, Tokio, libevent)
- Proactor pattern (OS completes I/O, notifies application — IOCP, `io_uring`)
- Zero-copy I/O (`sendfile`, `splice`, `mmap`)
- Vectored I/O (`readv`, `writev`)
- Scatter/gather I/O

#### 1.6.3 Socket Programming
- BSD Socket API (`socket`, `bind`, `listen`, `accept`, `connect`, `send`, `recv`, `close`)
- TCP server (iterative, concurrent, pre-forked, thread-pool, event-driven)
- TCP client (connection management, reconnection, timeouts)
- UDP server/client
- Socket options (`SO_REUSEADDR`, `SO_REUSEPORT`, `TCP_NODELAY`, `SO_KEEPALIVE`)
- Non-blocking sockets with `epoll`/`kqueue`
- Unix domain sockets (IPC)

#### 1.6.4 Databases Fundamentals
- RDBMS concepts (tables, indexes, transactions, ACID)
- B-tree/B+tree indexing (how databases store and retrieve data)
- Query plans and `EXPLAIN`
- ACID properties and isolation levels
- WAL (Write-Ahead Logging) — crash recovery
- MVCC (Multi-Version Concurrency Control)
- NoSQL categories (key-value, document, column-family, graph, time-series)
- CAP theorem and PACELC
- Connection pooling
- Embedded databases (SQLite, RocksDB, LevelDB, LMDB)
- Replication and sharding basics

---

### Module 1.7: Containers & Infrastructure Basics
#### 1.7.1 Containerization
- Virtual machines vs containers
- Docker fundamentals (images, layers, containers)
- Writing Dockerfiles for systems applications
  - Multi-stage builds (build stage → runtime with minimal base)
  - Static linking for minimal images (`scratch`, `alpine`, `distroless`)
  - Cross-compilation in Docker
- Docker networking and volumes
- Docker Compose

#### 1.7.2 Container Orchestration (Awareness)
- Kubernetes core concepts (pods, services, deployments, namespaces)
- `kubectl` basics
- ConfigMaps and Secrets
- When Kubernetes makes sense for systems software

---

### 🏗️ Phase 1 Project: Production-Grade Key-Value Store
> Build a persistent key-value store (like a simplified Redis) with:
> - **Clean systems code** applying RAII, composition, and design patterns
> - **TCP server** with concurrent client handling (`epoll`/`kqueue` or thread pool)
> - **Custom protocol** (binary or Redis-like RESP) with parser
> - **In-memory hash map** with configurable eviction (LRU)
> - **Write-Ahead Log (WAL)** for crash recovery and persistence
> - **Memory-mapped file** or append-only log for data storage
> - **Comprehensive test suite** (unit, integration, fuzz, sanitizers, benchmarks)
> - **Docker** containerization with multi-stage build
> - **CI/CD pipeline** (GitHub Actions: lint → test → sanitize → benchmark → build)
> - **Structured logging** and health check endpoints
> - Proper error handling, graceful shutdown, signal handling
>
> **Why:** Covers networking, concurrency, memory management, persistence, binary protocols, testing with sanitizers — the core of systems programming. Small enough to finish, complex enough to demonstrate all Phase 1 skills.

---

### ✅ After Phase 1 — You Can:
- [ ] Write clean, safe, performant systems code
- [ ] Understand CPU, memory hierarchy, and cache-friendly design
- [ ] Explain OS fundamentals (processes, threads, virtual memory, file systems)
- [ ] Apply design patterns with systems-specific adaptations
- [ ] Build concurrent programs with proper synchronization
- [ ] Implement network servers with modern I/O models
- [ ] Test systems code with sanitizers, fuzzers, and benchmarks
- [ ] Set up CI/CD pipelines and containerized builds

---
---

## PHASE 2: SYSTEMS ARCHITECTURE (Intermediate)
*Duration: ~6–9 months*

---

### Module 2.1: Advanced Memory Management & Allocation
#### 2.1.1 Allocator Design
- System allocators (`malloc`/`free` internals, `jemalloc`, `tcmalloc`, `mimalloc`)
- Custom allocators
  - Arena/region allocators (bump allocation, bulk free)
  - Pool allocators (fixed-size blocks, free lists)
  - Stack allocators (LIFO allocation)
  - Slab allocators (kernel-style, pre-allocated object caches)
- Allocation strategies for different workloads
  - Real-time (deterministic allocation time)
  - High-throughput (minimize fragmentation)
  - Embedded (static allocation, no heap)
- Memory fragmentation (internal, external) and mitigation
- Huge pages (2MB, 1GB — TLB pressure reduction)
- Memory pools and object recycling
- Placement new (C++) / unsafe allocation (Rust)

#### 2.1.2 Smart Memory Patterns
- Reference counting (strong, weak references, cycle detection)
- Garbage collection strategies (mark-sweep, generational, concurrent — understanding for interop)
- Copy-on-write (COW) semantics
- Memory-mapped files for data processing
- Zero-copy patterns (views, slices, borrows)
- Shared memory between processes
- Memory-safe abstractions over unsafe operations

#### 2.1.3 Memory Debugging & Profiling
- AddressSanitizer (ASan — buffer overflow, use-after-free, memory leaks)
- MemorySanitizer (MSan — uninitialized reads)
- ThreadSanitizer (TSan — data races)
- UndefinedBehaviorSanitizer (UBSan — undefined behavior)
- Valgrind Memcheck (memory leaks, invalid access)
- Valgrind Cachegrind/Callgrind (cache and call profiling)
- Heap profiling (`jemalloc` profiling, `heaptrack`, Rust's `dhat`)
- Leak sanitizers and production leak detection

---

### Module 2.2: Advanced Concurrency & Parallelism
#### 2.2.1 Lock-Free & Wait-Free Programming
- Compare-and-Swap (CAS) as building block
- Lock-free queue (Michael-Scott queue)
- Lock-free stack (Treiber stack)
- ABA problem and solutions (tagged pointers, hazard pointers, epoch-based reclamation)
- Memory reclamation in lock-free structures
  - Hazard pointers
  - Epoch-based reclamation (EBR)
  - Reference counting for lock-free structures
- Linearizability (correctness criterion for concurrent data structures)
- Wait-free algorithms (progress guarantee for every thread)
- When lock-free is worth it vs simple mutexes

#### 2.2.2 Advanced Threading Models
- Thread pools (work-stealing, work-sharing)
- M:N threading (green threads, goroutine-like models)
- Coroutines and fibers
  - C++ coroutines (`co_await`, `co_yield`, `co_return`)
  - Rust async (`async`/`await`, `Future`, `Pin`)
  - Stackful vs stackless coroutines
- Async runtimes (Tokio, async-std, Boost.Asio)
- Structured concurrency (scope-based task lifetime)
- Work-stealing schedulers (Tokio, Intel TBB)
- Thread-per-core architecture (seastar, Glommio)

#### 2.2.3 Parallel Computing
- Task parallelism vs data parallelism
- Fork-join parallelism (Rayon, Intel TBB)
- SIMD programming (SSE, AVX, NEON)
  - Auto-vectorization (compiler hints, loop structure)
  - Intrinsics (manual SIMD — `_mm256_add_ps`)
  - Portable SIMD (`std::simd` in Rust, Highway library in C++)
- GPU computing fundamentals (CUDA, OpenCL, Vulkan Compute — awareness)
- Cache-oblivious algorithms
- Parallel sorting, parallel reduction, parallel prefix sum
- Memory ordering deep dive
  - Sequential consistency (strongest, slowest)
  - Acquire-release semantics (synchronization pairs)
  - Relaxed ordering (counters, statistics)
  - Consume ordering (data-dependent — rarely used)
  - Fences (`std::atomic_thread_fence`)

#### 2.2.4 Concurrent Data Structures
- Concurrent hash maps (lock striping, lock-free)
- Concurrent queues (MPSC, MPMC, SPSC)
  - Bounded vs unbounded
  - Blocking vs non-blocking
- Concurrent skip lists
- Read-Copy-Update (RCU) — Linux kernel pattern
- Epoch-based memory reclamation with concurrent structures
- Crossbeam (Rust), Intel TBB (C++), libcds (C++)

---

### Module 2.3: Performance Engineering
#### 2.3.1 Profiling & Measurement
- CPU profiling (`perf`, `gprof`, `Instruments`, `VTune`, `Superluminal`)
  - `perf stat` (hardware counter statistics)
  - `perf record` + `perf report` (sampling profiler)
  - Flame graphs (Brendan Gregg's methodology)
- Memory profiling (heap profilers, allocation tracking)
- I/O profiling (`iostat`, `iotop`, `blktrace`)
- Network profiling (`tcpdump`, `Wireshark`, `ss`)
- System-wide tracing (`strace`, `ltrace`, `ftrace`, `eBPF`, `bpftrace`)
- Benchmarking methodology
  - Micro-benchmarks (Google Benchmark, Criterion.rs)
  - Statistical rigor (warmup, iterations, confidence intervals)
  - Avoiding common benchmarking pitfalls (dead code elimination, caching effects)
  - `perf stat` for hardware counters (IPC, cache misses, branch misses)

#### 2.3.2 Optimization Techniques
- Algorithmic optimization (always first — Big-O improvements)
- Data structure optimization (cache-friendly layouts, SoA vs AoS)
- Memory optimization
  - Reducing allocations (object pools, arenas, stack allocation)
  - Reducing cache misses (data locality, prefetching, alignment)
  - Reducing false sharing (padding between thread-local data)
  - Small buffer optimization (SBO/SSO — inline small data)
- CPU optimization
  - Branch prediction hints (`likely`/`unlikely`, `__builtin_expect`)
  - Loop unrolling and vectorization
  - Avoiding branch mispredictions (branchless programming)
  - Function inlining (`inline`, `__attribute__((always_inline))`, LTO)
- I/O optimization
  - Batching I/O operations
  - Buffering strategies
  - Zero-copy I/O
  - Async I/O (`io_uring`, `epoll`)
  - Direct I/O (bypass OS page cache)
- Compiler optimizations
  - Optimization levels (`-O2`, `-O3`, `-Os`)
  - Link-Time Optimization (LTO)
  - Profile-Guided Optimization (PGO)
  - Whole-program optimization

#### 2.3.3 Latency Engineering
- Latency vs throughput (trade-offs)
- Tail latency (P99, P99.9, P99.99)
- Latency measurement (high-resolution timers, TSC)
- Latency sources (system calls, allocations, locks, cache misses, page faults, GC pauses, context switches)
- Latency reduction techniques
  - Lock-free algorithms
  - Busy-waiting vs blocking (CPU cost vs latency)
  - CPU pinning and thread affinity
  - NUMA-aware allocation
  - Kernel bypass (DPDK, `io_uring`)
  - Real-time scheduling (`SCHED_FIFO`, `SCHED_RR`)
  - Disabling swap, huge pages, isolcpus
- Performance budgets and SLAs

---

### Module 2.4: Systems Design Patterns
#### 2.4.1 Architectural Patterns for Systems Software
- **Layered Architecture** (hardware abstraction layers, protocol stacks)
- **Microkernel Architecture** (minimal core, plugins/extensions)
- **Pipeline Architecture** (data processing stages)
- **Event-Driven Architecture** (event loops, reactor/proactor)
- **Actor Model** (message-passing concurrency — Erlang-style)
- **CSP (Communicating Sequential Processes)** (Go-style channels)
- **ECS (Entity-Component-System)** (game engines, simulation)
- **Plugin/Extension Architecture** (shared libraries, dynamic loading)
- **Shared-Nothing Architecture** (process isolation, message passing)
- **Thread-Per-Core Architecture** (Seastar, ScyllaDB)

#### 2.4.2 Reliability & Resilience Patterns
- Crash-only software design
- Write-ahead logging (WAL) for durability
- Checksumming and data integrity verification (CRC32, xxHash)
- Graceful degradation
- Circuit breaker pattern (for external dependencies)
- Retry with exponential backoff and jitter
- Timeout strategies
- Watchdog timers (detect hangs)
- Core dumps and post-mortem debugging
- Defensive programming (assertions, invariant checking)
- Error handling strategies (error codes, exceptions, `Result` type, error categories)

#### 2.4.3 Scalability Patterns
- Horizontal vs vertical scaling for systems software
- Sharding and partitioning strategies
- Connection pooling and resource management
- Read replicas and write distribution
- Caching layers (L1/L2/L3 → application cache → distributed cache)
- Rate limiting and backpressure
- Batching and coalescing
- Write combining and read coalescing
- Async processing and work queues
- Load shedding (reject work to protect system)

---

### Module 2.5: Network Programming (Advanced)
#### 2.5.1 High-Performance Networking
- Event-driven servers (`epoll` + non-blocking sockets)
- `io_uring` for high-performance I/O (Linux 5.1+)
  - Submission Queue / Completion Queue architecture
  - Buffer registration, file registration
  - Linked operations, timeout operations
- Kernel bypass networking (DPDK — awareness)
- Zero-copy networking (`sendfile`, `splice`, `MSG_ZEROCOPY`)
- Connection management at scale (millions of connections)
- SO_REUSEPORT (kernel load balancing)
- TCP tuning (buffer sizes, congestion control algorithms, keepalive)

#### 2.5.2 Protocol Design & Implementation
- Protocol design principles (framing, versioning, extensibility)
- Binary protocol design (length-prefixed, delimiter-based, TLV)
- Text protocol design (HTTP-like, Redis RESP, SMTP)
- Protocol Buffers (protobuf) — schema, code generation, wire format
- FlatBuffers (zero-copy serialization)
- Cap'n Proto (zero-copy, RPC built-in)
- MessagePack, CBOR (binary JSON alternatives)
- gRPC implementation (HTTP/2 framing, streaming, flow control)
- Custom RPC frameworks

#### 2.5.3 Security in Systems
- TLS implementation and configuration
  - TLS 1.3 (reduced round trips, forward secrecy)
  - Certificate management, mutual TLS (mTLS)
  - OpenSSL, BoringSSL, rustls
- Cryptographic primitives (AES, ChaCha20, SHA-256, HMAC, Ed25519 — usage, not implementation)
- Secure coding practices
  - Buffer overflow prevention
  - Integer overflow checking
  - Format string vulnerabilities
  - Use-after-free prevention
  - Time-of-check-time-of-use (TOCTOU)
- Sandboxing and privilege separation
  - `seccomp` (syscall filtering)
  - Capabilities (Linux)
  - Namespaces and cgroups (isolation)
- Constant-time comparison (preventing timing attacks)
- Memory wiping for secrets (`explicit_bzero`, `zeroize`)
- Dependency auditing and supply chain security

---

### Module 2.6: Embedded & Resource-Constrained Systems (Fundamentals)
#### 2.6.1 Embedded Concepts
- Bare-metal programming (no OS, direct hardware access)
- Cross-compilation for embedded targets
- Startup code and linker scripts (awareness)
- Memory constraints (limited RAM, limited flash)
- `no_std` Rust / freestanding C++ (no standard library)
- Real-time constraints (hard real-time vs soft real-time)
- Interrupt handling (ISRs, priority, reentrancy)
- Peripheral access (GPIO, UART, SPI, I2C — awareness)
- Watchdog timers
- Power management and sleep modes (awareness)

#### 2.6.2 Resource-Constrained Design
- Static allocation strategies (no heap, compile-time allocation)
- Fixed-point arithmetic (when floating-point is unavailable)
- Code size optimization (`-Os`, LTO, dead code elimination)
- Memory-efficient data structures
- Deterministic memory management (no fragmentation)
- Stack usage analysis
- Worst-case execution time (WCET) analysis — awareness

---

### Module 2.7: Build Systems & Toolchain Mastery
#### 2.7.1 Advanced Build Systems
- CMake in depth (modern CMake targets, generator expressions, presets)
- Cargo workspaces and feature flags (Rust)
- Bazel (hermetic builds, remote caching, remote execution — awareness)
- Build caching (`ccache`, `sccache`)
- Distributed builds
- Custom toolchains and cross-compilation

#### 2.7.2 Compiler Toolchains
- Compiler pipeline (preprocessor → parser → AST → IR → optimizer → code generator → assembler → linker)
- Compiler flags for safety (`-Wall`, `-Wextra`, `-Werror`, `-fsanitize=*`)
- Compiler flags for performance (`-O2`, `-O3`, `-march=native`, `-flto`)
- Static vs dynamic linking (trade-offs, symbol resolution, PLT/GOT)
- Shared libraries (`.so`, `.dll`, `.dylib`)
  - Symbol visibility (`__attribute__((visibility("default")))`)
  - ABI compatibility (binary compatibility across versions)
  - Versioned symbols
- Linker scripts (awareness — for embedded/OS dev)
- LLVM ecosystem (Clang, lld, LLVM IR — awareness)

---

### 🏗️ Phase 2 Project: High-Performance Database Engine
> Build a storage engine (like a simplified LSM-tree or B+tree engine) with:
> - **B+tree or LSM-tree** data structure for ordered key-value storage
> - **Write-Ahead Log (WAL)** with crash recovery and checkpointing
> - **MVCC** (Multi-Version Concurrency Control) for concurrent reads/writes
> - **Custom memory allocator** (arena for transactions, pool for pages)
> - **Memory-mapped I/O** or direct I/O for page management
> - **Buffer pool** with clock/LRU eviction
> - **Concurrent access** with fine-grained locking or lock-free structures
> - **Binary protocol** for client communication (TCP + custom wire format)
> - **Compression** (LZ4, Snappy, Zstd per block/page)
> - **Bloom filters** for efficient negative lookups
> - **Extensive benchmarks** (throughput, latency, comparison with RocksDB/SQLite)
> - **Sanitizer-clean** (ASan, TSan, UBSan — zero issues)
> - **Fuzz-tested** for parser, protocol handler, and storage engine
> - **C4 architecture diagrams** and design documentation
>
> **Why:** Covers every core systems concern — memory management, concurrency, persistence, I/O optimization, binary protocols, and performance engineering — in one cohesive project.

---

### ✅ After Phase 2 — You Can:
- [ ] Design and implement custom memory allocators
- [ ] Build lock-free and concurrent data structures
- [ ] Profile and optimize systems for latency and throughput
- [ ] Implement high-performance network servers
- [ ] Design binary protocols and serialization formats
- [ ] Build persistent storage engines with crash recovery
- [ ] Apply systems-specific design patterns
- [ ] Write security-conscious systems code

---
---

## PHASE 3: MASTERY & SPECIALIZATION (Advanced)
*Duration: ~6–12 months + ongoing*

---

### Module 3.1: Distributed Systems Engineering
#### 3.1.1 Distributed Systems Fundamentals
- Fallacies of distributed computing (Peter Deutsch)
- Consistency models (strong, eventual, causal, linearizable, serializable)
- Consensus algorithms
  - Paxos (conceptual understanding)
  - Raft (leader election, log replication, safety — implement or deeply study)
  - Multi-Paxos / Multi-Raft
- Distributed transactions (2PC, 3PC, Saga)
- Time in distributed systems
  - Physical clocks (NTP, PTP, clock drift)
  - Logical clocks (Lamport timestamps)
  - Vector clocks
  - Hybrid Logical Clocks (HLC)
  - TrueTime (Google — GPS + atomic clocks)
- Failure detection (heartbeats, phi accrual failure detector)
- Split-brain and partition handling
- Quorum systems (read/write quorums, flexible quorums)
- Consistent hashing (virtual nodes, rebalancing)
- Gossip protocols (membership, failure detection, dissemination)

#### 3.1.2 Distributed Storage
- Replication strategies (single-leader, multi-leader, leaderless)
- Conflict resolution (last-write-wins, CRDTs, merge functions)
- CRDTs (Conflict-Free Replicated Data Types)
  - G-Counter, PN-Counter, G-Set, OR-Set, LWW-Register
  - State-based vs operation-based CRDTs
- Log-structured storage (LSM-trees, compaction strategies)
- B+tree storage engines
- Data partitioning (hash, range, composite)
- Anti-entropy protocols
- Merkle trees for data synchronization
- Change Data Capture (CDC)

#### 3.1.3 Distributed Messaging & Streaming
- Message broker architecture (queues, topics, partitions)
- Apache Kafka internals (log-structured storage, ISR, leader election, compaction)
- NATS / NATS JetStream (lightweight messaging)
- ZeroMQ (broker-less messaging — library)
- Message ordering guarantees (partition-level, total-order)
- Exactly-once semantics (idempotency, deduplication, transactions)
- Backpressure and flow control
- Event sourcing and event-driven architecture

#### 3.1.4 RPC Frameworks
- gRPC deep dive
  - Protocol Buffers (schema design, evolution, wire format)
  - HTTP/2 transport (streams, flow control, header compression)
  - Streaming patterns (unary, server-stream, client-stream, bidirectional)
  - Interceptors/middleware
  - Load balancing (client-side, look-aside)
  - Health checking and graceful shutdown
  - Deadline propagation
- Apache Thrift (awareness)
- Cap'n Proto RPC (awareness)
- Custom RPC frameworks (when to build your own)

---

### Module 3.2: Database Internals
#### 3.2.1 Storage Engine Design
- **B+Tree Engines**
  - Page-based storage (fixed-size pages, page directory)
  - Buffer pool management (clock, LRU, LRU-K, 2Q)
  - Slotted pages (variable-length records)
  - Overflow pages
  - Index organization (clustered vs non-clustered)
  - Concurrent B+tree (latch crabbing, B-link trees, optimistic latching)
- **LSM-Tree Engines**
  - MemTable → Immutable MemTable → SSTable flush
  - Compaction strategies (size-tiered, leveled, FIFO, universal)
  - Bloom filters for point lookups
  - Block caches
  - Write amplification vs read amplification vs space amplification trade-offs
  - RocksDB architecture (detailed)
- **Other Storage Models**
  - Column-oriented storage (Parquet, Arrow, ClickHouse model)
  - Log-structured storage (append-only, immutable)
  - In-memory storage engines (skiplist, adaptive radix tree)

#### 3.2.2 Transaction Processing
- ACID implementation
- Concurrency control
  - Two-Phase Locking (2PL) — strict, strong strict
  - Optimistic Concurrency Control (OCC)
  - MVCC implementation (version chains, garbage collection)
  - Timestamp ordering
- Isolation levels implementation
  - Read Committed (how databases achieve it)
  - Snapshot Isolation (write skew anomaly)
  - Serializable Snapshot Isolation (SSI)
- Write-Ahead Logging
  - Log record format (LSN, prevLSN, transaction ID, page ID, operation)
  - ARIES recovery algorithm (analysis, redo, undo)
  - Group commit
  - Log truncation and checkpointing

#### 3.2.3 Query Processing (Awareness)
- Query parsing and planning
- Query optimization (cost-based, rule-based)
- Join algorithms (nested loop, hash, sort-merge)
- Query execution models (volcano/iterator, vectorized, compiled)
- Vectorized execution (columnar processing, SIMD)
- JIT query compilation (awareness — LLVM-based)

---

### Module 3.3: Operating Systems Internals (Advanced)
#### 3.3.1 Kernel Concepts
- Kernel architecture (monolithic, microkernel, hybrid)
- System call implementation (trap, context switch, dispatch table)
- Interrupt handling (top-half, bottom-half, softirqs, tasklets)
- Kernel memory management (buddy allocator, slab allocator, kmalloc)
- Kernel synchronization (spinlocks, RCU, seqlocks, per-CPU variables)
- Virtual file system (VFS) layer implementation
- Device driver model (awareness)

#### 3.3.2 Advanced Process & Thread Management
- Scheduler design (CFS, O(1), deadline scheduler)
- Real-time scheduling (SCHED_FIFO, SCHED_RR, SCHED_DEADLINE)
- CPU affinity and NUMA topology
- `cgroups` v2 (resource limiting, accounting)
- Namespaces (PID, network, mount, user, IPC — container foundations)
- Process tracing (`ptrace`, `strace`, `perf`)
- eBPF (Extended Berkeley Packet Filter)
  - eBPF programs (tracing, networking, security)
  - eBPF maps (data sharing between kernel and user space)
  - `bpftrace` (high-level tracing language)
  - `libbpf` (C/C++ eBPF library)
  - Aya (Rust eBPF library)
  - Use cases: observability, networking, security enforcement

#### 3.3.3 Networking Stack Internals
- Linux networking stack (socket → TCP/IP → device driver)
- sk_buff (socket buffer — kernel network data structure)
- Netfilter and iptables/nftables (packet filtering)
- XDP (eXpress Data Path) — high-performance packet processing
- TCP stack implementation details (connection tracking, window management)
- DPDK (Data Plane Development Kit) — kernel bypass networking

---

### Module 3.4: Compiler & Language Implementation
#### 3.4.1 Compiler Frontend
- Lexical analysis (tokenization, regular expressions, finite automata)
- Parsing (recursive descent, Pratt parsing, parser combinators)
  - LL, LR, LALR parsers (conceptual)
  - PEG (Parsing Expression Grammars)
- Abstract Syntax Trees (AST design, visitor pattern)
- Semantic analysis (type checking, name resolution, scope analysis)
- Error reporting and recovery

#### 3.4.2 Compiler Backend (Awareness)
- Intermediate representations (SSA form, three-address code)
- Optimization passes (dead code elimination, constant folding, inlining, loop optimization)
- Register allocation (graph coloring — conceptual)
- Code generation (instruction selection, scheduling)
- LLVM as backend (LLVM IR, passes, targets — awareness)

#### 3.4.3 Runtime Systems
- Runtime system design (initialization, cleanup, panic handling)
- Stack management (stack frames, calling conventions, stack unwinding)
- Exception handling implementation (C++ exceptions, setjmp/longjmp, Itanium ABI)
- Garbage collector implementation
  - Mark-and-sweep
  - Copying collector
  - Generational GC
  - Concurrent/incremental GC
  - Reference counting with cycle detection
- JIT compilation (basic concepts — tracing, method-based)
- FFI (Foreign Function Interface) implementation
  - C ABI as lingua franca
  - Calling conventions (cdecl, stdcall, System V AMD64 ABI)
  - `extern "C"` (C++ name mangling avoidance)
  - Rust `#[no_mangle]`, `extern "C"`

---

### Module 3.5: Advanced Networking & Distributed Protocols
#### 3.5.1 Custom Protocol Implementation
- Implementing a simple TCP-based protocol from scratch
- Connection management (connection pools, keepalive, reconnection)
- Serialization/deserialization performance
- Protocol versioning and backward compatibility
- Flow control and backpressure implementation
- Multiplexing connections (HTTP/2-style stream multiplexing)
- TLS integration (handshake, certificate validation)

#### 3.5.2 Consensus Protocol Implementation
- Raft implementation (leader election, log replication, membership changes)
- Membership changes (joint consensus, single-server changes)
- Snapshotting and log compaction
- Testing distributed protocols (deterministic simulation, Jepsen-style testing)
- Formal verification of protocols (TLA+ — awareness)

---

### Module 3.6: Security Engineering (Advanced)
#### 3.6.1 Memory Safety & Exploit Mitigation
- Buffer overflows (stack, heap, off-by-one)
- Use-after-free exploitation
- Return-Oriented Programming (ROP) — awareness
- Mitigation techniques
  - Stack canaries
  - ASLR (Address Space Layout Randomization)
  - DEP/NX (Non-Executable Memory)
  - Control-Flow Integrity (CFI)
  - Shadow stacks
  - Rust's ownership model as memory safety solution
- Secure memory allocation (guard pages, randomized allocation)
- Constant-time programming (preventing side-channel attacks)
- Fuzzing for security (coverage-guided fuzzing, structure-aware fuzzing)

#### 3.6.2 Cryptographic Engineering
- Using cryptographic libraries correctly (not implementing your own)
- Secure random number generation
- Key derivation functions (PBKDF2, scrypt, Argon2)
- Authenticated encryption (AES-GCM, ChaCha20-Poly1305)
- Digital signatures (Ed25519, ECDSA)
- Certificate management and PKI
- TLS configuration best practices
- Secure coding guidelines (CERT C, CERT C++, Rust Safety)

---

### Module 3.7: Observability & Production Operations
#### 3.7.1 Systems Observability
- **Metrics**
  - Prometheus client libraries (counters, gauges, histograms)
  - Custom metrics for systems software (allocation rates, cache hit rates, queue depths, latency distributions)
  - Grafana dashboards
  - USE methodology (Utilization, Saturation, Errors — Brendan Gregg)
  - RED methodology (Rate, Errors, Duration)
- **Logging**
  - Structured logging (JSON format)
  - Log levels and filtering
  - High-performance logging (lock-free log buffers, async writing)
  - Log aggregation (ELK, Loki)
- **Tracing**
  - Distributed tracing (OpenTelemetry, Jaeger)
  - In-process tracing (`perf`, `ftrace`, eBPF)
  - Custom span instrumentation
  - Trace sampling strategies
- **Continuous Profiling**
  - Production profiling (`pprof`, Pyroscope, Parca)
  - Always-on CPU profiling (low-overhead sampling)
  - Memory profiling in production

#### 3.7.2 Deployment & Operations
- CI/CD for systems software
  - Multi-platform builds (Linux, macOS, Windows, embedded targets)
  - Cross-compilation pipelines
  - Sanitizer runs in CI (ASan, TSan, UBSan, MSan)
  - Fuzz testing in CI
  - Benchmark regression detection
  - Static analysis in CI
- Deployment strategies
  - Blue/green deployments
  - Canary releases
  - Rolling updates
  - Feature flags for systems software
- Kubernetes deployment for systems services
  - Custom resource definitions
  - Operators (for stateful systems — database operators)
  - Pod disruption budgets
  - Resource limits (CPU, memory)
  - Node affinity and anti-affinity
- Infrastructure as Code (Terraform)
- Configuration management
- Chaos engineering for systems software
  - Fault injection (kill process, network partition, disk failure, clock skew)
  - Jepsen testing framework (correctness under failure)
  - Deterministic simulation testing (FoundationDB approach)

---

### Module 3.8: Architecture Documentation & Technical Leadership
#### 3.8.1 Architecture Documentation
- C4 Model (Context, Container, Component, Code diagrams)
- Architecture Decision Records (ADRs)
- RFC process for technical proposals
- Technical writing for systems engineers
- Performance benchmark reports
- Diagramming tools (PlantUML, Mermaid, draw.io)

#### 3.8.2 Architecture Evaluation
- Performance modeling and capacity planning
- Architecture trade-off analysis (ATAM)
- Quality attribute workshops
- Technical debt quantification and management
- Architecture fitness functions
- Risk-storming

#### 3.8.3 Technical Leadership
- Architect's role in systems teams
- Mentoring systems engineers
- Establishing coding standards for systems code
- Code review as architectural tool
- Building communities of practice
- Technology radar
- Buy vs Build analysis for systems components
- Open-source strategy (when to use, when to build, when to contribute)

---

### Module 3.9: Specialization Tracks (Choose 1–2)

#### 3.9.1 Track: Database Engine Development
- Full storage engine implementation (B+tree or LSM-tree)
- Query optimizer design
- Distributed database design (sharding, replication, consensus)
- Vectorized execution engine
- Transaction processing (MVCC, 2PL, SSI)
- Study: SQLite, PostgreSQL, CockroachDB, TiKV, DuckDB architecture

#### 3.9.2 Track: Game Engine Development
- Rendering architecture (forward, deferred, clustered)
- Entity-Component-System (ECS) architecture
- Physics engine basics (collision detection, rigid body dynamics)
- Asset pipeline (loading, streaming, hot-reload)
- Frame-based programming model
- Multi-threaded job systems
- Memory management for games (frame allocators, double buffering)
- Audio engine basics
- Networking for games (client-side prediction, lag compensation, state synchronization)
- Study: Bevy, Unreal Engine, Godot, Unity architecture

#### 3.9.3 Track: Operating Systems Development
- Writing a simple kernel (boot, memory management, scheduling, file system)
- Device driver development (Linux kernel modules — awareness)
- Hypervisor basics (hardware virtualization, VMX — awareness)
- Container runtime implementation (namespaces + cgroups)
- eBPF program development
- Study: Linux kernel, xv6, Redox OS, seL4

#### 3.9.4 Track: Networking & Infrastructure
- Custom proxy / load balancer implementation
- Service mesh data plane (Envoy-like — awareness)
- DNS server implementation
- VPN / tunnel implementation
- Network protocol implementation (QUIC, custom reliable UDP)
- Packet processing pipelines (XDP, DPDK)
- Study: Envoy, HAProxy, Nginx, DPDK architecture

#### 3.9.5 Track: Embedded Systems & IoT
- RTOS development (FreeRTOS, Zephyr — integration)
- Bare-metal programming (startup code, linker scripts, interrupt tables)
- Peripheral driver development (UART, SPI, I2C, GPIO)
- Communication protocols (MQTT, CoAP, BLE, LoRa)
- OTA (Over-the-Air) update systems
- Safety-critical systems (MISRA, DO-178C — awareness)
- Power optimization and battery management
- Study: Embassy (Rust), Zephyr, FreeRTOS, RIOT architecture

#### 3.9.6 Track: High-Frequency Trading / Low-Latency Systems
- Ultra-low-latency architecture (microsecond/nanosecond level)
- Kernel bypass (DPDK, Solarflare OpenOnload)
- Lock-free order books
- FPGA integration (awareness)
- Market data feed handlers
- Co-location and network optimization
- Deterministic execution and latency jitter elimination
- Hot path optimization (no allocation, no syscalls, no branches)

#### 3.9.7 Track: Compiler & Language Tools
- Full compiler implementation (lexer → parser → type checker → codegen)
- Language Server Protocol (LSP) implementation
- Debugger implementation (DWARF, breakpoints, stepping)
- Code formatter and linter implementation
- Build system design
- Package manager design
- Study: rustc, Clang/LLVM, GCC, TypeScript compiler

---

### 🏗️ Phase 3 Project: Distributed Key-Value Store with Consensus
> Architect and build a distributed key-value store:
> - **Raft consensus** implementation (leader election, log replication, snapshotting)
> - **Multi-node cluster** with membership changes
> - **LSM-tree or B+tree storage engine** (from Phase 2 project, improved)
> - **MVCC** for snapshot isolation
> - **Custom binary protocol** with Protocol Buffers or FlatBuffers
> - **gRPC** for inter-node communication
> - **Client library** with retry, timeout, leader-following
> - **Linearizable reads** (read from leader with lease)
> - **Jepsen-style testing** (fault injection, partition testing)
> - **Full observability** (Prometheus metrics, OpenTelemetry tracing, structured logging)
> - **Multi-platform Docker builds** with Kubernetes deployment (Helm charts, StatefulSet)
> - **Performance benchmarks** (YCSB workloads, comparison with etcd/Redis cluster)
> - **Architecture documentation** (C4 diagrams, ADRs, RFC for protocol design)
>
> **Why:** This is the mastery capstone for systems engineering — it ties together distributed systems, storage engines, consensus, networking, performance, testing, observability, and deployment.

---

### ✅ After Phase 3 — You Can:
- [ ] Design and implement distributed systems with consensus
- [ ] Build database storage engines from scratch
- [ ] Optimize systems for nanosecond-level latency
- [ ] Lead architecture reviews and trade-off analysis
- [ ] Write and evaluate RFCs and ADRs
- [ ] Conduct Jepsen-style correctness testing
- [ ] Profile and optimize at CPU instruction level
- [ ] Mentor and grow systems engineers
- [ ] Make and defend strategic technical decisions

---
---

## PHASE 4: AI-ERA SYSTEMS ENGINEERING
*Duration: ~4–6 months*

---

### Module 4.1: AI/ML Infrastructure Foundations
#### 4.1.1 Machine Learning Concepts (Systems Engineer's Perspective)
- Supervised vs unsupervised vs reinforcement learning (conceptual)
- Training vs inference lifecycle (systems implications)
- Tensors and multi-dimensional arrays (the fundamental data type)
- Model parameters, weights, gradients
- Forward pass and backward pass (computational graph)
- Batch processing and mini-batch SGD
- Model size vs memory (parameter count × precision = memory requirement)
- Cost economics of training vs inference

#### 4.1.2 GPU Computing & Heterogeneous Systems
- GPU architecture (streaming multiprocessors, warps, CUDA cores)
- GPU memory hierarchy (registers, shared memory, L1/L2 cache, global memory)
- CUDA programming model (kernels, grids, blocks, threads)
  - Thread indexing (`threadIdx`, `blockIdx`, `blockDim`, `gridDim`)
  - Memory management (`cudaMalloc`, `cudaMemcpy`, `cudaFree`)
  - Synchronization (`__syncthreads`, CUDA streams, events)
  - Occupancy optimization
- GPU memory management
  - Host ↔ device transfers (PCIe bottleneck)
  - Unified memory (`cudaMallocManaged`)
  - Pinned memory (`cudaMallocHost`)
  - Memory coalescing (aligned, sequential access)
- Alternative GPU APIs
  - Vulkan Compute (cross-platform GPU compute)
  - Metal (Apple — awareness)
  - OpenCL (cross-vendor — awareness)
  - SYCL (C++ abstraction — awareness)
  - WebGPU/wgpu (Rust — awareness)
- CUDA vs ROCm (NVIDIA vs AMD)
- TPUs, NPUs, custom AI accelerators (awareness)

#### 4.1.3 Tensor Libraries & Frameworks (Systems Perspective)
- NumPy memory layout (contiguous arrays, strides, broadcasting)
- PyTorch internals (awareness)
  - ATen (C++ tensor library)
  - Autograd (automatic differentiation engine)
  - TorchScript (JIT compilation)
  - Custom C++/CUDA extensions for PyTorch
- ONNX Runtime (cross-framework model inference)
- TensorRT (NVIDIA inference optimization — awareness)
- Triton (GPU kernel language for ML — awareness)

---

### Module 4.2: ML Model Inference Systems
#### 4.2.1 Inference Engine Architecture
- Model loading and initialization
- Input preprocessing and output postprocessing
- Batch inference vs single inference
- Dynamic batching (collect requests, batch, process, unbatch)
- Model execution
  - Graph-based execution (operator fusion, graph optimization)
  - Eager execution vs graph execution trade-offs
- Multi-model serving (load multiple models, route requests)
- Model versioning and hot-swapping

#### 4.2.2 Inference Optimization
- Quantization
  - FP32 → FP16 → INT8 → INT4 (precision vs quality trade-off)
  - Post-Training Quantization (PTQ)
  - Quantization-Aware Training (QAT) — awareness
  - GPTQ, AWQ, GGUF quantization formats
- Operator fusion (combine multiple operations into one kernel)
- Graph optimization (constant folding, dead node elimination)
- Memory optimization
  - KV cache management for transformer models
  - PagedAttention (vLLM approach — virtual memory for KV cache)
  - Tensor parallelism (split model across GPUs)
  - Pipeline parallelism (split layers across GPUs)
- Speculative decoding (draft model + verification)
- Continuous batching (process new requests without waiting for batch completion)
- FlashAttention (memory-efficient attention computation)

#### 4.2.3 Model Serving Frameworks
- vLLM architecture (PagedAttention, continuous batching, OpenAI-compatible API)
- TensorRT-LLM (NVIDIA inference — awareness)
- ONNX Runtime for serving
- Triton Inference Server (NVIDIA — multi-framework serving)
- llama.cpp (CPU inference, quantization, cross-platform)
- Custom inference server design
- Serving metrics (tokens/second, time-to-first-token, throughput, latency)

---

### Module 4.3: LLM Systems Architecture
#### 4.3.1 Transformer Architecture (Systems Perspective)
- Attention mechanism (matrix multiplication at scale)
- Multi-head attention (parallel computation)
- Feed-forward networks (computation-bound)
- Memory requirements calculation
  - Model weights: `parameters × bytes_per_parameter`
  - KV cache: `layers × heads × seq_len × head_dim × batch_size × 2 × precision`
  - Activation memory during training
- Context window scaling challenges
  - Quadratic attention complexity
  - Linear attention alternatives (Mamba, RWKV — awareness)
  - Sliding window attention
  - Sparse attention patterns

#### 4.3.2 LLM Training Infrastructure
- Distributed training patterns
  - Data parallelism (replicate model, split data)
  - Model parallelism (split model across devices)
  - Tensor parallelism (split individual operations)
  - Pipeline parallelism (split layers)
  - ZeRO optimizer (partition optimizer states, gradients, parameters)
  - FSDP (Fully Sharded Data Parallel)
- Training framework internals
  - DeepSpeed (Microsoft — distributed training library)
  - Megatron-LM (NVIDIA — large model training)
  - JAX/XLA (Google — array computing with auto-differentiation)
- Mixed precision training (FP16/BF16 + FP32 master weights)
- Gradient accumulation (simulate larger batches)
- Checkpointing and fault tolerance
- Training data pipelines (high-throughput data loading)

#### 4.3.3 Fine-Tuning Infrastructure
- Full fine-tuning (all parameters — expensive)
- LoRA (Low-Rank Adaptation — parameter-efficient)
  - How LoRA works (freeze base, train small adapter matrices)
  - Memory savings calculation
  - LoRA serving (multiple adapters on single base model)
- QLoRA (quantized base + LoRA adapters)
- Adapter serving architecture (dynamic adapter loading)
- Training data preparation pipelines

---

### Module 4.4: Vector Search & RAG Infrastructure
#### 4.4.1 Vector Index Implementation
- Vector similarity algorithms
  - Brute-force (exact, O(n))
  - KD-trees (low dimensions)
  - IVF (Inverted File Index — partition + search)
  - HNSW (Hierarchical Navigable Small World — state of the art for ANN)
    - Graph construction (insertion algorithm, neighbor selection)
    - Search algorithm (greedy traversal)
    - Parameters (M, ef_construction, ef_search)
  - Product Quantization (PQ — compressed vectors for memory efficiency)
  - ScaNN (Google — learned quantization)
- Vector index storage (memory-mapped, disk-based)
- Hybrid search (vector + inverted index — BM25 fusion)
- Filtering with vector search (pre-filter vs post-filter)
- Billion-scale vector search (sharding, distributed index)

#### 4.4.2 Embedding Pipeline Infrastructure
- Embedding model serving (batch encoding, GPU inference)
- Embedding computation optimization (quantized models, ONNX)
- Document processing pipelines (chunking, parsing, OCR)
- Index building pipelines (batch embedding → index construction)
- Incremental index updates (insert, delete, update without full rebuild)

#### 4.4.3 RAG System Architecture (Infrastructure Perspective)
- Document ingestion pipeline (scalable, fault-tolerant)
- Vector database architecture (Qdrant, Milvus, Weaviate, Pinecone internals — awareness)
- Query pipeline optimization (parallel retrieval, re-ranking)
- Caching strategies for RAG (query cache, embedding cache, LLM response cache)
- Hybrid retrieval (dense + sparse + metadata filtering)

---

### Module 4.5: AI Systems in Production
#### 4.5.1 ML Serving Infrastructure
- Model registry and versioning
- A/B testing infrastructure for models
- Shadow/canary deployment for models
- Autoscaling based on inference load
- GPU cluster management (scheduling, allocation, preemption)
- Multi-tenancy for GPU resources
- Cost optimization (spot instances, GPU sharing, batching efficiency)

#### 4.5.2 LLM Gateway & Proxy
- Request routing (model selection, load balancing)
- Token counting and cost tracking
- Rate limiting and quota management
- Streaming response proxying
- Fallback chains (primary → secondary → degradation)
- Semantic caching (embedding-based response caching)
- Guardrail integration (input/output filtering)
- Request/response logging and auditing

#### 4.5.3 AI Observability
- Inference latency monitoring (time-to-first-token, tokens/second, total latency)
- GPU utilization monitoring (SM occupancy, memory utilization, PCIe bandwidth)
- Model quality monitoring (drift detection, quality scoring)
- Token usage tracking and cost attribution
- Trace-based debugging for AI pipelines
- Alert on quality degradation, latency spikes, error rate changes

#### 4.5.4 AI Safety Systems
- Prompt injection detection (classifier-based, heuristic-based)
- Content filtering pipelines (toxicity, PII, prohibited topics)
- Output validation (format checking, factuality checking)
- Rate limiting and abuse prevention
- Audit logging for compliance
- Guardrail frameworks and their implementation

---

### Module 4.6: AI-Augmented Systems Engineering
#### 4.6.1 AI for Systems Code
- AI coding assistants for C++/Rust (Copilot, Cursor, Cline effectiveness and limitations)
- AI for code review (detecting memory safety issues, concurrency bugs)
- AI for test generation (edge cases, fuzz seed generation)
- AI for performance optimization suggestions
- AI for debugging (crash analysis, log analysis)
- Limitations: AI often generates unsafe systems code — always verify

#### 4.6.2 AI for Systems Operations
- AIOps for systems (anomaly detection in metrics, log analysis)
- AI-assisted incident response
- Predictive autoscaling
- Automated root cause analysis
- AI for capacity planning

---

### 🏗️ Phase 4 Project: LLM Inference Engine
> Build a production-grade LLM inference engine:
> - **Transformer inference** from scratch (attention, feed-forward, layer norm — no PyTorch)
> - **GGUF model loading** (parse model file, load weights, configure architecture)
> - **KV cache** with memory management (pre-allocation, reuse)
> - **Quantization support** (FP16, INT8, INT4 inference)
> - **Batch inference** with dynamic batching (continuous batching)
> - **SIMD optimization** for CPU inference (AVX2, NEON)
> - **GPU inference** with CUDA kernels (optional — FlashAttention-style)
> - **HTTP API** (OpenAI-compatible `/v1/chat/completions`)
> - **Streaming responses** (Server-Sent Events, token-by-token)
> - **Concurrent request handling** with thread pool
> - **Memory-mapped model loading** (mmap for fast startup)
> - **Prometheus metrics** (tokens/sec, latency, memory, GPU utilization)
> - **Benchmarks** comparing against llama.cpp and vLLM
> - **Docker deployment** with GPU support
>
> **Why:** Covers GPU programming, numerical computing, memory management, high-performance I/O, binary format parsing, and API design — applied to the hottest domain in computing.

---

### ✅ After Phase 4 — You Can:
- [ ] Build GPU-accelerated compute kernels (CUDA or Vulkan Compute)
- [ ] Implement LLM inference engines with optimization
- [ ] Design and build vector search systems
- [ ] Architect ML serving infrastructure for production
- [ ] Optimize models for inference (quantization, operator fusion)
- [ ] Build LLM proxy/gateway with caching and guardrails
- [ ] Monitor and operate AI systems in production
- [ ] Make informed decisions about AI infrastructure trade-offs
- [ ] Use AI tools effectively while understanding their limitations for systems code

---
---

## 📚 ESSENTIAL RESOURCES

### Must-Read Books (In Order)
| Phase | Book | Author |
|-------|------|--------|
| 1 | Computer Systems: A Programmer's Perspective (CS:APP) | Bryant & O'Hallaron |
| 1 | The Linux Programming Interface | Michael Kerrisk |
| 1 | Operating Systems: Three Easy Pieces (OSTEP — free) | Arpaci-Dusseau |
| 1 | Design Patterns | Gang of Four |
| 1 | The Pragmatic Programmer | Hunt & Thomas |
| 2 | The Art of Multiprocessor Programming | Herlihy & Shavit |
| 2 | C++ Concurrency in Action (2nd Ed) | Anthony Williams |
| 2 | Is Parallel Programming Hard? (free) | Paul McKenney |
| 2 | Systems Performance (2nd Ed) | Brendan Gregg |
| 2 | Designing Data-Intensive Applications | Martin Kleppmann |
| 3 | Database Internals | Alex Petrov |
| 3 | Crafting Interpreters | Robert Nystrom |
| 3 | Software Architecture: The Hard Parts | Richards, Ford, et al. |
| 3 | Understanding the Linux Kernel | Bovet & Cesati |
| 3 | TCP/IP Illustrated Vol. 1 | W. Richard Stevens |
| 3 | Distributed Systems (free — Maarten van Steen) | van Steen & Tanenbaum |
| 4 | Programming Massively Parallel Processors | Kirk & Hwu |
| 4 | AI Engineering | Chip Huyen |
| 4 | Efficient Transformers Survey (Papers) | Various |

### Practice Platforms & Activities
- Build your own: Redis, Git, Docker, SQLite, Compiler, OS kernel
- Contribute to open-source systems projects (Linux kernel, Tokio, RocksDB, DuckDB)
- Benchmark and profile real-world systems (PostgreSQL, Nginx, Redis)
- Study architecture of: SQLite, Redis, Nginx, Linux kernel, Tokio, Bevy, TiKV
- Read source code of production systems
- Write technical blog posts about systems topics
- Attend systems conferences (OSDI, SOSP, VLDB, SIGMOD, Strange Loop)

---

## 🗺️ VISUAL ROADMAP SUMMARY

