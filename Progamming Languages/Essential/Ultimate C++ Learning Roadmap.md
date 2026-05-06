## Roadmap Overview

```
Phase 1 ▸ Getting Started         (Weeks 1–3)     → "How do I write and run C++ programs?"
Phase 2 ▸ Building Blocks         (Weeks 4–7)     → "How do I organize logic and data?"
Phase 3 ▸ Object-Oriented Design  (Weeks 8–12)    → "How do I model the real world in code?"
Phase 4 ▸ Memory & Resources      (Weeks 13–16)   → "How do I manage what my program owns?"
Phase 5 ▸ Generic Programming     (Weeks 17–20)   → "How do I write code that works with any type?"
Phase 6 ▸ The Standard Library    (Weeks 21–24)   → "What tools does C++ give me for free?"
Phase 7 ▸ Modern C++ Patterns     (Weeks 25–28)   → "How do professionals write C++ today?"
Phase 8 ▸ Systems & Performance   (Weeks 29–32)   → "How do I write software that flies?"

Total: ~32 weeks at 10–15 hours/week
```

```
                    YOU ARE HERE
                         │
                         ▼
    ┌─────────────────────────────────────────────────┐
    │        PHASE 1: GETTING STARTED                 │
    │     Your First Programs & Core Syntax           │
    └──────────────────────┬──────────────────────────┘
                           │
                           ▼
    ┌─────────────────────────────────────────────────┐
    │        PHASE 2: BUILDING BLOCKS                 │
    │     Functions, Collections & Text               │
    └──────────────────────┬──────────────────────────┘
                           │
                           ▼
    ┌─────────────────────────────────────────────────┐
    │     PHASE 3: OBJECT-ORIENTED DESIGN             │
    │   Classes, Inheritance & Polymorphism            │
    └──────────────────────┬──────────────────────────┘
                           │
                           ▼
    ┌─────────────────────────────────────────────────┐
    │      PHASE 4: MEMORY & RESOURCES                │
    │   Ownership, Smart Pointers & RAII              │
    └──────────────────────┬──────────────────────────┘
                           │
                           ▼
    ┌─────────────────────────────────────────────────┐
    │      PHASE 5: GENERIC PROGRAMMING               │
    │    Templates, Concepts & Compile-Time Magic      │
    └──────────────────────┬──────────────────────────┘
                           │
                           ▼
    ┌─────────────────────────────────────────────────┐
    │      PHASE 6: THE STANDARD LIBRARY              │
    │    Containers, Algorithms, Iterators & More      │
    └──────────────────────┬──────────────────────────┘
                           │
                           ▼
    ┌─────────────────────────────────────────────────┐
    │     PHASE 7: MODERN C++ PATTERNS                │
    │   Lambdas, Move Semantics, Error Handling        │
    └──────────────────────┬──────────────────────────┘
                           │
                           ▼
    ┌─────────────────────────────────────────────────┐
    │     PHASE 8: SYSTEMS & PERFORMANCE              │
    │   Concurrency, Optimization & Real-World C++     │
    └─────────────────────────────────────────────────┘
                           │
                           ▼
                      MASTERY ✓
```

---

---

## PHASE 1 — GETTING STARTED

> **"How do I write and run C++ programs?"**

> You will learn the absolute basics: setting up your tools, understanding how C++ turns text into a running program, and writing simple interactive programs.

---

### Module 1.1 — Setting Up Your Workshop

#### Section 1.1.1 — What C++ Is and Why It Matters
- Where C++ came from and how it evolved from C
- Where C++ is used today: games, browsers, operating systems, finance, embedded devices
- How C++ compares to other languages at a high level
- The philosophy of C++: "you don't pay for what you don't use"

#### Section 1.1.2 — Installing Your Tools
- Choosing a compiler: GCC, Clang, or MSVC
- Setting up VS Code with C++ extensions
- Alternative: CLion, Visual Studio, or Qt Creator
- Compiling your first file from the terminal
- The compilation pipeline: preprocessing, compiling, linking

#### Section 1.1.3 — The Shape of a C++ Program
- The entry point: what `main` does and what it returns
- Including standard library headers
- Namespaces at a glance: why `std::` appears everywhere
- Comments: single-line and multi-line
- How whitespace and formatting conventions work

---

### Module 1.2 — Storing and Working with Data

#### Section 1.2.1 — Variables: Giving Names to Data
- What a variable is: a named box in memory
- Declaring a variable vs. giving it an initial value
- Choosing meaningful names: rules and best practices
- The `auto` keyword: letting the compiler figure out the type

#### Section 1.2.2 — Fundamental Data Types
- Whole numbers: `int`, `short`, `long`, `long long`
- Decimal numbers: `float`, `double`
- Single characters: `char`
- True or false: `bool`
- Signed vs. unsigned: what happens when numbers go negative
- Finding the size of any type with `sizeof`

#### Section 1.2.3 — Constants: Data That Never Changes
- `const` variables
- `constexpr`: values known at compile time
- When to use each and why magic numbers are bad

#### Section 1.2.4 — Operators: Doing Things with Data
- Math operators: addition, subtraction, multiplication, division, remainder
- Comparison operators: equal, not equal, greater, less
- Logical operators: and, or, not
- Assignment shortcuts: add-and-assign, multiply-and-assign, and others
- How C++ decides which operation happens first (precedence)

---

### Module 1.3 — Talking to the User

#### Section 1.3.1 — Printing Output to the Screen
- Using `cout` to display text and numbers
- Combining multiple pieces of output in one statement
- Formatting output: new lines, tabs, alignment
- Controlling decimal precision for floating-point numbers

#### Section 1.3.2 — Reading Input from the Keyboard
- Using `cin` to read numbers, words, and characters
- Reading an entire line of text (including spaces)
- What happens when the user types something unexpected
- Validating input: checking if the read succeeded

---

### Module 1.4 — Making Decisions and Repeating Actions

#### Section 1.4.1 — Branching: Choosing a Path
- `if`, `else if`, and `else`: running code conditionally
- Nesting conditions inside each other
- `switch` statements: choosing from many options
- The conditional (ternary) operator: compact decisions

#### Section 1.4.2 — Loops: Doing Things Again and Again
- `while` loops: repeat while a condition is true
- `do-while` loops: always run at least once
- `for` loops: when you know how many times to repeat
- Range-based `for` loops: the modern way to walk through collections
- Breaking out of a loop early
- Skipping to the next repetition with `continue`
- Avoiding infinite loops

#### Section 1.4.3 — Nesting and Combining Control Flow
- Loops inside loops
- Conditions inside loops
- When deep nesting is a sign of a design problem

---

### Module 1.5 — Understanding Type Safety

#### Section 1.5.1 — Implicit Conversions: What the Compiler Does Quietly
- Widening conversions: small type to large type (safe)
- Narrowing conversions: large type to small type (dangerous)
- Mixing signed and unsigned numbers: a common trap

#### Section 1.5.2 — Explicit Conversions: Being Clear About Your Intent
- `static_cast`: the safe, readable way to convert types
- Why old C-style casts are discouraged in C++
- When conversions lose data and how to detect it

