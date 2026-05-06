## Roadmap Overview

```
Phase 1 ▸ Foundation          (Weeks 1–3)     → "What is C and how does it work?"
Phase 2 ▸ Core Language        (Weeks 4–7)     → "How do I write real programs?"
Phase 3 ▸ Memory Mastery       (Weeks 8–11)    → "How does memory actually work?"
Phase 4 ▸ Data Structures      (Weeks 12–15)   → "How do I organize complex data?"
Phase 5 ▸ Systems Programming  (Weeks 16–19)   → "How do I talk to the OS?"
Phase 6 ▸ Advanced C           (Weeks 20–24)   → "How do I write production-grade C?"

Total: ~24 weeks at 10–15 hours/week
```

```
                    YOU ARE HERE
                         │
                         ▼
    ┌─────────────────────────────────────────────────┐
    │              PHASE 1: FOUNDATION                │
    │         Variables, Types, Control Flow           │
    └──────────────────────┬──────────────────────────┘
                           │
                           ▼
    ┌─────────────────────────────────────────────────┐
    │            PHASE 2: CORE LANGUAGE               │
    │       Functions, Arrays, Strings, Structs       │
    └──────────────────────┬──────────────────────────┘
                           │
                           ▼
    ┌─────────────────────────────────────────────────┐
    │           PHASE 3: MEMORY MASTERY               │
    │     Pointers, Dynamic Allocation, Debugging     │
    └──────────────────────┬──────────────────────────┘
                           │
                           ▼
    ┌─────────────────────────────────────────────────┐
    │          PHASE 4: DATA STRUCTURES               │
    │     Linked Lists, Trees, Hash Tables, Graphs    │
    └──────────────────────┬──────────────────────────┘
                           │
                           ▼
    ┌─────────────────────────────────────────────────┐
    │        PHASE 5: SYSTEMS PROGRAMMING             │
    │     File I/O, Processes, Threads, Sockets       │
    └──────────────────────┬──────────────────────────┘
                           │
                           ▼
    ┌─────────────────────────────────────────────────┐
    │            PHASE 6: ADVANCED C                  │
    │   Preprocessor, Optimization, Build Systems     │
    └─────────────────────────────────────────────────┘
                           │
                           ▼
                      MASTERY ✓
```

---

---

## PHASE 1 — FOUNDATION

> **Goal**: Understand how C works at a fundamental level, set up your environment, and write your first programs.

---

### Module 1.1 — Environment Setup & How C Works

#### Section 1.1.1 — How C Programs Run
- What C is and why it still matters (OS kernels, embedded, performance)
- Compiled vs. interpreted languages
- The compilation pipeline: Source → Preprocessor → Compiler → Assembler → Linker → Executable
- What the CPU actually executes (brief mental model of registers, stack, instructions)

#### Section 1.1.2 — Setting Up Your Tools
- Installing a compiler: `gcc` (Linux/Mac) or `MinGW` / WSL (Windows)
- Choosing an editor: VS Code with C/C++ extension (recommended for beginners)
- Compiling from the command line: `gcc -o program program.c`
- Useful compiler flags from day one: `-Wall -Wextra -std=c17`
- Running and debugging with `gdb` (basic: run, break, print, step)

#### Section 1.1.3 — Your First C Program
- Anatomy of `hello.c`: `#include`, `main()`, `return 0`
- What `#include <stdio.h>` actually does
- What `main()` is and why it returns `int`
- `printf()` basics: printing strings and newlines

```c
#include <stdio.h>

int main(void) {
    printf("Hello, World!\n");
    return 0;
}
```

---

### Module 1.2 — Variables, Data Types & Operators

#### Section 1.2.1 — Primitive Data Types
- `char` (1 byte), `short` (2), `int` (4), `long` (4/8), `long long` (8)
- `float` (4 bytes), `double` (8 bytes)
- `signed` vs `unsigned` — range implications
- `sizeof()` operator — measuring type sizes
- Why sizes are platform-dependent (ILP32 vs LP64)

#### Section 1.2.2 — Variables & Constants
- Declaration vs. initialization
- Naming rules and conventions (`snake_case` in C)
- `const` keyword
- `#define` preprocessor constants
- `enum` for named integer constants

#### Section 1.2.3 — Operators
- Arithmetic: `+  -  *  /  %`
- Relational: `==  !=  <  >  <=  >=`
- Logical: `&&  ||  !`
- Bitwise: `&  |  ^  ~  <<  >>`
- Assignment: `=  +=  -=  *=  /=  %=  &=  |=  ^=  <<=  >>=`
- Increment/Decrement: `++i` vs `i++` (prefix vs postfix)
- Ternary: `condition ? a : b`
- Operator precedence table (and why you should use parentheses)

#### Section 1.2.4 — Type Conversion
- Implicit conversions (integer promotion rules)
- Explicit casting: `(double)x`
- Dangerous casts and data loss (`int` ← `double`)
- The integer promotion trap: `unsigned + signed`

---

### Module 1.3 — Input/Output

#### Section 1.3.1 — Formatted Output with `printf()`
- Format specifiers: `%d  %u  %ld  %f  %lf  %c  %s  %x  %o  %p  %%`
- Width and precision: `%10d  %-10d  %.2f  %08x`
- Escape sequences: `\n  \t  \\  \"  \0`

