## 🟢 PHASE 1: Foundation & Core Basics
> **Goal:** Understand how JavaScript works and write basic programs.

### 📦 Module 1.1: Introduction to JavaScript
- What is JavaScript & Why Learn It
- History & Evolution (ES1 → ES2024+)
- JavaScript vs ECMAScript
- How JS Executes (JS Engine, V8, SpiderMonkey)
- Compilation vs Interpretation (JIT Compilation)
- JavaScript Runtime Environment (Browser vs Node.js)
- Setting Up (VS Code, Browser DevTools, Node.js)
- Writing Your First "Hello World" (Console & Browser)
- `<script>` Tag Placement (`defer`, `async`)
- `"use strict"` Mode
- REPL (Browser Console, Node REPL)

### 📦 Module 1.2: Variables & Data Types
- `var` vs `let` vs `const`
- Hoisting (Variable & Function Hoisting)
- Temporal Dead Zone (TDZ)
- Primitive Types (`string`, `number`, `bigint`, `boolean`, `undefined`, `null`, `symbol`)
- Reference Types (`object`, `array`, `function`)
- `typeof` Operator & Its Quirks (`typeof null === "object"`)
- Type Coercion (Implicit vs Explicit)
- Truthy & Falsy Values
- `==` vs `===` (Loose vs Strict Equality)
- `NaN`, `Infinity`, `-0`
- Template Literals (`` ` ` ``, `${}`)
- Tagged Template Literals

### 📦 Module 1.3: Operators & Expressions
- Arithmetic, Assignment, Comparison Operators
- Logical Operators (`&&`, `||`, `!`)
- Short-Circuit Evaluation
- Nullish Coalescing (`??`)
- Optional Chaining (`?.`)
- Ternary Operator (`? :`)
- Bitwise Operators
- Comma Operator
- Operator Precedence
- `in` Operator & `delete` Operator

### 📦 Module 1.4: Control Flow
- `if`, `else if`, `else`
- `switch` Statement
- `for` Loop, `while` Loop, `do-while` Loop
- `for...in` (Objects) vs `for...of` (Iterables)
- `break`, `continue`, `return`
- Labelled Statements
- Nested Loops
- Error-Free Looping Patterns

### 📦 Module 1.5: Functions — The Heart of JavaScript
- Function Declarations vs Expressions
- Arrow Functions (`=>`) & When NOT to Use Them
- Parameters: Default, Rest (`...args`)
- Return Values
- First-Class Functions (Functions as Values)
- Higher-Order Functions
- Callback Functions
- IIFE (Immediately Invoked Function Expression)
- Function Scope vs Block Scope
- Closures (Introduction)
- `arguments` Object (vs Rest Parameters)
- Pure Functions

### 📦 Module 1.6: Strings & Numbers In-Depth
- String Methods (`slice`, `substring`, `indexOf`, `includes`, `startsWith`, `replace`, `replaceAll`, `split`, `trim`, `padStart`, `padEnd`, `repeat`, `at`)
- String Immutability
- Number Methods (`parseInt`, `parseFloat`, `toFixed`, `toPrecision`, `isNaN`, `isFinite`, `Number.isInteger`)
- `Math` Object (`random`, `floor`, `ceil`, `round`, `max`, `min`, `abs`, `pow`, `sqrt`)
- `BigInt`
- Template Literals Deep Dive

### 📦 Module 1.7: Arrays
- Creating Arrays (Literal, `Array()`, `Array.of()`, `Array.from()`)
- Accessing & Modifying Elements
- **Mutating Methods:** `push`, `pop`, `shift`, `unshift`, `splice`, `sort`, `reverse`, `fill`, `copyWithin`
- **Non-Mutating Methods:** `slice`, `concat`, `flat`, `flatMap`
- **Iteration Methods:** `forEach`, `map`, `filter`, `reduce`, `reduceRight`, `find`, `findIndex`, `findLast`, `findLastIndex`, `some`, `every`
- **Search Methods:** `indexOf`, `lastIndexOf`, `includes`
- **Static Methods:** `Array.isArray()`, `Array.from()`, `Array.of()`
- Destructuring Arrays
- Spread Operator (`...`)
- Array-Like Objects & Converting to Arrays
- Multidimensional Arrays
- `at()` Method (Negative Indexing)

### 📦 Module 1.8: Objects
- Object Literals & Properties
- Accessing Properties (Dot vs Bracket Notation)
- Shorthand Properties & Methods
- Computed Property Names
- Destructuring Objects (Nested, Aliases, Defaults)
- Spread & Rest with Objects
- `Object.keys()`, `Object.values()`, `Object.entries()`
- `Object.assign()` & `Object.freeze()` & `Object.seal()`
- Property Descriptors (`Object.defineProperty`)
- `hasOwnProperty()` & `in` Operator
- Iterating Over Objects
- Shallow vs Deep Copy (`structuredClone()`)
- Optional Chaining with Objects

> ### 🛠 Phase 1 Project: **CLI-Based Budget Tracker (Node.js)**
> Build a terminal-based budget app using Node.js that tracks income/expenses, categorizes transactions, calculates totals, and saves data to a JSON file. Uses arrays, objects, functions, and control flow.

---

## 🔵 PHASE 2: Deep Dive — How JavaScript Really Works
> **Goal:** Understand the engine under the hood.

### 📦 Module 2.1: Execution Context & Call Stack
- Global Execution Context
- Function Execution Context
- Creation Phase vs Execution Phase
- Call Stack (LIFO)
- Stack Overflow (Infinite Recursion)
- Visualizing the Call Stack (DevTools)

### 📦 Module 2.2: Scope & Closures
- Global Scope, Function Scope, Block Scope
- Lexical Scope (Static Scoping)
- Scope Chain
- Closures Deep Dive
  - What Closures Actually Are
  - Closures in Loops (Classic `var` Problem)
  - Practical Use Cases (Data Privacy, Factories, Memoization)
  - Memory Implications
