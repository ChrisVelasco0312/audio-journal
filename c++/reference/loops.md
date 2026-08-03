### 1. The `while` Loop (Condition-First)

Use a `while` loop when you want to repeat something **as long as a condition remains true**, and you don't necessarily know beforehand how many times it will run.

```cpp
#include <iostream>

int main() {
    int energy = 3;

    // Checks the condition BEFORE running the block
    while (energy > 0) {
        std::cout << "Running... Energy remaining: " << energy << "\n";
        energy--; // Decrease energy so the loop eventually stops
    }

    std::cout << "Out of energy!\n";
    return 0;
}

```

* **Key Detail:** If the condition is `false` from the start, the code inside never runs.

---

### 2. The `do-while` Loop (Run At Least Once)

Use a `do-while` loop when you need the block of code to run **at least once** before checking the condition (e.g., prompting a user for input).

```cpp
#include <iostream>

int main() {
    int secret_number = 7;
    int guess;

    do {
        std::cout << "Enter a number between 1 and 10: ";
        std::cin >> guess;
    } while (guess != secret_number); // Checks condition AFTER running

    std::cout << "Correct! You guessed it.\n";
    return 0;
}

```

* **Key Detail:** Note the mandatory semicolon `;` after the `while(...)` condition at the end.

---

### 3. The Standard `for` Loop (Index & Count)

Use a standard `for` loop when you know **how many times** you want to repeat a task. It combines initialization, condition checking, and incrementing in a single line.

```cpp
#include <iostream>

int main() {
    //  Initialization ; Condition ; Increment/Decrement
    for (int i = 0; i < 5; i++) {
        std::cout << "Iteration count: " << i << "\n";
    }

    return 0;
}

```

* **Breakdown:**
1. `int i = 0`: Runs once at the very start.
2. `i < 5`: Checked before every cycle.
3. `i++`: Executes after the loop body finishes each cycle.