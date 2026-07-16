# 🔷 TypeScript Mastery Roadmap — Phase 1: Foundations
> Aligned with Phase 1 of the Software Engineering Mastery Roadmap
> **Estimated Duration: 4–6 months**

---

## 🟢 PHASE 1: Foundation & Core Basics
> **Goal:** Understand JavaScript's runtime, TypeScript's role on top of it, and write basic programs.

### 📦 Module 1.1: Introduction to TypeScript & JavaScript
- What is JavaScript (The Runtime Language)
- What is TypeScript (A Superset — Compiles to JavaScript)
- Why TypeScript Exists (Type Safety in a Dynamic Language)
- TypeScript's Philosophy (Structural Typing, Type Erasure, Gradual Adoption)
- JavaScript Runtimes
  - Node.js (Server-Side — V8 Engine, libuv)
  - Deno (Modern Alternative — Built-in TypeScript, Secure by Default)
  - Bun (Fast Runtime — Awareness)
  - Browser (Client-Side — Awareness)
- How TypeScript Code Executes
  - TypeScript → `tsc` Compiler → JavaScript → Node.js/Browser
  - Type Erasure (Types Disappear at Runtime — Critical to Understand)
  - `tsconfig.json` (Compiler Configuration)
- Installing Node.js, npm, TypeScript
- Setting Up IDE (VS Code — TypeScript Is Built for VS Code)
  - IntelliSense, Error Highlighting, Go to Definition, Rename Symbol
- Writing Your First Program
- Running TypeScript
  - `tsc` + `node` (Traditional)
  - `ts-node` (Execute Directly)
  - `tsx` (Modern, Fast, Preferred for Development)
- `tsconfig.json` Essentials
  - `target` (ES2020, ES2022, ESNext)
  - `module` (CommonJS, ESNext, NodeNext)
  - `strict` (ALWAYS Enable — Non-Negotiable)
  - `outDir`, `rootDir`, `sourceMap`
  - `esModuleInterop`, `resolveJsonModule`
  - `paths` and `baseUrl` (Path Aliases)

### 📦 Module 1.2: Variables, Types & Operators
- **Variable Declarations**
  - `let`, `const`, `var` (Why `var` Is Dead)
  - Block Scoping vs Function Scoping
  - Temporal Dead Zone (`let` and `const` Before Declaration)
  - `const` for Objects and Arrays (Reference Is Const, Contents Are Mutable)
- **Primitive Types**
  - `string`, `number`, `boolean`, `bigint`, `symbol`
  - `null` and `undefined` (The Two "Nothings")
  - `void` (Functions That Return Nothing)
  - `never` (Functions That Never Return — Throws, Infinite Loops)