---

### 🔨 Phase 1 Project — **Personal Budget Tracker**

```
Build a command-line application that:
  ✓ Lets the user add income and expense entries with descriptions
  ✓ Categorizes expenses (food, transport, entertainment, bills, other)
  ✓ Displays a summary: total income, total expenses, net balance
  ✓ Shows a breakdown by category with percentage of total spending
  ✓ Warns the user when expenses exceed income
  ✓ Supports a monthly view (filter entries by month)
  ✓ Runs in a menu-driven loop until the user chooses to quit
  ✓ Validates all user input (rejects negative amounts, empty descriptions)

Skills practiced:
  → variables, types, input/output, if/else, switch, loops,
    basic arithmetic, input validation
```

---

---

## PHASE 2 — BUILDING BLOCKS

> **"How do I organize logic and data?"**

> You will learn how to break programs into reusable pieces with functions, work with collections of data using arrays and vectors, and manipulate text with strings.

---

### Module 2.1 — Functions: Reusable Pieces of Logic

#### Section 2.1.1 — Creating and Calling Functions
- What a function is: input → processing → output
- Defining a function: name, parameters, return type, body
- Calling a function and using its return value
- Functions that return nothing (`void`)
- Why every program should be built from small, focused functions

#### Section 2.1.2 — How Data Flows Into and Out of Functions
- Pass by value: the function gets a copy
- Pass by reference: the function works with the original
- Pass by `const` reference: read-only access without copying
- When to use each approach
- Returning multiple values: using reference parameters or structured types

#### Section 2.1.3 — Default Values, Overloading, and Flexibility
- Default arguments: giving parameters fallback values
- Function overloading: same name, different parameter lists
- How the compiler chooses which overloaded function to call
- Why overloading improves readability when used wisely

#### Section 2.1.4 — Scope, Lifetime, and Visibility
- Local variables: born when declared, die when the block ends
- Global variables: why they are usually a bad idea
- Static local variables: they remember their value between calls
- Namespaces: organizing code to avoid name collisions
- Creating your own namespaces

#### Section 2.1.5 — Recursion: Functions That Call Themselves
- The concept: a problem defined in terms of smaller versions of itself
- Base case and recursive case
- How the call stack grows and shrinks with each recursive call
- Comparing recursion to loops: clarity vs. performance
- When recursion is the natural solution (trees, divide-and-conquer)

---

### Module 2.2 — Collections of Data

#### Section 2.2.1 — Raw Arrays: The Low-Level Foundation
- Declaring and initializing fixed-size arrays
- Accessing elements by index (zero-based)
- Why arrays don't know their own size
- The danger of going out of bounds
- Multidimensional arrays: rows and columns

#### Section 2.2.2 — `std::vector`: The Dynamic Collection
- What a vector is: a resizable array that manages its own memory
- Creating vectors, adding elements, removing elements
- Accessing elements safely (`at`) vs. fast (`[]`)
- How vectors grow: capacity vs. size
- Iterating over vectors with range-based `for`
- Vectors of vectors: dynamic 2D collections
- Why vectors should be your default collection in C++

#### Section 2.2.3 — `std::array`: The Modern Fixed-Size Collection
- Compile-time fixed size with bounds checking
- When to use `std::array` vs. raw arrays vs. `std::vector`

---

### Module 2.3 — Working with Text

#### Section 2.3.1 — `std::string`: Text Done Right
- Creating and initializing strings
- Concatenation: joining strings together
- Accessing individual characters
- Finding the length of a string
- Comparing strings: equality and ordering
- Searching within strings: finding substrings and characters
- Extracting parts of a string: substrings
- Replacing, inserting, and erasing portions of text
- Converting between strings and numbers

#### Section 2.3.2 — `std::string_view`: Looking Without Owning
- What a string view is: a read-only window into existing text
- Why it avoids unnecessary copies
- When to use `string_view` as a function parameter
- The danger: the original string must outlive the view

#### Section 2.3.3 — Character-Level Operations
- Checking character properties: is it a letter, a digit, uppercase, lowercase?
- Converting case: uppercase to lowercase and back
- The ASCII table: how characters map to numbers

---

### Module 2.4 — Grouping Related Data Together

#### Section 2.4.1 — Structures: Your First Custom Types
- Defining a structure: grouping variables under one name
- Creating and initializing structure variables
- Accessing members with the dot operator
- Structures inside other structures (nesting)
- Arrays and vectors of structures
- Passing structures to functions (by value, by reference, by `const` reference)

#### Section 2.4.2 — Enumerations: Named Choices
- `enum class`: defining a set of named options (scoped enumerations)
- Why `enum class` is safer than old-style `enum`
- Using enumerations with `switch` statements
- Giving enum values explicit underlying numbers

#### Section 2.4.3 — Type Aliases: Making Types Easier to Read
- `using` declarations: giving complex types simple names
- When type aliases improve readability and when they hide too much

---

### Module 2.5 — Organizing Code Across Files

#### Section 2.5.1 — Header Files and Source Files
- The convention: declarations in `.h` files, definitions in `.cpp` files
- Include guards: preventing the same header from being included twice
- `#pragma once`: the modern shortcut
- What `#include` actually does behind the scenes

#### Section 2.5.2 — Building Multi-File Programs
- How the compiler processes each file independently
- How the linker connects everything together
- Common errors: undefined references, multiple definitions
- Forward declarations: telling the compiler "this exists, trust me"

#### Section 2.5.3 — Introduction to Build Systems
- Why typing compiler commands by hand doesn't scale
- Basic Makefiles: targets, dependencies, and recipes
- First look at CMake: the industry standard build system

---

### 🔨 Phase 2 Project — **Contact Book Application**

```
Build a command-line contact management system that:
  ✓ Stores contacts with: name, phone, email, address, birthday, group
  ✓ Supports groups: Family, Friends, Work, Other
  ✓ Operations: add, search (by name, by group), edit, delete, list all
  ✓ Sorts contacts alphabetically or by group
  ✓ Detects and warns about duplicate phone numbers or emails
  ✓ Displays birthday reminders (contacts with birthdays this month)
  ✓ Exports contacts to a text file and imports them back
  ✓ Uses functions for every operation (no giant main function)
  ✓ Splits code across multiple files (contacts, file I/O, utilities)
  ✓ Builds using a Makefile or CMake

Skills practiced:
  → functions, vectors, strings, structures, enums,
    file I/O basics, multi-file organization, loops, sorting
```

---

---

## PHASE 3 — OBJECT-ORIENTED DESIGN

> **"How do I model the real world in code?"**

> You will learn the core paradigm that defines C++: creating classes that bundle data and behavior together, building hierarchies of related types, and designing clean interfaces.

---

### Module 3.1 — Classes: Blueprints for Objects

#### Section 3.1.1 — From Structures to Classes
- What object-oriented programming means at a high level
- Classes as blueprints: they describe what an object knows and can do
- Members: data (attributes) and functions (methods) living together
- Creating objects from a class (instantiation)
- The `this` pointer: how an object refers to itself