#### Section 1.3.2 — Formatted Input with `scanf()`
- Reading integers, floats, characters, strings
- The `&` (address-of) operator — why it is needed
- Return value of `scanf()` — always check it
- Buffer overflow risk with `%s` (preview of why C is dangerous)
- Clearing the input buffer: `while(getchar() != '\n');`

#### Section 1.3.3 — Character I/O
- `getchar()` and `putchar()`
- Reading a full line: `fgets(buf, size, stdin)` (safe) vs `gets()` (never use)

---

### Module 1.4 — Control Flow

#### Section 1.4.1 — Conditional Statements
- `if`, `else if`, `else`
- Nested conditionals
- `switch` / `case` / `default` / `break` / fall-through behavior
- Dangling else problem

#### Section 1.4.2 — Loops
- `while` loop
- `do...while` loop
- `for` loop (initialization; condition; update)
- Nested loops
- `break` — exit the loop
- `continue` — skip to next iteration
- Infinite loops: `for(;;)` and `while(1)`

#### Section 1.4.3 — `goto` and Labels
- What `goto` is
- Why it is almost always avoided
- The one acceptable use: error cleanup in systems code

---

### 🔨 Phase 1 Project — **Interactive Calculator**

```
Build a command-line calculator that:
  ✓ Displays a menu: Add, Subtract, Multiply, Divide, Modulo, Exit
  ✓ Reads two numbers from the user (support both int and float mode)
  ✓ Performs the selected operation
  ✓ Handles division by zero gracefully
  ✓ Loops until the user selects Exit
  ✓ Tracks and displays a running history of calculations
  ✓ Supports chained operations (use the last result as the next input)

Skills practiced:
  → variables, types, operators, printf/scanf, if/else, switch, loops
```

---

---

## PHASE 2 — CORE LANGUAGE

> **Goal**: Master functions, arrays, strings, and structs — the building blocks of any C program.

---

### Module 2.1 — Functions

#### Section 2.1.1 — Function Basics
- Declaration (prototype) vs. definition
- Parameters and return values
- `void` functions and `void` parameters
- Why prototypes matter (declare before use)
- Header file convention (`.h` for declarations, `.c` for definitions)

#### Section 2.1.2 — How Function Calls Work
- The call stack — stack frames, local variables, return addresses
- Pass-by-value semantics (C always copies)
- Returning values vs. modifying through pointers (preview)
- Stack overflow from infinite recursion

#### Section 2.1.3 — Scope & Lifetime
- Local (block) scope
- File scope (`static` at file level)
- `static` local variables — persistent across calls
- `extern` keyword — sharing variables across files
- Variable shadowing

#### Section 2.1.4 — Recursion
- How recursion uses the stack
- Base case + recursive case
- Classic examples: factorial, Fibonacci, power
- Tail recursion (concept — C compilers may or may not optimize)
- When to use recursion vs. iteration

---

### Module 2.2 — Arrays

#### Section 2.2.1 — One-Dimensional Arrays
- Declaration and initialization: `int arr[5] = {1, 2, 3, 4, 5};`
- Zero-based indexing
- Iterating with `for` loops
- Arrays and memory: contiguous storage
- No bounds checking in C — the #1 source of bugs
- Partial initialization and zero-fill: `int arr[100] = {0};`

#### Section 2.2.2 — Multidimensional Arrays
- 2D arrays: `int matrix[3][4];`
- Row-major memory layout
- Iterating with nested loops
- Initializing with nested braces

#### Section 2.2.3 — Arrays and Functions
- Passing arrays to functions (decays to pointer)
- Why you must pass the size separately
- Modifying arrays inside functions (they ARE modified — no copy)
- `const` arrays as parameters: `void print(const int arr[], int size);`

#### Section 2.2.4 — Variable-Length Arrays (VLAs)
- C99 VLAs: `int arr[n];`
- Stack allocation — dangerous for large `n`
- Why they were made optional in C11 (and why many avoid them)

---

### Module 2.3 — Strings

#### Section 2.3.1 — C Strings Fundamentals
- Strings as `char` arrays terminated by `\0` (null terminator)
- String literals: `"hello"` — stored in read-only memory
- `char str[] = "hello";` (mutable copy) vs. `char *str = "hello";` (pointer to read-only)
- Manual null termination when building strings

#### Section 2.3.2 — String Library Functions (`<string.h>`)
- `strlen()` — length (does NOT count `\0`)
- `strcpy()` / `strncpy()` — copy
- `strcat()` / `strncat()` — concatenate
- `strcmp()` / `strncmp()` — compare (returns 0 if equal)
- `strchr()` / `strrchr()` — find character
- `strstr()` — find substring
- `strtok()` — tokenize (destructive, stateful — tricky)

#### Section 2.3.3 — String Conversions
- `atoi()`, `atof()`, `atol()` — simple but no error checking
- `strtol()`, `strtod()` — robust with error detection
- `sprintf()` / `snprintf()` — format into a string buffer
- `sscanf()` — parse from a string

#### Section 2.3.4 — Common String Pitfalls
- Buffer overflow: writing past array bounds
- Missing null terminator
- Modifying string literals (undefined behavior)
- Off-by-one: forgetting to allocate space for `\0`
- Using `==` instead of `strcmp()` to compare strings

---

### Module 2.4 — Structures, Unions & Enums

#### Section 2.4.1 — Structures (`struct`)
- Defining a struct
- Declaring and initializing struct variables
- Accessing members with `.` operator
- Designated initializers: `{.name = "Alice", .age = 30}`
- Nested structures
- Arrays of structures

