# 🐍 Python Mastery Roadmap — Phase 1: Foundations
> Aligned with Phase 1 of the Software Engineering Mastery Roadmap
> **Estimated Duration: 4–6 months**

---

## 🟢 PHASE 1: Foundation & Core Basics
> **Goal:** Understand how Python works and write basic programs.

### 📦 Module 1.1: Introduction to Python
- What is Python & Why Learn It
- History & Evolution (Python 2 vs Python 3)
- Python's Philosophy (`import this` — The Zen of Python)
- How Python Code Executes (Interpreter, Bytecode, PVM)
- CPython vs PyPy vs Jython vs IronPython
- Installing Python & Setting Up IDE (VS Code / PyCharm)
- Writing Your First "Hello World" Program
- Python REPL & Interactive Mode
- Running Scripts from Terminal

### 📦 Module 1.2: Python Syntax & Basics
- Variables & Dynamic Typing
- Data Types (`int`, `float`, `complex`, `str`, `bool`, `None`)
- Type Checking (`type()`, `isinstance()`)
- Type Casting (`int()`, `float()`, `str()`, `bool()`)
- Operators (Arithmetic, Comparison, Logical, Bitwise, Assignment, Walrus `:=`)
- String Basics (Concatenation, Repetition, Indexing, Slicing)
- String Methods (`upper`, `lower`, `strip`, `split`, `join`, `replace`, `find`)
- f-Strings & String Formatting (`f""`, `.format()`, `%`)
- Taking User Input (`input()`)
- Comments (Single-line `#`, Docstrings `"""`)
- Indentation Rules (Python's Signature Feature)

### 📦 Module 1.3: Control Flow
- `if`, `elif`, `else`
- Ternary Expression (`x if condition else y`)
- `match`-`case` (Structural Pattern Matching — Python 3.10+)
- `for` Loop & `range()`
- `while` Loop
- `break`, `continue`, `pass`
- `for...else` & `while...else`
- Nested Loops
- Loop Unpacking

### 📦 Module 1.4: Data Structures — Built-in
- **Lists:** Creation, Indexing, Slicing, Methods (`append`, `extend`, `pop`, `sort`, `reverse`)
- **Tuples:** Immutability, Packing & Unpacking, Named Tuples
- **Sets:** Creation, Methods (`add`, `remove`, `union`, `intersection`, `difference`)
- **Dictionaries:** Key-Value Pairs, Methods (`get`, `keys`, `values`, `items`, `update`, `setdefault`)
- **Comprehensions:** List, Dict, Set, Nested Comprehensions
- **Frozen Sets**
- Shallow Copy vs Deep Copy (`copy`, `deepcopy`)
- Mutability vs Immutability
- `collections` Module Preview (`defaultdict`, `Counter`, `deque`, `OrderedDict`)

### 📦 Module 1.5: Functions
- Defining & Calling Functions (`def`)
- Parameters & Return Values
- Default Arguments & Keyword Arguments
- `*args` & `**kwargs`
- Return Multiple Values (Tuple Unpacking)
- First-Class Functions (Functions as Objects)
- Lambda Functions (`lambda`)
- `map()`, `filter()`, `reduce()`
- Scope & `LEGB` Rule (Local, Enclosing, Global, Built-in)
- `global` & `nonlocal` Keywords
- Recursion Basics
- Type Hints / Annotations (`def greet(name: str) -> str:`)
- Docstrings & `help()`

> ### 🛠 Phase 1 Milestone Project: **CLI-Based Expense Tracker**
> Track daily expenses via console input. Categorize spending, calculate totals by category, show daily/weekly/monthly summaries, and display insights like "most spent category."

---

## 🔵 PHASE 2: Object-Oriented Programming (OOP)
> **Goal:** Master OOP principles in Python.

### 📦 Module 2.1: Classes & Objects
- Defining Classes & Creating Objects
- Instance Attributes & Methods
- `self` Parameter
- `__init__()` Constructor
- Class Attributes vs Instance Attributes
- `__str__()` & `__repr__()`
- Object Identity (`is` vs `==`, `id()`)

### 📦 Module 2.2: Encapsulation
- Public, Protected (`_`), Private (`__`) Naming Conventions
- Name Mangling (`_ClassName__attr`)
- Properties & `@property` Decorator
- Getters, Setters, Deleters
- Read-Only Properties
- `__slots__` (Memory Optimization)

### 📦 Module 2.3: Inheritance
- Single Inheritance
- Multiple Inheritance
- Multilevel & Hierarchical Inheritance
- Method Resolution Order (MRO) & `C3 Linearization`
- `super()` Function
- Method Overriding
- `isinstance()` & `issubclass()`

### 📦 Module 2.4: Polymorphism
- Duck Typing ("If it walks like a duck...")
- Method Overriding (Runtime Polymorphism)
- Operator Overloading (Magic Methods)
- `__add__`, `__sub__`, `__mul__`, `__eq__`, `__lt__`, `__len__`, `__getitem__`
- `__call__` (Making Objects Callable)
- `__iter__` & `__next__` (Iterable Objects)
- `__enter__` & `__exit__` (Context Managers)
- No Traditional Method Overloading (Workarounds)

### 📦 Module 2.5: Abstraction
- Abstract Base Classes (`ABC`, `@abstractmethod`)
- `abc` Module
- Abstract Properties
- Interface-Like Patterns in Python
- Protocols (`typing.Protocol` — Structural Subtyping, Python 3.8+)

### 📦 Module 2.6: Other OOP Concepts
- Class Methods (`@classmethod`) & Static Methods (`@staticmethod`)
- Factory Methods Using `@classmethod`
- Composition vs Inheritance
- Mixins
- Enums (`enum.Enum`, `enum.IntEnum`, `@unique`)
- Dataclasses (`@dataclass` — Python 3.7+)
  - Fields, `__post_init__`, `field()`, Frozen Dataclasses
- `NamedTuple` (Typed & `collections`)
- Metaclasses (Introduction)
- `__new__()` vs `__init__()`
- Descriptors (`__get__`, `__set__`, `__delete__`)

> ### 🛠 Phase 2 Milestone Project: **Library Management System**
> Create `Book`, `Member`, `Librarian`, `Library` classes. Support borrowing, returning, searching, overdue tracking, and fine calculation using inheritance, polymorphism, and dataclasses.

---

## ==🟡 PHASE 3: Core Python Essentials==
> **Goal:** Master essential Python modules, patterns, and techniques.

### 📦 Module 3.1: Advanced String & Text Processing
- String Slicing Mastery
- `textwrap` Module
- `string` Module (Constants, `Template`)
- Regular Expressions (`re` module)
  - `match`, `search`, `findall`, `finditer`
  - `sub`, `split`, `compile`
  - Groups, Lookahead, Lookbehind
  - Named Groups & Backreferences
- Unicode Handling & Encoding (`encode`, `decode`, `utf-8`)

### 📦 Module 3.2: Error & Exception Handling
- Exception Hierarchy (`BaseException → Exception`)
- `try`, `except`, `else`, `finally`
- Catching Multiple Exceptions
- `raise` & Re-raising Exceptions
- Custom Exception Classes
- Exception Chaining (`raise ... from ...`)
- Exception Groups & `except*` (Python 3.11+)
- Context Managers for Resource Cleanup
- `warnings` Module
- Best Practices & Anti-Patterns

### 📦 Module 3.3: File I/O & Data Formats
- Reading & Writing Text Files (`open`, `read`, `write`, `readlines`)
- File Modes (`r`, `w`, `a`, `rb`, `wb`, `r+`)
- Context Managers for Files (`with open(...)`)
- Working with CSV (`csv.reader`, `csv.writer`, `DictReader`, `DictWriter`)
- Working with JSON (`json.load`, `json.dump`, `json.loads`, `json.dumps`)
- Working with YAML (`PyYAML`)
- Working with XML (`xml.etree.ElementTree`)
- Working with INI / TOML (`configparser`, `tomllib` Python 3.11+)
- Binary Files & `struct` Module
- `pathlib` Module (Modern Path Handling)
- `os` & `shutil` Modules (File System Operations)
- Temporary Files (`tempfile`)

### 📦 Module 3.4: Collections Deep Dive
- `collections.defaultdict`
- `collections.Counter`
- `collections.deque`
- `collections.OrderedDict`
- `collections.ChainMap`
- `collections.namedtuple`
- `heapq` Module (Heap Queue / Priority Queue)
- `bisect` Module (Binary Search on Sorted Lists)
- `array` Module (Typed Arrays)
- `queue` Module (`Queue`, `LifoQueue`, `PriorityQueue`)

### 📦 Module 3.5: Iterators, Generators & Functional Tools
- Iterator Protocol (`__iter__`, `__next__`)
- Custom Iterators
- Generators (`yield`)
- Generator Expressions (`(x for x in range(10))`)
- `yield from` (Delegating Generators)
- `itertools` Module:
  - `chain`, `cycle`, `repeat`
  - `combinations`, `permutations`, `product`
  - `groupby`, `islice`, `starmap`
  - `tee`, `zip_longest`, `accumulate`
- `functools` Module:
  - `reduce`, `partial`, `lru_cache`, `cache`
  - `wraps`, `total_ordering`, `singledispatch`
- Coroutines Introduction (Generator-Based)

### 📦 Module 3.6: Modules & Packages
- Importing Modules (`import`, `from...import`, `as`)
- Creating Your Own Modules
- Packages & `__init__.py`
- Relative vs Absolute Imports
- `__name__ == "__main__"` Guard
- `sys.path` & Module Search Order
- `pip` & Package Installation
- Virtual Environments (`venv`, `virtualenv`)
- `requirements.txt` & `pip freeze`
- Introduction to `pyproject.toml`
- Publishing to PyPI (Overview)

> ### 🛠 Phase 3 Milestone Project: **Multi-Format Data Analyzer**
> Build a CLI tool that reads data from CSV, JSON, and text files, performs statistical analysis (mean, median, mode, std dev), generates summaries using generators and itertools, and exports reports in multiple formats.

---

## ==🟠 PHASE 4: Advanced Python Features==
> **Goal:** Learn powerful and modern Python language features including concurrency, metaprogramming, and internals.

### 📦 Module 4.1: Decorators
- Functions as First-Class Objects (Recap)
- Closures
- Basic Decorators
- Decorators with Arguments
- `@functools.wraps` (Preserving Metadata)
- Stacking Multiple Decorators
- Class Decorators
- Built-in Decorators Recap (`@property`, `@classmethod`, `@staticmethod`)
- Real-World Use Cases (Logging, Timing, Auth, Caching, Retry)

### 📦 Module 4.2: Context Managers
- `with` Statement Deep Dive
- Writing Context Managers with `__enter__` & `__exit__`
- `contextlib.contextmanager` Decorator
- `contextlib.suppress`
- `contextlib.ExitStack`
- Async Context Managers (`async with`)
- Real-World Use Cases (DB Connections, File Locks, Timing)

### 📦 Module 4.3: Asynchronous Programming
- Why Async Matters
- Event Loop (`asyncio.get_event_loop()`, `asyncio.run()`)
- `async def` & `await`
- Coroutines vs Generators
- `asyncio.gather()`, `asyncio.wait()`, `asyncio.create_task()`
- `asyncio.Queue`
- `asyncio.Semaphore` (Throttling)
- `asyncio.sleep()` vs `time.sleep()`
- `asyncio.TimeoutError` & `asyncio.wait_for()`
- Async Generators (`async for`)
- Async Context Managers (`async with`)
- `aiohttp` (Async HTTP Client/Server)
- `aiofiles` (Async File I/O)
- `anyio` & `trio` (Alternative Async Frameworks — Awareness)
- Async Best Practices & Common Pitfalls
- Declarative vs Imperative Approaches in Python

### 📦 Module 4.4: Multithreading & Multiprocessing
- **Threading:**
  - `threading.Thread`
  - GIL (Global Interpreter Lock) — Why It Matters
  - Thread Synchronization (`Lock`, `RLock`, `Semaphore`, `Event`, `Condition`)
  - `concurrent.futures.ThreadPoolExecutor`
  - Thread-Safe Data Structures (`queue.Queue`)
- **Multiprocessing:**
  - `multiprocessing.Process`
  - `Pool` (Map, Apply, Starmap)
  - `concurrent.futures.ProcessPoolExecutor`
  - Shared Memory & `Manager`
  - Inter-Process Communication (`Pipe`, `Queue`)
- **Choosing:** Threading vs Multiprocessing vs Asyncio
- `subprocess` Module (Running External Commands)

### 📦 Module 4.5: Reactive Programming Concepts
- Reactive Programming Principles (Streams, Backpressure, Event-Driven Models)
- Async Generators as Reactive-Like Streams
- `asyncio.Queue` as Backpressure Mechanism
- Observer Pattern with `asyncio` Events
- RxPY (ReactiveX for Python — Conceptual Awareness)
  - Observables, Operators, Schedulers
  - `pipe()`, `map()`, `filter()`, `merge()`, `flat_map()`
- Reactive vs Imperative: When to Use What
- Event-Driven Architecture Concepts in Python

### 📦 Module 4.6: Type Hints & Static Analysis
- Basic Type Hints (`int`, `str`, `float`, `bool`, `None`)
- Complex Types (`List[int]`, `Dict[str, int]`, `Tuple[int, ...]`, `Set[str]`)
- `Optional[T]` & `Union[T1, T2]`
- `Any`, `NoReturn`, `Callable`, `Literal`
- `TypeAlias` (Python 3.10+)
- `TypeVar` & Generics
- `ParamSpec` & `Concatenate` (Python 3.10+)
- `TypeGuard` (Python 3.10+)
- `typing.Protocol` (Structural Subtyping)
- `dataclasses` + Type Hints
- `mypy` (Static Type Checker)
- `pyright` / `Pylance` (VS Code Integration)
- `pydantic` (Runtime Data Validation — Intro)

### 📦 Module 4.7: Metaprogramming
- Metaclasses Deep Dive (`type`, `__metaclass__`)
- `__new__` vs `__init__` (Object Creation)
- Descriptors (`__get__`, `__set__`, `__delete__`, `__set_name__`)
- `__init_subclass__` (Hook for Subclassing)
- `__class_getitem__` (Generic Class Syntax)
- Dynamic Attribute Access (`__getattr__`, `__setattr__`, `__delattr__`)
- `inspect` Module (Introspection)
- Code Generation & `exec()` / `eval()` (Use with Caution)
- Abstract Base Classes Registration (`register`)

### 📦 Module 4.8: Memory Management & Performance
- Python Memory Model (Everything is an Object)
- Reference Counting & Garbage Collection
- `gc` Module
- Memory Profiling (`tracemalloc`, `memory_profiler`)
- `sys.getsizeof()`
- `__slots__` for Memory Optimization
- Weak References (`weakref`)
- Object Interning (Small Integers, String Interning)
- Performance Profiling (`cProfile`, `profile`, `timeit`)
- Optimization Tips (List vs Generator, Dict Lookups, Local Variables)
- `Cython` & `ctypes` (Intro — Calling C from Python)

### 📦 Module 4.9: Modern Python Features (Python 3.10–3.13+)
- Structural Pattern Matching (`match`-`case`) — Python 3.10 (Revisited Deeply)
- `ParamSpec` & `TypeVarTuple` — Python 3.10
- Exception Groups & `except*` — Python 3.11
- `tomllib` (Built-in TOML Parser) — Python 3.11
- Performance Improvements (Faster CPython) — Python 3.11+
- `type` Statement (Type Alias) — Python 3.12
- f-String Improvements — Python 3.12
- `@override` Decorator (`typing`) — Python 3.12
- Per-Interpreter GIL — Python 3.12
- Free-Threaded Python (No GIL!) — Python 3.13+
- JIT Compiler (Experimental) — Python 3.13+

> ### 🛠 Phase 4 Milestone Project: **Async API Aggregator**
> Build an async app that concurrently fetches data from multiple public APIs (weather, news, crypto prices) using `aiohttp`, processes responses with decorators and type hints, caches results with `lru_cache`, uses reactive-style event streams, and presents a unified dashboard in the terminal.

---

## ==🔴 PHASE 5: Data Structures & Algorithms in Python==
> **Goal:** Strengthen problem-solving skills using Python.

### 📦 Module 5.1: Complexity Analysis
- Time & Space Complexity
- Big O, Big Ω, Big Θ
- Analyzing Loops, Recursion
- Amortized Analysis Basics
- Python Built-in Time Complexities (List, Dict, Set Operations)

### 📦 Module 5.2: Data Structures Implementation
- Linked Lists (Singly, Doubly, Circular)
- Stacks & Queues (List-based & `deque`-based)
- Hash Tables (Custom Dictionary Implementation)
- Trees (Binary Tree, BST, AVL)
- Heaps (Min-Heap, Max-Heap — Custom + `heapq`)
- Graphs (Adjacency List & Matrix)
- Tries (Prefix Trees)
- Disjoint Set / Union-Find
- LRU Cache (Custom Implementation)

### 📦 Module 5.3: Algorithms
- Sorting: Bubble, Selection, Insertion, Merge, Quick, Heap, Counting, Radix, Tim Sort (Python's Built-in)
- Searching: Linear, Binary, Ternary
- Recursion & Backtracking (N-Queens, Sudoku, Maze)
- Dynamic Programming (Memoization & Tabulation)
  - Fibonacci, Knapsack, LCS, LIS, Coin Change, Edit Distance
- Greedy Algorithms (Activity Selection, Huffman, Fractional Knapsack)
- Graph Algorithms (BFS, DFS, Dijkstra, Bellman-Ford, Floyd-Warshall, Kruskal, Prim, Topological Sort)
- Sliding Window, Two Pointers
- Bit Manipulation

> ### 🛠 Phase 5 Milestone Project: **LeetCode Problem Solver Framework**
> Build a testing framework that lets you write algorithm solutions, automatically tests them against multiple test cases, benchmarks execution time, compares brute force vs optimized solutions, and generates performance reports.

---

## ==🟣 PHASE 6: Design Principles, Patterns & Clean Code==
> **Goal:** Write professional, maintainable, and Pythonic code using proven principles and patterns.

### 📦 Module 6.1: Pythonic Code & Clean Code Practices
- The Zen of Python (`import this`)
- EAFP vs LBYL (Ask Forgiveness vs Look Before You Leap)
- Pythonic Idioms & Anti-Patterns
- DRY, KISS, YAGNI
- PEP 8 Style Guide
- PEP 20 (The Zen)
- Writing Readable & Self-Documenting Code
- Docstrings (Google, NumPy, Sphinx Styles)
- Code Smells & Refactoring Techniques (Martin Fowler's Catalog)
- Meaningful Naming Conventions
- Function & Class Design
- Proper Error Handling Design
- Code Reviews Best Practices

### 📦 Module 6.2: SOLID Principles in Python (Deep Understanding with Real Examples)
- Single Responsibility Principle (SRP)
- Open/Closed Principle (OCP)
- Liskov Substitution Principle (LSP)
- Interface Segregation Principle (ISP) — via ABCs & Protocols
- Dependency Inversion Principle (DIP)

### 📦 Module 6.3: Design Principles (Beyond SOLID)
- Separation of Concerns
- High Cohesion / Low Coupling
- Composition over Inheritance
- Dependency Inversion & Inversion of Control
- Law of Demeter (Principle of Least Knowledge)
- Principle of Least Astonishment
- Information Hiding (Parnas)

### 📦 Module 6.4: Creational Patterns
- Singleton Pattern (Module-Level, `__new__`, Metaclass)
- Factory Method Pattern
- Abstract Factory Pattern
- Builder Pattern
- Prototype Pattern (`copy.deepcopy`)
- Borg / Monostate Pattern (Pythonic Singleton)

### 📦 Module 6.5: Structural Patterns
- Adapter Pattern
- Bridge Pattern
- Composite Pattern
- Decorator Pattern (Already Native in Python!)
- Facade Pattern
- Flyweight Pattern
- Proxy Pattern

### 📦 Module 6.6: Behavioral Patterns
- Strategy Pattern (Functions as Strategies — Pythonic)
- Observer Pattern (& `signal` Libraries)
- Command Pattern
- State Pattern
- Template Method Pattern
- Chain of Responsibility Pattern
- Mediator Pattern
- Visitor Pattern
- Iterator Pattern (Built-in with `__iter__`)

### 📦 Module 6.7: Concurrency Patterns
- Producer-Consumer Pattern (`asyncio.Queue`, `queue.Queue`)
- Read-Write Lock Pattern (`threading.RLock`)
- Thread Pool Pattern (`concurrent.futures.ThreadPoolExecutor`)
- Future/Promise Pattern (`concurrent.futures.Future`, `asyncio.Future`)
- Actor Model Concepts (Awareness)

### 📦 Module 6.8: Anti-Patterns & When NOT to Use Patterns
- Common Anti-Patterns (God Class, Spaghetti Code, Golden Hammer, Lava Flow)
- Pythonic Anti-Patterns (Overusing Classes When Functions Suffice, Unnecessary Metaclasses)
- Over-Engineering with Patterns
- Recognizing When a Pattern Adds Unnecessary Complexity
- Pattern Selection Decision Framework
- "Simple is Better Than Complex" — When to Just Write Simple Code

> ### 🛠 Phase 6 Milestone Project: **Plugin-Based CLI Tool Framework**
> Build an extensible CLI framework where users can create plugins (commands) that auto-register. Use Factory, Strategy, Observer, Chain of Responsibility, and Template Method patterns. Apply SOLID and design principles throughout. Include comprehensive code review checklist.

---

## ==⚫ PHASE 7: Testing, Build Tools & Version Control==
> **Goal:** Master professional Python development practices — testing, tooling, and collaborating.

### 📦 Module 7.1: Unit Testing
- `unittest` Module (Built-in)
  - `TestCase`, `setUp`, `tearDown`
  - Assertions (`assertEqual`, `assertTrue`, `assertRaises`)
- `pytest` Framework (Industry Standard)
  - Test Discovery & Naming
  - Assertions (Plain `assert`)
  - Fixtures (`@pytest.fixture`, Scopes)
  - Parametrized Tests (`@pytest.mark.parametrize`)
  - Markers (`@pytest.mark.skip`, `@pytest.mark.xfail`)
  - Plugins (`pytest-cov`, `pytest-asyncio`, `pytest-mock`)
- Mocking (`unittest.mock`)
  - `Mock`, `MagicMock`, `patch`
  - `side_effect`, `return_value`
  - Mocking External APIs & Databases
  - AAA Pattern (Arrange, Act, Assert)
- Test-Driven Development (TDD) — Red/Green/Refactor
- Code Coverage (`pytest-cov`, `coverage.py`): Metrics and Their Limitations

### 📦 Module 7.2: Integration Testing & Advanced Testing
- Integration Testing Strategies
- Behavior-Driven Development (BDD):
  - `behave` (Gherkin Syntax)
  - `pytest-bdd`
- Test Pyramid (Unit → Integration → E2E)
- Testing Anti-Patterns
- Property-Based Testing (`hypothesis`)
- Testcontainers for Python (`testcontainers-python`)
  - PostgreSQL, Redis, MongoDB, Kafka Containers
- Writing Testable Code (Dependency Injection for Testability)
- Mutation Testing (`mutmut` — Awareness)

### 📦 Module 7.3: Code Quality Tools
- Linters: `flake8`, `pylint`, `ruff` (Fast!)
- Formatters: `black` (Opinionated), `autopep8`, `yapf`
- Import Sorting: `isort`
- Type Checking: `mypy`, `pyright`
- Security Scanning: `bandit`, `safety`
- Pre-commit Hooks (`pre-commit` Framework)
- `pyproject.toml` Unified Configuration

### 📦 Module 7.4: Build Tools & Dependency Management
- `pip` Deep Dive
- Virtual Environments (`venv`, `virtualenv`, `conda`)
- `requirements.txt` vs `pyproject.toml`
- `poetry` (Modern Dependency Management — Preferred)
  - `pyproject.toml`, Lock Files, Dependency Groups
  - Publishing to PyPI
- `hatch` & `flit` (Build Backends — Awareness)
- Semantic Versioning and Release Management
- `Makefile` / `taskipy` for Task Automation
- `tox` (Testing Across Python Versions)
- Dependency Vulnerability Scanning (`safety`, `pip-audit`)
- Reproducible Builds (Lock Files, Pinned Dependencies)

### 📦 Module 7.5: Version Control Mastery
- Git Internals (Objects, Refs, DAG)
- Branching Strategies (GitFlow, Trunk-Based Development, GitHub Flow)
- Monorepo vs Polyrepo Trade-offs
- Advanced Git (Rebase, Cherry-Pick, Bisect, Stash, Hooks)
- GitHub / GitLab Collaboration (PRs, Code Reviews, Protected Branches)
- `.gitignore` for Python Projects
- Conventional Commits

### 📦 Module 7.6: CI/CD Foundations
- Continuous Integration Best Practices
- Pipeline-as-Code (GitHub Actions)
- Pipeline Stages (Lint → Type Check → Test → Security Scan → Package)
- Automated Testing in CI Pipelines
- Quality Gates (Coverage Thresholds, Type Checking, Linting)
- Dependency Vulnerability Scanning in CI (`safety`, `pip-audit`, Snyk)
- Publishing to PyPI from CI

### 📦 Module 7.7: Logging & Debugging
- `print()` vs `logging` Module
- Log Levels (`DEBUG`, `INFO`, `WARNING`, `ERROR`, `CRITICAL`)
- Handlers (Console, File, Rotating, Timed)
- Formatters & Filters
- Structured Logging (`structlog`)
- `loguru` (Modern Logging Library)
- Debugging with IDE (Breakpoints, Watch, Evaluate)
- `pdb` (Python Debugger) & `breakpoint()`
- `icecream` (`ic()` for Quick Debugging)

> ### 🛠 Phase 7 Milestone Project: **URL Shortener (Fully Tested & Packaged)**
> Build a URL shortener library + CLI with comprehensive pytest tests (TDD), integration tests with testcontainers, BDD scenarios with `pytest-bdd`, >85% code coverage, structured logging with `structlog`, type hints verified by `mypy`, formatted by `black`, linted by `ruff`, pre-commit hooks, CI/CD with GitHub Actions, and published as a Python package via `poetry`.

---

## ==🔶 PHASE 8: Databases & Data Modeling==
> **Goal:** Understand data modeling, master SQL, connect Python to databases, and understand database internals.

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
- PostgreSQL / MySQL / SQLite

### 📦 Module 8.3: RDBMS Internals & Advanced Concepts
- Indexing Deep Dive (B-Tree, B+Tree, Hash Index, Composite Index)
- Query Plans & `EXPLAIN` / `EXPLAIN ANALYZE`
- ACID Properties (Atomicity, Consistency, Isolation, Durability)
- Isolation Levels (Read Uncommitted, Read Committed, Repeatable Read, Serializable)
- Transactions & MVCC (Multi-Version Concurrency Control)
- Connection Pooling Concepts
- Replication Basics (Leader-Follower)
- Sharding Basics (Concepts & Trade-offs)

### 📦 Module 8.4: Python Database Access (Raw)
- `sqlite3` Module (Built-in)
  - Connecting, Creating Tables, CRUD
  - Parameterized Queries (Preventing SQL Injection)
  - Transactions (`commit`, `rollback`)
  - Context Managers for Connections
- `psycopg` / `psycopg2` (PostgreSQL)
  - Sync and Async Access
  - Connection Pooling (`psycopg_pool`)
- `PyMySQL` / `mysql-connector-python` (MySQL — Awareness)

### 📦 Module 8.5: SQLAlchemy (ORM)
- What is SQLAlchemy & ORM Concepts
- SQLAlchemy Core vs ORM
- Engine, Session, Connection
- Declarative Base & Model Definition
- Column Types & Constraints
- Relationships (`relationship`, `ForeignKey`)
  - One-to-One, One-to-Many, Many-to-Many
- CRUD Operations with ORM
- Querying (`select`, `filter`, `filter_by`, `join`)
- SQLAlchemy 2.0 Style (Modern — `select()` API)
- Migrations with Alembic
  - `alembic init`, `revision`, `upgrade`, `downgrade`
  - Auto-Generating Migrations
- Eager vs Lazy Loading (N+1 Problem)
- Hybrid Properties
- Events & Hooks

### 📦 Module 8.6: NoSQL & Distributed Data Concepts
- NoSQL Categories (Document, Key-Value, Column-Family, Graph, Time-Series)
- When to Use SQL vs NoSQL
- CAP Theorem and PACELC
- MongoDB with `pymongo`:
  - Collections, Documents, CRUD
  - Queries, Aggregation Pipeline
  - Indexing
- `motor` (Async MongoDB — Awareness)
- Redis with `redis-py`:
  - Key-Value Operations
  - Data Structures (Lists, Sets, Hashes, Sorted Sets)
  - Pub/Sub
  - Caching Patterns (Cache-Aside)
  - TTL & Expiration
- Polyglot Persistence Concepts

> ### 🛠 Phase 8 Milestone Project: **Blog Engine Database Layer**
> Build a complete database layer for a blog with Users, Posts, Comments, Tags, and Categories using SQLAlchemy ORM (2.0 style), Alembic migrations, proper schema design with normalization, indexing strategies, complex queries with `EXPLAIN ANALYZE`, Redis caching for hot posts, and query performance benchmarks.

---

## ==🔷 PHASE 9: Networking, Infrastructure & Operations==
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

### 📦 Module 9.2: Python Networking & HTTP
- `socket` Module:
  - Building a Simple TCP Client/Server
  - UDP Client/Server
- `http.server` Module (Built-in HTTP Server)
- `requests` Library (Sync HTTP Client)
- `httpx` (Modern Async/Sync HTTP Client)
- Making HTTP Requests from Python (GET, POST, Headers, Auth)
- REST Principles & HTTP Semantics

### 📦 Module 9.3: Operating Systems & Linux Fundamentals
- Linux Basics (File System, Permissions, Users)
- Essential Commands (Navigation, File Manipulation, Process Management)
- Package Management (apt, yum)
- Shell Scripting Basics
- Processes, Signals, and Systemd
- Environment Variables and Configuration
- SSH and Remote Access
- Python's `os`, `subprocess`, `shutil` for System Interaction

### 📦 Module 9.4: Containers & Docker
- Virtual Machines vs Containers
- Docker Fundamentals (Images, Containers, Layers)
- Writing Dockerfiles (for Python Applications)
  - Choosing Base Images (`python:3.12-slim`, `python:3.12-alpine`)
  - Multi-Stage Builds for Python
  - `.dockerignore` for Python
  - Installing Dependencies (`requirements.txt` / `poetry`)
  - Non-Root User, Security Best Practices
- Docker Networking (Bridge, Host, Custom Networks)
- Docker Volumes (Persistent Data)
- Docker Compose (Multi-Container Applications)
- Dockerizing a Python Application
  - WSGI Server (Gunicorn) / ASGI Server (Uvicorn) in Docker
  - Health Checks in Docker
- Docker Best Practices (Layer Caching, Image Size Optimization)

### 📦 Module 9.5: Container Orchestration Basics
- Why Orchestration? (Problems Docker Alone Doesn't Solve)
- Kubernetes Core Concepts (Pods, Services, Deployments, Namespaces)
- `kubectl` Basics
- YAML Manifests (Awareness)
- ConfigMaps and Secrets (Awareness)
- Kubernetes vs Docker Compose — When to Use What

> ### 🛠 Phase 9 Milestone Project: **Containerized Python TCP Chat Server**
> Build a multi-client chat server using Python `socket` and `asyncio`. Dockerize it with a multi-stage Dockerfile. Create a docker-compose setup with the chat server + Redis (for message persistence/pub-sub) + PostgreSQL (for user accounts). Deploy locally using Docker Compose. Include structured logging and health check endpoints.

---

## 🏗️ CAPSTONE PROJECT: Production-Grade URL Shortener
> **This is the Phase 1 capstone that ties everything together.**
>
> Build a URL shortener service (like bit.ly) with:
> - **Clean Python code** applying SOLID principles and design patterns
> - **RESTful API** with proper HTTP semantics and error handling (using lightweight framework — `http.server` or minimal `aiohttp`)
> - **PostgreSQL** with proper schema design, normalization, and indexing (SQLAlchemy + Alembic)
> - **Redis** caching layer for hot URLs
> - **Docker** containerization with docker-compose (app + PostgreSQL + Redis)
> - **Comprehensive test suite** (unit + integration tests with testcontainers, TDD approach, >85% coverage)
> - **CI/CD pipeline** (GitHub Actions: lint → type-check → test → security-scan → docker build)
> - **Structured logging** with `structlog` and health check endpoints
> - **Type hints** verified by `mypy`, formatted by `black`, linted by `ruff`
> - **Git** with proper branching strategy and semantic versioning
> - Architecture documented with decision rationale
>
> **Why:** Small enough to finish, complex enough to demonstrate all Phase 1 skills — clean code, design patterns, testing, databases, Docker, CI/CD, networking, and infrastructure.

---

## ✅ After Completing This Roadmap — You Can:
- [ ] Write clean, testable, maintainable, Pythonic code
- [ ] Apply appropriate design patterns with justification
- [ ] Understand Python internals, concurrency (async, threading, multiprocessing), and memory management
- [ ] Solve DSA problems confidently in Python
- [ ] Design normalized/denormalized data models
- [ ] Work fluently with SQL, raw DB access, and SQLAlchemy ORM
- [ ] Understand NoSQL concepts and CAP theorem
- [ ] Explain networking and infrastructure fundamentals
- [ ] Containerize applications with Docker and Docker Compose
- [ ] Set up CI/CD pipelines with GitHub Actions
- [ ] Use Git professionally with proper branching strategies
- [ ] Write comprehensive tests (unit, integration, BDD, TDD)
- [ ] Use type hints, linters, and static analysis professionally
- [ ] **You are fully ready for Phase 2: FastAPI & Architectural Thinking**

---

## 📋 Quick Reference Summary