#### Section 3.1.2 — Controlling Access: Public, Private, Protected
- Why hiding internal details matters (encapsulation)
- `public`: the interface the world sees
- `private`: the internals only the class itself can touch
- `protected`: accessible to the class and its children
- Getter and setter methods: controlled doorways to private data
- The `friend` keyword: granting special access (and why to use it sparingly)

#### Section 3.1.3 — Constructors: Setting Up Objects Properly
- What a constructor does: bringing an object to life in a valid state
- Default constructors: the no-argument version
- Parameterized constructors: customizing objects at creation
- Member initializer lists: the efficient way to initialize data
- Delegating constructors: one constructor calling another
- `explicit` keyword: preventing accidental type conversions

#### Section 3.1.4 — Destructors: Cleaning Up After Yourself
- What a destructor does: releasing resources when an object dies
- When destructors are called automatically
- Why you rarely need to write one in modern C++ (but must understand them)
- The order of construction and destruction

#### Section 3.1.5 — Static Members: Shared Across All Objects
- Static data members: one copy shared by every object of the class
- Static member functions: callable without an object
- Use cases: counters, configuration, factory methods

---

### Module 3.2 — Operator Overloading: Teaching Objects New Tricks

#### Section 3.2.1 — The Idea Behind Operator Overloading
- Why it makes sense for custom types to support `+`, `==`, `<<`, and others
- The rules: which operators can be overloaded, which cannot
- Member functions vs. free functions for operator overloading

#### Section 3.2.2 — Commonly Overloaded Operators
- Arithmetic operators: making your types support math
- Comparison operators: defining what "equal" and "less than" mean
- The spaceship operator (`<=>`): defining all comparisons at once (C++20)
- Stream insertion and extraction: making your types printable and readable
- Subscript operator: making your types behave like arrays
- Function call operator: making your types behave like functions (functors)

#### Section 3.2.3 — Overloading Responsibly
- Principle of least surprise: operators should do what users expect
- When overloading helps readability and when it creates confusion
- Operators you should almost never overload

---

### Module 3.3 — Inheritance: Building Family Trees of Types

#### Section 3.3.1 — What Inheritance Models
- "Is-a" relationships: a Dog is an Animal, a Circle is a Shape
- Base classes and derived classes
- What gets inherited: members and methods
- Access control in inheritance: public, protected, and private inheritance
- Why public inheritance is used 95% of the time

#### Section 3.3.2 — How Construction and Destruction Work in Hierarchies
- Constructing a derived object: base is built first, then derived
- Passing arguments to the base constructor
- Destruction in reverse order: derived dies first, then base
- Why base class destructors should usually be virtual

#### Section 3.3.3 — Method Overriding: Changing Inherited Behavior
- Redefining a base class method in a derived class
- The `override` keyword: catching mistakes at compile time
- The `final` keyword: preventing further overriding or inheritance
- Calling the base class version from the derived class

#### Section 3.3.4 — Multiple Inheritance and Its Complexities
- Inheriting from more than one base class
- The diamond problem: when two paths lead to the same grandparent
- Virtual inheritance: solving the diamond problem
- Why many C++ programmers prefer interfaces over multiple inheritance

---

### Module 3.4 — Polymorphism: One Interface, Many Behaviors

#### Section 3.4.1 — The Power of Treating Different Types Uniformly
- What polymorphism means: "many forms"
- Using a base class pointer or reference to work with derived objects
- Why this enables writing code that doesn't need to know every specific type

#### Section 3.4.2 — Virtual Functions: Runtime Dispatch
- What `virtual` means: "let the actual object type decide"
- How the virtual table (vtable) works behind the scenes
- The performance cost: one indirect function call
- Pure virtual functions: methods with no implementation in the base
- Abstract classes: classes that cannot be instantiated directly

#### Section 3.4.3 — Designing with Interfaces
- Abstract classes as contracts: "any type that fits this shape"
- Interface segregation: small, focused abstract classes
- Dependency inversion: depending on abstractions, not concrete types
- Real-world example: shapes, file parsers, payment processors

#### Section 3.4.4 — Runtime Type Information
- `dynamic_cast`: safely converting between types in a hierarchy
- `typeid`: asking an object what type it really is
- Why heavy use of these features often signals a design problem

---

### Module 3.5 — Composition vs. Inheritance

#### Section 3.5.1 — "Has-a" vs. "Is-a" Relationships
- Composition: a Car has an Engine (embedding objects as members)
- Inheritance: an ElectricCar is a Car (extending a type)
- Why "prefer composition over inheritance" is a common guideline
- When inheritance is the right choice

#### Section 3.5.2 — Designing Clean Class Hierarchies
- The Liskov Substitution Principle: every derived type must be usable as its base
- Signs of a bad hierarchy: override methods that throw "not supported"
- Keeping hierarchies shallow: deep trees are fragile
- The rule of "is-a" must hold in every context, not just linguistically

---

### 🔨 Phase 3 Project — **Shape Drawing Engine**

```
Build an object-oriented 2D shape engine that:
  ✓ Defines a Shape base class with pure virtual methods:
    area, perimeter, draw (text-based), describe
  ✓ Implements derived classes: Circle, Rectangle, Triangle,
    Square (derived from Rectangle), Polygon
  ✓ Stores a collection of shapes as base-class pointers
  ✓ Draws all shapes to a text grid (simple ASCII rendering)
  ✓ Sorts shapes by area or perimeter
  ✓ Groups shapes by type and displays statistics
  ✓ Supports operations: add shape, remove shape, find largest,
    find smallest, calculate total area
  ✓ Uses operator overloading: == (same dimensions), < (compare area),
    << (print description)
  ✓ Demonstrates polymorphism: processes all shapes through
    base class pointers without knowing concrete types
  ✓ Saves and loads shape collections to/from a file
  ✓ Properly frees all memory (no leaks)

Skills practiced:
  → classes, encapsulation, constructors, destructors,
    inheritance, polymorphism, virtual functions, abstract classes,
    operator overloading, composition, vectors of pointers
```

---

---

## PHASE 4 — MEMORY & RESOURCES

> **"How do I manage what my program owns?"**

> You will understand how C++ handles memory, learn the RAII principle, master smart pointers, and understand move semantics — the concepts that make C++ both powerful and safe.

---

### Module 4.1 — How Memory Works in C++

#### Section 4.1.1 — The Two Kingdoms: Stack and Heap
- Stack memory: fast, automatic, limited, ordered
- Heap memory: large, manual, flexible, fragmented
- How the program's memory is organized (text, data, stack, heap)
- Why choosing the right storage location matters for performance

#### Section 4.1.2 — Manual Memory Management: `new` and `delete`
- Allocating single objects on the heap
- Allocating arrays on the heap
- Why every `new` must have a matching `delete`
- What happens when you forget: memory leaks
- What happens when you delete twice: undefined behavior
- What happens when you use memory after deleting: dangling pointers
- Why manual `new`/`delete` is almost never the right approach in modern C++

#### Section 4.1.3 — References vs. Pointers
- References: an alias, always valid, cannot be reseated
- Pointers: can be null, can be reassigned, can point to nothing
- When to use references (almost always) vs. pointers (when nullability is needed)
- `nullptr`: the modern way to say "points to nothing"