#### Section 2.4.2 — Structures and Functions
- Passing structs by value (entire copy — expensive for large structs)
- Passing structs by pointer: `void print_student(const Student *s);`
- Arrow operator: `s->name` (equivalent to `(*s).name`)
- Returning structs from functions

#### Section 2.4.3 — `typedef`
- Creating type aliases: `typedef struct { ... } Student;`
- Simplifying complex declarations
- Convention: `typedef` for opaque types, raw `struct` for transparent ones

#### Section 2.4.4 — Unions
- Syntax and memory layout (all members share the same memory)
- Use case: type-punning, variant types
- Tagged unions: `struct { enum type tag; union { int i; float f; char *s; } value; };`

#### Section 2.4.5 — Bit Fields
- Packing flags into a struct: `unsigned int is_active : 1;`
- Memory savings for embedded systems
- Portability concerns

#### Section 2.4.6 — Enums (Deeper)
- Named constants with `enum`
- Underlying type is `int`
- Enum vs. `#define` — when to use which

---

### Module 2.5 — Multi-File Programs

#### Section 2.5.1 — Compilation Units
- What a translation unit is
- Separating declarations (`.h`) from definitions (`.c`)
- Include guards: `#ifndef / #define / #endif` (or `#pragma once`)

#### Section 2.5.2 — Linking
- How the linker resolves symbols
- `extern` declarations
- `static` functions and variables (internal linkage — file-private)
- Duplicate symbol errors and how to fix them

#### Section 2.5.3 — Building Multi-File Projects
- Compiling: `gcc -c file1.c -o file1.o && gcc -c file2.c -o file2.o`
- Linking: `gcc file1.o file2.o -o program`
- Introduction to `Makefile` (basic targets, dependencies, variables)

---

### 🔨 Phase 2 Project — **Student Records System**

```
Build a student record management system that:
  ✓ Defines a Student struct (name, ID, grades array, GPA)
  ✓ Supports up to 100 students (static array of structs)
  ✓ Menu-driven: Add, Search, Update, Delete, List All, Sort, Exit
  ✓ Search by name (substring match) and by ID
  ✓ Sort by name (alphabetical) or by GPA (descending)
  ✓ Calculate GPA from grades array automatically
  ✓ Save records to a text file and load on startup
  ✓ Split across multiple files:
      - main.c (menu loop)
      - student.h / student.c (struct + functions)
      - file_io.h / file_io.c (save/load)
      - utils.h / utils.c (input validation, sorting)
  ✓ Compile using a Makefile

Skills practiced:
  → functions, arrays, strings, structs, multi-file, Makefile, file I/O basics
```

---

---

## PHASE 3 — MEMORY MASTERY

> **Goal**: Deeply understand pointers, dynamic memory allocation, and how to debug memory issues. This is what separates C beginners from competent C programmers.

---

### Module 3.1 — Pointers Fundamentals

#### Section 3.1.1 — What Pointers Are
- A pointer is a variable that stores a memory address
- Declaration: `int *p;` — `p` is a pointer to an `int`
- Address-of operator: `&x` — get the address of `x`
- Dereference operator: `*p` — access the value at the address
- NULL pointer: `NULL` (always initialize pointers)
- Visualizing memory: drawing boxes with addresses and values

```
  Variable x:       Pointer p:
  ┌─────────┐       ┌─────────────┐
  │   42    │       │  0x7FFE0010 │──────► address of x
  └─────────┘       └─────────────┘
  addr: 0x7FFE0010
```

#### Section 3.1.2 — Pointer Arithmetic
- `p + 1` advances by `sizeof(*p)` bytes (not 1 byte)
- Pointer subtraction: `p2 - p1` gives number of elements between
- Array-pointer equivalence: `arr[i]` is `*(arr + i)`
- Why pointer arithmetic only works within arrays (undefined behavior otherwise)

#### Section 3.1.3 — Pointers and Functions
- Pass-by-pointer to modify caller's variables: `void swap(int *a, int *b);`
- Pointer to pointer: `int **pp;` — why it is needed (e.g., modifying a pointer itself)
- Returning pointers from functions — danger of returning local addresses

#### Section 3.1.4 — Pointers and Arrays (Deep Dive)
- Array name decays to pointer to first element
- `int arr[5]` vs `int *p` — what is different (sizeof, addressof, assignment)
- Pointer to array: `int (*p)[5]` vs array of pointers: `int *p[5]`
- Iterating arrays with pointer arithmetic

#### Section 3.1.5 — Pointers and Strings
- `char *s = "hello";` — pointer to string literal
- Why modifying string literals is undefined behavior
- String functions that return pointers (`strchr`, `strstr`)
- Building strings manually with pointer manipulation

---

### Module 3.2 — Dynamic Memory Allocation

#### Section 3.2.1 — The Heap vs. The Stack
- Stack: automatic, fast, limited size, LIFO
- Heap: manual, larger, slower, fragmentation risk
- Memory layout of a C program: Text → Data → BSS → Heap ↕ ... ↕ Stack

```
┌──────────────────┐ High Address
│      Stack       │ ← Local variables, function frames
│        ↓         │
│                  │
│        ↑         │
│      Heap        │ ← malloc/calloc/realloc
├──────────────────┤
│   BSS (uninit)   │ ← Uninitialized globals
├──────────────────┤
│   Data (init)    │ ← Initialized globals, static
├──────────────────┤
│   Text (code)    │ ← Machine instructions (read-only)
└──────────────────┘ Low Address
```

