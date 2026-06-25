---
title: "Arrays - STL Guide"
section: "Coding"
---

# Array STL Guide

This document covers the essential C++ Standard Template Library (STL) components and functions for array coding.

---

## 1. C++ STL Array Tools

| STL Component | Purpose | Syntax | Time Complexity | When to Use |
| :--- | :--- | :--- | :---: | :--- |
| **`std::vector`** | Dynamic array wrapper | `vector<int> v;` | $O(1)$ amortized insert | When array size is variable. |
| **`std::sort`** | Sort range | `sort(v.begin(), v.end());` | $O(N \log N)$ | When sorting is needed. |
| **`std::reverse`** | Reverse range | `reverse(v.begin(), v.end());` | $O(N)$ | Reversing or rotating segments. |
| **`std::accumulate`** | Sum range | `accumulate(v.begin(), v.end(), 0LL);` | $O(N)$ | Finding array sums. |
| **`std::find`** | Search value | `find(v.begin(), v.end(), val);` | $O(N)$ | Unsorted lookup checks. |
| **`std::lower_bound`**| First element $\ge$ val | `lower_bound(v.begin(), v.end(), val);`| $O(\log N)$ | Binary search range checks (sorted). |
| **`std::binary_search`**| Check existence | `binary_search(v.begin(), v.end(), val);`| $O(\log N)$ | Check if value exists (sorted). |

---

## 2. Common STL Pitfalls

### A. Accumulate Integer Overflow
*   **The Trap**: Writing `accumulate(v.begin(), v.end(), 0)`.
*   **Why it fails**: The third argument `0` sets the accumulator type as a 32-bit `int`. If the sum exceeds $2 \times 10^9$, it overflows even if the result variable is declared as `long long`.
*   **The Fix**: Use `0LL` to set the accumulator type to `long long`:
    ```cpp
    long long total = accumulate(v.begin(), v.end(), 0LL);
    ```

---

### B. Vector Erase Shifting Overhead
*   **The Trap**: Using `v.erase(v.begin() + i)` inside a loop to remove elements.
*   **Why it fails**: `erase()` shifts all elements to the right of `i` one position left, taking $O(N)$ time. Calling this inside a loop results in an $O(N^2)$ execution time, causing TLEs.
*   **The Fix**: Use the "remove-erase" idiom or swap the target element with the last element and pop it (if order does not matter):
    ```cpp
    swap(v[i], v.back());
    v.pop_back(); // O(1) time
    ```

---

### C. Binary Search on Unsorted Vectors
*   **The Trap**: Calling `std::binary_search()` or `std::lower_bound()` on an unsorted vector.
*   **Why it fails**: These functions assume the range is sorted. If it is not, they run without compiler warnings but return incorrect boolean flags.
*   **The Fix**: Always call `std::sort()` before applying binary search functions.