---

### Module 4.2 — RAII: The Most Important Idea in C++

#### Section 4.2.1 — Resource Acquisition Is Initialization
- The principle: acquire resources in the constructor, release in the destructor
- Why this makes resource leaks nearly impossible
- Resources beyond memory: files, sockets, mutexes, database connections
- How RAII works with the stack: automatic cleanup when scope ends
- RAII and exceptions: resources are still cleaned up when errors occur

#### Section 4.2.2 — Building RAII Wrappers
- Designing a class that owns a resource
- Constructor acquires, destructor releases
- Disabling copying when sharing doesn't make sense
- Real-world examples: file handles, lock guards, database transactions

---

### Module 4.3 — Smart Pointers: Ownership Made Explicit

#### Section 4.3.1 — `std::unique_ptr`: Sole Ownership
- What it is: a pointer that owns the object and deletes it automatically
- Creating unique pointers with `std::make_unique`
- Transferring ownership with `std::move`
- Why copying a unique pointer is forbidden (and why that is a feature)
- Using unique pointers with polymorphism (base class unique pointers)
- Custom deleters: special cleanup logic

#### Section 4.3.2 — `std::shared_ptr`: Shared Ownership
- What it is: multiple pointers share ownership; object dies when last one does
- Reference counting: how the bookkeeping works internally
- Creating shared pointers with `std::make_shared`
- The overhead: two allocations, atomic reference counting
- When shared ownership is genuinely needed (and when it is overused)

#### Section 4.3.3 — `std::weak_ptr`: Breaking Cycles
- The problem: two shared pointers pointing at each other (circular reference)
- Weak pointers: observing without owning
- Checking if the observed object still exists
- The classic use case: parent-child relationships, caches, observer patterns

#### Section 4.3.4 — Choosing the Right Ownership Model
- Default: value semantics (objects on the stack or as members)
- Need heap allocation with single owner: `unique_ptr`
- Need genuinely shared ownership: `shared_ptr`
- Need to observe without owning: `weak_ptr`
- Need nullable reference: `unique_ptr` or raw pointer (non-owning)
- Raw pointers in modern C++: only for non-owning, never for ownership

---

### Module 4.4 — The Rule of Zero, Three, and Five

#### Section 4.4.1 — Special Member Functions
- The six functions the compiler can generate: default constructor, destructor, copy constructor, copy assignment, move constructor, move assignment
- When the compiler generates them and when it does not

#### Section 4.4.2 — The Rule of Three
- If you define any of: destructor, copy constructor, copy assignment — define all three
- Why: if you manage a resource manually, default copy is almost certainly wrong
- Shallow copy vs. deep copy

#### Section 4.4.3 — The Rule of Five
- Adding move constructor and move assignment to the Rule of Three
- Why moves are important for performance

#### Section 4.4.4 — The Rule of Zero (The Goal)
- If your class uses only RAII types (smart pointers, strings, vectors) as members, you need none of the five
- Let the compiler generate everything
- Why this is the most maintainable design

---

### Module 4.5 — Move Semantics: Transferring Instead of Copying

#### Section 4.5.1 — Why Moving Matters
- The cost of copying large objects (vectors, strings, buffers)
- The idea: if the source is about to die, steal its guts instead of copying
- Lvalues vs. rvalues: what stays around vs. what is temporary

#### Section 4.5.2 — Rvalue References and `std::move`
- Rvalue references (`&&`): binding to temporaries
- `std::move`: casting an lvalue to an rvalue (a declaration of intent, not an action)
- What a moved-from object looks like: valid but unspecified state

#### Section 4.5.3 — Writing Move Constructors and Move Assignment
- Transferring internal resources (swap the pointers, zero out the source)
- `noexcept`: why marking moves as non-throwing is critical for performance
- How the standard library uses moves everywhere (vector resizing, returning from functions)

#### Section 4.5.4 — Perfect Forwarding (Preview)
- The forwarding problem: how to pass arguments without losing their value category
- `std::forward`: preserving lvalue-ness or rvalue-ness
- Why this is critical for generic code (fully explored in Phase 5)

---

### 🔨 Phase 4 Project — **Smart Resource Manager Library**

```
Build a library of RAII resource wrappers that:
  ✓ Implements a UniqueFile class: opens a file in constructor,
    closes in destructor, supports move but not copy
  ✓ Implements a SharedBuffer class: reference-counted byte buffer,
    supports both copy and move, tracks active references
  ✓ Implements a ConnectionPool: manages a fixed number of
    database-style connection objects, hands out RAII guards
    that return connections to the pool when destroyed
  ✓ Implements a ScopeGuard: runs a cleanup function automatically
    when the scope ends (similar to Go's defer)
  ✓ Tests each class for: proper construction, destruction,
    copy behavior, move behavior, exception safety
  ✓ Verifies zero memory leaks using AddressSanitizer
  ✓ Demonstrates the Rule of Zero in a higher-level class
    that uses only smart pointers and standard containers
  ✓ Includes clear documentation explaining ownership for each class

Skills practiced:
  → RAII, smart pointers, constructors, destructors,
    copy/move semantics, Rule of 0/3/5, resource management,
    exception safety
```

---

---

## PHASE 5 — GENERIC PROGRAMMING

> **"How do I write code that works with any type?"**

> You will learn templates — the feature that makes C++ one of the most powerful languages for writing reusable, type-safe, zero-overhead abstractions.

---

### Module 5.1 — Function Templates: One Recipe, Many Types

#### Section 5.1.1 — The Problem Templates Solve
- Writing the same function for `int`, `double`, `string` — tedious and error-prone
- What a template does: the compiler generates the right version for each type
- Your first function template: a generic `max` function
- Template argument deduction: the compiler figures out the type

#### Section 5.1.2 — Multiple Template Parameters
- Functions with two or more independent type parameters
- Mixing template parameters with regular parameters
- Explicit template arguments: when deduction is not enough
- Return type deduction with `auto` and `decltype`

#### Section 5.1.3 — Non-Type Template Parameters
- Using values (not just types) as template parameters
- Fixed-size arrays, compile-time dimensions, buffer sizes
- Why this enables zero-overhead abstractions

---

### Module 5.2 — Class Templates: Generic Data Structures

#### Section 5.2.1 — Defining and Using Class Templates
- Creating a generic `Pair`, `Stack`, or `DynamicArray` class
- Template specialization: providing a custom version for a specific type
- Partial specialization: customizing for a category of types (e.g., all pointers)
- Where to put template code: why it usually lives in header files

#### Section 5.2.2 — Template Member Functions
- Defining member functions outside the class template
- Member function templates within a class template
- Dependent names and the `typename` keyword

#### Section 5.2.3 — Alias Templates and Variable Templates
- Creating shorthand names for complex template types
- Variable templates: compile-time constants parameterized by type

---

### Module 5.3 — Concepts and Constraints (C++20)