#### Section 3.2.2 — `malloc`, `calloc`, `realloc`, `free`
- `malloc(size)` — allocate `size` bytes, uninitialized
- `calloc(count, size)` — allocate and zero-initialize
- `realloc(ptr, new_size)` — resize (may move the block)
- `free(ptr)` — release memory
- Always check for `NULL` return (allocation failure)
- Always `free()` what you `malloc()` — no garbage collector

```c
int *arr = malloc(10 * sizeof(int));
if (arr == NULL) {
    perror("malloc failed");
    exit(EXIT_FAILURE);
}
// ... use arr ...
free(arr);
arr = NULL;  // prevent dangling pointer
```

#### Section 3.2.3 — Dynamic Arrays
- Growing an array with `realloc()` (doubling strategy)
- Shrinking arrays
- Implementing a basic `vector` (dynamic array with size + capacity)

#### Section 3.2.4 — Dynamic Strings
- Allocating strings: `char *s = malloc(strlen(src) + 1);`
- `strdup()` (POSIX, not standard C — know the alternative)
- Building strings of unknown length dynamically

#### Section 3.2.5 — Dynamic 2D Arrays
- Array of pointers: `int **matrix = malloc(rows * sizeof(int *));`
- Each row separately allocated
- Contiguous block approach: `int *matrix = malloc(rows * cols * sizeof(int));`
- Freeing in reverse order of allocation

---

### Module 3.3 — Advanced Pointer Topics

#### Section 3.3.1 — Function Pointers
- Declaration: `int (*fp)(int, int);`
- Assigning: `fp = &add;` (or just `fp = add;`)
- Calling: `fp(3, 4);` or `(*fp)(3, 4);`
- Use cases: callbacks, strategy pattern, dispatch tables
- `qsort()` as a real-world example of function pointer usage

#### Section 3.3.2 — `void *` (Generic Pointers)
- Can point to any type
- Must be cast before dereferencing
- Used heavily in generic C APIs (`malloc` returns `void *`, `qsort` accepts `void *`)
- `memcpy()`, `memset()`, `memmove()` — generic memory operations

