https://www.programiz.com/cpp-programming/memory-management
[[pointers_guide]]

Memory allocation is the process by which a computer program reserves segments of system memory (RAM) to store variables, data structures, and instructions needed during execution.

---

## 1. How Memory Works in C++

When a C++ program executes, its address space is organized into distinct segments:

* **Stack Memory:** Used for automatic storage (local variables, function call parameters). It operates on a Last-In, First-Out (LIFO) structure. Allocation and deallocation are handled automatically by moving the stack pointer.
* **Heap Memory (Free Store):** A large pool of unmanaged memory used for dynamic allocation. Memory requested here stays allocated until explicitly freed or until the program terminates.
* **Data/BSS Segment:** Stores global and static variables.
* **Text Segment:** Stores the compiled machine instructions.

### Automatic vs. Dynamic Allocation

| Feature | Automatic (Stack) | Dynamic (Heap) |
| --- | --- | --- |
| **Lifetime** | Tied to scope (ends at `}`) | Manual (ends when freed) |
| **Size Determination** | Must be known at compile time | Determined at runtime |
| **Performance** | Extremely fast (pointer shift) | Slower (allocator overhead) |
| **Size Limit** | Limited (causes stack overflow if exceeded) | Large (bounded by RAM/swap) |

---

## 2. Key Concepts & Mechanics

### Basic Dynamic Operators in C++

* `new`: Reserves memory on the heap and calls the object constructor.
* `delete`: Calls the object destructor and releases heap memory.
* `new[]` / `delete[]`: Used specifically for allocating and freeing contiguous arrays.

```cpp
// Allocate an integer on the heap
int* p = new int(42);

// Free memory
delete p;
p = nullptr; // Prevent dangling pointer

```

### Common Memory Pitfalls

* **Memory Leaks:** Allocated heap memory is never freed, exhausting available system memory.
* **Dangling Pointers:** Accessing memory after it has been deleted.
* **Double Free:** Deallocating the same memory address twice, causing undefined behavior or crashes.
* **Buffer Overflow:** Writing past the allocated memory boundaries.

---

## 3. Best Practices in Modern C++ (C++11 and Beyond)

Modern C++ shifts away from manual memory management (`new`/`delete`) in favor of deterministic resource handling patterns.

### RAII (Resource Acquisition Is Initialization)

Bind the lifecycle of a heap resource to the scope of a stack object. When the stack object goes out of scope, its destructor automatically frees the heap resource.

### Smart Pointers (`<memory>`)

* `std::unique_ptr<T>`: Expresses **exclusive ownership**. Cannot be copied, only moved. Negligible overhead over raw pointers.
* `std::shared_ptr<T>`: Expresses **shared ownership**. Uses reference counting to track active users; frees memory when the last owner is destroyed.
* `std::weak_ptr<T>`: Provides a non-owning observer reference to a `std::shared_ptr` to prevent reference cycles.

```cpp
#include <memory>
#include <string>

struct Node {
    std::string data;
    Node(const std::string& str) : data(str) {}
};

void run() {
    // Prefer factory functions std::make_unique and std::make_shared
    auto ptr = std::make_unique<Node>("Modern C++");
    
    // Memory is automatically released when ptr goes out of scope
}

```

### Core Rules for Dynamic Memory

1. **Avoid manual `new` and `delete`:** Use standard library containers (`std::vector`, `std::string`) or smart pointers (`std::make_unique`, `std::make_shared`).
2. **Use raw pointers only as non-owning observers:** If a function needs to read a object without taking ownership, pass a raw reference `T&` or raw pointer `T*`.
3. **Follow the Rule of Five / Rule of Zero:** If a class manually manages resources, explicitly define or delete the destructor, copy constructor, copy assignment operator, move constructor, and move assignment operator. Whenever possible, rely on standard components so the compiler handles all five automatically (Rule of Zero).