#### Section 5.3.1 — The Problem: Unreadable Error Messages
- What happens when you pass a wrong type to a template (before concepts)
- Pages of incomprehensible compiler errors
- How concepts solve this: "this template requires types that can do X"

#### Section 5.3.2 — Using Standard Concepts
- `std::integral`, `std::floating_point`, `std::copyable`, `std::sortable`
- The `requires` clause: constraining template parameters
- Shorthand syntax: using concepts directly in the template parameter list

#### Section 5.3.3 — Writing Your Own Concepts
- Defining what operations a type must support
- Compound requirements: requiring expressions and their return types
- Nesting concepts: building complex constraints from simpler ones

---

### Module 5.4 — Compile-Time Programming

#### Section 5.4.1 — `constexpr`: Computing at Compile Time
- `constexpr` functions: functions the compiler can evaluate before the program runs
- `constexpr` variables: values guaranteed to be known at compile time
- `consteval` (C++20): functions that must run at compile time
- `constinit` (C++20): ensuring static variables are initialized at compile time

#### Section 5.4.2 — `if constexpr`: Compile-Time Branching
- Choosing code paths at compile time based on type properties
- How this replaces complex template specialization patterns
- Combining with type traits for powerful generic code

#### Section 5.4.3 — Template Metaprogramming (Awareness Level)
- What it is: using templates to compute values and types at compile time
- Recursive templates: compile-time factorial, Fibonacci (the classic examples)
- Why `constexpr` has replaced most template metaprogramming
- SFINAE: "Substitution Failure Is Not An Error" (historical, now replaced by concepts)

---

### Module 5.5 — Variadic Templates: Any Number of Arguments

#### Section 5.5.1 — Parameter Packs
- Accepting any number of template arguments
- Accepting any number of function arguments
- The sizeof... operator: counting arguments at compile time

#### Section 5.5.2 — Fold Expressions (C++17)
- Processing all arguments in a parameter pack with a single expression
- Summing, printing, combining — all with concise syntax

#### Section 5.5.3 — Practical Applications
- Writing a type-safe `print` function that accepts any arguments
- Building a generic `make_unique` or `emplace`
- How the standard library uses variadic templates internally

---

### 🔨 Phase 5 Project — **Generic Collections Library**

```
Build a header-only library of generic data structures:
  ✓ DynamicArray<T>: a simplified vector with push, pop, insert,
    remove, sort (using a comparator), and iterator support
  ✓ LinkedList<T>: a doubly-linked list with forward and reverse iteration
  ✓ HashMap<K, V>: a hash map with configurable hash function
    and collision strategy
  ✓ Optional<T>: a simplified std::optional (value or nothing)
  ✓ Result<T, E>: a type that holds either a success value or an error
  ✓ All containers constrained with C++20 concepts
    (e.g., HashMap requires Hashable keys)
  ✓ All containers support range-based for loops
  ✓ All containers properly handle copy, move, and destruction
  ✓ Includes a comprehensive test suite exercising each container
    with primitive types, strings, and custom objects
  ✓ Compiles with no warnings on GCC, Clang, and MSVC

Skills practiced:
  → function templates, class templates, concepts, iterators,
    operator overloading, move semantics, RAII,
    header-only library design, cross-compiler compatibility
```

---

---

## PHASE 6 — THE STANDARD LIBRARY

> **"What tools does C++ give me for free?"**

> You will learn the C++ Standard Library (STL): the containers that store data, the algorithms that process it, and the utilities that make everyday programming easier.

---

### Module 6.1 — Containers: Where Data Lives

#### Section 6.1.1 — Sequence Containers
- `std::vector`: the workhorse dynamic array
- `std::deque`: efficient insertion at both ends
- `std::list`: doubly-linked list (rare in practice)
- `std::forward_list`: singly-linked list (even rarer)
- When to use each: performance trade-offs for insert, delete, access

#### Section 6.1.2 — Associative Containers (Ordered)
- `std::set`: unique elements, always sorted
- `std::map`: key-value pairs, sorted by key
- `std::multiset` and `std::multimap`: allowing duplicates
- How they work internally: balanced binary search trees (red-black trees)
- Custom comparison: providing your own sort order

#### Section 6.1.3 — Unordered Containers (Hash-Based)
- `std::unordered_set` and `std::unordered_map`
- How they work internally: hash tables with buckets
- Average O(1) lookup vs. ordered containers' O(log n)
- Writing custom hash functions for your own types
- When to prefer ordered vs. unordered containers

#### Section 6.1.4 — Container Adaptors
- `std::stack`: last-in, first-out
- `std::queue`: first-in, first-out
- `std::priority_queue`: highest-priority element comes out first
- How adaptors wrap other containers

#### Section 6.1.5 — Choosing the Right Container
- Decision flowchart: do you need ordering? fast lookup? fast insertion?
- Performance comparison table: access, insert, delete, search
- Memory overhead of each container
- The default answer: start with `std::vector` unless you have a reason not to

---

### Module 6.2 — Iterators: The Bridge Between Containers and Algorithms

#### Section 6.2.1 — What Iterators Are
- The concept: a generalized pointer that walks through a container
- `begin()` and `end()`: the half-open range convention
- Dereferencing, incrementing, comparing iterators
- Why iterators decouple containers from algorithms

#### Section 6.2.2 — Iterator Categories
- Input iterators: read forward once
- Output iterators: write forward once
- Forward iterators: read/write forward, multi-pass
- Bidirectional iterators: forward and backward
- Random access iterators: jump to any position
- Contiguous iterators (C++20): elements are in adjacent memory
- Which containers provide which category

#### Section 6.2.3 — Iterator Utilities
- `std::advance`: move an iterator forward or backward by N steps
- `std::distance`: count steps between two iterators
- `std::next` and `std::prev`: get a new iterator offset from another
- Reverse iterators: `rbegin()` and `rend()`
- Insert iterators: `back_inserter`, `front_inserter`, `inserter`

---

### Module 6.3 — Algorithms: Powerful Operations in One Line

#### Section 6.3.1 — Non-Modifying Algorithms
- `find`, `find_if`: locating elements by value or condition
- `count`, `count_if`: counting elements
- `all_of`, `any_of`, `none_of`: checking conditions across a range
- `for_each`: applying an operation to every element
- `equal`, `mismatch`: comparing two ranges
- `search`: finding a subsequence

#### Section 6.3.2 — Modifying Algorithms
- `copy`, `copy_if`: copying elements to another range
- `transform`: applying a function and storing results
- `fill`, `generate`: assigning values to a range
- `replace`, `replace_if`: swapping certain values
- `remove`, `remove_if`: logical removal (the erase-remove idiom)
- `unique`: removing consecutive duplicates
- `reverse`, `rotate`, `shuffle`: rearranging elements

#### Section 6.3.3 — Sorting and Related Operations
- `sort`: fast general-purpose sorting
- `stable_sort`: preserving order of equal elements
- `partial_sort`: sorting only the first N elements
- `nth_element`: putting the Nth element in its correct position
- `binary_search`, `lower_bound`, `upper_bound`: searching sorted ranges
- `merge`: combining two sorted ranges
- `min_element`, `max_element`, `minmax_element`