#### Section 3.3.3 — `const` and Pointers
- `const int *p` — pointer to constant int (can't modify value)
- `int * const p` — constant pointer to int (can't modify pointer)
- `const int * const p` — both constant
- Read declarations right-to-left

#### Section 3.3.4 — Common Pointer Bugs
- Dangling pointer: using a pointer after `free()`
- Double free: calling `free()` twice on the same pointer
- Memory leak: losing the last reference to allocated memory
- Buffer overflow/underflow: writing out of bounds
- Uninitialized pointer: dereferencing garbage
- Use-after-free

---

### Module 3.4 — Memory Debugging

#### Section 3.4.1 — Valgrind
- Installing and running: `valgrind --leak-check=full ./program`
- Reading Valgrind output: definitely lost, indirectly lost, possibly lost
- Detecting invalid reads/writes
- Detecting use of uninitialized values

#### Section 3.4.2 — AddressSanitizer (ASan)
- Compile-time instrumentation: `gcc -fsanitize=address -g program.c`
- Detects: heap buffer overflow, stack buffer overflow, use-after-free, double-free, memory leaks
- Much faster than Valgrind for development

#### Section 3.4.3 — GDB for Memory Debugging
- Inspecting pointer values: `print p`, `print *p`, `print p[0]@10`
- Watchpoints: break when a memory address changes
- Examining raw memory: `x/16xb address`

---

### 🔨 Phase 3 Project — **Custom Memory Allocator**

```
Build your own simple memory allocator that:
  ✓ Implements my_malloc(), my_free(), my_calloc(), my_realloc()
  ✓ Uses sbrk() or a large static buffer as the backing store
  ✓ Maintains a free list (linked list of free blocks)
  ✓ Implements first-fit allocation strategy
  ✓ Coalesces adjacent free blocks on free()
  ✓ Tracks allocation statistics (total allocated, total freed, peak usage)
  ✓ Detects double-free and prints a warning
  ✓ Passes a test suite that allocates/frees in random patterns
  ✓ Compile and test with Valgrind and ASan to verify zero leaks

Skills practiced:
  → pointers, pointer arithmetic, dynamic allocation, void*,
    structs, linked list concepts, memory layout understanding
```

---

---

## PHASE 4 — DATA STRUCTURES IN C

> **Goal**: Implement classic data structures from scratch using pointers and dynamic memory. This is where C mastery is forged.

---

### Module 4.1 — Linked Lists

#### Section 4.1.1 — Singly Linked List
- Node structure: `struct Node { int data; struct Node *next; };`
- Creating nodes with `malloc`
- Operations: insert (head, tail, at index), delete, search, print, reverse
- Time complexity for each operation

#### Section 4.1.2 — Doubly Linked List
- Node with `prev` and `next` pointers
- Bidirectional traversal
- Insert and delete operations (simpler than singly linked for deletion)

#### Section 4.1.3 — Circular Linked List
- Last node points back to head
- Use case: round-robin scheduling
- Detecting cycles (Floyd's algorithm — tortoise and hare)

#### Section 4.1.4 — Generic Linked List
- Using `void *data` for type-agnostic lists
- Function pointers for comparison, printing, freeing data
- Building a reusable linked list library

---

### Module 4.2 — Stacks & Queues

#### Section 4.2.1 — Stack
- Array-based implementation (fixed capacity)
- Linked list–based implementation (dynamic)
- Operations: `push`, `pop`, `peek`, `is_empty`, `is_full`
- Applications: expression evaluation, balanced parentheses, undo system

#### Section 4.2.2 — Queue
- Circular array–based implementation
- Linked list–based implementation
- Operations: `enqueue`, `dequeue`, `peek`, `is_empty`
- Priority queue (sorted insert or heap-based)

---

### Module 4.3 — Hash Tables

#### Section 4.3.1 — Hash Functions
- What makes a good hash function (uniform distribution, fast)
- DJB2 hash, FNV-1a hash
- Hash for integers vs. hash for strings

#### Section 4.3.2 — Collision Resolution
- Chaining (linked list per bucket)
- Open addressing: linear probing, quadratic probing
- Load factor and rehashing (growing the table)

#### Section 4.3.3 — Implementation
- `struct HashTable { Entry **buckets; int capacity; int size; };`
- Operations: `put`, `get`, `delete`, `contains`, `keys`
- Handling `strdup` for key ownership
- Proper cleanup: freeing all entries and keys

---

### Module 4.4 — Trees

#### Section 4.4.1 — Binary Search Tree (BST)
- Node: `struct TreeNode { int key; TreeNode *left, *right; };`
- Insert, search, delete (3 cases: leaf, one child, two children)
- In-order, pre-order, post-order traversal (recursive)
- Finding min, max, height

#### Section 4.4.2 — Balanced Trees (Conceptual)
- Why unbalanced BSTs degrade to O(n)
- AVL tree concept (balance factor, rotations)
- Red-black tree concept (used in Linux kernel)
- When to use a library vs. implement your own

#### Section 4.4.3 — Heap (Priority Queue)
- Array-based binary min-heap / max-heap
- `insert` (bubble up), `extract_min` (bubble down)
- `heapify` — building a heap in O(n)
- Heap sort algorithm

---

### Module 4.5 — Graphs (Introduction)

#### Section 4.5.1 — Representation
- Adjacency matrix: `int graph[V][V];`
- Adjacency list: `struct Graph { Node **adj_lists; int num_vertices; };`
- Trade-offs: memory vs. lookup speed

#### Section 4.5.2 — Traversal
- Breadth-first search (BFS) using a queue
- Depth-first search (DFS) using recursion or a stack

---

### Module 4.6 — Sorting & Searching

#### Section 4.6.1 — Sorting Algorithms (Implement Each)
- Bubble sort, selection sort, insertion sort — O(n²) but simple
- Merge sort — O(n log n), stable, great for linked lists
- Quick sort — O(n log n) average, in-place
- Using `qsort()` from `<stdlib.h>` with custom comparators

#### Section 4.6.2 — Searching
- Linear search — O(n)
- Binary search — O(log n), requires sorted data
- Using `bsearch()` from `<stdlib.h>`

---

### 🔨 Phase 4 Project — **In-Memory Key-Value Database**

```
Build a command-line key-value store that:
  ✓ Stores string keys → string values in a hash table
  ✓ Supports commands: SET key value, GET key, DEL key,
    KEYS (list all), COUNT, CLEAR, EXIT
  ✓ Handles hash collisions via chaining
  ✓ Auto-resizes (rehashes) when load factor exceeds 0.75
  ✓ Supports TTL (time-to-live) per key using a min-heap
    for expiration tracking
  ✓ Logs all operations to a write-ahead log (append-only file)
  ✓ Can replay the log on startup to restore state
  ✓ Displays internal stats: bucket distribution, collision count,
    longest chain, memory usage estimate
  ✓ All memory properly freed on exit (verify with Valgrind)

Skills practiced:
  → hash tables, linked lists, heap, dynamic arrays, file I/O,
    string manipulation, memory management, function pointers
```

---

---

## PHASE 5 — SYSTEMS PROGRAMMING

> **Goal**: Learn how C interfaces with the operating system — files, processes, threads, and network sockets. This is where C's true power lives.

---

### Module 5.1 — File I/O (Advanced)

#### Section 5.1.1 — Standard I/O (`<stdio.h>`)
- `fopen`, `fclose`, `fflush`
- Modes: `"r"`, `"w"`, `"a"`, `"rb"`, `"wb"`, `"r+"`
- `fprintf`, `fscanf`, `fputs`, `fgets`
- `fread`, `fwrite` — binary I/O
- `fseek`, `ftell`, `rewind` — random access
- `feof` vs checking return values (the `feof` trap)

#### Section 5.1.2 — Low-Level I/O (POSIX)
- File descriptors: `0` (stdin), `1` (stdout), `2` (stderr)
- `open()`, `close()`, `read()`, `write()`, `lseek()`
- `O_RDONLY`, `O_WRONLY`, `O_CREAT`, `O_TRUNC`, `O_APPEND`
- File permissions: `0644`, `0755`
- Buffered (`stdio.h`) vs unbuffered (POSIX) I/O

#### Section 5.1.3 — File System Operations
- `stat()` — file metadata (size, permissions, timestamps)
- `opendir()`, `readdir()`, `closedir()` — directory traversal
- `rename()`, `remove()`, `mkdir()`
- Symbolic links: `symlink()`, `readlink()`

#### Section 5.1.4 — Memory-Mapped Files
- `mmap()` — map a file into memory
- `munmap()` — unmap
- Use cases: fast file access, shared memory between processes
- `msync()` — flush changes to disk

---

### Module 5.2 — Process Management

#### Section 5.2.1 — Process Basics
- What a process is (PID, address space, file descriptor table)
- `getpid()`, `getppid()`
- `fork()` — creating a child process (returns twice!)
- Parent vs. child: return value of `fork()`
- `wait()`, `waitpid()` — reaping child processes
- Zombie and orphan processes

#### Section 5.2.2 — Executing Programs
- `exec` family: `execl`, `execv`, `execvp`, `execve`
- `fork()` + `exec()` pattern — how shells work
- `system()` — simple but insecure

#### Section 5.2.3 — Inter-Process Communication (IPC)
- Pipes: `pipe()`, `dup2()` for redirection
- Named pipes (FIFOs): `mkfifo()`
- Signals: `signal()`, `sigaction()`, `kill()`
- Common signals: `SIGINT`, `SIGTERM`, `SIGKILL`, `SIGCHLD`, `SIGSEGV`
- Shared memory: `shmget()`, `shmat()`, `shmdt()` (or POSIX `shm_open`)

---

### Module 5.3 — Multithreading (pthreads)

#### Section 5.3.1 — Thread Basics
- `pthread_create()`, `pthread_join()`, `pthread_exit()`
- Thread vs. process: shared memory, lighter weight
- Passing arguments to threads (via `void *`)
- Returning values from threads

#### Section 5.3.2 — Synchronization
- Race conditions — why they happen
- Mutex: `pthread_mutex_lock()`, `pthread_mutex_unlock()`
- Deadlock: causes and prevention (lock ordering)
- Condition variables: `pthread_cond_wait()`, `pthread_cond_signal()`
- Producer-consumer pattern implementation

#### Section 5.3.3 — Thread Safety
- Thread-safe vs. thread-unsafe functions
- `static` local variables are NOT thread-safe
- Thread-local storage: `_Thread_local` (C11) or `__thread` (GCC)
- Atomic operations: `<stdatomic.h>` (C11)
- Read-write locks: `pthread_rwlock_t`

#### Section 5.3.4 — Thread Pool Pattern
- Why: avoid thread creation overhead
- Design: fixed number of worker threads + shared job queue
- Implementation using mutex + condition variable

---

### Module 5.4 — Network Programming (Sockets)

#### Section 5.4.1 — Socket Basics
- TCP vs UDP
- `socket()`, `bind()`, `listen()`, `accept()`, `connect()`
- `send()`, `recv()`, `close()`
- `struct sockaddr_in`, `htons()`, `inet_pton()`
- Byte order: big-endian (network) vs little-endian (host)

#### Section 5.4.2 — TCP Client
- Connect to a server
- Send an HTTP GET request manually
- Read and print the response

#### Section 5.4.3 — TCP Server
- Bind to a port, listen, accept connections
- Single-client server (blocking)
- Multi-client server: `fork()`-per-connection
- Multi-client server: thread-per-connection
- Multi-client server: `select()` / `poll()` / `epoll()` (event-driven)

---

### 🔨 Phase 5 Project — **Concurrent HTTP Server**

```
Build a minimal HTTP/1.1 server that:
  ✓ Listens on a configurable port (default 8080)
  ✓ Accepts TCP connections via sockets
  ✓ Parses HTTP GET requests (method, path, headers)
  ✓ Serves static files from a document root directory
  ✓ Returns proper HTTP responses (200 OK, 404 Not Found, 403 Forbidden)
  ✓ Sets Content-Type based on file extension (.html, .css, .js, .png, .jpg)
  ✓ Handles multiple concurrent clients using a thread pool (4 threads)
  ✓ Logs each request: timestamp, client IP, method, path, status code
  ✓ Handles SIGINT gracefully (clean shutdown, close all sockets)
  ✓ Handles malformed requests without crashing
  ✓ Passes stress testing with `ab` (Apache Bench) or `wrk`

Project structure:
  ├── server.c          (main, socket setup, accept loop)
  ├── http_parser.c/h   (parse request line + headers)
  ├── http_response.c/h (build + send responses)
  ├── file_handler.c/h  (read files, MIME types)
  ├── thread_pool.c/h   (worker threads + job queue)
  ├── logger.c/h        (thread-safe logging)
  └── Makefile

Skills practiced:
  → sockets, TCP, pthreads, mutex, file I/O, string parsing,
    process signals, multi-file projects, Makefile
```

---

---

## PHASE 6 — ADVANCED C

> **Goal**: Master the preprocessor, understand undefined behavior, write portable and optimized code, and learn professional build systems and practices.

---

### Module 6.1 — The C Preprocessor (Deep Dive)

#### Section 6.1.1 — Macros
- Object-like macros: `#define PI 3.14159`
- Function-like macros: `#define MAX(a,b) ((a) > (b) ? (a) : (b))`
- Why all the parentheses matter (macro expansion pitfalls)
- Multi-line macros with `\`
- `do { ... } while(0)` trick for statement macros
- Variadic macros: `#define LOG(fmt, ...) fprintf(stderr, fmt, __VA_ARGS__)`

#### Section 6.1.2 — Conditional Compilation
- `#ifdef`, `#ifndef`, `#if`, `#elif`, `#else`, `#endif`
- Platform-specific code: `#ifdef _WIN32` / `#ifdef __linux__`
- Feature flags: `#if ENABLE_DEBUG`
- Include guards vs. `#pragma once`

#### Section 6.1.3 — Preprocessor Utilities
- `#` (stringification): `#define STR(x) #x`
- `##` (token pasting): `#define CONCAT(a,b) a##b`
- `__FILE__`, `__LINE__`, `__func__`, `__DATE__`, `__TIME__`
- `_Static_assert` (C11) — compile-time assertions

#### Section 6.1.4 — Macros vs. Inline Functions
- `static inline` functions (C99): type-safe, debuggable
- When macros are still necessary (generics before C11)
- `_Generic` (C11): type-generic expressions

---

### Module 6.2 — Undefined Behavior & Language Lawyering

#### Section 6.2.1 — Categories of Behavior
- **Defined behavior**: specified by the standard
- **Implementation-defined**: compiler chooses, must document (e.g., `sizeof(int)`)
- **Unspecified behavior**: compiler chooses, doesn't have to document (e.g., evaluation order)
- **Undefined behavior (UB)**: anything can happen — nasal demons

#### Section 6.2.2 — Common Sources of UB
- Signed integer overflow
- Dereferencing NULL or dangling pointers
- Buffer overflow (out-of-bounds access)
- Modifying string literals
- Accessing uninitialized variables
- Sequence point violations: `i = i++ + ++i;`
- Strict aliasing violations: casting `int *` to `float *`
- Shifting by ≥ bit width: `1 << 32` (on 32-bit int)
- Double free, use-after-free
- Missing return in non-void function

#### Section 6.2.3 — How UB Breaks Programs
- Why "it works on my machine" is not proof of correctness
- How optimizers exploit UB (dead code elimination, infinite loop removal)
- Real-world CVEs caused by UB
- Tools to detect UB: `-fsanitize=undefined` (UBSan)

---

### Module 6.3 — C Standards & Portability

#### Section 6.3.1 — C Standards Evolution
- **C89/C90** — ANSI C, the original standard
- **C99** — `//` comments, VLAs, `<stdbool.h>`, `<stdint.h>`, `inline`, designated initializers
- **C11** — `_Generic`, `_Static_assert`, `<stdatomic.h>`, `<threads.h>`, anonymous structs/unions
- **C17** — Bug fixes only (no new features)
- **C23** — `typeof`, `nullptr`, `#embed`, binary literals, `constexpr`
- Setting the standard: `-std=c17`, `-std=c23`

#### Section 6.3.2 — Fixed-Width Integers (`<stdint.h>`)
- `int8_t`, `int16_t`, `int32_t`, `int64_t` (and unsigned variants)
- `size_t`, `ptrdiff_t`, `intptr_t`, `uintptr_t`
- Format specifiers: `PRId32`, `PRIu64` from `<inttypes.h>`
- Why you should use these for portable code

#### Section 6.3.3 — Writing Portable Code
- Avoid assuming sizes: use `sizeof`, use `<stdint.h>`
- Avoid assuming endianness: use conversion functions for network/file I/O
- Avoid platform-specific APIs (or abstract them behind `#ifdef`)
- Avoid compiler-specific extensions (or guard them)

---

### Module 6.4 — Performance & Optimization

#### Section 6.4.1 — Compiler Optimization
- Optimization levels: `-O0`, `-O1`, `-O2`, `-O3`, `-Os`, `-Ofast`
- What the optimizer does: inlining, loop unrolling, dead code elimination, constant folding
- Inspecting output: `gcc -S` (assembly), Godbolt Compiler Explorer

#### Section 6.4.2 — Cache-Friendly Code
- How CPU caches work (L1, L2, L3)
- Spatial locality: access memory sequentially (row-major for 2D arrays)
- Temporal locality: reuse recently accessed data
- Struct-of-arrays (SoA) vs. array-of-structs (AoS)
- `struct` padding and `__attribute__((packed))` — alignment matters

#### Section 6.4.3 — Profiling
- `gprof` — function-level profiling
- `perf` — Linux performance counters (cache misses, branch mispredictions)
- `time` command — wall clock, user, sys
- Rule: **measure before you optimize**

#### Section 6.4.4 — `volatile`, `restrict`, `inline`
- `volatile` — prevent optimizer from caching reads (hardware registers, signal handlers)
- `restrict` — promise no aliasing (enables optimizer for pointer-heavy code)
- `inline` — suggest inlining (compiler may ignore)

---

### Module 6.5 — Build Systems & Professional Practices

#### Section 6.5.1 — Makefiles (Advanced)
- Pattern rules: `%.o: %.c`
- Automatic variables: `$@`, `$<`, `$^`
- Phony targets: `.PHONY: clean all test`
- Dependency generation: `gcc -MMD -MP`
- Recursive vs. non-recursive make

#### Section 6.5.2 — CMake
- `CMakeLists.txt` basics: `project`, `add_executable`, `target_link_libraries`
- Finding libraries: `find_package`
- Configuring: `cmake -B build -DCMAKE_BUILD_TYPE=Release`
- Building: `cmake --build build`

#### Section 6.5.3 — Static & Dynamic Libraries
- Static libraries: `ar rcs libfoo.a foo.o bar.o`, linking with `-lfoo`
- Shared libraries: `gcc -shared -fPIC -o libfoo.so foo.c`, `LD_LIBRARY_PATH`
- When to use which
- `dlopen`, `dlsym` — runtime dynamic loading

#### Section 6.5.4 — Testing in C
- Unit testing frameworks: `Unity`, `Check`, `cmocka`
- Writing testable C code (dependency injection via function pointers)
- Mocking strategies
- Code coverage: `gcov`, `lcov`

#### Section 6.5.5 — Static Analysis & Linting
- `cppcheck` — static analyzer
- `clang-tidy` — linter + modernizer
- Compiler warnings as errors: `-Werror`
- The ultimate warning set: `-Wall -Wextra -Wpedantic -Wshadow -Wconversion`

---

### Module 6.6 — Design Patterns in C

#### Section 6.6.1 — Opaque Types (Information Hiding)
- Forward-declare struct in header: `typedef struct Foo Foo;`
- Define struct only in `.c` file
- Expose only functions: `Foo *foo_create()`, `void foo_destroy(Foo *f)`
- Achieves encapsulation similar to OOP

#### Section 6.6.2 — Object-Oriented C
- Structs with function pointer "methods"
- Vtable pattern for polymorphism
- How Linux kernel, GLib, and SQLite use these patterns

#### Section 6.6.3 — Error Handling Patterns
- Return codes + `errno` (POSIX style)
- Out-parameter for result + return code for status
- `goto cleanup` pattern for resource cleanup (the one good use of `goto`)
- Error propagation strategies

---

### 🔨 Phase 6 Project — **Redis-Lite: An In-Memory Data Store with Networking**

```
Build a simplified Redis clone that:
  ✓ Accepts TCP connections on a configurable port
  ✓ Implements a text-based protocol (RESP-like):
      SET key value [EX seconds]
      GET key
      DEL key [key ...]
      KEYS pattern
      EXPIRE key seconds
      TTL key
      SAVE
      PING → PONG
  ✓ Stores data in a hash table (from Phase 4, refined)
  ✓ Supports key expiration using a sorted structure (heap or skip list)
  ✓ Handles multiple concurrent clients with epoll (Linux) or select
  ✓ Implements an event loop (single-threaded, non-blocking I/O)
  ✓ Persists to disk: RDB-style snapshot (serialize hash table to binary file)
  ✓ Loads snapshot on startup
  ✓ Built with CMake
  ✓ Unit tested with Unity or Check framework
  ✓ Packaged as a static library (libredislite.a) + server binary
  ✓ Includes a simple CLI client
  ✓ All memory verified clean with ASan + Valgrind
  ✓ README with build instructions, protocol spec, benchmarks

Project structure:
  ├── CMakeLists.txt
  ├── include/
  │   ├── hashtable.h
  │   ├── server.h
  │   ├── protocol.h
  │   ├── persistence.h
  │   └── event_loop.h
  ├── src/
  │   ├── main.c
  │   ├── hashtable.c
  │   ├── server.c
  │   ├── protocol.c
  │   ├── persistence.c
  │   └── event_loop.c
  ├── client/
  │   └── cli.c
  ├── tests/
  │   ├── test_hashtable.c
  │   ├── test_protocol.c
  │   └── test_persistence.c
  └── README.md

Skills practiced:
  → EVERYTHING from all previous phases combined:
    pointers, dynamic memory, data structures, file I/O (binary),
    sockets, event-driven I/O, parsing, serialization, CMake,
    testing, library creation, professional project structure
```

---

---

## Recommended Resources

| Resource | Type | Best For |
|---|---|---|
| **"C Programming: A Modern Approach" — K.N. King** | Book | Best textbook for learning C systematically (matches this roadmap) |
| **"The C Programming Language" — K&R** | Book | Classic reference; read AFTER King, not as first book |
| **"Expert C Programming" — Peter van der Linden** | Book | Deep dives, war stories, expert-level understanding |
| **"Modern C" — Jens Gustedt** (free online) | Book | Modern C standards (C11/C17/C23) |
| **Beej's Guide to C Programming** | Free Online | Excellent free reference, casual tone |
| **Beej's Guide to Network Programming** | Free Online | Best socket programming tutorial |
| **CS:APP (Computer Systems: A Programmer's Perspective)** | Book | How C maps to hardware, memory, OS |
| **Exercism C Track** | Practice | Structured exercises with mentoring |
| **Godbolt Compiler Explorer** | Tool | See what assembly your C generates |

---

## Final Advice

```
  ┌────────────────────────────────────────────────────────┐
  │                                                        │
  │   1. TYPE every example. Never copy-paste.             │
  │                                                        │
  │   2. COMPILE with all warnings:                        │
  │      gcc -Wall -Wextra -Wpedantic -std=c17 -g          │
  │                                                        │
  │   3. DEBUG with tools, not printf:                     │
  │      gdb, valgrind, -fsanitize=address,undefined       │
  │                                                        │
  │   4. DRAW memory diagrams on paper.                    │
  │      Pointers make sense when you visualize them.      │
  │                                                        │
  │   5. BUILD the projects. Reading is not learning.      │
  │      The projects are where 80% of learning happens.   │
  │                                                        │
  │   6. READ other people's C code:                       │
  │      Redis, SQLite, curl, Linux kernel (small parts)   │
  │                                                        │
  └────────────────────────────────────────────────────────┘
```