- **Type Annotations**
  - Variable Annotations (`let name: string = "hello"`)
  - Type Inference (TypeScript Infers When You Don't Annotate)
  - When to Annotate vs When to Let TypeScript Infer
- **Special Types**
  - `any` (Escape Hatch — Avoid at All Costs)
  - `unknown` (Safe `any` — Must Type-Check Before Use)
  - `any` vs `unknown` (Why `unknown` Is Almost Always Better)
- **Literal Types**
  - String Literal Types (`"success" | "error"`)
  - Numeric Literal Types (`1 | 2 | 3`)
  - Boolean Literal Types (`true | false`)
  - `as const` Assertion (Make Values Literal Types)
- **Operators**
  - Arithmetic, Comparison, Logical, Assignment
  - Strict Equality (`===` vs `==` — Always Use `===`)
  - Nullish Coalescing (`??`)
  - Optional Chaining (`?.`)
  - Non-Null Assertion (`!` — Use Sparingly)
  - Type Assertion (`as` — Use Carefully)
  - `typeof` Operator (Runtime Type Check)
  - `in` Operator (Property Check)
  - `instanceof` Operator (Prototype Chain Check)
- **Strings**
  - Template Literals (Backtick Strings with `${expression}`)
  - String Methods (`includes`, `startsWith`, `endsWith`, `split`, `trim`, `slice`, `replace`, `replaceAll`)
  - Regular Expressions (`RegExp`, `match`, `test`, `exec`)
  - Tagged Template Literals (Advanced — Awareness)

### 📦 Module 1.3: Control Flow
- `if`, `else if`, `else`
- Ternary Expression (`condition ? a : b`)
- `switch` Statement
- Type Narrowing in Control Flow
  - `typeof` Guards (`typeof x === "string"`)
  - `instanceof` Guards
  - Truthiness Narrowing
  - Equality Narrowing
  - `in` Operator Narrowing
  - Discriminated Unions (Narrowing by Literal Property)
  - Custom Type Guards (`is` Keyword — `function isString(x: unknown): x is string`)
  - Exhaustive Checks with `never`
- `for` Loop, `while` Loop, `do-while` Loop
- `for...of` (Iterate Values — Preferred)
- `for...in` (Iterate Keys — Use Carefully)
- `break`, `continue`, `return`
- Labelled Statements (Awareness)

### 📦 Module 1.4: Arrays, Tuples & Core Data Structures
- **Arrays**
  - Array Type Annotations (`string[]` vs `Array<string>`)
  - Array Creation and Initialization
  - Array Methods (Mutating vs Non-Mutating)
    - Mutating: `push`, `pop`, `shift`, `unshift`, `splice`, `sort`, `reverse`, `fill`
    - Non-Mutating: `map`, `filter`, `reduce`, `find`, `findIndex`, `some`, `every`, `includes`, `indexOf`, `flat`, `flatMap`, `slice`, `concat`
  - `forEach` (Iteration Without Return)
  - Readonly Arrays (`readonly string[]`, `ReadonlyArray<string>`)
  - Array Destructuring
  - Spread Operator (`...`) for Arrays
- **Tuples**
  - Tuple Type Annotations (`[string, number]`)
  - Named Tuples (`[name: string, age: number]`)
  - Optional Tuple Elements
  - Rest Elements in Tuples (`[string, ...number[]]`)
  - Readonly Tuples
  - Tuple Destructuring
- **Objects (Basics)**
  - Object Literal Syntax
  - Object Type Annotations (Inline)
  - Optional Properties (`name?: string`)
  - Readonly Properties (`readonly id: number`)
  - Index Signatures (`[key: string]: unknown`)
  - Object Destructuring
  - Spread Operator for Objects
  - Excess Property Checks (TypeScript Catches Extra Properties on Literals)

### 📦 Module 1.5: Functions
- Function Declarations vs Function Expressions
- Arrow Functions (`=>`)
- Parameter Types and Return Types
- Optional Parameters (`name?: string`)
- Default Parameters (`name: string = "World"`)
- Rest Parameters (`...args: number[]`)
- Function Overloads (Multiple Signatures, Single Implementation)
- `this` Context in Functions
  - `this` in Regular Functions vs Arrow Functions
  - `this` Parameter in TypeScript (`function greet(this: User)`)
- Callbacks and Higher-Order Functions
- Closures (Functions That Capture Outer Scope)
- Immediately Invoked Function Expressions (IIFE)
- `void` Return Type vs `undefined` Return Type
- `never` Return Type (Throwing Functions, Infinite Loops)
- Function Type Expressions (`type Callback = (data: string) => void`)
- Call Signatures and Construct Signatures

> ### 🛠 Phase 1 Milestone Project: **CLI-Based Task Tracker**
> Build a CLI task tracker with Node.js: add/complete/delete tasks, filter by status, save to JSON file. Use proper TypeScript types for all task structures, type guards for input validation, tuples for command parsing, and array methods for data manipulation.

---

## 🔵 PHASE 2: Object-Oriented Programming
> **Goal:** Master OOP in TypeScript — classes, interfaces, and TypeScript-specific patterns.

### 📦 Module 2.1: Classes & Objects
- Class Declaration and Instantiation
- Constructor and Property Initialization
- Instance Methods
- `this` Keyword in Classes
- Class Type Annotations (TypeScript Infers from Class Definition)
- Classes as Types (A Class Creates Both a Value and a Type)

### 📦 Module 2.2: Encapsulation & Access Control
- Access Modifiers (`public`, `private`, `protected`)
- JavaScript Private Fields (`#field`) vs TypeScript `private`
  - `#field` Is Runtime Private (Truly Hidden)
  - `private` Is Compile-Time Only (Erased at Runtime)
- Getters and Setters (`get` / `set`)
- Readonly Properties in Classes (`readonly`)
- Parameter Properties (Shorthand: `constructor(private name: string)`)
- Immutable Objects (`Object.freeze`, `as const`, Readonly Types)

### 📦 Module 2.3: Inheritance
- `extends` Keyword
- `super()` for Constructor Chaining
- Method Overriding
- `override` Keyword (TypeScript 4.3+ — Explicit Override)
- Protected Members in Inheritance Hierarchy
- `abstract` Classes and Methods
- Single Inheritance (No Multiple Class Inheritance in TypeScript)

### 📦 Module 2.4: Interfaces & Structural Typing
- Interface Declaration (`interface`)
- Implementing Interfaces (`implements`)
- Optional and Readonly Properties in Interfaces
- Method Signatures in Interfaces
- Interface Extension (`extends` — Multiple Interface Inheritance)
- Interface Merging (Declaration Merging — Unique to TypeScript)
- `interface` vs `type` — When to Use What
  - `interface`: Object Shapes, Class Contracts, Declaration Merging
  - `type`: Unions, Intersections, Primitives, Tuples, Mapped Types
- Structural Typing (Duck Typing at the Type Level)
  - TypeScript Doesn't Care About Names — Only Shape
  - "If It Has the Right Properties, It Fits"
  - Implications for Design (No Need to Explicitly `implements` for Compatibility)

### 📦 Module 2.5: Polymorphism
- Interface-Based Polymorphism (Multiple Classes Implementing Same Interface)
- Method Overriding (Runtime Polymorphism)
- No Traditional Method Overloading (Use Function Overloads or Union Parameters)
- `instanceof` Checks (Runtime Type Narrowing)
- Discriminated Unions as Polymorphism Alternative
  - Tagged Unions (`type Shape = Circle | Square`, `kind` Discriminant)
  - Pattern Matching with `switch` on Discriminant
  - Exhaustive Checks with `never`
  - **💡 Discriminated unions are often MORE idiomatic than class hierarchies in TypeScript**

### 📦 Module 2.6: Abstraction
- Abstract Classes (Partial Implementation + Contract)
- Abstract Methods and Properties
- Interfaces as Pure Contracts (No Implementation)
- Abstract Class vs Interface — When to Use What
- Dependency on Abstractions (Programming to Interfaces)

### 📦 Module 2.7: Other OOP Concepts
- Static Members (Properties and Methods)
- Static Factory Methods
- Composition vs Inheritance (Strongly Prefer Composition in TypeScript)
- Mixins (Function That Takes a Class and Returns an Extended Class)
- Enums
  - Numeric Enums
  - String Enums
  - `const` Enums (Inlined at Compile Time)
  - Enum Pitfalls (Why Many TypeScript Developers Avoid Enums)
  - Union Types as Enum Alternative (`type Direction = "north" | "south" | "east" | "west"`)
- Symbols as Unique Keys
- `this` Types (Fluent Interfaces, Method Chaining)
- Class Expressions
- Implementing Multiple Interfaces

> ### 🛠 Phase 2 Milestone Project: **Shape Calculator with Plugin System**
> Build a geometry calculator: abstract `Shape` base, concrete shapes (`Circle`, `Rectangle`, `Triangle`). Use interfaces for `Serializable`, `Drawable`. Discriminated union variant for comparison. Plugin system using composition and interfaces. Demonstrate when class hierarchy vs discriminated unions makes more sense.

---

## 🟡 PHASE 3: Core TypeScript Essentials
> **Goal:** Master essential utilities, error handling, generics, modules, and the type system's power features.

### 📦 Module 3.1: Union & Intersection Types
- Union Types (`string | number`)
- Intersection Types (`TypeA & TypeB`)
- Discriminated Unions (Revisited — Complex Patterns)
  - Multi-Level Discriminants
  - Nested Discriminated Unions
- Union Type Narrowing (All Techniques Combined)
- Distributive Behavior of Unions in Conditional Types (Preview)
- Intersection for Mixin-Like Type Composition
- `never` as the Empty Union (Bottom Type)
- `unknown` as the Universal Union (Top Type)

### 📦 Module 3.2: Type Aliases & Advanced Object Types
- Type Aliases (`type Name = ...`)
- Complex Type Aliases (Functions, Objects, Unions, Intersections)
- Index Signatures (`[key: string]: ValueType`)
- Record Type (`Record<Keys, ValueType>`)
- Mapped Types Preview (`{ [K in keyof T]: ... }`)
- Template Literal Types (`\`${string}-id\``)
- Branded Types (Nominal Typing in a Structural System)
  - `type UserId = string & { __brand: "UserId" }`
  - Preventing Accidental Type Interchangeability
  - Factory Functions for Branded Types

### 📦 Module 3.3: Generics
- ==Why Generics== (Type-Safe Reusable Code)
- ==Generic Functions== (`function identity<T>(value: T): T`)
- ==Generic Interfaces==
- ==Generic Classes==
- ==Generic Type Aliases==
- ==Constraining Generics== (`<T extends HasId>`)
- ==Default Generic Parameters== (`<T = string>`)
- ==Multiple Generic Parameters== (`<K, V>`)
- ==Generic Inference== (TypeScript Infers Generic Types from Arguments)
- `keyof` Operator (Get Union of Object Keys)
- Indexed Access Types (`T[K]`)
- `keyof` + Generics (`function getProperty<T, K extends keyof T>(obj: T, key: K): T[K]`)
- Generic Utility Types (Built-in)
  - `Partial<T>`, `Required<T>`, `Readonly<T>`
  - `Pick<T, Keys>`, `Omit<T, Keys>`
  - `Record<Keys, Value>`
  - `Exclude<Union, Excluded>`, `Extract<Union, Extracted>`
  - `NonNullable<T>`
  - `ReturnType<F>`, `Parameters<F>`
  - `ConstructorParameters<C>`, `InstanceType<C>`
  - `Awaited<T>` (Unwrap Promise Type)

### 📦 Module 3.4: Error Handling
- JavaScript Error Types (`Error`, `TypeError`, `RangeError`, `SyntaxError`, `ReferenceError`)
- `try`, `catch`, `finally`
- `catch` Parameter Typing (`catch (error: unknown)` — Always `unknown`)
- Throwing Errors (`throw new Error("message")`)
- Custom Error Classes (Extending `Error`)
  - Setting `name` Property
  - Custom Properties (Error Code, HTTP Status, Context)
  - `Error.captureStackTrace` (Node.js)
- Error Handling Patterns
  - Result Pattern (`{ success: true, data: T } | { success: false, error: E }`)
  - Discriminated Union for Error Handling (TypeScript-Idiomatic)
  - `neverthrow` Library (Rust-Inspired `Result<T, E>` — Awareness)
  - Error Wrapping (Preserving Causal Chain with `cause` Property — ES2022)
- Best Practices
  - Never Catch and Swallow Errors Silently
  - Type-Narrow `unknown` Errors Before Using
  - Centralized Error Handling Strategy
  - Error Boundaries (Conceptual)
- Assertions (`assert` in Node.js)
  - `assert` Module
  - Assertion Functions in TypeScript (`asserts condition`)

### 📦 Module 3.5: Asynchronous Programming
- **JavaScript Event Loop**
  - Single-Threaded, Non-Blocking (Fundamental Mental Model)
  - Call Stack, Web APIs / Node APIs, Callback Queue, Microtask Queue
  - Event Loop Phases (Timers, I/O, Check, Close)
  - Microtasks vs Macrotasks (`Promise.then` vs `setTimeout`)
  - Why Blocking the Event Loop Is Catastrophic
- **Callbacks (Historical — Know Why They Died)**
  - Callback Pattern
  - Callback Hell / Pyramid of Doom
  - Error-First Callbacks (Node.js Convention)
- **Promises**
  - `new Promise<T>((resolve, reject) => { ... })`
  - `.then()`, `.catch()`, `.finally()`
  - Promise States (Pending, Fulfilled, Rejected)
  - Promise Chaining
  - `Promise.all()` (All Must Succeed — Parallel)
  - `Promise.allSettled()` (All Complete — Success or Failure)
  - `Promise.race()` (First to Complete)
  - `Promise.any()` (First to Succeed)
  - Promise Typing in TypeScript (`Promise<string>`)
  - Common Mistakes (Unhandled Promise Rejections, Missing `await`)
- **Async/Await**
  - `async function` (Always Returns a Promise)
  - `await` (Pauses Execution Until Promise Resolves)
  - Error Handling with `try/catch` in Async Functions
  - `await` in Loops (Sequential) vs `Promise.all` (Parallel)
  - Top-Level `await` (ES Modules)
  - Typing Async Functions (`async function getData(): Promise<User[]>`)
- **Timers and Scheduling**
  - `setTimeout`, `setInterval`, `setImmediate` (Node.js)
  - `process.nextTick` (Node.js — Microtask)
  - `queueMicrotask`
- **Event Emitters (Node.js)**
  - `EventEmitter` Class
  - `.on()`, `.once()`, `.emit()`, `.removeListener()`
  - Typed Event Emitters in TypeScript
  - Event-Driven Patterns

### 📦 Module 3.6: Collections & Iteration
- **Map** (`Map<K, V>`)
  - vs Plain Objects (Any Key Type, Preserves Insertion Order, Size Property)
  - Methods (`set`, `get`, `has`, `delete`, `clear`, `forEach`, `entries`, `keys`, `values`)
- **Set** (`Set<T>`)
  - Uniqueness Guarantee
  - Methods (`add`, `has`, `delete`, `clear`, `forEach`)
  - Set Operations (Union, Intersection, Difference — Manual or ES2025)
- **WeakMap** and **WeakSet** (Garbage-Collection Friendly)
  - Keys Must Be Objects
  - No Iteration (No `forEach`, No `size`)
  - Use Cases (Caching, Private Data, Metadata)
- **Iterators and Iterables**
  - `Symbol.iterator` Protocol
  - `for...of` Uses Iterators
  - Custom Iterables (Implementing `[Symbol.iterator]()`)
- **Generators**
  - `function*` Syntax
  - `yield` and `yield*`
  - Generator as Iterator (Lazy Evaluation)
  - Async Generators (`async function*`, `for await...of`)
  - Practical Use Cases (Pagination, Streaming Data, Infinite Sequences)

### 📦 Module 3.7: Modules & Package System
- **JavaScript Module History**
  - No Modules → CommonJS (`require`/`module.exports`) → ES Modules (`import`/`export`)
  - Why This History Matters (You'll Encounter Both)
- **ES Modules (Standard — Use This)**
  - Named Exports and Imports
  - Default Exports and Imports
  - Re-Exports (`export { ... } from "..."`)
  - `import type` (Type-Only Imports — Erased at Runtime)
  - Dynamic Imports (`import("module")` — Returns Promise)
  - Module Resolution (`node`, `node16`, `nodenext`, `bundler`)
- **CommonJS (Legacy — Know It, Don't Choose It)**
  - `require()` and `module.exports`
  - Interop with ES Modules (`esModuleInterop`)
- **Package Management**
  - npm (Default)
  - pnpm (Faster, Disk Efficient — Recommended)
  - yarn (Alternative — Awareness)
  - `package.json` Structure (name, version, scripts, dependencies, devDependencies)
  - `package-lock.json` / `pnpm-lock.yaml` (Deterministic Installs)
  - Semantic Versioning (`^`, `~`, Exact)
  - `devDependencies` vs `dependencies`
  - npm Scripts (`start`, `build`, `test`, `lint`, Custom)
- **TypeScript Module Configuration**
  - `"type": "module"` in `package.json`
  - `"module": "NodeNext"` and `"moduleResolution": "NodeNext"` in `tsconfig.json`
  - File Extensions in Imports (`.js` Extension Even for `.ts` Files — ESM Quirk)
  - Path Aliases (`paths` in `tsconfig.json` + `tsconfig-paths`)

### 📦 Module 3.8: File I/O & Working with Data
- **Node.js `fs` Module**
  - `fs/promises` (Async — Preferred)
  - Reading Files (`readFile`)
  - Writing Files (`writeFile`, `appendFile`)
  - File/Directory Operations (`mkdir`, `readdir`, `stat`, `unlink`, `rename`)
  - Checking Existence (`access`)
  - `fs.createReadStream` / `fs.createWriteStream` (Streaming I/O)
- **Path Module**
  - `path.join()`, `path.resolve()`, `path.basename()`, `path.dirname()`, `path.extname()`
  - Cross-Platform Path Handling
- **Working with JSON**
  - `JSON.parse()` and `JSON.stringify()`
  - Type Safety with `JSON.parse()` (Returns `any` — Must Validate)
  - Zod for Runtime JSON Validation (Parse, Don't Type-Assert)
- **Working with CSV, YAML, XML**
  - CSV Parsing Libraries (`csv-parse`, `papaparse`)
  - YAML (`yaml` Library)
  - XML (`fast-xml-parser` — Awareness)
- **Streams (Node.js)**
  - Readable, Writable, Transform, Duplex Streams
  - `pipe()` and `pipeline()`
  - Backpressure Handling
  - Stream Error Handling
  - Typed Streams in TypeScript
- **Buffer and Binary Data**
  - `Buffer` Class (Node.js)
  - `ArrayBuffer`, `Uint8Array` (Standard)
  - Encoding/Decoding (`utf-8`, `base64`, `hex`)

> ### 🛠 Phase 3 Milestone Project: **Multi-Format Data Pipeline**
> Build a CLI data processing tool: read data from CSV/JSON/YAML files, transform using generics and type-safe pipelines, validate with custom type guards and Result types, write output in multiple formats. Use async file I/O, streams for large files, custom iterables for lazy processing, and proper error handling with custom errors.

---

## 🟠 PHASE 4: Advanced TypeScript Features
> **Goal:** Master TypeScript's advanced type system, concurrency patterns, and runtime internals.

### 📦 Module 4.1: Advanced Type System
- **Conditional Types**
  - `T extends U ? X : Y` (Type-Level If/Else)
  - `infer` Keyword (Extract Types Within Conditional)
  - Distributive Conditional Types (How Unions Distribute)
  - `NonNullable<T>`, `Extract<T, U>`, `Exclude<T, U>` (Built on Conditionals)
- **Mapped Types**
  - `{ [K in keyof T]: ... }` (Transform Every Property)
  - Property Modifiers (`+readonly`, `-readonly`, `+?`, `-?`)
  - Key Remapping (`as` Clause in Mapped Types)
  - Building Custom Utility Types
    - `DeepReadonly<T>`
    - `DeepPartial<T>`
    - `Mutable<T>`
    - `PickByValue<T, V>`
- **Template Literal Types**
  - String Manipulation at the Type Level
  - `Uppercase<T>`, `Lowercase<T>`, `Capitalize<T>`, `Uncapitalize<T>`
  - Pattern Matching with Template Literals
  - Building Type-Safe Event Systems
  - Building Type-Safe Route Patterns
- **Recursive Types**
  - Recursive Type Aliases
  - `DeepReadonly<T>` Implementation
  - JSON Type (Recursive Definition)
  - Tree Structures at the Type Level
  - Recursion Depth Limits
- **Variadic Tuple Types**
  - `...T` in Tuple Types
  - Generic Rest Parameters
  - Composing Function Types

### 📦 Module 4.2: Runtime Validation & Schema Libraries
- **The Gap Between Compile-Time and Runtime**
  - TypeScript Types Are Erased (API Responses, User Input, DB Results Have No Types)
  - Validation Libraries Bridge the Gap
- **Zod (Preferred — TypeScript-First Schema Validation)**
  - Schema Definition (`z.object()`, `z.string()`, `z.number()`, etc.)
  - Type Inference from Schema (`z.infer<typeof schema>`)
  - Parsing vs Type Assertion (`schema.parse()` Validates at Runtime)
  - Refinements and Custom Validators (`.refine()`, `.superRefine()`)
  - Transformations (`.transform()`)
  - Unions, Discriminated Unions, Intersections
  - Nested Schemas and Arrays
  - Default Values, Optional Fields
  - Error Formatting and Custom Error Messages
  - Schema Composition and Reuse
  - Coercion (`z.coerce.number()`)
- **Alternatives (Awareness)**
  - Valibot (Smaller Bundle, Tree-Shakeable)
  - Yup (Older, Common in React Ecosystem)
  - ArkType (TypeScript-Native, Experimental)
  - io-ts (Functional Style — fp-ts)

### 📦 Module 4.3: Functional Programming in TypeScript
- Immutability
  - `const` Assertions (`as const`)
  - `Readonly<T>`, `ReadonlyArray<T>`
  - `Object.freeze()` (Shallow) vs Deep Freeze
  - Immutable Update Patterns (Spread Operator)
  - Immer Library (`produce()` for Immutable Updates — Awareness)
- Pure Functions (No Side Effects, Same Input → Same Output)
- Higher-Order Functions (Functions That Take/Return Functions)
- Function Composition
  - `pipe()` and `compose()` Utilities
  - Point-Free Style (Awareness)
- Currying and Partial Application
  - Manual Currying
  - Generic Curry Type
- Functors, Monads (Conceptual)
  - `Array.map` as Functor
  - `Promise` as Monad (`.then` is `flatMap`)
  - `Option/Maybe` Pattern (Avoiding `null`)
  - Railway-Oriented Programming (Result Type Chain)
- Declarative vs Imperative Approaches
  - Array Methods (Declarative) vs Loops (Imperative)
  - Configuration Objects vs Procedural Setup
  - When Each Style Wins

### 📦 Module 4.4: Concurrency & Parallelism
- **Event Loop Deep Dive**
  - Event Loop Phases in Node.js (Timers → I/O → Check → Close)
  - Microtasks (Promise, queueMicrotask) vs Macrotasks (setTimeout, setImmediate)
  - Event Loop Blocking Detection
  - `setImmediate` vs `process.nextTick` vs `setTimeout(fn, 0)`
- **Advanced Async Patterns**
  - Async Iteration (`for await...of`)
  - Async Generators (Producing Async Sequences)
  - Concurrency Control (Limiting Parallel Promises)
    - Manual Semaphore with Promises
    - `p-limit` Library (Concurrency Limiting)
    - `p-queue` Library (Priority Queue for Async Tasks)
  - Async Resource Management (`using` Declaration — TC39 Proposal, Node.js 20+)
  - AbortController (Cancelling Async Operations)
    - `AbortSignal` for Fetch, Streams, Custom Operations
    - Timeout with AbortSignal (`AbortSignal.timeout()`)
  - Debouncing and Throttling (Async Rate Control)
- **Worker Threads (True Parallelism in Node.js)**
  - `worker_threads` Module
  - When to Use Workers (CPU-Bound Tasks)
  - Worker Communication (`postMessage`, `MessageChannel`)
  - SharedArrayBuffer and Atomics (Shared Memory)
  - Worker Pool Pattern
  - TypeScript in Workers
- **Reactive Programming Concepts**
  - RxJS (ReactiveX for JavaScript/TypeScript)
    - Observables, Observers, Subscriptions
    - Creation Operators (`of`, `from`, `interval`, `fromEvent`)
    - Pipeable Operators (`map`, `filter`, `mergeMap`, `switchMap`, `debounceTime`, `throttleTime`, `catchError`, `retry`)
    - Subjects (Multicast Observables)
    - Hot vs Cold Observables
    - Backpressure Handling
  - Reactive Streams vs Promises vs Async Iterators
  - When Reactive Programming Adds Value vs Overcomplicates

### 📦 Module 4.5: Decorators & Metadata
- **Stage 3 Decorators (TC39 Standard — TypeScript 5+)**
  - Class Decorators
  - Method Decorators
  - Field Decorators
  - Accessor Decorators
  - Decorator Factories (Decorators with Arguments)
- **Legacy/Experimental Decorators (`experimentalDecorators`)**
  - Why They Still Exist (NestJS, TypeORM, class-validator Use Them)
  - `reflect-metadata` Library
  - Parameter Decorators (Legacy Only)
  - Metadata Reflection API
  - Differences Between Stage 3 and Experimental
- **Practical Decorator Use Cases**
  - Logging Decorator
  - Timing/Performance Decorator
  - Validation Decorator
  - Caching Decorator
  - Retry Decorator
  - Authorization Decorator

### 📦 Module 4.6: Node.js Runtime Internals
- **V8 Engine**
  - Compilation Pipeline (Parsing → AST → Bytecode → Optimized Machine Code)
  - JIT (Just-In-Time) Compilation
  - Hidden Classes and Inline Caches (Why Object Shape Matters for Performance)
  - Deoptimization (When V8 Falls Back to Slower Code)
- **Memory Management**
  - Heap and Stack in V8
  - Garbage Collection (Generational GC: Young Generation / Old Generation)
  - Scavenger (Minor GC) vs Mark-Sweep-Compact (Major GC)
  - Memory Leaks in Node.js
    - Closures Holding References
    - Event Listeners Not Removed
    - Global Variables Growing Unboundedly
    - Timer References (setInterval Not Cleared)
  - Memory Profiling (V8 Heap Snapshots, `--inspect`, Chrome DevTools)
  - `process.memoryUsage()` (RSS, HeapTotal, HeapUsed, External)
- **libuv (The Async Engine)**
  - Thread Pool (Default 4 Threads — File I/O, DNS, Crypto)
  - `UV_THREADPOOL_SIZE` Configuration
  - OS-Level Async I/O (epoll, kqueue, IOCP — Network I/O Bypasses Thread Pool)
- **Process and OS Interaction**
  - `process` Object (argv, env, cwd, exit, stdin/stdout/stderr)
  - `child_process` Module (spawn, exec, fork)
  - Signals (SIGINT, SIGTERM — Graceful Shutdown)
  - Cluster Module (Multi-Process for Multi-Core — Awareness)

### 📦 Module 4.7: Modern TypeScript & JavaScript Features
- **ES2020+**
  - Optional Chaining (`?.`)
  - Nullish Coalescing (`??`)
  - `Promise.allSettled()`
  - `globalThis`
  - `BigInt`
- **ES2021+**
  - `Promise.any()`
  - Logical Assignment (`&&=`, `||=`, `??=`)
  - `String.replaceAll()`
  - Numeric Separators (`1_000_000`)
  - `WeakRef` and `FinalizationRegistry`
- **ES2022+**
  - Top-Level `await`
  - `Error.cause`
  - `Array.at()` (Negative Indexing)
  - `Object.hasOwn()` (Replaces `hasOwnProperty`)
  - Class Fields (Public, Private `#`, Static)
  - Class Static Blocks
- **ES2023+**
  - Array Non-Mutating Methods (`toSorted()`, `toReversed()`, `toSpliced()`, `with()`)
  - `Array.findLast()`, `Array.findLastIndex()`
  - Hashbang Grammar (`#!/usr/bin/env node`)
- **TypeScript 5+ Features**
  - `const` Type Parameters
  - Decorators (Stage 3 — Covered Above)
  - `satisfies` Operator (Validate Type Without Widening)
  - Module Resolution Bundler Mode
  - `using` and `await using` (Explicit Resource Management)
  - Isolated Declarations (Faster Type Checking)

> ### 🛠 Phase 4 Milestone Project: **Concurrent Task Queue System**
> Build a concurrent task queue: generic typed tasks (`Task<TInput, TOutput>`), worker pool using Worker Threads for CPU tasks and async concurrency for I/O tasks, priority queue with RxJS observables for real-time status updates, AbortController for task cancellation, Zod for task payload validation, decorators for logging and retry logic, proper memory management with WeakMap for task metadata. Stream processing results via async generators.

---

## 🔴 PHASE 5: Data Structures & Algorithms in TypeScript
> **Goal:** Strengthen problem-solving skills using TypeScript with proper type safety.

### 📦 Module 5.1: Complexity Analysis
- Time and Space Complexity
- Big O, Big Ω, Big Θ
- Analyzing Loops, Recursion
- Amortized Analysis Basics
- JavaScript/TypeScript Built-in Complexities (Array, Map, Set, Object Operations)

### 📦 Module 5.2: Data Structures Implementation
- Linked Lists (Singly, Doubly, Circular) — Generically Typed (`LinkedList<T>`)
- Stacks and Queues (Array-Based and Linked-List-Based)
- Hash Tables (Custom HashMap — Understanding JavaScript's `Map` Internals)
- Trees (Binary Tree, BST, AVL) — Generic Nodes
- Heaps (Min-Heap, Max-Heap, Priority Queue) — Generic Comparators
- Graphs (Adjacency List and Matrix) — Generic Vertices and Edges
- Tries (Prefix Trees)
- Disjoint Set / Union-Find
- LRU Cache (Custom Implementation with `Map` Insertion Order)

### 📦 Module 5.3: Algorithms
- Sorting: Bubble, Selection, Insertion, Merge, Quick, Heap, Counting, Radix
  - V8's `Array.sort()` (TimSort — Know What's Under the Hood)
  - Custom Comparator Functions (Type-Safe)
- Searching: Linear, Binary, Ternary
- Recursion and Backtracking
- Dynamic Programming (Memoization with `Map` and Tabulation)
- Greedy Algorithms
- Graph Algorithms (BFS, DFS, Dijkstra, Kruskal, Prim, Topological Sort)
- Sliding Window, Two Pointers
- Bit Manipulation

> ### 🛠 Phase 5 Milestone Project: **Type-Safe Collections Library**
> Implement generically typed `ArrayList<T>`, `LinkedList<T>`, `HashMap<K, V>`, `BST<T>`, `Graph<V, E>`, `PriorityQueue<T>` with full CRUD, custom iterators (`Symbol.iterator`), comprehensive unit tests, and published as an npm package with proper type declarations.

---

## 🟣 PHASE 6: Design Principles, Patterns & Clean Code
> **Goal:** Write professional, maintainable, and scalable TypeScript code using proven principles and patterns.

### 📦 Module 6.1: SOLID Principles (Deep Understanding with TypeScript Examples)
- Single Responsibility Principle (SRP)
- Open/Closed Principle (OCP) — Generics and Composition Over Conditionals
- Liskov Substitution Principle (LSP) — Interface Contracts and Discriminated Unions
- Interface Segregation Principle (ISP) — Small Focused Interfaces
- Dependency Inversion Principle (DIP) — Depend on Interfaces, Inject Implementations

### 📦 Module 6.2: Design Principles (Beyond SOLID)
- Separation of Concerns
- High Cohesion / Low Coupling
- Composition over Inheritance (Especially Important in TypeScript)
- Dependency Inversion and Inversion of Control
- Law of Demeter (Principle of Least Knowledge)
- Principle of Least Astonishment
- Information Hiding (Parnas)

### 📦 Module 6.3: Creational Patterns
- Singleton Pattern (Module-Level Instance, Class-Based)
- Factory Method Pattern
- Abstract Factory Pattern
- Builder Pattern (Fluent API with `this` Return Types)
- Prototype Pattern (`structuredClone`, Spread Operator)

### 📦 Module 6.4: Structural Patterns
- Adapter Pattern
- Bridge Pattern
- Composite Pattern
- Decorator Pattern (Both GoF and TypeScript Decorators)
- Facade Pattern
- Flyweight Pattern
- Proxy Pattern (JavaScript `Proxy` Object — Native Support)

### 📦 Module 6.5: Behavioral Patterns
- Strategy Pattern (Functions as Strategies — TypeScript-Idiomatic)
- Observer Pattern (EventEmitter, Custom Typed Observers)
- Command Pattern
- State Pattern
- Template Method Pattern
- Chain of Responsibility Pattern
- Mediator Pattern
- Visitor Pattern
- Iterator Pattern (Built-in with `Symbol.iterator`)

### 📦 Module 6.6: Concurrency Patterns
- Producer-Consumer Pattern (Async Queue)
- Thread Pool Pattern (Worker Threads Pool)
- Future/Promise Pattern (Native Promises)
- Event-Driven Patterns (EventEmitter + Async)
- Pub/Sub Pattern (In-Process)

### 📦 Module 6.7: Anti-Patterns & When NOT to Use Patterns
- Common Anti-Patterns (God Class, Spaghetti Code, Golden Hammer, Lava Flow)
- TypeScript-Specific Anti-Patterns
  - `any` Everywhere (Defeating the Type System)
  - Overusing Classes When Functions and Modules Suffice
  - Overusing Enums When Union Types Work Better
  - Unnecessary Abstraction (Enterprise TypeScript Syndrome)
  - Type Assertion (`as`) Instead of Type Narrowing
- Over-Engineering with Patterns
- Pattern Selection Decision Framework
- "Keep It Simple" — When Plain Functions Beat Pattern Implementations

### 📦 Module 6.8: Clean Code Practices
- Meaningful Naming Conventions (TypeScript/JavaScript Conventions)
- Function and Class Design
- DRY, KISS, YAGNI Principles
- Code Smells and Refactoring Techniques (Martin Fowler's Catalog)
- Writing Self-Documenting Code
- Proper Error Handling Design
- TSDoc / JSDoc Best Practices
- Code Reviews Best Practices
- Type-Driven Development (Let Types Guide Your Design)

> ### 🛠 Phase 6 Milestone Project: **Event-Driven Notification System**
> Design a notification service supporting Email, SMS, Push, and Webhook notifications. Use Factory for notification creation, Strategy for delivery channels, Observer for event subscriptions, Builder for complex notification construction, Chain of Responsibility for filtering/routing. Typed event system with discriminated unions. Apply SOLID throughout. Comprehensive code review checklist.

---

## ⚫ PHASE 7: Testing, Build Tools & Version Control
> **Goal:** Master professional TypeScript development practices — testing, building, and collaborating.

### 📦 Module 7.1: Unit Testing
- **Vitest (Preferred — Fast, TypeScript-Native)**
  - Test Discovery, `describe`, `it`, `test`
  - Assertions (`expect`, `toBe`, `toEqual`, `toThrow`, `toContain`, etc.)
  - Setup and Teardown (`beforeEach`, `afterEach`, `beforeAll`, `afterAll`)
  - Mocking (`vi.fn()`, `vi.spyOn()`, `vi.mock()`)
  - Stubbing Module Imports
  - Fake Timers (`vi.useFakeTimers()`)
  - Snapshot Testing
  - Code Coverage (V8 or Istanbul)
  - In-Source Testing (Awareness)
- **Jest (Alternative — Widely Used)**
  - Same Assertion API (Vitest Is Jest-Compatible)
  - `ts-jest` or `@swc/jest` for TypeScript
  - When Jest vs Vitest
- **Testing Patterns**
  - AAA Pattern (Arrange, Act, Assert)
  - Mocking, Stubbing, Faking (Distinctions)
  - Testing Async Code (`async`/`await` in Tests)
  - Testing Error Cases (`expect(...).rejects.toThrow()`)
  - Testing Typed Code (Compile-Time Tests with `@ts-expect-error`)
  - TDD (Test-Driven Development) — Red/Green/Refactor
  - Code Coverage Metrics and Their Limitations

### 📦 Module 7.2: Integration Testing & Advanced Testing
- Integration Testing Strategies
- Behavior-Driven Development (BDD)
  - `cucumber-js` (Gherkin Syntax)
  - `vitest` / `jest` with BDD-Style Naming
- Test Pyramid (Unit → Integration → E2E)
- Testing Anti-Patterns
- Testcontainers for Node.js (`testcontainers`)
  - PostgreSQL, Redis, MongoDB, Kafka Containers
  - Container Lifecycle in Tests
- Writing Testable Code (Dependency Injection for Testability)
- Property-Based Testing (`fast-check`)

### 📦 Module 7.3: Code Quality Tools
- **Linting**
  - ESLint + `typescript-eslint` (Standard)
  - Flat Config (Modern ESLint — `eslint.config.ts`)
  - Essential Rules for TypeScript (`@typescript-eslint/recommended`, `strict`, `stylistic`)
  - Custom Rules
  - ESLint + Prettier Integration
- **Formatting**
  - Prettier (Opinionated Formatter — Standard for TS/JS)
  - EditorConfig
- **Type Checking**
  - `tsc --noEmit` (Type Check Without Compiling)
  - Strict Mode Rules (`strictNullChecks`, `noImplicitAny`, `strictFunctionTypes`, etc.)
- **Security Scanning**
  - `npm audit` / `pnpm audit`
  - Snyk
- **Pre-Commit Hooks**
  - Husky (Git Hooks)
  - lint-staged (Run Linters on Staged Files Only)
  - Commitlint (Enforce Conventional Commits)

### 📦 Module 7.4: Build Tools & Dependency Management
- **TypeScript Compilation**
  - `tsc` (Official Compiler — Type Checking + Transpilation)
  - `tsup` (Bundle TypeScript Libraries — esbuild Under the Hood)
  - `esbuild` (Extremely Fast Bundler — No Type Checking)
  - `swc` (Rust-Based Compiler — Fast Transpilation)
  - `tsc` for Type Checking + `esbuild`/`swc` for Transpilation (Common Pattern)
- **Build Pipelines**
  - `package.json` Scripts (Build, Test, Lint, Format)
  - `tsconfig.json` for Different Environments (Base + Extends)
  - Source Maps (Debugging Compiled Code)
  - Declaration Files (`.d.ts` Generation for Libraries)
  - Output Formats (CommonJS + ESM Dual Package)
- **Monorepo Tools (Awareness)**
  - Turborepo (Build Caching, Task Orchestration)
  - Nx (Full Monorepo Framework)
  - pnpm Workspaces (Native)
- **Dependency Management**
  - Dependency Vulnerability Scanning (`npm audit`, Snyk)
  - Lock Files (Always Commit Lock Files)
  - Semantic Versioning and Release Management
  - `changesets` (Versioning and Changelog for Libraries)
  - Reproducible Builds

### 📦 Module 7.5: Version Control Mastery
- Git Internals (Objects, Refs, DAG)
- Branching Strategies (GitFlow, Trunk-Based Development, GitHub Flow)
- Monorepo vs Polyrepo Trade-offs
- Advanced Git (Rebase, Cherry-Pick, Bisect, Stash, Hooks)
- GitHub / GitLab Collaboration (PRs, Code Reviews, Protected Branches)
- `.gitignore` for TypeScript Projects
- Conventional Commits

### 📦 Module 7.6: CI/CD Foundations
- Continuous Integration Best Practices
- Pipeline-as-Code (GitHub Actions)
- Pipeline Stages (Lint → Type Check → Unit Test → Integration Test → Build → Publish)
- Automated Testing in CI Pipelines
- Quality Gates (Type Check Pass, Lint Pass, Coverage Threshold)
- Dependency Vulnerability Scanning in CI
- Publishing to npm from CI (`npm publish`, GitHub Packages)
- Caching in CI (node_modules, Build Cache)

### 📦 Module 7.7: Logging & Debugging
- `console.log` vs Logging Libraries
- `pino` (Fast, Structured JSON Logging — Preferred for Node.js)
  - Log Levels, Child Loggers, Redaction
  - `pino-pretty` for Development
- `winston` (Alternative — Feature-Rich)
- Structured Logging Principles
  - Correlation IDs
  - Request Context Logging
- Debugging TypeScript
  - VS Code Debugger (Launch Configuration for `ts-node`/`tsx`)
  - Chrome DevTools for Node.js (`--inspect`)
  - Source Maps (Debugging TypeScript Through Compiled JS)
  - Breakpoints, Watch Expressions, Conditional Breakpoints

> ### 🛠 Phase 7 Milestone Project: **Task Queue Library (Fully Tested & Published)**
> Build an async task queue library with Vitest test suite (TDD), integration tests with Testcontainers (Redis for queue backend), property-based tests with `fast-check`, BDD scenarios, greater than 85% code coverage, structured logging with `pino`, type-checked with strict `tsc`, formatted by Prettier, linted by ESLint, pre-commit hooks with Husky, CI/CD with GitHub Actions, and published to npm as a dual CJS/ESM package with `.d.ts` declarations.

---

## 🔶 PHASE 8: Databases & Data Modeling
> **Goal:** Understand data modeling, master SQL, connect TypeScript to databases, and understand database internals.

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
- Subqueries and Common Table Expressions (CTEs)
- Aggregations and Window Functions
- Views, Stored Procedures, Triggers (Awareness)
- PostgreSQL / MySQL / SQLite

### 📦 Module 8.3: RDBMS Internals & Advanced Concepts
- Indexing Deep Dive (B-Tree, B+Tree, Hash Index, Composite Index)
- Query Plans and `EXPLAIN` / `EXPLAIN ANALYZE`
- ACID Properties (Atomicity, Consistency, Isolation, Durability)
- Isolation Levels (Read Uncommitted, Read Committed, Repeatable Read, Serializable)
- Transactions and MVCC (Multi-Version Concurrency Control)
- Connection Pooling Concepts
- Replication Basics (Leader-Follower)
- Sharding Basics (Concepts and Trade-offs)

### 📦 Module 8.4: TypeScript Database Access (Query Builders & Drivers)
- **PostgreSQL Drivers**
  - `pg` (node-postgres) — Low-Level Driver
    - Connection, Queries, Parameterized Queries (SQL Injection Prevention)
    - Connection Pooling (`Pool`)
    - Transactions (`BEGIN`, `COMMIT`, `ROLLBACK`)
    - Typing Query Results (Generic `query<T>()`)
  - `postgres` (porsager/postgres — Modern, Tagged Template Queries)
- **Query Builders**
  - Kysely (Type-Safe SQL Query Builder — Preferred)
    - Database Interface Definition (Schema Types)
    - Select, Insert, Update, Delete (Fully Typed)
    - Joins, Subqueries, CTEs (Type-Safe)
    - Migrations (Kysely Migrator)
    - Raw SQL When Needed
    - Transaction Support
    - Why Kysely Over ORMs (SQL Control + Type Safety)
  - Knex.js (Awareness — Popular but Less Type-Safe)
- **SQLite**
  - `better-sqlite3` (Synchronous — Fast for Embedded Use)
  - `sql.js` (WASM-Based — Awareness)

### 📦 Module 8.5: ORMs in TypeScript
- **Drizzle ORM (Preferred — SQL-Like, Type-Safe)**
  - Schema Definition in TypeScript
  - Query API (SQL-Like + Relational API)
  - Migrations (`drizzle-kit`)
  - Relationships (One-to-One, One-to-Many, Many-to-Many)
  - Prepared Statements
  - Drizzle vs Kysely (When to Use What)
- **Prisma (Popular — Schema-First)**
  - `schema.prisma` (Declarative Schema Definition)
  - Prisma Client (Auto-Generated, Fully Typed)
  - Prisma Migrate (Schema Migrations)
  - Relationships and Nested Queries
  - Prisma vs Drizzle (Trade-offs: DX vs SQL Control vs Performance)
  - N+1 Problem and `include` / `select`
  - Awareness of Prisma Overhead (Query Engine Process)
- **TypeORM (Legacy — Know Why to Move Away)**
  - Decorator-Based Entity Definition
  - Active Record vs Data Mapper Pattern
  - Why TypeORM Is Losing Favor (Type Safety Gaps, Maintenance)

### 📦 Module 8.6: Database Migrations
- Why Migrations Matter (Schema Evolution Over Time)
- Migration Strategies
  - Kysely Migrator
  - Drizzle Kit (`drizzle-kit generate`, `drizzle-kit migrate`)
  - Prisma Migrate
  - Raw SQL Migrations (`dbmate`, `graphile-migrate`)
- Zero-Downtime Migration Patterns (Expand/Contract)
- Data Migrations (Not Just Schema)
- Testing Migrations
- Running Migrations in CI/CD

### 📦 Module 8.7: NoSQL & Distributed Data Concepts
- NoSQL Categories (Document, Key-Value, Column-Family, Graph, Time-Series)
- When to Use SQL vs NoSQL
- CAP Theorem and PACELC
- **Redis with TypeScript**
  - `ioredis` (Preferred Redis Client)
  - Key-Value Operations, Data Structures (List, Set, Hash, Sorted Set)
  - Pub/Sub
  - Caching Patterns (Cache-Aside)
  - TTL and Expiration
- **MongoDB with TypeScript (Awareness)**
  - `mongodb` Driver (Native)
  - Mongoose (ODM — Schema Validation at Runtime)
  - Type Safety Challenges with MongoDB
- Polyglot Persistence Concepts

> ### 🛠 Phase 8 Milestone Project: **Blog Engine Database Layer**
> Build a complete database layer for a blog: Users, Posts, Comments, Tags, Categories. Use Kysely or Drizzle with PostgreSQL, fully typed schema, migrations, complex queries (joins, CTEs, window functions), `EXPLAIN ANALYZE` for optimization, Redis caching (ioredis) for hot posts, connection pooling tuning, and transaction management. Benchmark query performance.

---

## 🔷 PHASE 9: Networking, Infrastructure & Operations
> **Goal:** Understand networking, operating systems, containerization, and infrastructure fundamentals.

### 📦 Module 9.1: Networking Essentials
- OSI Model and TCP/IP Stack
- DNS Resolution
- HTTP/HTTPS Protocol Deep Dive (Methods, Headers, Status Codes)
- TLS/SSL Handshakes and Certificates
- Load Balancers (L4 vs L7)
- CDNs and Reverse Proxies
- WebSockets (Concepts)
- gRPC and Protocol Buffers (Concepts)
- HTTP/2 and HTTP/3 (QUIC) — Awareness

### 📦 Module 9.2: TypeScript Networking
- **Node.js `net` Module**
  - TCP Client and Server
  - Socket Events (`data`, `end`, `error`, `close`)
  - Typed Socket Communication
- **Node.js `http` / `http2` Module**
  - Building a Simple HTTP Server (No Framework)
  - Request and Response Objects
  - Routing, Headers, Status Codes — Manual
- **HTTP Clients**
  - `fetch` (Built-in Node.js 18+ — Standard)
  - `undici` (High-Performance HTTP Client — Powers `fetch` in Node.js)
    - Request, Pool, Agent
    - Typed Responses
  - `axios` (Legacy — Know But Prefer `fetch`/`undici`)
- **REST Principles and HTTP Semantics**

### 📦 Module 9.3: Operating Systems & Linux Fundamentals
- Linux Basics (File System, Permissions, Users)
- Essential Commands (Navigation, File Manipulation, Process Management)
- Package Management (apt, yum)
- Shell Scripting Basics
- Processes, Signals, and Systemd
- Environment Variables and Configuration
- SSH and Remote Access
- Node.js Process Management (`process` Object, Signals, Exit Codes)

### 📦 Module 9.4: Containers & Docker
- Virtual Machines vs Containers
- Docker Fundamentals (Images, Containers, Layers)
- Writing Dockerfiles for Node.js/TypeScript Applications
  - Choosing Base Images (`node:20-slim`, `node:20-alpine`)
  - Multi-Stage Builds (Build Stage with `tsc` → Runtime Stage with Just JS)
  - `.dockerignore` for Node.js (`node_modules`, `.git`, `dist`, etc.)
  - Installing Dependencies (Copy `package.json` + Lock File First for Layer Caching)
  - Non-Root User (`node` User)
  - `NODE_ENV=production` (Skip devDependencies)
  - Health Checks
- Docker Networking (Bridge, Host, Custom Networks)
- Docker Volumes (Persistent Data)
- Docker Compose (Multi-Container Applications)
- Dockerizing a TypeScript Application
  - Build Stage Compiles TypeScript → Runtime Stage Runs JavaScript
  - Source Map Handling in Containers
- Docker Best Practices (Layer Caching, Image Size Optimization, Security)

### 📦 Module 9.5: Container Orchestration Basics
- Why Orchestration (Problems Docker Alone Doesn't Solve)
- Kubernetes Core Concepts (Pods, Services, Deployments, Namespaces)
- `kubectl` Basics
- YAML Manifests (Awareness)
- ConfigMaps and Secrets (Awareness)
- Kubernetes vs Docker Compose — When to Use What

> ### 🛠 Phase 9 Milestone Project: **Containerized TypeScript WebSocket Chat Server**
> Build a multi-room chat server using Node.js `ws` library with TypeScript. Type-safe message protocol using discriminated unions and Zod validation. Dockerize with a multi-stage Dockerfile (TypeScript build stage → Node.js runtime stage). Docker Compose with the chat server + Redis (for pub/sub across instances and message persistence) + PostgreSQL (for user accounts and chat history). Structured logging with `pino`. Health check endpoints. Deploy locally with Docker Compose.

---

## 🏗️ CAPSTONE PROJECT: Production-Grade URL Shortener
> **This is the Phase 1 capstone that ties everything together.**
>
> Build a URL shortener service (like bit.ly) with:
> - **Clean TypeScript code** applying SOLID principles and design patterns (strict mode, no `any`)
> - **RESTful API** with proper HTTP semantics and error handling (using Node.js `http` module or lightweight framework — Hono or Fastify with no magic)
> - **Zod** for all request validation and response schemas
> - **PostgreSQL** with proper schema design, normalization, and indexing (Kysely or Drizzle — fully type-safe)
> - **Redis** caching layer for hot URLs (ioredis)
> - **Database migrations** (Drizzle Kit or Kysely Migrator)
> - **Docker** containerization with docker-compose (app + PostgreSQL + Redis)
> - **Multi-stage Dockerfile** (TypeScript build → Node.js runtime)
> - **Comprehensive test suite** (Vitest: unit + integration with Testcontainers, TDD approach, greater than 85% coverage)
> - **CI/CD pipeline** (GitHub Actions: lint → type-check → test → docker build → push)
> - **Structured logging** with `pino` and health check endpoints
> - **Git** with proper branching strategy and semantic versioning
> - Architecture documented with decision rationale
> - Strict `tsconfig.json` with all strict options enabled
>
> **Why:** Small enough to finish, complex enough to demonstrate all Phase 1 skills — clean code, design patterns, testing, databases, Docker, CI/CD, networking, and infrastructure. All type-safe, end to end.

---

## ✅ After Completing This Roadmap — You Can:
- Write clean, testable, maintainable, strictly-typed TypeScript code
- Leverage TypeScript's advanced type system (generics, conditional types, mapped types, template literals)
- Apply appropriate design patterns with justification
- Understand Node.js internals (V8, event loop, libuv, memory management)
- Master async programming (Promises, async/await, event loop, Worker Threads)
- Apply functional and reactive programming patterns
- Solve DSA problems confidently in TypeScript
- Design normalized/denormalized data models
- Work fluently with SQL, type-safe query builders, and ORMs
- Understand NoSQL concepts and CAP theorem
- Validate runtime data with Zod (bridging compile-time and runtime type safety)
- Explain networking and infrastructure fundamentals
- Containerize applications with Docker and Docker Compose
- Set up CI/CD pipelines with GitHub Actions
- Use Git professionally with proper branching strategies
- Write comprehensive tests (unit, integration, TDD)
- **You are fully ready for Phase 2: NestJS / Fastify & Architectural Thinking**

---

## 📋 Quick Reference Summary

