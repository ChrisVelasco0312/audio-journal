# Range-Based `for` Loops (Modern C++)

Introduced in C++11, range-based `for` loops simplify iterating through collections like `std::vector`, `std::array`, or raw arrays. You do not need to manually manage index variables (`i`).

### 1. Basic Read-Only Iteration

Iterate over every element directly by value.

```cpp
#include <iostream>
#include <vector>

int main() {
    std::vector<int> scores = {85, 92, 78, 90};

    // "For each score in scores"
    for (int score : scores) {
        std::cout << "Score: " << score << "\n";
    }

    return 0;
}

```

---

### 2. Modern Practice: Using `auto`

Instead of writing the explicit type, use `auto` to let the compiler deduce the type for you.

```cpp
#include <iostream>
#include <vector>

int main() {
    std::vector<double> frequencies = {440.0, 880.0, 220.0};

    for (auto freq : frequencies) {
        std::cout << freq << " Hz\n";
    }

    return 0;
}

```

---

### 3. Modifying Elements with References (`auto&`)

By default, range-based loops create a copy of each element. If you want to modify the actual elements inside the collection, pass them by reference using `&`.

```cpp
#include <iostream>
#include <vector>

int main() {
    std::vector<int> values = {1, 2, 3, 4};

    // Multiply every value in the vector by 10
    for (auto& val : values) {
        val *= 10;
    }

    // Print updated values
    for (auto val : values) {
        std::cout << val << " "; // Output: 10 20 30 40
    }
    std::cout << "\n";

    return 0;
}

```

---

### 4. Efficient Read-Only with `const auto&`

When working with heavy objects (like `std::string` or custom classes), copying each element can hurt performance. Using `const auto&` avoids making copies while preventing accidental modifications.

```cpp
#include <iostream>
#include <vector>
#include <string>

int main() {
    std::vector<std::string> names = {"Alice", "Bob", "Charlie"};

    // No copying, read-only protection
    for (const auto& name : names) {
        std::cout << "Hello, " << name << "\n";
    }

    return 0;
}

```
