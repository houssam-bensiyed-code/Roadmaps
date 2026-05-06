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

> ### 🛠 Phase 1 Project: **CLI-Based Expense Tracker**
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

> ### 🛠 Phase 2 Project: **Library Management System**
> Create `Book`, `Member`, `Librarian`, `Library` classes. Support borrowing, returning, searching, overdue tracking, and fine calculation using inheritance, polymorphism, and dataclasses.

---

## 🟡 PHASE 3: Core Python Essentials
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

> ### 🛠 Phase 3 Project: **Multi-Format Data Analyzer**
> Build a CLI tool that reads data from CSV, JSON, and text files, performs statistical analysis (mean, median, mode, std dev), generates summaries using generators and itertools, and exports reports in multiple formats.

---

## 🟠 PHASE 4: Advanced Python Features
> **Goal:** Learn powerful and modern Python language features.

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
- `anyio` & `trio` (Alternative Async Frameworks)
- Async Best Practices & Common Pitfalls

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

### 📦 Module 4.5: Type Hints & Static Analysis
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

### 📦 Module 4.6: Metaprogramming
- Metaclasses Deep Dive (`type`, `__metaclass__`)
- `__new__` vs `__init__` (Object Creation)
- Descriptors (`__get__`, `__set__`, `__delete__`, `__set_name__`)
- `__init_subclass__` (Hook for Subclassing)
- `__class_getitem__` (Generic Class Syntax)
- Dynamic Attribute Access (`__getattr__`, `__setattr__`, `__delattr__`)
- `inspect` Module (Introspection)
- Code Generation & `exec()` / `eval()` (Use with Caution)
- Abstract Base Classes Registration (`register`)

### 📦 Module 4.7: Memory Management & Performance
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

> ### 🛠 Phase 4 Project: **Async API Aggregator**
> Build an async app that concurrently fetches data from multiple public APIs (weather, news, crypto prices) using `aiohttp`, processes responses with decorators and type hints, caches results, and presents a unified dashboard in the terminal.

---

## 🔴 PHASE 5: Data Structures & Algorithms in Python
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

> ### 🛠 Phase 5 Project: **LeetCode Problem Solver Framework**
> Build a testing framework that lets you write algorithm solutions, automatically tests them against multiple test cases, benchmarks execution time, compares brute force vs optimized solutions, and generates performance reports.

---

## 🟣 PHASE 6: Design Patterns & Clean Code
> **Goal:** Write professional, maintainable, and Pythonic code.

### 📦 Module 6.1: Pythonic Code & Principles
- The Zen of Python (`import this`)
- EAFP vs LBYL (Ask Forgiveness vs Look Before You Leap)
- Pythonic Idioms & Anti-Patterns
- DRY, KISS, YAGNI
- PEP 8 Style Guide
- PEP 20 (The Zen)
- Writing Readable Code
- Docstrings (Google, NumPy, Sphinx Styles)

### 📦 Module 6.2: SOLID Principles in Python
- Single Responsibility Principle (SRP)
- Open/Closed Principle (OCP)
- Liskov Substitution Principle (LSP)
- Interface Segregation Principle (ISP) — via ABCs & Protocols
- Dependency Inversion Principle (DIP)

### 📦 Module 6.3: Creational Patterns
- Singleton Pattern (Module-Level, `__new__`, Metaclass)
- Factory Method Pattern
- Abstract Factory Pattern
- Builder Pattern
- Prototype Pattern (`copy.deepcopy`)
- Borg / Monostate Pattern (Pythonic Singleton)

### 📦 Module 6.4: Structural Patterns
- Adapter Pattern
- Decorator Pattern (Already Native in Python!)
- Facade Pattern
- Proxy Pattern
- Composite Pattern
- Flyweight Pattern

### 📦 Module 6.5: Behavioral Patterns
- Observer Pattern (& `signal` Libraries)
- Strategy Pattern (Functions as Strategies — Pythonic)
- Command Pattern
- Template Method Pattern
- Iterator Pattern (Built-in with `__iter__`)
- State Pattern
- Chain of Responsibility
- Mediator Pattern

### 📦 Module 6.6: Architectural Patterns
- Repository Pattern
- Service Layer Pattern
- Dependency Injection (Manual & `dependency-injector` Library)
- Clean Architecture Overview
- Hexagonal Architecture (Ports & Adapters)
- CQRS (Command Query Responsibility Segregation)