- Module Pattern (Using Closures)

### 📦 Module 2.3: Hoisting In-Depth
- Variable Hoisting (`var` vs `let`/`const`)
- Function Declaration Hoisting
- Function Expression — NOT Hoisted
- Class Hoisting (TDZ)
- Priority Order of Hoisting

### 📦 Module 2.4: `this` Keyword Mastery
- `this` in Global Context
- `this` in Regular Functions
- `this` in Object Methods
- `this` in Arrow Functions (Lexical `this`)
- `this` in Event Handlers
- `this` in Classes
- Explicit Binding: `call()`, `apply()`, `bind()`
- `this` Gotchas & Common Mistakes
- `globalThis` (ES2020)

### 📦 Module 2.5: Prototypes & Prototypal Inheritance
- Prototype Chain (`__proto__` vs `prototype`)
- `Object.getPrototypeOf()` & `Object.setPrototypeOf()`
- `Object.create()`
- Constructor Functions & `new` Keyword
- How `new` Works Internally
- Property Lookup in Prototype Chain
- `hasOwnProperty()` vs `in`
- Prototypal vs Classical Inheritance
- Performance Considerations

### 📦 Module 2.6: Event Loop & Asynchronous Model
- Single-Threaded Nature of JavaScript
- Event Loop Architecture
- Call Stack → Web APIs → Callback Queue → Microtask Queue
- Macrotasks vs Microtasks
- `setTimeout`, `setInterval`, `setImmediate` (Node)
- `requestAnimationFrame` (Browser)
- `queueMicrotask()`
- Starvation & Priority
- Visualizing with Loupe / JS Visualizer

> ### 🛠 Phase 2 Project: **Custom `this` & Closure Playground**
> Build an interactive Node.js app that demonstrates scope, closures, `this` binding, and the event loop with visual step-by-step explanations. Include a custom `bind()`, `call()`, `apply()` implementation.

---

## 🟡 PHASE 3: Object-Oriented & Functional Programming
> **Goal:** Master both paradigms that JavaScript supports.

### 📦 Module 3.1: OOP with Classes (ES6+)
- `class` Declaration
- `constructor()` Method
- Instance Methods & Properties
- `static` Methods & Properties
- Getters & Setters (`get`, `set`)
- Private Fields & Methods (`#privateField`)
- Public Class Fields
- `extends` & `super` (Inheritance)
- Method Overriding
- `instanceof` Operator
- Class Expressions
- Abstract-Like Classes (Throwing in Constructor)
- Mixins Pattern
- Static Initialization Blocks (ES2022)

### 📦 Module 3.2: OOP Principles Applied
- Encapsulation (Private Fields, Closures, WeakMaps)
- Inheritance (Prototypal + Class-Based)
- Polymorphism (Duck Typing, Method Overriding)
- Abstraction Patterns
- Composition Over Inheritance
- SOLID Principles in JavaScript
- Factory Functions vs Classes

### 📦 Module 3.3: Functional Programming
- Pure Functions & Side Effects
- Immutability (Object.freeze, Spread, `structuredClone`)
- First-Class & Higher-Order Functions
- Function Composition (`compose`, `pipe`)
- Currying & Partial Application
- Memoization
- Recursion & Tail Call Optimization
- `map`, `filter`, `reduce` Mastery
- Avoiding Mutation (Functional Array/Object Patterns)
- Monads & Functors (Conceptual)
- Point-Free Style
- Libraries: `Ramda`, `Lodash/fp` (Overview)

### 📦 Module 3.4: Iterators & Generators
- Iterator Protocol (`Symbol.iterator`, `next()`)
- Custom Iterables
- `for...of` with Custom Objects
- Generator Functions (`function*`, `yield`)
- `yield*` (Delegating Generators)
- Infinite Generators
- Generator-Based Async (Historical Context)
- Lazy Evaluation with Generators
- Practical Use Cases (Pagination, Streaming Data)

### 📦 Module 3.5: Symbols & Well-Known Symbols
- `Symbol()` & `Symbol.for()`
- `Symbol.iterator`, `Symbol.toPrimitive`
- `Symbol.hasInstance`, `Symbol.toStringTag`
- `Symbol.species`
- Using Symbols as Private-Like Keys
- Symbol Registry

> ### 🛠 Phase 3 Project: **Functional Utility Library**
> Build your own mini-Lodash library with: `map`, `filter`, `reduce`, `compose`, `pipe`, `curry`, `memoize`, `debounce`, `throttle`, `deepClone`, `flattenDeep`, `groupBy`, `zip`. Write all functions using pure functional programming & full test coverage.

---

## 🟠 PHASE 4: Asynchronous JavaScript Mastery
> **Goal:** Master async patterns — the most critical JS skill.

### 📦 Module 4.1: Callbacks
- Callback Pattern
- Callback Hell / Pyramid of Doom
- Error-First Callbacks (Node.js Convention)
- Inversion of Control Problem
- Converting Callbacks to Promises

### 📦 Module 4.2: Promises
- What Are Promises (Pending, Fulfilled, Rejected)
- Creating Promises (`new Promise((resolve, reject) => {})`)
- `.then()`, `.catch()`, `.finally()`
- Promise Chaining
- Returning Values from `.then()`
- Error Handling in Chains
- `Promise.all()` (All Must Succeed)
- `Promise.allSettled()` (Get All Results)
- `Promise.race()` (First to Settle)
- `Promise.any()` (First to Fulfill)
- `Promise.resolve()` & `Promise.reject()`
- Microtask Queue & Promise Execution Order
- Common Anti-Patterns
- `Promise.withResolvers()` (ES2024)