#### Section 6.3.4 — Numeric Algorithms
- `accumulate`: summing or folding a range
- `inner_product`: dot product of two ranges
- `partial_sum`: running totals
- `adjacent_difference`: differences between neighbors
- `reduce` and `transform_reduce` (C++17): parallelizable versions

#### Section 6.3.5 — Ranges (C++20)
- The ranges library: algorithms on ranges instead of iterator pairs
- Pipe syntax: chaining operations with `|`
- Views: lazy, composable transformations (filter, transform, take, drop)
- Why ranges are the future of C++ algorithms

---

### Module 6.4 — Essential Utilities

#### Section 6.4.1 — `std::pair` and `std::tuple`
- Bundling two values together
- Bundling any number of values together
- Structured bindings (C++17): unpacking into named variables
- When to use these vs. a named struct

#### Section 6.4.2 — `std::optional`: Maybe a Value
- Representing "there might not be a value" without using pointers or magic numbers
- Creating, checking, and accessing the contained value
- Using with functions that might fail to produce a result

#### Section 6.4.3 — `std::variant`: One of Several Types
- A type-safe union: holds exactly one of several possible types
- Visiting variants: processing whichever type is stored
- Using variant to replace class hierarchies in certain cases

#### Section 6.4.4 — `std::any`: Anything at All
- Holding any type (type-erased container)
- Why it is rarely the right choice (prefer variant or templates)

#### Section 6.4.5 — `std::function`: Wrapping Callable Things
- Storing any callable: functions, lambdas, functors
- The type-erased callable wrapper
- Performance cost: heap allocation, indirect call
- When to use `std::function` vs. templates

#### Section 6.4.6 — Date and Time with `<chrono>`
- Durations: representing time intervals (seconds, milliseconds, hours)
- Clocks: system clock, steady clock, high-resolution clock
- Time points: specific moments in time
- Measuring elapsed time: benchmarking code
- Calendar types (C++20): year, month, day, weekday

---

### 🔨 Phase 6 Project — **Log File Analyzer**

```
Build a command-line tool that analyzes server log files:
  ✓ Parses structured log entries: timestamp, level (INFO, WARN, ERROR),
    source module, message
  ✓ Stores entries in appropriate containers (vector for ordered data,
    maps for aggregation, sets for unique values)
  ✓ Supports queries:
    - Filter by log level, date range, or module
    - Count entries by level (using algorithms)
    - Find the busiest hour of the day
    - List the top N most frequent error messages
    - Detect bursts: time windows with abnormally high error rates
  ✓ Uses STL algorithms for all data processing
    (no manual loops for operations where an algorithm exists)
  ✓ Uses ranges and views (C++20) for query pipelines
  ✓ Measures and displays processing time using <chrono>
  ✓ Supports multiple output formats: summary, detailed, CSV
  ✓ Handles files with millions of lines efficiently

Skills practiced:
  → containers (vector, map, unordered_map, set, priority_queue),
    iterators, algorithms (sort, find_if, count_if, accumulate,
    transform, remove_if), ranges, chrono, string parsing,
    structured bindings, optional
```

---

---

## PHASE 7 — MODERN C++ PATTERNS

> **"How do professionals write C++ today?"**

> You will learn the idioms, patterns, and techniques that define modern C++ development: lambda expressions, robust error handling, functional patterns, and clean API design.

---

### Module 7.1 — Lambda Expressions: Functions on the Fly

#### Section 7.1.1 — What Lambdas Are and Why They Matter
- The problem: passing tiny functions to algorithms is verbose with functors
- Lambda syntax: captures, parameters, return type, body
- Using lambdas with standard algorithms (`sort`, `find_if`, `transform`)
- How lambdas are actually implemented by the compiler (anonymous functor objects)

#### Section 7.1.2 — Captures: Giving Lambdas Context
- Capturing by value: the lambda gets a copy
- Capturing by reference: the lambda sees the original
- Capture-all shortcuts: `[=]` (all by value) and `[&]` (all by reference)
- Mutable lambdas: modifying captured-by-value variables
- Capturing `this`: accessing class members from a lambda
- Dangling capture references: the lifetime trap

#### Section 7.1.3 — Advanced Lambda Techniques
- Generic lambdas (`auto` parameters) — C++14
- Lambda templates (explicit template parameter list) — C++20
- Immediately-invoked lambdas: creating complex constant initializations
- Storing lambdas: `std::function` vs. template parameter vs. `auto`
- Lambdas as callbacks and event handlers

---

### Module 7.2 — Error Handling: When Things Go Wrong

#### Section 7.2.1 — Exceptions: The C++ Error Mechanism
- What exceptions are: objects thrown on error, caught by a handler
- `throw`, `try`, `catch`: the mechanics
- Standard exception types: `runtime_error`, `logic_error`, `out_of_range`, and others
- Creating custom exception classes
- Exception propagation: unwinding the stack

#### Section 7.2.2 — Writing Exception-Safe Code
- The three levels of exception safety: basic, strong, no-throw
- RAII as the foundation of exception safety
- The copy-and-swap idiom for strong exception safety
- `noexcept`: declaring that a function will not throw
- Why destructors must never throw

#### Section 7.2.3 — Alternatives to Exceptions
- Error codes and `std::error_code` / `std::error_category`
- Return-value based error handling with `std::optional` and `std::expected` (C++23)
- When to use exceptions vs. return codes
- Performance implications of exceptions (zero-cost when not thrown, expensive when thrown)

#### Section 7.2.4 — Assertions and Contracts
- `assert`: catching programmer errors during development
- `static_assert`: catching errors at compile time
- Pre-conditions and post-conditions: defensive programming
- Contracts (future direction of C++)

---

### Module 7.3 — Type Erasure and Polymorphism Without Inheritance

#### Section 7.3.1 — The Limits of Classical Polymorphism
- Virtual functions require inheritance hierarchies
- Intrusive: types must be designed upfront to participate
- The concept of "duck typing": if it walks like a duck and quacks like a duck

#### Section 7.3.2 — Type Erasure Patterns
- `std::function` as a type erasure example
- `std::any` as generic type erasure
- Writing your own type-erased wrapper
- How this achieves runtime polymorphism without a base class

#### Section 7.3.3 — `std::variant` + `std::visit` as Polymorphism
- Closed set of types: you know all possibilities upfront
- The visitor pattern implemented with `std::visit`
- Comparing this approach to virtual functions: trade-offs

---

### Module 7.4 — Functional Programming Patterns in C++

#### Section 7.4.1 — Higher-Order Functions
- Functions that take functions as parameters
- Functions that return functions
- Combining with lambdas for expressive pipelines

#### Section 7.4.2 — Closures and Partial Application
- What a closure is: a lambda that captures state
- Simulating partial application with `std::bind` (older style)
- Simulating partial application with lambdas (modern, preferred)

#### Section 7.4.3 — Immutability and Value Semantics
- `const` everywhere: making data immutable by default
- Value types vs. reference types
- Why value semantics reduces bugs in concurrent code
- The functional pipeline: transform data through a chain of pure functions

---

### Module 7.5 — API Design and Best Practices