> ### 🛠 Phase 6 Project: **Plugin-Based CLI Tool Framework**
> Build an extensible CLI framework where users can create plugins (commands) that auto-register. Use Factory, Strategy, Observer, and Template Method patterns. Follow SOLID and Pythonic principles.

---

## ⚫ PHASE 7: Testing, Tooling & DevOps Basics
> **Goal:** Learn the professional Python development ecosystem.

### 📦 Module 7.1: Code Quality Tools
- Linters: `flake8`, `pylint`, `ruff` (Fast!)
- Formatters: `black` (Opinionated), `autopep8`, `yapf`
- Import Sorting: `isort`
- Type Checking: `mypy`, `pyright`
- Security: `bandit`, `safety`
- Pre-commit Hooks (`pre-commit` Framework)
- `pyproject.toml` Configuration

### 📦 Module 7.2: Unit Testing
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
- Test-Driven Development (TDD) Workflow
- Code Coverage (`pytest-cov`, `coverage.py`)
- Integration Testing Basics
- Property-Based Testing (`hypothesis`)

### 📦 Module 7.3: Logging & Debugging
- `print()` vs `logging` Module
- Log Levels (`DEBUG`, `INFO`, `WARNING`, `ERROR`, `CRITICAL`)
- Handlers (Console, File, Rotating, Timed)
- Formatters & Filters
- `structlog` (Structured Logging)
- `loguru` (Modern Logging Library)
- Debugging with IDE (Breakpoints, Watch, Evaluate)
- `pdb` (Python Debugger) & `breakpoint()`
- `icecream` (`ic()` for Quick Debugging)

### 📦 Module 7.4: Package Management & Build Tools
- `pip` Deep Dive
- Virtual Environments (`venv`, `virtualenv`, `conda`)
- `requirements.txt` vs `pyproject.toml`
- `poetry` (Modern Dependency Management)
- `pipenv` (Alternative)
- `hatch` & `flit` (Build Backends)
- Building & Publishing Packages to PyPI
- Semantic Versioning
- `Makefile` for Task Automation
- `tox` (Testing Across Python Versions)

### 📦 Module 7.5: Version Control
- Git Fundamentals (init, add, commit, branch, merge, rebase)
- Branching Strategies (Git Flow, Trunk-Based)
- GitHub / GitLab Collaboration
- `.gitignore` for Python Projects
- Pull Requests & Code Reviews
- Conventional Commits

> ### 🛠 Phase 7 Project: **URL Shortener (Fully Tested & Packaged)**
> Build a URL shortener library + CLI with comprehensive pytest tests, mocking, 90%+ code coverage, structured logging, type hints verified by mypy, formatted by black, linted by ruff, and published as a Python package.

---

## 🔶 PHASE 8: Databases & Data Access
> **Goal:** Connect Python applications to databases.

### 📦 Module 8.1: SQL Fundamentals
- DDL, DML, DCL, TCL
- CRUD Operations
- Joins, Subqueries, Aggregations
- Indexing & Normalization Basics
- PostgreSQL / MySQL / SQLite

### 📦 Module 8.2: SQLite & Raw Database Access
- `sqlite3` Module (Built-in)
- Connecting, Creating Tables, CRUD
- Parameterized Queries (Preventing SQL Injection)
- Transactions (`commit`, `rollback`)
- Context Managers for Connections
- `psycopg2` / `psycopg3` (PostgreSQL)
- `mysql-connector-python` / `PyMySQL` (MySQL)

### 📦 Module 8.3: SQLAlchemy (ORM)
- What is SQLAlchemy & ORM Concepts
- SQLAlchemy Core vs ORM
- Engine, Session, Connection
- Declarative Base & Model Definition
- Column Types & Constraints
- Relationships (`relationship`, `ForeignKey`)
  - One-to-One, One-to-Many, Many-to-Many
- CRUD Operations with ORM
- Querying (`query`, `filter`, `filter_by`, `join`)
- SQLAlchemy 2.0 Style (Modern)
- Migrations with Alembic
  - `alembic init`, `revision`, `upgrade`, `downgrade`
  - Auto-Generating Migrations
- Eager vs Lazy Loading
- Hybrid Properties
- Events & Hooks

### 📦 Module 8.4: NoSQL Databases
- MongoDB with `pymongo`
  - Collections, Documents, CRUD
  - Queries, Aggregation Pipeline
  - Indexing