### 📦 Module 4.3: Async / Await
- `async` Functions (Always Return Promises)
- `await` (Pausing Execution)
- Error Handling (`try/catch` with Async)
- `await` in Loops (Sequential vs Parallel)
- `Promise.all()` with `await` (Parallel Execution)
- Top-Level `await` (ES Modules)
- Async Iteration (`for await...of`)
- Async Generators (`async function*`)
- Converting Promise Chains to Async/Await
- Common Mistakes & Best Practices

### 📦 Module 4.4: Advanced Async Patterns
- Retry Logic with Async
- Timeout Pattern (`Promise.race` with Timer)
- Debouncing & Throttling (Async-Aware)
- Concurrent Task Limiting (Semaphore Pattern)
- `AbortController` & `AbortSignal`
- Async Queue / Task Pool
- `structuredClone()` for Async Data
- Web Workers (Intro — True Parallelism)
- `SharedArrayBuffer` & `Atomics` (Intro)

### 📦 Module 4.5: Fetch API & HTTP
- `fetch()` Basics (GET, POST, PUT, DELETE)
- Headers, Body, & Request Options
- Response Object (`.json()`, `.text()`, `.blob()`)
- Error Handling with Fetch (Network vs HTTP Errors)
- `AbortController` with Fetch
- Streaming Responses (`ReadableStream`)
- `FormData` for File Uploads
- CORS (Cross-Origin Resource Sharing)
- `axios` Library (Overview & Comparison)
- `URLSearchParams`

> ### 🛠 Phase 4 Project: **Async Task Orchestrator**
> Build an advanced async job runner that: queues async tasks, runs them with configurable concurrency limits, retries on failure with exponential backoff, supports cancellation via `AbortController`, tracks progress, and logs results. Fetches data from multiple public APIs concurrently.

---

## 🔴 PHASE 5: The DOM & Browser JavaScript
> **Goal:** Master browser-side JavaScript.

### 📦 Module 5.1: DOM Fundamentals
- What is the DOM (Document Object Model)
- DOM Tree Structure (Nodes, Elements, Text)
- Selecting Elements:
  - `getElementById`, `getElementsByClassName`, `getElementsByTagName`
  - `querySelector`, `querySelectorAll`
- Traversing the DOM:
  - `parentNode`, `parentElement`
  - `childNodes`, `children`
  - `firstChild`, `firstElementChild`, `lastElementChild`
  - `nextSibling`, `nextElementSibling`, `previousElementSibling`
  - `closest()`
- `NodeList` vs `HTMLCollection`

### 📦 Module 5.2: DOM Manipulation
- Creating Elements (`createElement`, `createTextNode`, `createDocumentFragment`)
- Adding Elements (`appendChild`, `append`, `prepend`, `insertBefore`, `insertAdjacentElement`, `insertAdjacentHTML`)
- Removing Elements (`removeChild`, `remove`)
- Replacing Elements (`replaceChild`, `replaceWith`)
- Cloning Elements (`cloneNode`)
- Modifying Content (`textContent`, `innerHTML`, `innerText`, `outerHTML`)
- Modifying Attributes (`getAttribute`, `setAttribute`, `removeAttribute`, `dataset`)
- Modifying Styles (`style`, `classList.add/remove/toggle/contains`, `getComputedStyle`)
- `data-*` Attributes & `dataset`

### 📦 Module 5.3: Events
- Event Listeners (`addEventListener`, `removeEventListener`)
- Event Object (`e.target`, `e.currentTarget`, `e.type`)
- Event Flow (Capturing → Target → Bubbling)
- `stopPropagation()` & `stopImmediatePropagation()`
- `preventDefault()`
- Event Delegation (Performance Pattern)
- Common Events:
  - Mouse: `click`, `dblclick`, `mouseenter`, `mouseleave`, `mousemove`
  - Keyboard: `keydown`, `keyup`, `keypress`
  - Form: `submit`, `change`, `input`, `focus`, `blur`
  - Window: `load`, `DOMContentLoaded`, `resize`, `scroll`
  - Drag & Drop Events
  - Touch Events
- Custom Events (`CustomEvent`, `dispatchEvent`)
- Passive Event Listeners (`{ passive: true }`)
- `once` Option (`{ once: true }`)

### 📦 Module 5.4: Browser APIs
- `localStorage` & `sessionStorage`
- `Cookies` (`document.cookie`)
- `history` API (`pushState`, `replaceState`, `popstate`)
- `location` Object
- `navigator` Object (Geolocation, Clipboard, Online/Offline)
- `Intersection Observer` (Lazy Loading, Infinite Scroll)
- `Mutation Observer` (DOM Change Detection)
- `Resize Observer`
- `requestAnimationFrame` (Smooth Animations)
- `Notification API`
- `Geolocation API`
- `Clipboard API`
- `URL` & `URLSearchParams`
- `Intl` API (Formatting Dates, Numbers, Currencies)
- `structuredClone()`
- `Broadcast Channel` (Tab Communication)

### 📦 Module 5.5: Forms & Validation
- Accessing Form Elements
- Form Submission Handling
- `FormData` API
- Client-Side Validation (Built-in & Custom)
- Constraint Validation API
- Dynamic Form Generation
- Debouncing Input Events

### 📦 Module 5.6: Web Performance
- Critical Rendering Path
- Reflow vs Repaint
- DOM Batch Updates (`DocumentFragment`)
- Lazy Loading (Images, Components)
- Debounce & Throttle for Events
- `requestIdleCallback`
- Memory Leaks (Event Listeners, Closures, Detached DOM)
- Performance API (`performance.now()`, `performance.mark()`)

> ### 🛠 Phase 5 Project: **Interactive Kanban Board**
> Build a fully interactive Kanban board (like Trello) with:
> - Drag & Drop (native API)
> - Dynamic card creation, editing, deletion
> - Column management
> - `localStorage` persistence
> - Search & filter cards
> - Keyboard shortcuts
> - Responsive design
> - Smooth animations with `requestAnimationFrame`
> - No frameworks — pure vanilla JS

---