#### Section 7.5.1 — Designing Clear Interfaces
- Naming conventions: what the C++ community expects
- Parameter passing guidelines (the "Herb Sutter" flowchart): value, const ref, ref, pointer, smart pointer
- Return value guidelines: return by value (move semantics makes this free)
- Making interfaces hard to misuse: strong types, enums instead of bools

#### Section 7.5.2 — The "Don't Pay for What You Don't Use" Principle
- Zero-overhead abstractions: templates vs. virtual functions
- Avoiding hidden allocations
- Understanding when standard library features have hidden costs
- Benchmarking to verify assumptions

#### Section 7.5.3 — Code Organization and Module System
- Traditional header/source organization
- C++20 modules: the future of code organization
- Module basics: `export module`, `import`
- How modules improve compile times and encapsulation

---

### 🔨 Phase 7 Project — **Task Automation Framework**

```
Build a configurable task runner / workflow engine that:
  ✓ Defines a Task as any callable that accepts context and
    returns a Result<Output, Error>
  ✓ Tasks are composable: chain, parallel group, conditional branch
  ✓ Supports task pipelines: output of one feeds into the next
  ✓ Each task has: name, description, retry policy, timeout
  ✓ Implements a Pipeline builder using a fluent API:
    Pipeline::create("backup")
      .then(validate_config)
      .then(compress_files)
      .on_error(send_alert)
      .then(upload_to_cloud)
      .finally(cleanup)
  ✓ Uses lambdas and std::function for task definitions
  ✓ Uses std::variant for polymorphic task results
    (different tasks return different types)
  ✓ Uses std::optional for optional configuration
  ✓ Implements comprehensive error handling:
    per-task retry, pipeline abort, partial results
  ✓ Logs each step with timestamps using <chrono>
  ✓ Includes test pipelines that simulate file operations

Skills practiced:
  → lambdas, std::function, std::variant, std::visit,
    std::optional, error handling, move semantics,
    fluent API design, type erasure, RAII, functional patterns
```

---

---

## PHASE 8 — SYSTEMS & PERFORMANCE

> **"How do I write software that flies?"**

> You will learn multithreading, performance optimization, advanced memory techniques, and real-world software engineering practices that prepare you for professional C++ development.

---

### Module 8.1 — Concurrency: Doing Multiple Things at Once

#### Section 8.1.1 — Threads: The Basics
- What a thread is: an independent path of execution
- Creating threads and waiting for them to finish
- Passing data to threads and retrieving results
- Detaching threads: fire and forget (and why it is risky)
- Thread lifetimes and the danger of dangling references

#### Section 8.1.2 — Protecting Shared Data
- Race conditions: when two threads touch the same data
- Mutexes: locking shared resources
- Lock guards and scoped locks: RAII for mutexes
- Deadlock: when two threads wait for each other forever
- Deadlock prevention strategies: lock ordering, `std::scoped_lock`
- Shared mutexes: multiple readers or one writer

#### Section 8.1.3 — Communicating Between Threads
- Condition variables: waiting for something to happen
- The producer-consumer pattern
- Spurious wakeups: why you always check the condition in a loop
- `std::barrier` and `std::latch` (C++20): synchronization points

#### Section 8.1.4 — Futures and Promises: Asynchronous Results
- `std::async`: launching a task and getting the result later
- `std::future` and `std::promise`: the result-passing mechanism
- `std::packaged_task`: wrapping a callable for async execution
- Launch policies: truly async vs. deferred execution

#### Section 8.1.5 — Lock-Free Programming (Awareness Level)
- Atomic operations: `std::atomic` types
- What "lock-free" means and why it matters for performance
- Memory ordering: relaxed, acquire, release, sequential consistency
- Why lock-free programming is extremely difficult to get right
- When to use atomics vs. mutexes

---

### Module 8.2 — Memory Layout and Cache Performance

#### Section 8.2.1 — How the CPU Reads Memory
- Cache hierarchy: L1, L2, L3 — speed vs. size
- Cache lines: data is loaded in chunks (typically 64 bytes)
- Spatial locality: accessing nearby memory is fast
- Temporal locality: recently accessed memory stays in cache

#### Section 8.2.2 — Data-Oriented Design
- Array of Structures vs. Structure of Arrays
- Why iterating a vector of compact data is faster than chasing pointers
- Minimizing struct size: ordering fields by alignment
- Padding and alignment: what the compiler adds and why
- `alignas` and `alignof`: controlling alignment

#### Section 8.2.3 — Memory Pools and Custom Allocators
- Why `new`/`delete` can be slow (global heap contention, fragmentation)
- The allocator concept in the standard library
- Arena allocators: allocate fast, free all at once
- Pool allocators: fixed-size block allocation
- `std::pmr` (Polymorphic Memory Resources): C++17 allocator framework
- When custom allocators are worth the complexity

---

### Module 8.3 — Profiling and Optimization

#### Section 8.3.1 — Measuring Before Optimizing
- The cardinal rule: never optimize without profiling first
- Microbenchmarking with Google Benchmark or `<chrono>`
- CPU profilers: `perf`, `Instruments`, `VTune`
- Memory profilers: Valgrind (massif), AddressSanitizer, Heaptrack
- Compiler optimization reports: `-fopt-info`, `-Rpass`

#### Section 8.3.2 — Common Optimization Techniques
- Reducing unnecessary copies (move semantics, passing by reference)
- Reserving vector capacity when size is known
- Avoiding repeated heap allocations (reuse buffers)
- Branch prediction: helping the CPU guess right
- Loop optimization: strength reduction, hoisting invariants
- Small string optimization: how `std::string` avoids heap allocation for short strings

#### Section 8.3.3 — Compiler Explorer and Understanding Assembly
- Using Godbolt Compiler Explorer to see what the compiler generates
- Reading basic x86 assembly: moves, jumps, calls
- How to verify that your abstraction was optimized away
- Comparing optimization levels: what `-O2` actually does

---

### Module 8.4 — File and Network I/O

#### Section 8.4.1 — File Streams
- Reading and writing text files with `ifstream` and `ofstream`
- Binary file I/O: reading and writing raw bytes
- String streams: treating strings as streams
- Error checking on file operations
- `std::filesystem` (C++17): paths, directory traversal, file operations

#### Section 8.4.2 — Serialization
- What serialization is: converting objects to bytes and back
- Text-based formats: JSON parsing and generation
- Binary formats: designing compact, versioned wire formats
- Third-party libraries: nlohmann/json, Protocol Buffers, FlatBuffers

#### Section 8.4.3 — Network Programming (Overview)
- Sockets in C++ (POSIX or platform-specific)
- Third-party networking libraries: Asio (Boost.Asio), POCO
- Building a simple client and server
- Asynchronous I/O with Asio: event-driven networking

---

### Module 8.5 — Testing, Tooling, and Professional Practices

#### Section 8.5.1 — Unit Testing
- Google Test framework: test cases, assertions, fixtures
- Test-driven development: write the test first
- Mocking dependencies with Google Mock
- Code coverage measurement and what to aim for