- `motor` (Async MongoDB)
- Redis with `redis-py`
  - Key-Value Operations
  - Data Structures (Lists, Sets, Hashes, Sorted Sets)
  - Pub/Sub
  - Caching Patterns
- ODM: `mongoengine` / `beanie` (Async)

> ### 🛠 Phase 8 Project: **Blog Engine Database Layer**
> Build a complete database layer for a blog with Users, Posts, Comments, Tags, and Categories using SQLAlchemy ORM, Alembic migrations, complex queries, and Redis caching for hot posts.

---

## 🔷 PHASE 9: Web Development with Python
> **Goal:** Build modern web applications and REST APIs.

### 📦 Module 9.1: Web Fundamentals
- HTTP Protocol (Methods, Status Codes, Headers)
- REST Principles & API Design
- `requests` Library (Making HTTP Calls)
- `httpx` (Modern Async HTTP Client)
- JSON & API Communication
- Authentication (API Keys, OAuth, JWT)

### 📦 Module 9.2: Flask (Lightweight Framework)
- Flask Setup & Project Structure
- Routes & Views
- Request & Response Objects
- Templates (Jinja2)
- Static Files
- Blueprints (Modular Applications)
- Flask-RESTful / Flask-Smorest (REST APIs)
- Flask-SQLAlchemy (Database Integration)
- Flask-Migrate (Alembic Integration)
- Flask-JWT-Extended (Authentication)
- Flask-Marshmallow (Serialization)
- Error Handling
- Testing Flask Apps

### 📦 Module 9.3: FastAPI (Modern Async Framework) ⭐
- Why FastAPI & Its Advantages
- Installation & Project Structure
- Path Operations (`@app.get`, `@app.post`, `@app.put`, `@app.delete`)
- Path Parameters & Query Parameters
- Request Body with Pydantic Models
- Response Models & Status Codes
- Data Validation (Pydantic V2)
  - Validators (`@field_validator`, `@model_validator`)
  - Nested Models, `Optional`, `Field()`
- Dependency Injection System
- Middleware
- Background Tasks
- File Upload & Download
- Authentication & Authorization (JWT, OAuth2)
  - OAuth2 Password Flow
  - JWT Token Creation & Verification
  - Protected Routes
- Database Integration (SQLAlchemy + Async)
- Async Endpoints
- WebSockets
- Error Handling (`HTTPException`, Custom Handlers)
- CORS Configuration
- API Versioning
- Testing FastAPI (`TestClient`, `httpx`)
- OpenAPI / Swagger Docs (Auto-Generated!)

### 📦 Module 9.4: Django (Full-Stack Framework)
- Django Philosophy ("Batteries Included")
- Project Structure (`startproject`, `startapp`)
- Models & Django ORM
  - Fields, Relationships, Migrations
  - QuerySet API (`filter`, `exclude`, `annotate`, `aggregate`)
  - Managers & Custom QuerySets
- Views (Function-Based & Class-Based)
- URL Routing
- Templates & Template Tags
- Forms & ModelForms
- Django Admin (Auto-Generated Admin Panel)
- Authentication System (Built-in)
- Django REST Framework (DRF) ⭐
  - Serializers (ModelSerializer, Custom)
  - ViewSets & Routers
  - Authentication (Token, JWT, Session)
  - Permissions & Throttling
  - Pagination, Filtering (`django-filter`), Searching, Ordering
  - Nested Serializers
  - File Upload
- Django Signals
- Celery Integration (Async Tasks)
- Django Channels (WebSockets)
- Testing Django Apps

### 📦 Module 9.5: API Advanced Concepts
- Pagination Strategies (Offset, Cursor, Keyset)
- Rate Limiting
- Caching Strategies (Redis, In-Memory)
- API Documentation Best Practices
- GraphQL with Python (`strawberry`, `graphene`) — Overview
- gRPC with Python (`grpcio`) — Overview

> ### 🛠 Phase 9 Project: **Full-Stack Task Management API**
> Build with **FastAPI**:
> - User registration/login (JWT + Refresh Tokens)
> - CRUD for projects, tasks, subtasks
> - Role-based access (Admin, Manager, Member)
> - Task assignment, status tracking, due dates
> - File attachments
> - Real-time notifications (WebSockets)
> - Pagination, filtering, sorting
> - Background email notifications
> - SQLAlchemy + PostgreSQL + Alembic migrations
> - Redis caching
> - Comprehensive test suite
> - Auto-generated Swagger docs