## 🟣 PHASE 6: Modern JavaScript & Tooling
> **Goal:** Master the modern JS ecosystem and developer tooling.

### 📦 Module 6.1: ES Modules
- `import` & `export` (Named & Default)
- `import * as` (Namespace Import)
- Dynamic Imports (`import()`)
- Module Scope (No Global Pollution)
- `<script type="module">`
- CommonJS vs ES Modules (`require` vs `import`)
- Circular Dependencies
- Import Assertions / Attributes
- Top-Level `await` in Modules
- `import.meta`

### 📦 Module 6.2: Error Handling Mastery
- `Error` Object & Properties (`message`, `name`, `stack`, `cause`)
- Error Types (`TypeError`, `ReferenceError`, `SyntaxError`, `RangeError`, `URIError`)
- Custom Error Classes (`extends Error`)
- `try/catch/finally` Patterns
- Error Handling in Async Code
- Global Error Handlers (`window.onerror`, `unhandledrejection`)
- `Error.cause` (ES2022 — Error Chaining)
- `AggregateError`
- Defensive Programming Patterns
- Graceful Degradation

### 📦 Module 6.3: Regular Expressions
- Creating Regex (Literal `/pattern/` vs `new RegExp()`)
- Flags (`g`, `i`, `m`, `s`, `u`, `d`, `v`)
- Character Classes, Quantifiers, Anchors
- Groups & Backreferences
- Lookahead & Lookbehind
- Named Groups (`(?<name>...)`)
- `match`, `matchAll`, `replace`, `replaceAll`, `search`, `split`, `test`, `exec`
- Common Patterns (Email, URL, Phone, Password)
- `v` Flag (Unicode Sets — ES2024)

### 📦 Module 6.4: Modern ES Features (ES2020–ES2024+)
- **ES2020:** `?.`, `??`, `BigInt`, `globalThis`, `Promise.allSettled`, `matchAll`, Dynamic `import()`
- **ES2021:** `replaceAll`, `Promise.any`, `??=`, `||=`, `&&=`, Numeric Separators (`1_000_000`), `WeakRef`, `FinalizationRegistry`
- **ES2022:** Top-Level `await`, `.at()`, `Object.hasOwn()`, `Error.cause`, Class Fields, Private Methods, `#private`, Static Blocks
- **ES2023:** `findLast`, `findLastIndex`, `toSorted`, `toReversed`, `toSpliced`, `with()`, `#!` Hashbang, Array Grouping (Stage 3→4)
- **ES2024:** `Object.groupBy`, `Map.groupBy`, `Promise.withResolvers`, `Atomics.waitAsync`, `v` RegExp Flag, `ArrayBuffer.transfer`
- **Stage 3+ Proposals:** Decorators, Temporal API, Pattern Matching, Pipeline Operator (`|>`), Records & Tuples, Iterator Helpers

### 📦 Module 6.5: Package Managers & Build Tools
- **npm** (init, install, scripts, `package.json`, `package-lock.json`, Workspaces)
- **yarn** (Classic & Berry)
- **pnpm** (Fast, Disk-Efficient)
- **Bundlers:**
  - Vite ⭐ (Fast Dev Server, HMR, Build)
  - Webpack (Concepts: Entry, Output, Loaders, Plugins)
  - esbuild (Blazing Fast)
  - Rollup (Library Bundling)
  - Parcel (Zero Config)
  - Turbopack (Next.js)
- **Transpilers:**
  - Babel (ES6+ → ES5, Plugins, Presets)
  - SWC (Rust-Based, Faster)
- **Task Runners:** npm Scripts
- Source Maps
- Tree Shaking & Code Splitting
- Environment Variables (`.env`, `dotenv`)

### 📦 Module 6.6: TypeScript Fundamentals
- Why TypeScript
- Basic Types (`string`, `number`, `boolean`, `any`, `unknown`, `never`, `void`)
- Interfaces & Type Aliases
- Union & Intersection Types
- Generics
- Enums
- Type Guards & Narrowing
- Utility Types (`Partial`, `Required`, `Pick`, `Omit`, `Record`, `Readonly`)
- `as const` Assertions
- Discriminated Unions
- Module System in TS
- `tsconfig.json` Configuration
- TypeScript with React / Node.js
- `Zod` (Runtime Validation + Type Inference)

> ### 🛠 Phase 6 Project: **TypeScript Utility Library (Published to npm)**
> Build a typed utility library in TypeScript with: string helpers, array helpers, object helpers, async helpers, validation functions. Full test coverage, bundled with Vite/Rollup, published to npm with proper `package.json`, types declarations, and documentation.

---

## ⚫ PHASE 7: Testing & Code Quality
> **Goal:** Write reliable, tested, and maintainable JavaScript code.

### 📦 Module 7.1: Unit Testing
- **Vitest** ⭐ (Fast, Vite-Native)
  - Test Suites (`describe`, `it`/`test`)
  - Assertions (`expect`, `toBe`, `toEqual`, `toThrow`, `toContain`)
  - Setup/Teardown (`beforeEach`, `afterEach`, `beforeAll`, `afterAll`)
  - Mocking (`vi.fn()`, `vi.mock()`, `vi.spyOn()`)
  - Snapshot Testing
  - Code Coverage (`--coverage`)
  - Parameterized / Table Tests (`it.each`)
- **Jest** (Alternative — Most Popular)
  - Same API as Vitest
  - Timer Mocks (`jest.useFakeTimers`)
  - Module Mocking
- **Testing Library** Philosophy ("Test Behavior, Not Implementation")

### 📦 Module 7.2: Integration & E2E Testing
- **Playwright** ⭐ (Cross-Browser E2E)
  - Page Navigation, Selectors, Actions
  - Assertions, Screenshots, Videos
  - API Testing
- **Cypress** (Alternative E2E)
- **Supertest** (API Integration Testing — Node.js)
- Test Pyramind (Unit → Integration → E2E)

