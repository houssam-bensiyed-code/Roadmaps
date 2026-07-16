# 🐹 Go (Golang) Mastery Roadmap — Phase 1: Foundations
> Aligned with Phase 1 of the Software Engineering Mastery Roadmap
> **Estimated Duration: 4–6 months**

---

## 🟢 PHASE 1: Foundation & Core Basics
> **Goal:** Understand how Go works and write basic programs.

### 📦 Module 1.1: Introduction to Go
- What is Go & Why Learn It
- Go's Philosophy (Simplicity, Readability, Concurrency, Composition)
- History (Created at Google — Rob Pike, Ken Thompson, Robert Griesemer)
- Go vs Other Languages (When Go Wins, When It Doesn't)
  - Go vs Java (Simplicity, Compilation Speed, Concurrency Model)
  - Go vs Python (Performance, Static Typing, Deployment)
  - Go vs Rust (Simplicity vs Zero-Cost Abstractions, GC vs Ownership)
  - Go vs Node.js (Goroutines vs Event Loop, Static Typing)
- How Go Code Executes (Compilation → Single Binary — No Runtime Dependencies)
- Go Toolchain (`go build`, `go run`, `go fmt`, `go vet`, `go doc`)
- Installing Go & Setting Up IDE (VS Code + Go Extension / GoLand)
- Writing Your First "Hello World" Program
- `go.mod` & Module System (Project Initialization)
- Go Playground (Online Experimentation)
- The Go Specification (Learning to Read It)

### 📦 Module 1.2: Go Syntax & Basics
- **Variables & Declarations**
  - `var` Declaration (Explicit Type)
  - Short Variable Declaration (`:=` — Type Inference)
  - Multiple Variable Declaration
  - Zero Values (Every Type Has a Default — `0`, `""`, `false`, `nil`)
  - Constants (`const`, Typed vs Untyped Constants)
  - `iota` (Constant Generator)
  - Naming Conventions (camelCase, Exported = Uppercase First Letter)
- **Basic Types**
  - Integers (`int`, `int8`, `int16`, `int32`, `int64`, `uint`, `uint8`/`byte`, `uint16`, `uint32`, `uint64`)
  - Floating Point (`float32`, `float64`)
  - Complex Numbers (`complex64`, `complex128`)
  - Boolean (`bool`)
  - String (`string` — Immutable Byte Sequence, UTF-8)
  - Rune (`rune` — Alias for `int32`, Represents Unicode Code Point)
  - Byte (`byte` — Alias for `uint8`)
- **Type System Fundamentals**
  - Static Typing (Types Checked at Compile Time)
  - Type Inference (`:=` Infers Type from Right Side)
  - Type Conversion (Explicit — `int(x)`, `float64(y)` — No Implicit Conversion)
  - Type Aliases (`type Celsius float64`)
  - Defined Types vs Type Aliases (`type ID = int` vs `type ID int`)
- **Operators**
  - Arithmetic, Comparison, Logical, Bitwise, Assignment
  - No Ternary Operator (Use `if/else` — Go Is Explicit)
  - Pointer Operators (`&` Address-Of, `*` Dereference)
- **Strings**
  - String Literals (Double Quotes `"..."`, Raw Strings Backticks `` `...` ``)
  - String Immutability (Strings Cannot Be Modified In-Place)
  - `strings` Package (`Contains`, `HasPrefix`, `HasSuffix`, `Join`, `Split`, `Replace`, `ToUpper`, `ToLower`, `TrimSpace`, `Index`)
  - `strconv` Package (String ↔ Number Conversion)
  - Rune Iteration (`for _, r := range s`)
  - `fmt` Package (`Sprintf`, `Printf`, `Fprintf`, Verb Formatting `%s`, `%d`, `%v`, `%+v`, `%#v`, `%T`)
  - `strings.Builder` (Efficient String Concatenation)
  - Byte Slices vs Strings (`[]byte(s)`, `string(b)`)
- **Console I/O**
  - `fmt.Println`, `fmt.Printf`, `fmt.Sprintf`
  - `fmt.Scan`, `fmt.Scanf`, `fmt.Scanln`
  - `bufio.Scanner` (Read Lines from Stdin)
  - `os.Args` (Command-Line Arguments)

### 📦 Module 1.3: Control Flow
- `if`, `else if`, `else`
- `if` with Short Statement (`if err := doSomething(); err != nil { ... }`)
- `switch` Statement
  - Expression Switch (No `break` Needed — Implicit)
  - `fallthrough` (Explicit Fall-Through — Rare)
  - Type Switch (`switch v := x.(type) { ... }`)
  - Tagless Switch (Replace Long If/Else Chains)
- `for` Loop (Go's Only Loop Keyword)
  - Traditional `for i := 0; i < n; i++ { ... }`
  - While-Style `for condition { ... }`
  - Infinite Loop `for { ... }`
  - `for range` (Iterate Slices, Maps, Strings, Channels)
  - `break`, `continue`
  - Labelled Loops and `break`/`continue` with Labels
- `goto` (Exists — Almost Never Used)
- No `while`, No `do-while` (Just `for`)

### 📦 Module 1.4: Composite Types — Arrays, Slices, Maps
- **Arrays**
  - Fixed-Length (`[5]int`)
  - Value Type (Arrays Are Copied on Assignment)
  - Array Comparison (Arrays Are Comparable if Element Type Is)
  - Multi-Dimensional Arrays
  - When to Use Arrays (Rarely — Prefer Slices)
- **Slices**
  - Slice Declaration (`[]int`, `make([]int, len, cap)`)
  - Slice Internals (Pointer + Length + Capacity — Reference to Underlying Array)
  - Slice Operations (`append`, Slicing `s[low:high:max]`, `copy`)
  - Nil Slices vs Empty Slices
  - Slice Growth Strategy (How `append` Reallocates)
  - `slices` Package (Go 1.21+ — `Sort`, `Contains`, `Index`, `Compact`, `Equal`)
  - Common Slice Patterns (Filter, Map, Reduce — Manual Implementations)
  - Slice Gotchas (Shared Underlying Array, Memory Leaks from Large Slice References)
- **Maps**
  - Map Declaration (`map[string]int`, `make(map[string]int)`)
  - Map Operations (Insert, Lookup, Delete, Iteration, Length)
  - Comma-Ok Idiom (`val, ok := m[key]`)
  - Nil Maps vs Initialized Maps (Nil Map Panics on Write)
  - Map Iteration Order (Random — Not Deterministic)
  - `maps` Package (Go 1.21+ — `Keys`, `Values`, `Equal`, `Clone`)
  - Maps Are Not Safe for Concurrent Access (Preview — `sync.Map`)
- **Structs**
  - Struct Declaration and Initialization
  - Named Fields vs Anonymous Fields
  - Struct Literals (`Point{X: 1, Y: 2}`, `Point{1, 2}`)
  - Zero Value of Struct (All Fields Zero-Valued)
  - Struct Comparison (Comparable if All Fields Are Comparable)
  - Exported vs Unexported Fields (Uppercase vs Lowercase)
  - Struct Tags (`json:"name"`, `db:"column"` — Metadata for Reflection)
  - Anonymous Structs (Inline, One-Off Use)
  - Struct Embedding (Composition — Preview)

### 📦 Module 1.5: Functions
- Function Declaration (`func name(params) returnType { ... }`)
- Multiple Return Values (`func divide(a, b int) (int, error)`)
- Named Return Values (Document Intent — Use Sparingly)
- Variadic Functions (`func sum(nums ...int) int`)
- First-Class Functions (Functions as Values, Assigned to Variables)
- Anonymous Functions (Function Literals / Closures)
- Closures (Functions Capture Outer Scope Variables)
- Higher-Order Functions (Functions That Accept/Return Functions)
- `defer` Statement
  - Deferred Function Calls (Execute When Surrounding Function Returns)
  - LIFO Order (Last Deferred = First Executed)
  - `defer` with Closures (Capture Current Variable Values — Gotcha)
  - Use Cases: Resource Cleanup, Unlocking Mutexes, Closing Files
- `init()` Function (Package Initialization — Runs Before `main`)
- Recursion Basics
- Function Type Declarations (`type Handler func(w http.ResponseWriter, r *http.Request)`)

### 📦 Module 1.6: Pointers
- What Are Pointers (Variables That Store Memory Addresses)
- `&` (Address-Of Operator) and `*` (Dereference Operator)
- Pointer Types (`*int`, `*string`, `*MyStruct`)
- `new()` Function (Allocate Memory, Return Pointer)
- Nil Pointers (Zero Value of Pointer Is `nil`)
- Pointers vs Values (When to Use Pointers)
  - Mutability (Modify Caller's Data — Use Pointer)
  - Large Structs (Avoid Copy — Use Pointer)
  - Optional Values (Nil Pointer Means Absent)
  - Interface Satisfaction (Pointer Receivers)
- No Pointer Arithmetic (Unlike C — Safety)
- Pointer Receivers vs Value Receivers (Preview — Covered in OOP Phase)

> ### 🛠 Phase 1 Milestone Project: **CLI-Based Expense Tracker**
> Build a CLI expense tracker: add expenses with category/amount/date, list expenses with filtering, calculate totals by category, save/load from JSON file. Use structs for data modeling, slices and maps for storage, proper error handling with multiple returns, `defer` for file cleanup, and `fmt`/`bufio` for I/O.

---

## 🔵 PHASE 2: Go's "OOP" — Interfaces, Composition & Methods
> **Goal:** Master Go's approach to object-oriented design — structs, methods, interfaces, and composition instead of class hierarchies.

### 📦 Module 2.1: Methods
- Methods on Structs (`func (r Receiver) MethodName() { ... }`)
- Value Receivers vs Pointer Receivers
  - Value Receiver (Method Gets Copy — Cannot Modify Original)
  - Pointer Receiver (Method Gets Pointer — Can Modify Original)
  - When to Use Which (Consistency Rule — If One Method Needs Pointer, All Should Use Pointer)
- Method Sets (Which Methods a Type Has — Determines Interface Satisfaction)
  - Value Type: Value Receiver Methods
  - Pointer Type: Both Value and Pointer Receiver Methods
- Methods on Non-Struct Types (`type Celsius float64` → Methods on `Celsius`)
- Methods Cannot Be Defined on Types from Other Packages

### 📦 Module 2.2: Interfaces
- Interface Declaration (`type Reader interface { Read(p []byte) (n int, err error) }`)
- Implicit Implementation (No `implements` Keyword — If Type Has Methods, It Satisfies Interface)
  - **💡 This is Go's most powerful feature — Structural Typing for Interfaces**
- Empty Interface (`interface{}` / `any` — Accepts Any Type)
  - `any` (Go 1.18+ Alias for `interface{}`)
  - When to Use `any` (Rarely — Lose Type Safety)
- Interface Values (Two-Word Data: Type + Value)
  - Nil Interface vs Interface Holding Nil Value (Subtle Difference — Common Bug)
- Type Assertion (`val, ok := i.(ConcreteType)`)
- Type Switch (`switch v := i.(type) { case string: ... }`)
- Interface Composition (Embedding Interfaces)
  - `io.ReadWriter` = `io.Reader` + `io.Writer`
  - Small, Focused Interfaces (Go Proverb: "The bigger the interface, the weaker the abstraction")
- Standard Library Interfaces (Know These — They're Everywhere)
  - `fmt.Stringer` (`String() string` — Like `toString()`)
  - `error` (`Error() string`)
  - `io.Reader`, `io.Writer`, `io.Closer`, `io.ReadWriter`, `io.ReadCloser`
  - `sort.Interface` (`Len`, `Less`, `Swap`)
  - `json.Marshaler`, `json.Unmarshaler`
  - `http.Handler` (`ServeHTTP(w, r)`)
- Interface Design Guidelines
  - Accept Interfaces, Return Concrete Types
  - Keep Interfaces Small (1-3 Methods)
  - Define Interfaces at Consumer Side, Not Provider Side
  - Don't Create Interfaces Prematurely

### 📦 Module 2.3: Composition & Embedding
- Struct Embedding (Go's Alternative to Inheritance)
  - Embedded Structs (Promoted Fields and Methods)
  - Anonymous Fields
  - Method Promotion (Embedded Type's Methods Are Promoted to Outer Type)
  - Shadowing (Outer Type Can Override Embedded Methods)
- Interface Embedding (Compose Interfaces from Smaller Interfaces)
- Composition Over Inheritance
  - Go Has No Classes, No Inheritance (By Design)
  - Build Complex Types by Composing Simple Types
  - Delegation vs Inheritance Mental Model
- Embedding vs Named Fields (When Each Is Appropriate)
- Embedding Interfaces in Structs (Implement Part of Interface, Delegate Rest)

### 📦 Module 2.4: Encapsulation & Visibility
- Exported vs Unexported (Uppercase = Public, Lowercase = Package-Private)
- Package-Level Encapsulation (No Private/Protected/Public Keywords)
- Unexported Fields in Exported Structs (Common Pattern)
- Constructor Functions (`func NewUser(name string) *User`)
  - No Constructors — Use Factory Functions
  - Returning Pointer vs Value from Constructor
- Getter/Setter Conventions
  - Getter: `Name()` (Not `GetName()`)
  - Setter: `SetName(n string)` (Use Only When Necessary)
- Information Hiding with Unexported Types

### 📦 Module 2.5: Polymorphism in Go
- Interface-Based Polymorphism (Multiple Types Implementing Same Interface)
- Duck Typing at Compile Time (If It Has the Methods, It Fits)
- No Method Overloading (Use Different Names or Variadic/Options)
- No Method Overriding (Use Embedding + Shadowing)
- No Generics for Polymorphism (Before Go 1.18 — Use Interfaces)
- Functional Polymorphism (Functions as Strategy — Common in Go)

### 📦 Module 2.6: Other OOP Concepts in Go
- Association, Aggregation, Composition (Via Struct Fields and Embedding)
- Enums in Go
  - `iota` + Custom Type (`type Status int` with `const (...)`)
  - String Representation (`String()` Method on Enum Type)
  - Enum Validation
  - No Built-In Enum Type (Common Pattern with `iota`)
- Functional Options Pattern (Idiomatic Constructor with Options)
  - `type Option func(*Config)`
  - `func WithTimeout(d time.Duration) Option`
  - `func NewServer(opts ...Option) *Server`
- Builder Pattern (When Functional Options Don't Fit)

> ### 🛠 Phase 2 Milestone Project: **Shape Calculator with Plugin System**
> Build a geometry calculator: `Shape` interface with `Area()` and `Perimeter()`. Concrete types: `Circle`, `Rectangle`, `Triangle`. Composition via struct embedding for extended shapes. Factory functions for creation. Functional options pattern for configuration. Plugin system using interface-based polymorphism (register shape calculators at runtime). Demonstrate Go's composition model.

---

## 🟡 PHASE 3: Core Go Essentials
> **Goal:** Master essential packages, error handling, generics, modules, and I/O.

### 📦 Module 3.1: Error Handling — Go's Way
- **Error Philosophy (Errors Are Values, Not Exceptions)**
  - No Try/Catch — Errors Are Returned As Values
  - `error` Interface (`Error() string`)
  - The `if err != nil` Pattern (Ubiquitous — Embrace It)
  - Why Go Chose This (Explicit Error Handling, No Hidden Control Flow)
- **Creating Errors**
  - `errors.New("message")` (Simple Error)
  - `fmt.Errorf("message: %w", err)` (Formatted Error with Wrapping)
  - Custom Error Types (Structs Implementing `error` Interface)
    - Add Context (Error Code, HTTP Status, Field Name)
    - `Unwrap() error` Method (For Error Chain)
- **Error Wrapping & Unwrapping**
  - `%w` Verb in `fmt.Errorf` (Wrap Error — Preserve Chain)
  - `errors.Is(err, target)` (Check If Error In Chain Matches Target)
  - `errors.As(err, &target)` (Extract Specific Error Type from Chain)
  - `errors.Unwrap(err)` (Get Wrapped Error)
  - Error Chain (Wrapping Adds Context at Each Level)
- **Sentinel Errors**
  - `var ErrNotFound = errors.New("not found")`
  - Convention: `Err` Prefix
  - Standard Library Sentinels (`io.EOF`, `sql.ErrNoRows`, `context.Canceled`)
  - When to Define Sentinel Errors
- **Error Handling Patterns**
  - Early Return (Handle Error, Return — Happy Path Left-Aligned)
  - Error Wrapping at Each Layer (Add Context As Error Bubbles Up)
  - Domain Errors vs Infrastructure Errors (Separation)
  - Error Logging (Log at Top Level, Not at Every Level)
- **Panic & Recover**
  - `panic()` (Unrecoverable Errors — Program Bug, Not User Error)
  - `recover()` (Catch Panic — Only in Deferred Functions)
  - When to Panic (Programmer Errors: Invalid Arguments, Missing Config)
  - When NOT to Panic (Almost Always — Return Errors Instead)
  - Panics in Libraries (Libraries Should Return Errors, Not Panic)

### 📦 Module 3.2: Packages & Modules
- **Packages**
  - Package Declaration (`package main`, `package user`)
  - One Package Per Directory
  - Package Naming Conventions (Short, Lowercase, No Underscores)
    - `user`, not `userService`, not `user_service`
  - `main` Package (Entry Point — `func main()`)
  - Package Initialization (`init()` Functions — Run Order)
  - Internal Packages (`internal/` — Unexported to Outside Module)
  - `_test` Package Suffix (Black-Box Testing)
- **Modules**
  - `go.mod` (Module Definition — Module Path, Go Version, Dependencies)
  - `go.sum` (Dependency Checksums — Lock File)
  - `go mod init` (Create Module)
  - `go mod tidy` (Add Missing, Remove Unused Dependencies)
  - `go get` (Add Dependencies)
  - Module Path (Import Path = Module Path + Package Path)
  - Semantic Import Versioning (`v2`, `v3` — Major Version in Path)
  - Replace and Exclude Directives
  - Private Modules (GOPRIVATE, GONOSUMCHECK)
  - Vendoring (`go mod vendor` — Copy Dependencies Locally)
  - Workspace Mode (`go.work` — Multi-Module Development)

### 📦 Module 3.3: Generics (Go 1.18+)
- Why Generics (Type-Safe Reusable Code Without `interface{}`)
- Type Parameters (`func Map[T, U any](s []T, f func(T) U) []U`)
- Type Constraints
  - `any` (No Constraint — Accepts Everything)
  - `comparable` (Types That Support `==` and `!=`)
  - Custom Constraints (Interface with Type Elements)
  - `constraints` Package (Awareness — `Ordered`, `Signed`, `Unsigned`)
- Type Inference (Go Infers Type Parameters from Arguments)
- Generic Functions
- Generic Types (Generic Structs — `type Stack[T any] struct { ... }`)
- Generic Interfaces
- Type Sets (Union Types in Constraints — `~int | ~float64`)
  - `~` Tilde (Underlying Type — Includes Custom Types Based On)
- When to Use Generics vs Interfaces
  - Generics: Collections, Algorithms, Type-Safe Containers
  - Interfaces: Behavioral Abstraction, Dependency Injection
  - Don't Overuse Generics (Go Proverb: "A little copying is better than a little dependency")

### 📦 Module 3.4: Standard Library Deep Dive — Collections & Utilities
- **`sort` Package**
  - `sort.Ints()`, `sort.Strings()`, `sort.Float64s()`
  - `sort.Slice()` (Custom Sort Function)
  - `sort.Search()` (Binary Search)
  - `slices` Package (Go 1.21+ — Modern Alternative)
    - `slices.Sort()`, `slices.SortFunc()`
    - `slices.Contains()`, `slices.Index()`
    - `slices.Compact()`, `slices.Equal()`
- **`maps` Package (Go 1.21+)**
  - `maps.Keys()`, `maps.Values()`
  - `maps.Clone()`, `maps.Equal()`
  - `maps.DeleteFunc()`
- **`math` Package**
  - `math.Max()`, `math.Min()`, `math.Abs()`, `math.Sqrt()`, `math.Pow()`
  - `math/rand` (Pseudo-Random — `rand.Intn`, `rand.Float64`)
  - `crypto/rand` (Cryptographically Secure Random)
- **`time` Package**
  - `time.Now()`, `time.Since()`, `time.Until()`
  - `time.Duration` (Nanoseconds, Milliseconds, Seconds)
  - `time.Parse()`, `time.Format()` (Reference Time: `2006-01-02 15:04:05`)
  - `time.Sleep()`, `time.After()`, `time.Tick()`
  - `time.Timer`, `time.Ticker`
  - Timezones (`time.LoadLocation`, `time.UTC`, `time.Local`)
- **`regexp` Package**
  - `regexp.Compile()`, `regexp.MustCompile()`
  - `FindString`, `FindAllString`, `MatchString`
  - `ReplaceAllString`
  - Named Groups
- **`unicode` and `unicode/utf8` Packages**
  - `utf8.RuneCountInString()` (String Length in Runes vs Bytes)
  - `unicode.IsLetter()`, `unicode.IsDigit()`, `unicode.IsSpace()`

### 📦 Module 3.5: File I/O & Data Formats
- **`os` Package**
  - `os.Open()`, `os.Create()`, `os.OpenFile()` (Flags and Permissions)
  - `os.ReadFile()`, `os.WriteFile()` (Simple Whole-File I/O)
  - `os.Mkdir()`, `os.MkdirAll()`, `os.Remove()`, `os.Rename()`
  - `os.Stat()`, `os.IsNotExist()`
  - `os.Getenv()`, `os.Setenv()` (Environment Variables)
  - `os.Exit()`, `os.Getwd()`
  - `os.Stdin`, `os.Stdout`, `os.Stderr`
  - `defer file.Close()` (Always Close Files)
- **`io` Package**
  - `io.Reader`, `io.Writer` Interfaces (Foundation of All I/O)
  - `io.Copy()`, `io.ReadAll()`
  - `io.TeeReader`, `io.MultiWriter`, `io.LimitReader`
  - `io.Pipe()` (Connected Reader/Writer)
  - `io.NopCloser()` (Wrap Reader as ReadCloser)
- **`bufio` Package**
  - `bufio.Scanner` (Line-by-Line Reading)
  - `bufio.Reader` (Buffered Reading)
  - `bufio.Writer` (Buffered Writing — `Flush()`)
- **`encoding/json` Package**
  - `json.Marshal()`, `json.Unmarshal()` (Struct ↔ JSON)
  - `json.NewEncoder()`, `json.NewDecoder()` (Stream-Based)
  - Struct Tags (`json:"name"`, `json:"name,omitempty"`, `json:"-"`)
  - Custom `MarshalJSON()` / `UnmarshalJSON()` (Custom Serialization)
  - `json.RawMessage` (Delay Parsing)
  - `map[string]interface{}` for Dynamic JSON (Use `any` in Go 1.18+)
- **Other Data Formats**
  - `encoding/csv` (CSV Read/Write)
  - `encoding/xml` (XML — Awareness)
  - YAML (`gopkg.in/yaml.v3` — Third-Party)
  - TOML (`github.com/BurntSushi/toml` — Third-Party)
  - Protocol Buffers (Awareness — Covered in Phase 2)
- **`path/filepath` Package**
  - `filepath.Join()`, `filepath.Abs()`, `filepath.Dir()`, `filepath.Base()`, `filepath.Ext()`
  - `filepath.Walk()` / `filepath.WalkDir()` (Traverse Directory Tree)
  - `filepath.Glob()` (Pattern Matching)
- **Embedded Files (`embed` Package — Go 1.16+)**
  - `//go:embed` Directive (Embed Files in Binary)
  - Embedding Single Files, Directories
  - Use Cases: Static Assets, Config Files, Templates

> ### 🛠 Phase 3 Milestone Project: **Multi-Format Data Pipeline**
> Build a CLI data processing tool: read data from CSV/JSON/YAML files, transform using generics (generic `Map`, `Filter`, `Reduce` functions), validate with custom error types and error wrapping, write output in multiple formats. Use `io.Reader`/`io.Writer` interfaces for composable I/O, `embed` for default config, and proper error handling with sentinel errors and wrapping.

---

## 🟠 PHASE 4: Advanced Go Features
> **Goal:** Master concurrency (Go's superpower), context, reflection, testing patterns, and runtime internals.

### 📦 Module 4.1: Goroutines & Channels — Go's Concurrency Model
- **Goroutines**
  - What is a Goroutine (Lightweight Thread — Managed by Go Runtime, Not OS)
  - `go` Keyword (`go functionCall()`)
  - Goroutine Stack (Starts Small ~2KB, Grows Dynamically)
  - Goroutines vs OS Threads (M:N Scheduling — Many Goroutines on Few Threads)
  - Goroutine Lifecycle (Created → Running → Blocked → Terminated)
  - Main Goroutine Exits = All Goroutines Die
  - Goroutine Leaks (Started But Never Terminated — Memory Leak)
- **Channels**
  - Channel Declaration (`ch := make(chan int)`)
  - Send (`ch <- value`) and Receive (`value := <-ch`)
  - Unbuffered Channels (Synchronous — Sender Blocks Until Receiver Ready)
  - Buffered Channels (`make(chan int, 100)` — Sender Blocks When Buffer Full)
  - Channel Direction in Function Parameters (`chan<-` Send-Only, `<-chan` Receive-Only)
  - Closing Channels (`close(ch)`)
    - Receivers Get Zero Value After Close
    - `val, ok := <-ch` (Detect Closed Channel)
    - Only Sender Should Close (Never Close from Receiver Side)
  - Ranging Over Channels (`for val := range ch { ... }` — Until Closed)
  - Nil Channels (Send/Receive on Nil Channel Blocks Forever)
- **`select` Statement**
  - Multiplexing Channels (Wait on Multiple Channel Operations)
  - `default` Case (Non-Blocking Channel Operations)
  - Timeouts (`case <-time.After(5 * time.Second):`)
  - `done` Channel Pattern (Signal Goroutine Termination)
- **Channel Patterns**
  - Fan-Out (One Producer, Multiple Consumers)
  - Fan-In (Multiple Producers, One Consumer — Merge Channels)
  - Pipeline (Chain of Goroutines Connected by Channels)
  - Worker Pool (Fixed Number of Goroutines Processing From Queue)
  - Generator Pattern (Function Returns Channel of Values)
  - Semaphore Pattern (Buffered Channel to Limit Concurrency)
  - Or-Channel (Wait for First of N Channels)
  - Tee-Channel (Duplicate Channel Output)
  - Bridge-Channel (Flatten Channel of Channels)

### 📦 Module 4.2: Synchronization Primitives
- **`sync` Package**
  - `sync.Mutex` (Mutual Exclusion Lock)
    - `Lock()`, `Unlock()`
    - Always `defer mu.Unlock()` After Lock
    - Protect Shared State
  - `sync.RWMutex` (Read-Write Lock)
    - `RLock()`, `RUnlock()` (Multiple Concurrent Readers)
    - `Lock()`, `Unlock()` (Exclusive Writer)
    - When RWMutex Outperforms Mutex
  - `sync.WaitGroup` (Wait for Goroutine Completion)
    - `Add()`, `Done()`, `Wait()`
    - Common Pattern: Launch N Goroutines, Wait for All
  - `sync.Once` (Execute Function Exactly Once — Thread-Safe)
    - Lazy Initialization Pattern
    - Singleton Pattern
  - `sync.Map` (Concurrent Map — Thread-Safe)
    - `Store()`, `Load()`, `Delete()`, `Range()`
    - When `sync.Map` vs `map` + `Mutex`
  - `sync.Pool` (Object Pool — Reuse Temporary Objects)
    - Reduce GC Pressure
    - Use Cases: Buffer Pools, Connection Pools
  - `sync.Cond` (Condition Variable — Advanced, Rare)
- **`sync/atomic` Package**
  - Atomic Operations (`AddInt64`, `LoadInt64`, `StoreInt64`, `CompareAndSwapInt64`)
  - `atomic.Value` (Thread-Safe Value Storage)
  - When Atomic vs Mutex (Simple Counters/Flags → Atomic, Complex State → Mutex)
- **Channels vs Mutexes — When to Use Which**
  - Channels: Communication Between Goroutines, Pipeline Patterns
  - Mutexes: Protecting Shared State, Simple Synchronization
  - Go Proverb: "Don't communicate by sharing memory; share memory by communicating"
  - Pragmatic Reality: Sometimes Mutex Is Simpler Than Channel

### 📦 Module 4.3: Context Package
- **What is `context.Context` (Cancellation, Deadlines, Values Propagation)**
- **Creating Contexts**
  - `context.Background()` (Root Context — Starting Point)
  - `context.TODO()` (Placeholder — Refactor Later)
  - `context.WithCancel(parent)` (Manual Cancellation)
  - `context.WithTimeout(parent, duration)` (Auto-Cancel After Duration)
  - `context.WithDeadline(parent, time)` (Auto-Cancel at Specific Time)
  - `context.WithValue(parent, key, value)` (Store Request-Scoped Data — Use Sparingly)
  - `context.WithoutCancel(parent)` (Go 1.21+ — Detach From Parent Cancellation)
- **Context Propagation**
  - First Parameter Convention (`func DoSomething(ctx context.Context, ...) error`)
  - Pass Context Down the Call Chain (Never Store in Struct)
  - Check `ctx.Done()` Channel for Cancellation
  - `ctx.Err()` (Returns `context.Canceled` or `context.DeadlineExceeded`)
  - Select on `ctx.Done()` in Long-Running Operations
- **Context Best Practices**
  - Always Pass Context as First Parameter
  - Don't Store Context in Structs
  - Don't Pass `nil` Context (Use `context.Background()` or `context.TODO()`)
  - Use `WithValue` Only for Request-Scoped Data (Trace IDs, Auth Tokens)
  - Cancel Context When Done (Prevent Goroutine Leaks)

### 📦 Module 4.4: Advanced Concurrency Patterns
- **`errgroup` Package (`golang.org/x/sync/errgroup`)**
  - Run Goroutines with Error Propagation
  - `g.Go()` (Launch Goroutine)
  - `g.Wait()` (Wait and Return First Error)
  - Context Cancellation on Error
  - `SetLimit()` (Limit Concurrent Goroutines)
- **`semaphore` Package (`golang.org/x/sync/semaphore`)**
  - Weighted Semaphore (Limit Resource Access)
  - `Acquire()`, `Release()`
- **`singleflight` Package (`golang.org/x/sync/singleflight`)**
  - Deduplicate Concurrent Requests for Same Key
  - Use Cases: Cache Stampede Prevention, Deduplicate API Calls
- **Rate Limiting**
  - `time.Ticker` Based (Simple)
  - `golang.org/x/time/rate` Package (Token Bucket Algorithm)
  - `rate.Limiter` (`Allow()`, `Wait()`, `Reserve()`)
- **Graceful Shutdown Pattern**
  - Listen for OS Signals (`signal.NotifyContext()` or `signal.Notify()`)
  - `SIGINT`, `SIGTERM` Handling
  - Drain In-Flight Requests
  - Close Database Connections, Flush Buffers
  - Shutdown with Timeout

### 📦 Module 4.5: Reflection
- **`reflect` Package**
  - `reflect.TypeOf()` (Get Type Information)
  - `reflect.ValueOf()` (Get Value Information)
  - `reflect.Kind` (Underlying Kind — Struct, Map, Slice, etc.)
  - Inspecting Struct Fields and Tags
  - Dynamic Method Calls
  - Setting Values via Reflection (`CanSet()`, `Set()`)
- **Struct Tags and Reflection**
  - Reading Struct Tags (`reflect.StructField.Tag.Get("json")`)
  - Custom Struct Tags for Your Libraries
  - How `encoding/json` Uses Reflection (Understanding the Magic)
- **When to Use Reflection**
  - JSON/XML Marshaling (Standard Library Uses It)
  - ORM Mapping
  - Validation Libraries
  - Dependency Injection Frameworks
- **When NOT to Use Reflection**
  - Performance Cost (Reflection Is Slow)
  - Type Safety Loss (Bypasses Compile-Time Checks)
  - Complexity (Hard to Read, Debug, Maintain)
  - Prefer Generics (Go 1.18+) Over Reflection Where Possible

### 📦 Module 4.6: Go Runtime Internals
- **Go Scheduler (GMP Model)**
  - G (Goroutine), M (Machine / OS Thread), P (Processor / Logical CPU)
  - Work Stealing (Idle P Steals Goroutines from Busy P)
  - `GOMAXPROCS` (Number of Ps — Default: Number of CPU Cores)
  - Cooperative Preemption (Go 1.14+ — Asynchronous Preemption)
- **Memory Management**
  - Stack vs Heap Allocation
  - Escape Analysis (Compiler Decides Stack vs Heap — `go build -gcflags='-m'`)
  - When Variables Escape to Heap (Returned Pointers, Interface Conversions, Closures)
- **Garbage Collection**
  - Concurrent, Tri-Color Mark-and-Sweep GC
  - GC Pauses (Sub-Millisecond — Go's GC Is Very Good)
  - `GOGC` (GC Target Percentage — Default 100)
  - `GOMEMLIMIT` (Go 1.19+ — Soft Memory Limit)
  - `runtime.GC()` (Manual GC Trigger — Rarely Needed)
  - `runtime.ReadMemStats()` (Memory Statistics)
- **Memory Profiling**
  - `pprof` (Go's Built-In Profiler)
    - CPU Profile, Memory Profile, Goroutine Profile, Block Profile
    - `net/http/pprof` (HTTP-Based Profiling)
    - `go tool pprof` (Analyze Profiles)
  - `runtime.NumGoroutine()` (Detect Goroutine Leaks)
  - `runtime.MemStats` (Heap, Stack, GC Stats)
- **Build and Compilation**
  - Static Binary (Single Binary, No Dependencies)
  - Cross-Compilation (`GOOS=linux GOARCH=amd64 go build`)
  - Build Tags (`//go:build linux`, `//go:build !windows`)
  - `go build -ldflags` (Inject Version, Commit Hash at Build Time)
  - CGO (Calling C Code — Awareness, Avoid When Possible)
  - `-race` Flag (Race Condition Detector)

### 📦 Module 4.7: Code Generation & Build Tools
- `go generate` (Run Code Generation Commands)
- `stringer` Tool (Generate `String()` Methods for Enums)
- `mockgen` (Generate Mock Implementations — Testing)
- `go:embed` (Embed Files — Covered Earlier, Reinforced Here)
- `go:linkname` (Advanced — Awareness)
- Build Constraints (`//go:build`)

> ### 🛠 Phase 4 Milestone Project: **Concurrent File Processor**
> Build a concurrent file processing pipeline: watch a directory for new files, process files concurrently using worker pool pattern with goroutines and channels, apply configurable transformations (compress, encrypt, rename), track progress with channels, implement graceful shutdown on SIGINT/SIGTERM, use `context` for cancellation propagation, `errgroup` for error handling, rate limiting with `x/time/rate`, and profile memory/goroutines with `pprof`.

---

## 🔴 PHASE 5: Data Structures & Algorithms in Go
> **Goal:** Strengthen problem-solving skills using Go with proper type safety.

### 📦 Module 5.1: Complexity Analysis
- Time and Space Complexity
- Big O, Big Ω, Big Θ
- Analyzing Loops, Recursion
- Amortized Analysis Basics
- Go Built-in Complexities (Slice, Map Operations, Channel Operations)

### 📦 Module 5.2: Data Structures Implementation
- Linked Lists (Singly, Doubly, Circular) — Generic (`LinkedList[T any]`)
- Stacks and Queues (Slice-Based and Linked-List-Based)
- Hash Tables (Custom HashMap — Understanding Go's `map` Internals)
- Trees (Binary Tree, BST, AVL) — Generic Nodes
- Heaps (Min-Heap, Max-Heap — Custom + `container/heap` Interface)
- Graphs (Adjacency List and Matrix) — Generic Vertices and Edges
- Tries (Prefix Trees)
- Disjoint Set / Union-Find
- LRU Cache (Custom Implementation — `container/list` + `map`)
- Ring Buffer (`container/ring` + Custom)

### 📦 Module 5.3: Algorithms
- Sorting: Bubble, Selection, Insertion, Merge, Quick, Heap, Counting, Radix
  - Go's `sort.Slice()` and `slices.Sort()` (Pattern-Defeating Quicksort — Know What's Under the Hood)
  - Custom Comparators (`slices.SortFunc()`)
- Searching: Linear, Binary, Ternary
  - `sort.Search()`, `slices.BinarySearch()`
- Recursion and Backtracking
- Dynamic Programming (Memoization with `map`, Tabulation)
- Greedy Algorithms
- Graph Algorithms (BFS, DFS, Dijkstra, Kruskal, Prim, Topological Sort)
- Sliding Window, Two Pointers
- Bit Manipulation

> ### 🛠 Phase 5 Milestone Project: **Generic Collections Library**
> Implement generically typed `ArrayList[T]`, `LinkedList[T]`, `HashMap[K, V]`, `BST[T]`, `Graph[V, E]`, `PriorityQueue[T]` with full CRUD, iterator pattern via channels/callbacks, comprehensive unit tests with table-driven tests, and published as a Go module.

---

## 🟣 PHASE 6: Design Principles, Patterns & Clean Code
> **Goal:** Write professional, maintainable, and idiomatic Go code using proven principles and Go-specific patterns.

### 📦 Module 6.1: Idiomatic Go & Clean Code Practices
- **Go Proverbs (Rob Pike)**
  - "Don't communicate by sharing memory, share memory by communicating"
  - "The bigger the interface, the weaker the abstraction"
  - "Make the zero value useful"
  - "A little copying is better than a little dependency"
  - "Clear is better than clever"
  - "Errors are values"
  - "Don't just check errors, handle them gracefully"
- **Effective Go (Official Style Guide)**
  - Naming Conventions (Short Names, MixedCaps, Acronyms All-Caps)
  - Package Naming (Short, Lowercase, Singular)
  - Interface Naming (`-er` Suffix: `Reader`, `Writer`, `Stringer`, `Handler`)
  - Error Variable Naming (`Err` Prefix: `ErrNotFound`)
- **Code Organization**
  - Package Design (Small, Focused Packages)
  - `cmd/` (Application Entry Points)
  - `internal/` (Private Packages)
  - `pkg/` (Public Reusable Packages — Controversial, Often Unnecessary)
  - Standard Go Project Layout (Awareness — Not Official, But Common)
- **DRY, KISS, YAGNI in Go Context**
- **Code Smells and Refactoring (Go-Specific)**
  - Overusing `interface{}` / `any`
  - Giant Functions (Break Into Smaller Functions)
  - Package Cycles (Circular Imports — Go Forbids Them)
  - Overusing `init()` (Hard to Test, Implicit Side Effects)
  - Unused Exports (Unexport What's Not Needed)
- **Code Reviews Best Practices**
- **`go fmt` (Non-Negotiable — All Go Code Is Formatted the Same)**
- **`go vet` (Static Analysis — Catch Common Mistakes)**
- **`golangci-lint` (Meta-Linter — Multiple Linters Combined)**
  - Essential Linters: `errcheck`, `staticcheck`, `govet`, `gosec`, `ineffassign`, `unused`

### 📦 Module 6.2: SOLID Principles in Go (Deep Understanding)
- Single Responsibility Principle (Small Packages, Focused Functions)
- Open/Closed Principle (Extend Via Interfaces and Composition, Not Modification)
- Liskov Substitution Principle (Interface Contracts — Structural Typing Makes This Natural)
- Interface Segregation Principle (Small Interfaces — Go's Default Style)
- Dependency Inversion Principle (Depend on Interfaces, Not Concrete Types)
  - Accept Interfaces, Return Concrete Types (Go Proverb)
  - Constructor Injection (Pass Dependencies as Parameters)

### 📦 Module 6.3: Design Principles (Beyond SOLID)
- Separation of Concerns
- High Cohesion / Low Coupling
- Composition over Inheritance (Go Enforces This — No Inheritance)
- Dependency Inversion and Inversion of Control
- Law of Demeter (Principle of Least Knowledge)
- Principle of Least Astonishment
- Information Hiding (Parnas) — Via Exported/Unexported

### 📦 Module 6.4: Creational Patterns
- Singleton Pattern (`sync.Once` — Idiomatic Go Singleton)
- Factory Function Pattern (`func NewUser(name string) *User` — Most Common in Go)
- Abstract Factory Pattern (Interface-Based Factories)
- Builder Pattern (Method Chaining or Functional Options)
- Functional Options Pattern (Go-Idiomatic Alternative to Builder)
  - `type Option func(*Config)`
  - Widely Used in Go Libraries (`grpc.NewServer(opts...)`)
- Prototype Pattern (Deep Copy with `encoding/gob` or Manual)

### 📦 Module 6.5: Structural Patterns
- Adapter Pattern (Wrap Interface to Match Another)
- Bridge Pattern
- Composite Pattern
- Decorator Pattern (Wrap Functions — `http.HandlerFunc` Chain)
  - `func loggingMiddleware(next http.Handler) http.Handler`
  - Middleware Pattern Is Go's Native Decorator
- Facade Pattern
- Flyweight Pattern
- Proxy Pattern

### 📦 Module 6.6: Behavioral Patterns
- Strategy Pattern (Functions as Strategies — Most Idiomatic in Go)
  - Pass Function Parameters Instead of Strategy Interface
  - `sort.Slice(s, func(i, j int) bool { ... })` — Strategy via Function
- Observer Pattern (Channels for Event Notification)
- Command Pattern
- State Pattern
- Template Method Pattern (Embed Interface in Struct, Override Methods)
- Chain of Responsibility Pattern (Middleware Chain — `http.Handler` Wrapping)
- Mediator Pattern
- Visitor Pattern
- Iterator Pattern (Channels, Callbacks, or Go 1.23+ Range-Over-Func)

### 📦 Module 6.7: Concurrency Patterns (Go-Specific)
- Producer-Consumer Pattern (Channel-Based)
- Worker Pool Pattern (Fixed Goroutines, Shared Job Channel)
- Pipeline Pattern (Chain of Stages Connected by Channels)
- Fan-Out / Fan-In Pattern
- Publish-Subscribe Pattern (Channel-Based)
- Future/Promise Pattern (`chan Result` Returned Immediately)
- Context-Based Cancellation Pattern
- Semaphore Pattern (Buffered Channel or `sync.Semaphore`)
- Rate Limiting Pattern (`x/time/rate`)

### 📦 Module 6.8: Anti-Patterns & When NOT to Use Patterns
- Common Go Anti-Patterns
  - Premature Interfaces (Don't Create Interface Before You Have Two Implementations)
  - Java-Style Go (Excessive Abstraction, `interface{}` Everywhere, Huge Structs)
  - Goroutine Leaks (Launched But Never Terminated)
  - Channel Misuse (When Mutex Is Simpler)
  - `init()` Abuse (Implicit Side Effects)
  - Package Cycle Dependencies
  - Ignoring Errors (`_ = doSomething()`)
  - Over-Engineering with Patterns
- Pattern Selection Decision Framework
- "Keep It Simple" — Go Favors Simplicity Over Cleverness

> ### 🛠 Phase 6 Milestone Project: **Event-Driven Notification System**
> Design a notification service supporting Email, SMS, Push, and Webhook. Factory functions for notification creation. Strategy pattern via function types for delivery channels. Observer pattern via channels for event subscriptions. Middleware chain (Chain of Responsibility) for filtering/routing. Worker pool for concurrent delivery. Functional options for configuration. Apply SOLID and Go idioms throughout. Comprehensive code review checklist.

---

## ⚫ PHASE 7: Testing, Build Tools & Version Control
> **Goal:** Master Go's testing ecosystem, build tooling, and professional collaboration practices.

### 📦 Module 7.1: Unit Testing
- **Go's Built-in `testing` Package**
  - Test Functions (`func TestXxx(t *testing.T)`)
  - `t.Run()` (Subtests — Organize and Name Tests)
  - `t.Fatal()`, `t.Fatalf()` (Stop Test on Failure)
  - `t.Error()`, `t.Errorf()` (Report Failure, Continue)
  - `t.Skip()`, `t.Skipf()` (Skip Test Conditionally)
  - `t.Log()`, `t.Logf()` (Log in Tests — Visible with `-v`)
  - `t.Parallel()` (Run Test in Parallel)
  - `t.Helper()` (Mark Function as Test Helper — Better Stack Traces)
  - `t.Cleanup()` (Register Cleanup Function)
- **Table-Driven Tests (Go's Signature Testing Pattern)**
  - Slice of Test Cases (Name, Input, Expected Output)
  - Loop with `t.Run()` (One Subtest Per Case)
  - Why Table-Driven (Readable, Easy to Add Cases, Covers Edge Cases)
- **Test Fixtures**
  - `testdata/` Directory (Convention for Test Files)
  - `TestMain(m *testing.M)` (Setup/Teardown for Entire Test Package)
  - `t.TempDir()` (Automatic Temporary Directory — Cleaned Up After Test)
- **Mocking**
  - Interface-Based Mocking (Go's Primary Mock Strategy)
    - Define Interface → Create Mock Struct → Implement Methods
    - No Framework Needed (Interfaces + Manual Mocks)
  - `mockgen` (Auto-Generate Mocks from Interfaces — `go.uber.org/mock`)
  - `testify/mock` (Assertion + Mocking Library)
  - Fake Implementations vs Mocks vs Stubs (Distinctions)
  - Table-Driven Tests with Mocked Dependencies
- **Assertions**
  - Standard Library (No Built-in Assertion Library — Use `if` + `t.Errorf`)
  - `testify/assert` (Popular Third-Party — `Equal`, `NoError`, `Contains`, `Len`)
  - `testify/require` (Same as Assert But Fatal on Failure)
  - When to Use Standard vs testify (Team Preference)
- **Test Coverage**
  - `go test -cover` (Show Coverage Percentage)
  - `go test -coverprofile=coverage.out` (Generate Coverage Profile)
  - `go tool cover -html=coverage.out` (Visualize Coverage)
  - Coverage Metrics and Their Limitations
- **TDD (Test-Driven Development)**
  - Red/Green/Refactor in Go
  - Writing Test First, Then Implementation
  - When TDD Helps vs When It Doesn't
- **Golden Files**
  - Compare Output Against Known-Good File
  - Update Flag (`-update` Custom Flag to Regenerate Golden Files)
  - Use Cases: CLI Output, Serialized Data, Generated Code

### 📦 Module 7.2: Integration Testing & Advanced Testing
- **Integration Testing Strategies**
  - Build Tags for Integration Tests (`//go:build integration`)
  - Separate Test Commands (`go test -tags=integration`)
  - Real Database Tests (Docker-Based)
- **Testcontainers for Go (`testcontainers-go`)**
  - PostgreSQL, Redis, MongoDB, Kafka Containers
  - Container Lifecycle in Tests
  - Shared Container Strategy (Package-Level `TestMain`)
- **BDD (Behavior-Driven Development)**
  - `godog` (Cucumber for Go — Gherkin Syntax)
  - `goblin` (BDD-Style Test Framework — Awareness)
- **Test Pyramid (Unit → Integration → E2E)**
- **Testing Anti-Patterns**
  - Testing Implementation Instead of Behavior
  - Over-Mocking (Test Doesn't Test Anything Real)
  - Flaky Tests (Race Conditions in Tests)
- **Property-Based Testing**
  - `testing/quick` (Built-In — Basic)
  - `gopter` (Third-Party — More Powerful)
  - `rapid` (Modern Property Testing)
- **Race Detector**
  - `go test -race` (Detect Data Races)
  - Always Run with `-race` in CI
  - Understanding Race Detector Output
- **Fuzzing (Go 1.18+)**
  - `func FuzzXxx(f *testing.F)` (Built-In Fuzz Testing)
  - `f.Add()` (Seed Corpus)
  - `f.Fuzz()` (Fuzz Function)
  - Corpus Management
  - Finding Edge Cases Automatically
- **Benchmarks**
  - `func BenchmarkXxx(b *testing.B)` (Built-In Benchmarking)
  - `b.N` (Number of Iterations — Adjusted Automatically)
  - `b.ResetTimer()`, `b.StopTimer()`, `b.StartTimer()`
  - `go test -bench=. -benchmem` (Include Memory Allocations)
  - `benchstat` (Compare Benchmark Results — Statistical Analysis)
  - Avoiding Compiler Optimization of Benchmarks

### 📦 Module 7.3: Code Quality Tools
- **Linting**
  - `golangci-lint` (Meta-Linter — Run Multiple Linters)
    - Configuration (`.golangci.yml`)
    - Essential Linters: `errcheck`, `staticcheck`, `govet`, `gosec`, `ineffassign`, `unused`, `gosimple`, `revive`
  - `go vet` (Official Static Analysis)
  - `staticcheck` (Advanced Static Analysis)
  - `gosec` (Security Linter)
- **Formatting**
  - `go fmt` / `gofmt` (Standard Formatter — Non-Negotiable)
  - `goimports` (Format + Organize Imports)
  - `gofumpt` (Stricter Formatting — Superset of `gofmt`)
- **Code Documentation**
  - GoDoc Comments (Comment Format → Auto-Generated Documentation)
  - `go doc` (CLI Documentation Viewer)
  - Package Documentation (Package-Level Comment)
  - Example Functions (`func ExampleXxx()` — Executable Documentation)
  - `pkg.go.dev` (Public Module Documentation)

### 📦 Module 7.4: Build Tools & Dependency Management
- **Go Modules (Dependency Management)**
  - `go.mod` and `go.sum`
  - `go mod tidy` (Clean Up Dependencies)
  - `go mod vendor` (Vendor Dependencies)
  - Dependency Vulnerability Scanning (`govulncheck`)
  - Private Module Configuration (`GOPRIVATE`)
  - Semantic Versioning and Module Version Selection (MVS)
  - Reproducible Builds (Deterministic via `go.sum`)
- **Build Tooling**
  - `go build` (Compile)
  - `go install` (Compile and Install Binary)
  - Cross-Compilation (`GOOS`, `GOARCH`)
  - Build Flags (`-ldflags`, `-tags`, `-race`, `-trimpath`)
  - Injecting Version/Commit at Build Time (`-ldflags "-X main.version=1.0.0"`)
  - `Makefile` for Go Projects (Common Build Tasks)
  - `Task` / `Taskfile` (Modern Alternative to Make)
  - `goreleaser` (Automated Releases — Cross-Compile, Package, Publish)
- **Release Management**
  - Semantic Versioning
  - Git Tags for Releases
  - Changelog Generation
  - `goreleaser` for Automated Release Pipeline

### 📦 Module 7.5: Version Control Mastery
- Git Internals (Objects, Refs, DAG)
- Branching Strategies (GitFlow, Trunk-Based Development, GitHub Flow)
- Monorepo vs Polyrepo Trade-offs
- Advanced Git (Rebase, Cherry-Pick, Bisect, Stash, Hooks)
- GitHub / GitLab Collaboration (PRs, Code Reviews, Protected Branches)
- `.gitignore` for Go Projects (Binaries, Vendor, IDE Files)
- Conventional Commits

### 📦 Module 7.6: CI/CD Foundations
- Continuous Integration Best Practices
- Pipeline-as-Code (GitHub Actions)
- Pipeline Stages for Go Projects
  - `go fmt` Check (Formatting Must Pass)
  - `go vet` (Static Analysis)
  - `golangci-lint` (Linting)
  - `go test -race -cover ./...` (Tests with Race Detector)
  - `govulncheck` (Vulnerability Scanning)
  - `go build` (Compile)
  - Docker Build (Container Image)
- Quality Gates (Lint Pass, Test Pass, Coverage Threshold, No Vulnerabilities)
- Caching in CI (`go mod` Cache, Build Cache)
- Cross-Compilation in CI (Build for Multiple Platforms)
- Publishing Binaries (GitHub Releases via `goreleaser`)

### 📦 Module 7.7: Logging & Debugging
- **Logging**
  - `log` Package (Standard Library — Basic)
  - `log/slog` (Go 1.21+ — Structured Logging, Production-Grade)
    - `slog.Info()`, `slog.Error()`, `slog.Warn()`, `slog.Debug()`
    - `slog.With()` (Add Context Fields)
    - `slog.Group()` (Group Related Fields)
    - Handlers (JSON Handler, Text Handler, Custom Handlers)
    - Log Levels
    - Handler Chaining
    - **💡 `slog` is Go's answer to structured logging — use it**
  - `zerolog` (Third-Party — Zero-Allocation JSON Logger)
  - `zap` (Uber — High-Performance Structured Logger)
  - When `slog` vs `zerolog` vs `zap`
- **Debugging**
  - Delve Debugger (`dlv`) — Go's Standard Debugger
    - `dlv debug` (Start Debugging)
    - Breakpoints, Step, Continue, Print
    - VS Code Integration (Launch Configuration)
    - Attach to Running Process
  - `fmt.Printf` Debugging (Quick and Dirty — We All Do It)
  - `pprof` for Performance Debugging (Already Covered)
  - Race Detector (`-race` Flag)

> ### 🛠 Phase 7 Milestone Project: **CLI Task Queue (Fully Tested & Released)**
> Build a CLI task queue tool with comprehensive testing: table-driven unit tests, integration tests with Testcontainers (Redis for queue backend), fuzz tests for input parsing, benchmarks for queue operations, race detector in all tests, golden files for CLI output, greater than 85% coverage, structured logging with `slog`, linted with `golangci-lint`, formatted with `gofumpt`, CI/CD with GitHub Actions (lint → vet → test → race → build → release), published with `goreleaser` as multi-platform binaries.

---

## 🔶 PHASE 8: Databases & Data Modeling
> **Goal:** Understand data modeling, master SQL, connect Go to databases, and understand database internals.

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

### 📦 Module 8.4: Go Database Access — `database/sql`
- **`database/sql` Package (Standard Library)**
  - Database Drivers (`lib/pq`, `pgx`, `go-sql-driver/mysql`, `mattn/go-sqlite3`)
  - `sql.Open()` (Open Connection Pool — Not a Single Connection)
  - `sql.DB` (Connection Pool Manager)
    - `SetMaxOpenConns()`, `SetMaxIdleConns()`, `SetConnMaxLifetime()`, `SetConnMaxIdleTime()`
    - Pool Tuning for Production
  - `db.QueryContext()` (SELECT — Returns Rows)
  - `db.QueryRowContext()` (SELECT One Row)
  - `db.ExecContext()` (INSERT, UPDATE, DELETE — Returns Result)
  - `rows.Scan()` (Map Columns to Variables)
  - `rows.Close()` (Always Close — `defer rows.Close()`)
  - Parameterized Queries (SQL Injection Prevention — `$1`, `?`)
  - `sql.NullString`, `sql.NullInt64`, etc. (Handling NULL Values)
  - Context Integration (Pass `ctx` to All Database Calls)
- **Transactions**
  - `db.BeginTx()` (Start Transaction)
  - `tx.Commit()`, `tx.Rollback()`
  - `defer tx.Rollback()` + `tx.Commit()` Pattern (Rollback If Commit Not Reached)
  - Savepoints (Nested Transactions — Driver Dependent)
- **`pgx` (Preferred PostgreSQL Driver)**
  - `pgx` vs `lib/pq` (pgx Is Faster, More Features, Actively Maintained)
  - `pgxpool` (Connection Pool — Better Than `database/sql` Pool for PostgreSQL)
  - `pgx.CollectRows()`, `pgx.RowToStructByName()` (Convenient Row Scanning)
  - Native PostgreSQL Types (Arrays, JSON, UUID, Intervals)
  - Batch Operations (`pgx.Batch`)
  - Copy Protocol (Bulk Insert)
  - Listen/Notify (PostgreSQL Pub/Sub)

### 📦 Module 8.5: Query Builders & ORMs
- **sqlc (SQL Compiler — Preferred)**
  - Write SQL → Generate Type-Safe Go Code
  - `sqlc.yaml` Configuration
  - Queries File (`.sql` with Annotations `-- name: GetUser :one`)
  - Generated Code (Structs, Query Functions — Fully Typed)
  - Migrations Integration
  - Why sqlc (Write Real SQL, Get Type Safety, Zero Runtime Overhead)
- **GORM (Full ORM — Popular but Controversial)**
  - Model Definition (Struct Tags)
  - AutoMigrate (Awareness — Not for Production)
  - CRUD Operations
  - Relationships (HasOne, HasMany, BelongsTo, Many2Many)
  - Eager Loading (`Preload`, `Joins`)
  - Hooks (BeforeCreate, AfterCreate, etc.)
  - Scopes (Reusable Query Conditions)
  - Raw SQL When Needed
  - GORM Pitfalls (Implicit Behavior, Magic, Performance Surprises)
  - When GORM vs sqlc (GORM for Rapid Prototyping, sqlc for Production)
- **Ent (Entity Framework by Facebook — Awareness)**
  - Schema-as-Code (Generate Everything from Schema Definition)
  - Graph-Based Data Model
- **sqlx (Extension of `database/sql` — Awareness)**
  - `sqlx.Get()`, `sqlx.Select()` (Scan Directly into Structs)
  - Named Queries (`:name` Parameters)
  - Lighter Than ORM, More Convenient Than Raw `database/sql`
- **Choosing: `database/sql` + pgx vs sqlc vs GORM vs sqlx**
  - Simple CRUD → sqlc (Type-Safe SQL)
  - Complex Queries → `database/sql` + pgx (Full Control)
  - Rapid Prototyping → GORM (Speed of Development)
  - Middle Ground → sqlx (Convenience + SQL Control)

### 📦 Module 8.6: Database Migrations
- **`golang-migrate` (Most Popular)**
  - Migration Files (`NNNN_description.up.sql`, `NNNN_description.down.sql`)
  - CLI Usage (`migrate up`, `migrate down`, `migrate force`)
  - Programmatic Usage (Run Migrations in Application Startup)
- **`goose` (Alternative)**
  - SQL and Go Migrations
  - Versioned and Timestamped
- **`atlas` (Modern — Schema-as-Code)**
  - Declarative Schema Management
  - Auto-Generate Migrations from Schema Diff
- Zero-Downtime Migration Strategies (Expand/Contract)
- Data Migrations
- Running Migrations in CI/CD

### 📦 Module 8.7: NoSQL & Distributed Data Concepts
- NoSQL Categories (Document, Key-Value, Column-Family, Graph, Time-Series)
- When to Use SQL vs NoSQL
- CAP Theorem and PACELC
- **Redis with Go**
  - `go-redis` (Preferred Client — `github.com/redis/go-redis/v9`)
  - Key-Value Operations, Data Structures (List, Set, Hash, Sorted Set)
  - Pub/Sub
  - Caching Patterns (Cache-Aside)
  - TTL and Expiration
  - Context Integration
  - Pipeline and Transaction (`TxPipeline`)
- **MongoDB with Go (Awareness)**
  - `mongo-go-driver` (Official Driver)
  - Documents, Collections, CRUD
- Polyglot Persistence Concepts

> ### 🛠 Phase 8 Milestone Project: **Blog Engine Database Layer**
> Build a complete database layer for a blog: Users, Posts, Comments, Tags, Categories. Use `pgx` for PostgreSQL driver with connection pool tuning, sqlc for type-safe query generation, `golang-migrate` for migrations, complex queries (joins, CTEs, window functions), `EXPLAIN ANALYZE` for optimization, Redis caching (`go-redis`) for hot posts, transaction management, and query performance benchmarks.

---

## 🔷 PHASE 9: Networking, Infrastructure & Operations
> **Goal:** Understand networking, Go's powerful standard library for HTTP, containerization, and infrastructure fundamentals.

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

### 📦 Module 9.2: Go Networking — `net` Package
- **TCP Client and Server**
  - `net.Listen()`, `net.Dial()`
  - `net.Conn` Interface (Read, Write, Close)
  - Concurrent TCP Server (Goroutine Per Connection)
  - Connection Timeouts and Deadlines
- **UDP Client and Server (Awareness)**
  - `net.ListenPacket()`, `net.DialUDP()`
- **DNS Lookups**
  - `net.LookupHost()`, `net.LookupIP()`
  - Custom Resolver

### 📦 Module 9.3: Go HTTP — `net/http` Package
- **HTTP Server (Built Into Standard Library — No Framework Needed)**
  - `http.ListenAndServe()` (Start Server)
  - `http.HandleFunc()` (Register Handlers)
  - `http.Handler` Interface (`ServeHTTP(w, r)`)
  - `http.HandlerFunc` (Adapt Function to Handler)
  - `http.ServeMux` (Default Router — Enhanced in Go 1.22+)
    - Go 1.22+ Routing Patterns (`GET /users/{id}`, Method-Based Routing)
    - Path Parameters (`r.PathValue("id")`)
  - `http.Request` (Method, URL, Headers, Body, Context)
    - `r.URL.Query()` (Query Parameters)
    - `r.PathValue()` (Path Parameters — Go 1.22+)
    - `json.NewDecoder(r.Body).Decode(&v)` (Read JSON Body)
    - `r.Context()` (Request Context — Cancellation, Values)
  - `http.ResponseWriter` (WriteHeader, Write, Header)
    - `w.WriteHeader(statusCode)` (Set Status Code)
    - `w.Header().Set("Content-Type", "application/json")`
    - `json.NewEncoder(w).Encode(v)` (Write JSON Response)
  - `http.Server` (Custom Server Configuration)
    - Timeouts (`ReadTimeout`, `WriteTimeout`, `IdleTimeout`, `ReadHeaderTimeout`)
    - Graceful Shutdown (`server.Shutdown(ctx)`)
    - TLS Configuration (`server.ListenAndServeTLS()`)
- **HTTP Client**
  - `http.Get()`, `http.Post()` (Simple — Don't Use in Production)
  - `http.Client` (Custom Client with Timeout, Transport)
  - `http.NewRequestWithContext()` (Request with Context)
  - Response Handling (`resp.Body`, `defer resp.Body.Close()`, Status Check)
  - Connection Pooling (Default Transport Pools Connections)
  - Custom Transport (TLS Config, Proxy, Timeouts)
  - Retry Logic (Manual — No Built-In)
- **Middleware Pattern (Go's Native Decorator)**
  - `func middleware(next http.Handler) http.Handler`
  - Middleware Chaining
  - Common Middleware: Logging, Recovery, CORS, Auth, Request ID
  - `alice` Library (Middleware Chaining — Awareness)
- **REST API Design with `net/http`**
  - Resource-Based Routing
  - JSON Request/Response Handling
  - Error Response Standardization
  - Input Validation
  - Structured Logging per Request
  - Middleware Stack (Logging → Recovery → CORS → Auth → Handler)
- **💡 Go's `net/http` is production-grade — many Go services run without any framework**

### 📦 Module 9.4: Operating Systems & Linux Fundamentals
- Linux Basics (File System, Permissions, Users)
- Essential Commands (Navigation, File Manipulation, Process Management)
- Package Management (apt, yum)
- Shell Scripting Basics
- Processes, Signals, and Systemd
- Environment Variables and Configuration
- SSH and Remote Access
- Go's `os` and `os/exec` for System Interaction

### 📦 Module 9.5: Containers & Docker
- Virtual Machines vs Containers
- Docker Fundamentals (Images, Containers, Layers)
- **Writing Dockerfiles for Go Applications**
  - Multi-Stage Builds (Go's Killer Feature for Docker)
    - Stage 1: Build (`golang:1.22-alpine` → `go build -o /app`)
    - Stage 2: Runtime (`scratch` or `alpine` → Copy Binary Only)
    - Result: Tiny Image (Often < 20MB)
  - `scratch` Base Image (Empty — Just Your Binary, Nothing Else)
    - CA Certificates (`COPY --from=builder /etc/ssl/certs/ /etc/ssl/certs/`)
    - Timezone Data (`COPY --from=builder /usr/share/zoneinfo /usr/share/zoneinfo`)
  - `alpine` Base Image (When You Need Shell/Debugging)
  - `CGO_ENABLED=0` (Static Binary — No C Dependencies)
  - Non-Root User
  - `.dockerignore` for Go Projects
  - Build Arguments for Version Injection
  - Health Check in Dockerfile
- Docker Networking (Bridge, Host, Custom Networks)
- Docker Volumes (Persistent Data)
- Docker Compose (Multi-Container Applications)
- Dockerizing a Go Application (App + PostgreSQL + Redis)
- Docker Best Practices (Layer Caching, Image Size, Security)

### 📦 Module 9.6: Container Orchestration Basics
- Why Orchestration (Problems Docker Alone Doesn't Solve)
- Kubernetes Core Concepts (Pods, Services, Deployments, Namespaces)
- `kubectl` Basics
- YAML Manifests (Awareness)
- ConfigMaps and Secrets (Awareness)
- Kubernetes vs Docker Compose — When to Use What

> ### 🛠 Phase 9 Milestone Project: **Containerized Go TCP Chat Server**
> Build a multi-room chat server using Go `net` package with goroutines per connection, channels for message broadcasting, and `context` for graceful disconnect. HTTP API endpoints (Go 1.22+ `ServeMux`) for room management and user listing. Dockerize with multi-stage build to `scratch` image (< 15MB). Docker Compose with chat server + Redis (for pub/sub across instances) + PostgreSQL (for user accounts and message persistence). Structured logging with `slog`. Graceful shutdown on SIGTERM. Health check endpoints.

---

## 🏗️ CAPSTONE PROJECT: Production-Grade URL Shortener
> **This is the Phase 1 capstone that ties everything together.**
>
> Build a URL shortener service (like bit.ly) with:
> - **Clean Go code** applying SOLID principles, Go idioms, and composition patterns
> - **RESTful API** with proper HTTP semantics and error handling (Go 1.22+ `net/http` — no framework)
> - **Middleware chain** (logging, recovery, CORS, request ID, auth)
> - **PostgreSQL** with proper schema design, normalization, and indexing (`pgx` + `sqlc`)
> - **Redis** caching layer for hot URLs (`go-redis`)
> - **Database migrations** (`golang-migrate`)
> - **Docker** containerization with multi-stage build to `scratch` (< 15MB image)
> - **docker-compose** (app + PostgreSQL + Redis)
> - **Comprehensive test suite** (table-driven unit tests, integration tests with Testcontainers, fuzz tests for URL validation, benchmarks, race detector)
> - **CI/CD pipeline** (GitHub Actions: lint → vet → test → race → build → docker → release)
> - **Structured logging** with `slog` (JSON handler) and health check endpoints
> - **Graceful shutdown** (SIGTERM handling, drain connections)
> - **Context propagation** throughout request lifecycle
> - **Git** with proper branching strategy and semantic versioning
> - **goreleaser** for multi-platform binary releases
> - Architecture documented with decision rationale
>
> **Why:** Small enough to finish, complex enough to demonstrate all Phase 1 skills — clean code, Go idioms, concurrency, testing, databases, Docker, CI/CD, networking, and infrastructure. Built entirely with Go's standard library for HTTP (no framework dependency).

---

## ✅ After Completing This Roadmap — You Can:
- Write clean, testable, maintainable, idiomatic Go code
- Apply Go's composition-based design effectively (interfaces, embedding, functional options)
- Understand Go runtime internals (scheduler, GC, memory, escape analysis)
- Master goroutines, channels, context, and concurrency patterns
- Handle errors the Go way (wrapping, sentinel errors, custom error types)
- Use generics appropriately (without overusing them)
- Solve DSA problems confidently in Go
- Design normalized/denormalized data models
- Work fluently with SQL, `database/sql`, pgx, and sqlc
- Understand NoSQL concepts and CAP theorem
- Build production-grade HTTP servers with `net/http` (no framework needed)
- Containerize Go applications with tiny Docker images (multi-stage to `scratch`)
- Set up CI/CD pipelines with GitHub Actions
- Use Git professionally with proper branching strategies
- Write comprehensive tests (table-driven, integration, fuzz, benchmarks, race detection)
- Profile and optimize Go applications with `pprof`
- **You are fully ready for Phase 2: Go Backend Framework & Architectural Thinking**

---

## 📋 Quick Reference Summary