---

## 💎 PHASE 10: Specialization Tracks
> **Goal:** Choose your path and go deep.

### 📦 Module 10.1: DevOps & Deployment
- Docker (Dockerfile for Python Apps, Multi-Stage Builds)
- Docker Compose
- CI/CD (GitHub Actions, GitLab CI)
- Gunicorn / Uvicorn (Production ASGI/WSGI Servers)
- Nginx as Reverse Proxy
- Deploying to AWS (EC2, Lambda, ECS) / GCP / Azure
- Deploying to Heroku / Railway / Render / Fly.io
- Environment Variables & Secrets Management
- Monitoring (Prometheus + Grafana)
- Logging Aggregation (ELK Stack, Loki)

### 📦 Module 10.2: Microservices with Python
- Monolith vs Microservices
- Service Decomposition
- Inter-Service Communication (REST, gRPC, Message Queues)
- API Gateway (Kong, Traefik)
- Message Brokers:
  - RabbitMQ (`pika`, `aio-pika`)
  - Apache Kafka (`confluent-kafka`, `aiokafka`)
  - Celery (Distributed Task Queue)
- Event-Driven Architecture
- Saga Pattern
- Circuit Breaker (`pybreaker`, `tenacity` for retries)
- Distributed Tracing (OpenTelemetry, Jaeger)
- Service Mesh (Istio — Conceptual)

### 📦 Module 10.3: Data Science & Analytics Track 📊
- NumPy (Arrays, Broadcasting, Vectorization)
- Pandas (DataFrames, Series, Data Manipulation)
  - Reading/Writing (CSV, Excel, SQL, JSON)
  - Filtering, Grouping, Merging, Pivoting
  - Handling Missing Data
  - Time Series
- Data Visualization:
  - Matplotlib (Basic Plots)
  - Seaborn (Statistical Plots)
  - Plotly (Interactive Plots)
- Jupyter Notebooks
- Statistical Analysis (`scipy.stats`)
- Web Scraping:
  - `BeautifulSoup` + `requests`
  - `Scrapy` (Framework)
  - `Selenium` / `Playwright` (Browser Automation)

### 📦 Module 10.4: Machine Learning Track 🤖
- Scikit-Learn
  - Supervised Learning (Regression, Classification)
  - Unsupervised Learning (Clustering, Dimensionality Reduction)
  - Model Evaluation & Cross-Validation
  - Feature Engineering & Pipelines
- Deep Learning:
  - TensorFlow / Keras
  - PyTorch
  - Neural Networks, CNNs, RNNs, Transformers
- NLP:
  - NLTK, SpaCy
  - Hugging Face Transformers
  - LLM Integration (OpenAI API, LangChain)
- MLOps:
  - MLflow (Experiment Tracking)
  - Model Serving (FastAPI + ML Model)
  - Docker for ML

### 📦 Module 10.5: Automation & Scripting Track 🤖
- System Automation (`os`, `shutil`, `subprocess`, `pathlib`)
- Web Scraping (`BeautifulSoup`, `Scrapy`, `Selenium`)
- Excel Automation (`openpyxl`, `xlsxwriter`)
- PDF Manipulation (`PyPDF2`, `reportlab`)
- Email Automation (`smtplib`, `email`)
- Task Scheduling (`schedule`, `APScheduler`, `cron`)
- GUI Automation (`pyautogui`)
- Network Automation (`paramiko`, `netmiko`)
- CLI Tools (`click`, `typer`, `argparse`)

### 📦 Module 10.6: Modern Python Features (Python 3.10–3.13+)
- Structural Pattern Matching (`match`-`case`) — Python 3.10
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