### 📦 Module 7.3: Code Quality & Linting
- **ESLint** (Linting Rules, Plugins, Config)
  - Flat Config (New) vs Legacy Config
  - Popular Configs (`eslint-config-airbnb`, `@antfu/eslint-config`)
- **Prettier** (Code Formatting)
  - ESLint + Prettier Integration
- **Husky** (Git Hooks)
- **lint-staged** (Run Linters on Staged Files)
- **commitlint** (Conventional Commits)
- **EditorConfig**

### 📦 Module 7.4: Debugging & DevTools Mastery
- Chrome DevTools:
  - Elements Panel (DOM Inspection)
  - Console (Logging, `console.table`, `console.group`, `console.time`)
  - Sources (Breakpoints, Watch, Call Stack, Scope)
  - Network Panel (Requests, Throttling, Timing)
  - Performance Panel (Flame Charts, Layout Shifts)
  - Application Panel (Storage, Cache, Service Workers)
  - Memory Panel (Heap Snapshots, Leaks)
- `debugger` Statement
- Source Maps Debugging
- Node.js Debugging (`--inspect`, VS Code Debugger)
- Error Tracking (Sentry — Intro)

### 📦 Module 7.5: Version Control
- Git Fundamentals (init, add, commit, branch, merge, rebase, stash)
- Branching Strategies (Git Flow, Trunk-Based, GitHub Flow)
- GitHub Collaboration (PRs, Issues, Actions)
- `.gitignore` for JS Projects
- Conventional Commits & Changelogs
- Monorepos (Turborepo, Nx — Overview)

> ### 🛠 Phase 7 Project: **Form Validation Library (Fully Tested)**
> Build a framework-agnostic form validation library with: required, email, min/max length, regex, custom validators, async validators (e.g., check username availability). 95%+ test coverage with Vitest, linted with ESLint, formatted with Prettier, pre-commit hooks with Husky.

---

## 🔶 PHASE 8: Backend Development with Node.js
> **Goal:** Build server-side applications and REST APIs.

### 📦 Module 8.1: Node.js Fundamentals
- What is Node.js & V8 Engine
- Node.js Architecture (Event-Driven, Non-Blocking I/O)
- Node.js Event Loop (libuv — Different from Browser!)
  - Timers → Pending → Idle → Poll → Check → Close
- Global Objects (`process`, `__dirname`, `__filename`, `Buffer`, `global`)
- `process` Object (`env`, `argv`, `exit`, `cwd`, `stdin`, `stdout`)
- Core Modules:
  - `fs` / `fs/promises` (File System)
  - `path` (Path Utilities)
  - `http` / `https` (HTTP Server)
  - `events` (EventEmitter)
  - `stream` (Readable, Writable, Transform, Duplex)
  - `crypto` (Hashing, Encryption)
  - `url` & `querystring`
  - `os` (System Info)
  - `child_process` (Spawning Processes)
  - `worker_threads` (True Multithreading)
  - `cluster` (Multi-Process)
- CommonJS vs ES Modules in Node
- npm Scripts & `package.json` Deep Dive
- `npx` Usage
- Environment Variables (`process.env`, `dotenv`)
- `nodemon` / `tsx` (Auto-Restart)

### 📦 Module 8.2: Express.js
- Express Setup & Project Structure
- Middleware (Built-in, Third-Party, Custom)
- Routing (`Router`, Route Parameters, Query Strings)
- Request & Response Objects
- `express.json()`, `express.urlencoded()`, `express.static()`
- Error Handling Middleware
- Template Engines (EJS, Pug — Overview)
- File Uploads (`multer`)
- CORS (`cors` Package)
- Rate Limiting (`express-rate-limit`)
- Helmet (Security Headers)
- Compression (`compression`)
- Logging (`morgan`, `winston`, `pino`)
- MVC Pattern with Express
- Environment-Based Configuration

### 📦 Module 8.3: REST API Design & Best Practices
- RESTful Resource Naming
- HTTP Methods & Status Codes
- Request Validation (`Joi`, `Zod`, `express-validator`)
- DTO Pattern
- Pagination (Offset, Cursor)
- Filtering, Sorting, Searching
- HATEOAS (Overview)
- API Versioning (`/api/v1/`)
- Response Formatting (Consistent JSON Structure)
- Error Response Standards (RFC 7807 `ProblemDetails`)

### 📦 Module 8.4: Authentication & Authorization
- Session-Based Auth (`express-session`)
- Cookie-Based Auth
- JWT Authentication (`jsonwebtoken`)
  - Access Tokens & Refresh Tokens
  - Token Storage (httpOnly Cookies vs `localStorage`)
  - Token Rotation & Revocation
- Password Hashing (`bcrypt`, `argon2`)
- Role-Based Access Control (RBAC)
- OAuth2 / Social Login (`passport.js`, Google, GitHub)
- API Key Authentication
- Two-Factor Authentication (2FA — Overview)

### 📦 Module 8.5: Databases with Node.js
- **MongoDB + Mongoose:**
  - Schema & Model Definition
  - CRUD Operations
  - Validation & Middleware (Pre/Post Hooks)
  - Population (References)
  - Aggregation Pipeline
  - Indexing
  - Virtuals & Statics
- **PostgreSQL / MySQL:**
  - `pg` (node-postgres) / `mysql2`
  - Raw Queries & Parameterized Queries
  - Connection Pooling
  - Transactions
- **Prisma ORM** ⭐ (Modern Type-Safe ORM)
  - Schema Definition (`schema.prisma`)
  - Migrations
  - CRUD & Relations
  - Filtering, Sorting, Pagination
  - Raw Queries
  - Prisma Studio
- **Drizzle ORM** (Alternative — Lightweight)
- **Knex.js** (Query Builder)
- **Redis** (`ioredis`)
  - Caching
  - Session Store
  - Pub/Sub
  - Rate Limiting Backend