#### Section 8.5.2 — Static Analysis and Sanitizers
- Compiler warnings as first line of defense
- Clang-Tidy: automated code quality checks
- AddressSanitizer: detecting memory errors at runtime
- UndefinedBehaviorSanitizer: catching undefined behavior
- ThreadSanitizer: detecting data races

#### Section 8.5.3 — Build Systems and Package Management
- CMake in depth: targets, properties, generator expressions
- Creating libraries: static and shared
- Finding and linking external dependencies
- Package managers: Conan, vcpkg
- Continuous integration: building and testing on every commit

#### Section 8.5.4 — Documentation and Code Style
- Doxygen: generating API documentation from comments
- Coding standards: Google C++ Style Guide, C++ Core Guidelines
- Clang-Format: automatic code formatting
- Code review best practices

---

### Module 8.6 — Design Patterns in C++

#### Section 8.6.1 — Creational Patterns
- Factory Method: creating objects without specifying exact types
- Abstract Factory: families of related objects
- Builder: constructing complex objects step by step
- Singleton: ensuring only one instance (and why it is often overused)

#### Section 8.6.2 — Structural Patterns
- Adapter: making incompatible interfaces work together
- Decorator: adding behavior to objects dynamically
- Facade: simplifying a complex subsystem
- PIMPL (Pointer to Implementation): hiding implementation details and improving compile times

#### Section 8.6.3 — Behavioral Patterns
- Observer: notifying interested parties when something changes
- Strategy: swapping algorithms at runtime
- Command: encapsulating actions as objects
- State: changing behavior based on internal state
- Iterator: the pattern behind C++ iterators

---

### 🔨 Phase 8 Project — **Multi-Threaded Web Crawler**

```
Build a concurrent web crawler / site mapper that:
  ✓ Accepts a starting URL and a maximum crawl depth
  ✓ Fetches web pages concurrently using a configurable thread pool
  ✓ Parses HTML to extract links (using a lightweight parsing approach)
  ✓ Builds a site map: directed graph of page → linked pages
  ✓ Avoids visiting the same URL twice (thread-safe visited set)
  ✓ Respects a configurable rate limit (e.g., max 5 requests/second)
  ✓ Implements a producer-consumer architecture:
    - URL frontier queue (thread-safe)
    - Worker threads that fetch, parse, and enqueue new URLs
    - Coordinator thread that monitors progress
  ✓ Measures and displays: pages crawled, crawl speed,
    average page size, link distribution
  ✓ Outputs the site map as a JSON file
  ✓ Handles errors gracefully: timeouts, invalid URLs,
    non-HTML content, network failures
  ✓ Uses <chrono> for timing, <filesystem> for output
  ✓ Built with CMake, tested with Google Test
  ✓ Profiled to identify and fix bottlenecks
  ✓ Verified with ThreadSanitizer for race conditions
  ✓ Documented with usage instructions and architecture overview

Skills practiced:
  → threads, mutexes, condition variables, async,
    thread pool, producer-consumer, atomic operations,
    networking, JSON serialization, filesystem,
    CMake, testing, profiling, sanitizers,
    design patterns (strategy, observer, command),
    data-oriented design, error handling
```

---

---

## Recommended Resources

| Resource | Type | Best For |
|---|---|---|
| **"A Tour of C++" — Bjarne Stroustrup** | Book | Quick, authoritative overview from the creator of C++ |
| **"Programming: Principles and Practice Using C++" — Stroustrup** | Book | Best first book if you are completely new to programming |
| **"C++ Primer" — Lippman, Lajoie, Moo (5th ed.)** | Book | Thorough, comprehensive textbook for serious learners |
| **"Effective Modern C++" — Scott Meyers** | Book | Essential intermediate/advanced best practices (C++11/14) |
| **"The C++ Programming Language" — Stroustrup (4th ed.)** | Book | The definitive reference (encyclopedic, not for beginners) |
| **learncpp.com** | Free Online | Best free online tutorial, regularly updated |
| **C++ Core Guidelines** | Free Online | Official best practices by Stroustrup and Sutter |
| **CppReference.com** | Free Online | The definitive standard library reference |
| **Jason Turner — C++ Weekly (YouTube)** | Video | Short, focused episodes on modern C++ features |
| **CppCon talks (YouTube)** | Video | Conference talks from world experts |
| **Compiler Explorer (godbolt.org)** | Tool | See what assembly your C++ generates |
| **Exercism C++ Track** | Practice | Structured exercises with mentoring |

---

## How C++ Phases Build on Each Other

```
 Phase 1: "I can write basic programs"
     │
     │   You understand: variables, types, I/O, control flow
     │
 Phase 2: "I can organize code and data"
     │
     │   You understand: functions, arrays, vectors, strings, structs
     │
 Phase 3: "I can model domains with classes"
     │
     │   You understand: encapsulation, inheritance, polymorphism
     │
 Phase 4: "I manage resources safely"
     │
     │   You understand: RAII, smart pointers, move semantics
     │
 Phase 5: "I write code that works with any type"
     │
     │   You understand: templates, concepts, compile-time computation
     │
 Phase 6: "I leverage the standard library"
     │
     │   You understand: containers, algorithms, iterators, utilities
     │
 Phase 7: "I write idiomatic modern C++"
     │
     │   You understand: lambdas, error handling, type erasure, API design
     │
 Phase 8: "I build production-grade systems"
     │
     │   You understand: concurrency, performance, tooling, patterns
     │
     ▼
 MASTERY: You can design, build, optimize, test, and maintain
          complex C++ systems with confidence.
```

---

## Final Advice

```
  ┌───────────────────────────────────────────────────────────┐
  │                                                           │
  │   1. LEARN C++ AS C++, not as "C with classes."           │
  │      Embrace RAII, smart pointers, and the standard       │
  │      library from the start. Forget manual new/delete.    │
  │                                                           │
  │   2. COMPILE with every warning turned on:                │
  │      -Wall -Wextra -Wpedantic -Wshadow -Wconversion      │
  │      Treat warnings as errors: -Werror                    │
  │                                                           │
  │   3. USE SANITIZERS from day one:                         │
  │      -fsanitize=address,undefined                         │
  │      They catch bugs that would take hours to find.       │
  │                                                           │
  │   4. PREFER the standard library over hand-rolled code.   │
  │      std::vector over raw arrays.                         │
  │      std::string over char arrays.                        │
  │      std::unique_ptr over raw new/delete.                 │
  │      Algorithms over manual loops.                        │
  │                                                           │
  │   5. BUILD THE PROJECTS. Every single one.                │
  │      Reading about C++ is not learning C++.               │
  │      Wrestling with compiler errors is learning C++.      │
  │                                                           │
  │   6. READ other people's code:                            │
  │      abseil (Google), folly (Facebook), LLVM,             │
  │      JSON for Modern C++ (nlohmann).                      │
  │                                                           │
  │   7. C++ is enormous. You do NOT need to know everything. │
  │      Focus on writing clear, correct, maintainable code.  │
  │      Learn advanced features when you need them.          │
  │                                                           │
  └───────────────────────────────────────────────────────────┘
```