> ### 🛠 Phase 10 Project: Choose Based on Your Track
>
> **🌐 Web/Backend Track:** **Microservices E-Commerce Platform**
> - User Service (FastAPI + JWT)
> - Product Service (FastAPI + PostgreSQL)
> - Order Service (Saga Pattern + Celery)
> - Notification Service (RabbitMQ + Email)
> - API Gateway (Traefik)
> - Redis Caching, Docker Compose, CI/CD, OpenTelemetry
>
> **📊 Data Science Track:** **End-to-End Data Pipeline**
> - Scrape data from multiple sources
> - Clean & transform with Pandas
> - Analyze & visualize insights
> - Build predictive model with Scikit-Learn
> - Serve predictions via FastAPI
> - Dashboard with Plotly Dash
>
> **🤖 ML/AI Track:** **AI-Powered Content Platform**
> - Build a content generation/summarization tool
> - Integrate OpenAI API / Hugging Face models
> - FastAPI backend for model serving
> - Fine-tune a model on custom data
> - Deploy with Docker + monitoring
>
> **⚙️ Automation Track:** **Smart Office Automation Suite**
> - Auto-generate reports (Excel + PDF)
> - Email digest automation
> - File organizer & backup system
> - Web scraping for market data
> - CLI dashboard with `rich`
> - Scheduled via APScheduler

---

## 📋 Quick Reference Summary

```
Phase  1  ➜  Foundation & Basics              🟢
Phase  2  ➜  OOP Mastery                       🔵
Phase  3  ➜  Core Python Essentials            🟡
Phase  4  ➜  Advanced Python Features          🟠
Phase  5  ➜  DSA in Python                     🔴
Phase  6  ➜  Design Patterns & Clean Code      🟣
Phase  7  ➜  Testing, Tooling & DevOps         ⚫
Phase  8  ➜  Databases & Data Access           🔶
Phase  9  ➜  Web Dev (FastAPI/Django/Flask)     🔷
Phase 10  ➜  Specialization & Production       💎
```

---

## 🗺️ Python Career Paths After Completion

```
┌────────────────────────────────────────────────────────────┐
│                     Python Developer                       │
├───────────────┬───────────────┬────────────────────────────┤
│  Backend API  │  Full Stack   │    Data Scientist          │
│  (FastAPI /   │  (Django +    │    (Pandas, NumPy,         │
│   Django)     │   React/Vue)  │     Matplotlib)            │
├───────────────┼───────────────┼────────────────────────────┤
│  ML / AI      │  Data         │    DevOps /                │
│  Engineer     │  Engineer     │    Platform Engineer       │
│  (PyTorch,    │  (Airflow,    │    (Docker, CI/CD,         │
│   TensorFlow) │   Spark, ETL) │     Kubernetes)            │
├───────────────┼───────────────┼────────────────────────────┤
│  Automation   │  Cyber        │    Quantitative            │
│  Engineer     │  Security     │    Finance                 │
│  (Scripting,  │  (Pen Testing,│    (Algo Trading,          │
│   Web Scrape) │   Forensics)  │     Risk Analysis)         │
├───────────────┼───────────────┼────────────────────────────┤
│  Cloud        │  NLP / LLM    │    Game Dev /              │
│  Engineer     │  Engineer     │    Computer Vision         │
│  (AWS Lambda, │  (LangChain,  │    (Pygame, OpenCV,        │
│   Serverless) │   HuggingFace)│     MediaPipe)             │
└───────────────┴───────────────┴────────────────────────────┘
```

---

## 📚 Recommended Resources

```
┌─────────────────────────────────────────────────────────┐
│                    📖 BOOKS                             │
├─────────────────────────────────────────────────────────┤
│  Beginner    → "Automate the Boring Stuff" (Al Sweigart)│
│  Core        → "Python Crash Course" (Eric Matthes)     │
│  Advanced    → "Fluent Python" (Luciano Ramalho)        │
│  Expert      → "Python Cookbook" (David Beazley)         │
│  Patterns    → "Architecture Patterns w/ Python"        │
│  DSA         → "Grokking Algorithms" (Bhargava)         │
├─────────────────────────────────────────────────────────┤
│                    🌐 PLATFORMS                         │
├─────────────────────────────────────────────────────────┤
│  Practice    → LeetCode, HackerRank, Codewars           │
│  Projects    → Real Python, freeCodeCamp                 │
│  Docs        → docs.python.org (Official)                │
│  Videos      → Corey Schafer, ArjanCodes, mCoding        │
└─────────────────────────────────────────────────────────┘
```

---

> **⏱ Estimated Timeline:** 6–12 months (varies by specialization track)
> **💡 Pro Tip:** Python rewards those who build. Every concept you learn — immediately apply it in a mini-project. The Pythonic way is to *learn by doing.*

---

*Want me to deep dive into any specific phase, module, specialization track, or create a week-by-week study plan?* 🚀