### 📦 Module 8.6: Real-Time Communication
- WebSockets (`ws` Library)
- Socket.io
  - Events, Rooms, Namespaces
  - Broadcasting
  - Authentication with Sockets
- Server-Sent Events (SSE)
- Long Polling (Historical)

### 📦 Module 8.7: Alternative Frameworks
- **Fastify** ⭐ (Fast, Schema-Based Validation)
- **NestJS** (Enterprise-Grade, Angular-Inspired, DI)
- **Hono** (Ultralight, Multi-Runtime)
- **Koa** (Express Successor by Same Team)
- **tRPC** (End-to-End Type Safety)
- **AdonisJS** (Laravel-like for Node)

> ### 🛠 Phase 8 Project: **RESTful E-Commerce API**
> Build a complete e-commerce backend with Express/Fastify:
> - User registration/login (JWT + Refresh Tokens)
> - Product CRUD with categories & image upload
> - Shopping cart & order management
> - Payment integration (Stripe)
> - Role-based access (Admin, Customer)
> - Pagination, filtering, sorting, search
> - Input validation (Zod)
> - MongoDB + Mongoose / PostgreSQL + Prisma
> - Redis caching for products
> - Rate limiting & security headers
> - WebSocket for order status updates
> - Comprehensive error handling
> - Logging with Pino
> - Full test suite (Vitest + Supertest)

---

## 🔷 PHASE 9: Frontend Frameworks
> **Goal:** Build modern, reactive user interfaces.

### 📦 Module 9.1: Frontend Fundamentals (Pre-Framework)
- Component-Based Thinking
- State Management Concepts
- Declarative vs Imperative UI
- Virtual DOM vs Direct DOM
- SPA vs MPA vs SSR vs SSG vs ISR
- Client-Side Routing
- Build Tools Recap (Vite)

### 📦 Module 9.2: React ⭐ (Most Popular)
- **Core Concepts:**
  - JSX (Syntax, Expressions, Fragments)
  - Components (Function Components)
  - Props (Passing Data, Children, Destructuring)
  - State (`useState`)
  - Event Handling
  - Conditional Rendering
  - Lists & Keys
  - Forms (Controlled vs Uncontrolled)
- **Hooks Deep Dive:**
  - `useState` (State Management)
  - `useEffect` (Side Effects, Cleanup, Dependencies)
  - `useRef` (DOM Access, Persistent Values)
  - `useContext` (Context API — Prop Drilling Solution)
  - `useReducer` (Complex State Logic)
  - `useMemo` (Expensive Computation Caching)
  - `useCallback` (Function Memoization)
  - `useId` (Unique IDs)
  - `useTransition` & `useDeferredValue` (Concurrent Features)
  - Custom Hooks (Building Reusable Logic)
- **Advanced React:**
  - Component Composition Patterns
  - Higher-Order Components (HOC)
  - Render Props Pattern
  - Compound Components
  - React.lazy & Suspense (Code Splitting)
  - Error Boundaries
  - Portals
  - Forwarding Refs (`forwardRef`)
  - `React.memo` (Performance)
  - Context API + `useReducer` (State Management)
  - React DevTools
- **State Management:**
  - Context API (Built-in)
  - Zustand ⭐ (Simple, Lightweight)
  - Redux Toolkit (RTK) (Enterprise Standard)
  - Jotai / Recoil (Atomic State)
  - TanStack Query (React Query) ⭐ (Server State)
- **Routing:**
  - React Router v6+ (`BrowserRouter`, `Routes`, `Route`)
  - Dynamic Routes, Nested Routes
  - Route Parameters & Search Params
  - Loaders & Actions (React Router 6.4+)
  - Protected Routes
  - TanStack Router (Type-Safe Alternative)
- **Styling:**
  - CSS Modules
  - Tailwind CSS ⭐
  - styled-components / Emotion (CSS-in-JS)
  - Shadcn/ui ⭐ (Component Library)
  - Radix UI (Headless Components)
- **Forms:**
  - React Hook Form ⭐ + Zod Validation
  - Formik (Alternative)
- **Data Fetching:**
  - TanStack Query (React Query) ⭐
  - SWR (Alternative by Vercel)
  - `fetch` / `axios` with `useEffect`

### 📦 Module 9.3: Next.js ⭐ (React Meta-Framework)
- What is Next.js & Why Use It
- App Router (Next.js 13+)
  - File-Based Routing
  - Layouts, Templates, Loading, Error
  - Server Components vs Client Components (`"use client"`)
  - Route Handlers (API Routes)
  - Dynamic Routes & Catch-All Routes
- Rendering Strategies:
  - SSR (Server-Side Rendering)
  - SSG (Static Site Generation)
  - ISR (Incremental Static Regeneration)
  - CSR (Client-Side Rendering)
  - Streaming
- Server Actions (`"use server"`)
- Data Fetching (`fetch` with Caching & Revalidation)
- Middleware
- Image Optimization (`next/image`)
- Font Optimization (`next/font`)
- Metadata & SEO
- Deployment (Vercel, Docker, Self-Hosted)

### 📦 Module 9.4: Alternative Frameworks (Overview)
- **Vue.js** (Options API, Composition API, Pinia, Nuxt.js)
- **Angular** (Components, Services, DI, RxJS, NgModules, Standalone)
- **Svelte / SvelteKit** (No Virtual DOM, Compiled)
- **Astro** (Content-Focused, Islands Architecture)
- **Solid.js** (Fine-Grained Reactivity)
- **Qwik** (Resumability)

> ### 🛠 Phase 9 Project: **Full-Stack Project Management App (Next.js)**
> Build a Jira-like project management tool with Next.js:
> - Authentication (NextAuth.js / Clerk)
> - Workspace & project management
> - Task board with drag & drop
> - Real-time updates
> - Dashboard with charts (Recharts)
> - Role-based access
> - Server Actions for mutations
> - PostgreSQL + Prisma
> - TanStack Query for data fetching
> - React Hook Form + Zod validation
> - Tailwind CSS + Shadcn/ui
> - Responsive design
> - Dark mode
> - Deployed on Vercel

---

## 💎 PHASE 10: Advanced Topics & Production Readiness
> **Goal:** Build production-grade, scalable JavaScript applications.

### 📦 Module 10.1: Design Patterns in JavaScript
- **Creational:** Singleton, Factory, Abstract Factory, Builder, Prototype, Module
- **Structural:** Adapter, Decorator, Facade, Proxy, Flyweight, Composite
- **Behavioral:** Observer, Strategy, Command, Iterator, Mediator, State, Chain of Responsibility, Pub/Sub
- Dependency Injection Pattern
- Middleware Pattern
- Repository Pattern

### 📦 Module 10.2: Performance Optimization
- **Frontend Performance:**
  - Core Web Vitals (LCP, FID/INP, CLS)
  - Lighthouse Audits
  - Code Splitting & Lazy Loading
  - Tree Shaking
  - Image Optimization (WebP, AVIF, Lazy Load)
  - Font Loading Strategies
  - Preloading & Prefetching
  - Service Workers & Caching
  - CDN Usage
  - Bundle Analysis (`vite-bundle-analyzer`)
- **Backend Performance:**
  - Connection Pooling
  - Query Optimization
  - Caching (Redis, In-Memory)
  - Compression (gzip, Brotli)
  - Load Balancing
  - Horizontal Scaling with `cluster` Module
  - Streaming Large Responses
  - Database Indexing
- **JavaScript Performance:**
  - Memory Leaks Detection & Prevention
  - Event Loop Optimization
  - `WeakMap` & `WeakRef` for Memory
  - Web Workers for CPU-Intensive Tasks
  - `SharedArrayBuffer` & `Atomics`
  - Profiling with Chrome DevTools

### 📦 Module 10.3: Security
- **Frontend Security:**
  - XSS (Cross-Site Scripting) Prevention
  - CSRF (Cross-Site Request Forgery) Protection
  - Content Security Policy (CSP)
  - Sanitizing User Input (`DOMPurify`)
  - Secure Cookie Flags (`httpOnly`, `secure`, `sameSite`)
- **Backend Security:**
  - SQL Injection Prevention (Parameterized Queries)
  - NoSQL Injection Prevention
  - Rate Limiting & Brute Force Protection
  - Helmet.js (Security Headers)
  - Input Validation (Server-Side)
  - HTTPS & TLS
  - Secret Management (Environment Variables, Vault)
  - Dependency Auditing (`npm audit`)
  - OWASP Top 10 Awareness

### 📦 Module 10.4: Progressive Web Apps (PWA)
- Service Workers (Lifecycle, Caching Strategies)
- `manifest.json` (App Installability)
- Offline Support
- Push Notifications
- Background Sync
- Workbox (Google's PWA Library)

### 📦 Module 10.5: Microservices & Architecture
- Monolith vs Microservices
- API Gateway (Express Gateway, Kong)
- Inter-Service Communication (REST, gRPC, Message Queues)
- Message Brokers:
  - RabbitMQ (`amqplib`)
  - Apache Kafka (`kafkajs`)
  - BullMQ (Redis-Based Job Queue)
- Event-Driven Architecture
- CQRS & Event Sourcing
- Circuit Breaker Pattern
- Distributed Tracing (OpenTelemetry)
- Serverless Functions (AWS Lambda, Vercel Functions, Cloudflare Workers)
- Edge Computing (Cloudflare Workers, Deno Deploy)

### 📦 Module 10.6: DevOps & Deployment
- **Docker:**
  - Dockerfile for Node.js Apps
  - Multi-Stage Builds
  - Docker Compose
  - Docker Networking
- **CI/CD:**
  - GitHub Actions (Build, Test, Deploy)
  - GitLab CI
  - Automated Testing in Pipelines
  - Semantic Release
- **Cloud Deployment:**
  - Vercel (Next.js) ⭐
  - Netlify (Static + Functions)
  - Railway / Render (Node.js)
  - AWS (EC2, ECS, Lambda, S3, CloudFront)
  - DigitalOcean (App Platform)
- **Monitoring & Observability:**
  - Error Tracking (Sentry)
  - Application Monitoring (Datadog, New Relic)
  - Logging (Pino + ELK / Loki)
  - Health Checks & Uptime Monitoring
  - Analytics (PostHog, Plausible)

### 📦 Module 10.7: Advanced Ecosystem
- **GraphQL:**
  - Apollo Server & Client
  - Schema Definition Language (SDL)
  - Queries, Mutations, Subscriptions
  - Resolvers & Data Sources
  - Caching & Batching (DataLoader)
- **Monorepo Tools:**
  - Turborepo ⭐
  - Nx
  - pnpm Workspaces
- **Desktop Apps:** Electron, Tauri
- **Mobile Apps:** React Native, Expo
- **Deno & Bun:**
  - Deno (Secure Runtime, Built-in TS, Web Standards)
  - Bun (All-in-One: Runtime, Bundler, Test Runner, Package Manager)
- **WebAssembly (WASM):** Intro & Use Cases with JS

> ### 🛠 Phase 10 Project: **Full-Stack SaaS Platform**
> Build a production-ready SaaS application:
> - **Frontend:** Next.js + TypeScript + Tailwind + Shadcn/ui
> - **Backend:** Node.js (Express/Fastify) + TypeScript
> - **Database:** PostgreSQL + Prisma + Redis
> - **Auth:** NextAuth.js / Clerk (OAuth + Email)
> - **Payments:** Stripe (Subscriptions, Webhooks)
> - **Real-Time:** WebSockets / Server-Sent Events
> - **File Storage:** AWS S3 / Cloudflare R2
> - **Email:** Resend / SendGrid
> - **Background Jobs:** BullMQ + Redis
> - **Testing:** Vitest + Playwright
> - **CI/CD:** GitHub Actions
> - **Monitoring:** Sentry + Analytics
> - **Docker:** Containerized
> - **Deployed:** Vercel (Frontend) + Railway/AWS (Backend)
> - **Documentation:** API Docs + README

---

## 📋 Quick Reference Summary

```
Phase  1  ➜  Foundation & Core Basics          🟢
Phase  2  ➜  How JS Really Works (Engine)      🔵
Phase  3  ➜  OOP & Functional Programming      🟡
Phase  4  ➜  Asynchronous JavaScript            🟠
Phase  5  ➜  DOM & Browser JavaScript           🔴
Phase  6  ➜  Modern JS, TypeScript & Tooling    🟣
Phase  7  ➜  Testing & Code Quality             ⚫
Phase  8  ➜  Backend (Node.js)                  🔶
Phase  9  ➜  Frontend Frameworks (React)        🔷
Phase 10  ➜  Advanced & Production              💎
```

---

## 🗺️ JavaScript Career Paths After Completion

```
┌──────────────────────────────────────────────────────────────────┐
│                      JavaScript Developer                        │
├─────────────────┬─────────────────┬──────────────────────────────┤
│  Frontend       │  Backend        │    Full Stack                │
│  Engineer       │  Engineer       │    Engineer                  │
│  (React, Vue,   │  (Node.js,      │    (Next.js, T3 Stack,      │
│   Angular)      │   Express,      │     MERN, MEAN)             │
│                 │   Fastify)      │                              │
├─────────────────┼─────────────────┼──────────────────────────────┤
│  Mobile         │  DevOps /       │    Solutions                 │
│  Developer      │  Platform       │    Architect                 │
│  (React Native, │  Engineer       │    (System Design,           │
│   Expo, Ionic)  │  (Docker, CI/CD,│     Microservices,           │
│                 │   AWS, K8s)     │     Event-Driven)            │
├─────────────────┼─────────────────┼──────────────────────────────┤
│  Desktop App    │  Cloud /        │    Developer                 │
│  Developer      │  Serverless     │    Experience (DX)           │
│  (Electron,     │  Engineer       │    Engineer                  │
│   Tauri)        │  (Lambda,       │    (SDK/Tools/CLI            │
│                 │   Workers)      │     Development)             │
├─────────────────┼─────────────────┼──────────────────────────────┤
│  Web3 /         │  AI / ML        │    QA / Test                 │
│  Blockchain     │  Integration    │    Automation                │
│  Developer      │  Engineer       │    Engineer                  │
│  (Ethers.js,    │  (LangChain.js, │    (Playwright,              │
│   Solidity)     │   Vercel AI)    │     Cypress)                 │
└─────────────────┴─────────────────┴──────────────────────────────┘
```

---

## 🛠️ Recommended Tech Stacks (2024+)

```
┌──────────────────────────────────────────────────────────┐
│                    🔥 T3 Stack                           │
│  Next.js + TypeScript + tRPC + Prisma + Tailwind +       │
│  NextAuth.js                                             │
├──────────────────────────────────────────────────────────┤
│                    🟢 MERN Stack                         │
│  MongoDB + Express + React + Node.js                     │
├──────────────────────────────────────────────────────────┤
│                    💜 Modern Full Stack                   │
│  Next.js + TypeScript + Prisma + PostgreSQL +            │
│  Tailwind + Shadcn/ui + TanStack Query + Zod             │
├──────────────────────────────────────────────────────────┤
│                    ⚡ Serverless Stack                    │
│  Next.js / Remix + Cloudflare Workers + D1/Turso +       │
│  Drizzle ORM                                             │
├──────────────────────────────────────────────────────────┤
│                    🏢 Enterprise Stack                    │
│  NestJS + TypeScript + PostgreSQL + Prisma + Redis +     │
│  RabbitMQ + Docker + Kubernetes                          │
└──────────────────────────────────────────────────────────┘
```

---

## 📚 Recommended Resources

```
┌──────────────────────────────────────────────────────────┐
│                    📖 BOOKS                              │
├──────────────────────────────────────────────────────────┤
│  Beginner   → "Eloquent JavaScript" (Marijn Haverbeke)   │
│  Core       → "JavaScript: The Good Parts" (Crockford)   │
│  Deep Dive  → "You Don't Know JS Yet" (Kyle Simpson)     │
│  Advanced   → "JavaScript Patterns" (Stoyan Stefanov)    │
│  Functional → "Functional Light JS" (Kyle Simpson)       │
│  TypeScript → "Effective TypeScript" (Dan Vanderkam)     │
├──────────────────────────────────────────────────────────┤
│                    🌐 PLATFORMS                           │
├──────────────────────────────────────────────────────────┤
│  Learn      → javascript.info ⭐, MDN Web Docs           │
│  Practice   → LeetCode, Codewars, Exercism               │
│  Projects   → Frontend Mentor, JavaScript30 (Wes Bos)    │
│  Videos     → Fireship, Traversy Media, Jack Herrington   │
│  News       → JavaScript Weekly, Bytes.dev                │
│  TypeScript → Total TypeScript (Matt Pocock)              │
│  React      → react.dev (Official), Josh W. Comeau        │
│  Node.js    → nodejs.org, Node.js Best Practices (GitHub) │
└──────────────────────────────────────────────────────────┘
```

---

> **⏱ Estimated Timeline:** 7–12 months (with consistent daily practice)
> **💡 Pro Tip:** JavaScript's ecosystem moves fast, but the fundamentals don't. Master Phases 1–4 deeply — closures, `this`, prototypes, async — and frameworks will feel easy. Build something every single week.

---

*Want me to deep dive into any specific phase, module, career path, or create a week-by-week study plan?* 🚀