# Arrays: Frequently Asked Questions (FAQ)

This FAQ addresses compilation issues, runtime errors, and performance quirks encountered during online coding assessments.

---

## 🗺️ Array Initialization Methods

Refer to this table to choose the correct way to initialize arrays and prevent garbage value bugs:

| Initialization Code | What it does | Values stored | Recommended Use Case |
| :--- | :--- | :--- | :--- |
| `int arr[5];` | Allocates memory without setting values | Random garbage values | Overwriting immediately with input |
| `int arr[5] = {0};` | Sets all elements to zero | `[0, 0, 0, 0, 0]` | General clean-state arrays |
| `int arr[5] = {1, 2};` | Sets first two elements, defaults rest to zero | `[1, 2, 0, 0, 0]` | Partial initialization |
| `memset(arr, -1, sizeof(arr));` | Sets memory byte-by-byte to `-1` | `[-1, -1, -1, -1, -1]` | Resetting DP arrays quickly |

---

## 💬 Frequently Asked Questions

### Q1: My code works locally but gives "Time Limit Exceeded" (TLE) online. Why?
Online judges run test cases with large datasets (e.g., $N = 10^5$).
- A nested loop solution ($O(N^2)$ time complexity) performs $10^{10}$ operations, taking over 10 seconds.
- Most coding platforms enforce a **1-second or 2-second time limit** (approx. $10^8$ basic operations).
- **Solution**: Replace nested loops with sliding window, two-pointers, or hash maps to achieve $O(N)$ or $O(N \log N)$ complexity.

---

### Q2: What causes "Segmentation Fault (SIGSEGV)" on array problems?
A segmentation fault occurs when your program accesses memory it doesn't own.
- **Common Cause A**: Accessing out-of-bounds indices, like `arr[i]` when `i >= n` or `i < 0`.
- **Common Cause B**: Infinite recursion or huge static arrays on the stack, causing stack overflow.
- **Immediate Check**: Look at your loop conditions. Ensure they use `< n` instead of `<= n`.

---

### Q3: Why does my array print garbage values when initialized?
Declaring `int arr[10];` inside a function allocates stack space but does not clear the previous memory state.
- The memory contains whatever bits were left over by other functions.
- **Solution**: Initialize the array explicitly using `{0}`:
  ```cpp
  int arr[10] = {0}; // All elements initialized to 0
  ```

---

### Q4: Why does `sizeof(arr)` change when passed to a function?
In C++, raw arrays decay into pointers when passed to functions.
- **In `main()`**: `sizeof(arr)` returns the total size in bytes (e.g., $10 \times 4 = 40$ bytes for `int arr[10]`).
- **In function**: `sizeof(arr)` returns the size of the pointer itself (4 bytes on 32-bit systems, 8 bytes on 64-bit systems).
- **Solution**: Always pass the array size as a parameter: `void process(int arr[], int n)`.

---

### Q5: My code passes all sample test cases but fails on hidden test cases. Why?
Sample test cases only cover typical scenarios. Hidden test cases evaluate edge cases:
1. **$N = 0$ or $N = 1$**: Minimum size boundaries.
2. **Duplicate values**: e.g., finding the second largest element in `[5, 5, 5]`.
3. **Negative numbers**: e.g., Kadane's algorithm on all negative numbers.
4. **Integer Overflow**: e.g., accumulating array sums exceeding $2 \times 10^9$. Use `long long` for sums.

---

### Q6: Can I declare a variable-sized array like `int n; cin >> n; int arr[n];`?
This creates a **Variable Length Array (VLA)**.
- VLAs are part of the C99 standard, but they are **not** standard C++.
- Many compilers (like GCC) support them as an extension, but they can fail on strict standards-compliant compilers.
- **Solution**: Use `std::vector<int> arr(n);` instead.

---

### Q7: How do I reset all elements of an array to `-1` or `0` efficiently?
Use `std::fill` or `memset` from `<cstring>`:
- **Using `memset`**:
  ```cpp
  memset(arr, -1, sizeof(arr)); // Works for 0 and -1 only (sets byte-by-byte)
  ```
- **Using `std::fill`**:
  ```cpp
  std::fill(arr, arr + n, 5); // Works for any value
  ```

---

### Q8: Why does my sliding window solution fail on negative numbers?
The sliding window technique assumes that adding elements increases the window sum, and removing elements decreases it.
- With negative numbers, adding an element can decrease the sum.
- **Solution**: Use the Prefix Sum + Hash Map pattern to find subarrays summing to $K$ when negatives are present.

---

### Q9: How can I pass a 2D array of dynamic sizes to a function?
Pass the 2D array as a vector of vectors:
```cpp
void print2D(const std::vector<std::vector<int>>& grid) {
    int rows = grid.size();
    if (rows == 0) return;
    int cols = grid[0].size();
    for (int i = 0; i < rows; i++) {
        for (int j = 0; j < cols; j++) {
            std::cout << grid[i][j] << " ";
        }
        std::cout << "\n";
    }
}
```

---

### Q10: What is "Floating Point Exception (SIGFPE)" in array problems?
A `SIGFPE` occurs during arithmetic errors, most commonly **division by zero** or modulo by zero.
- It often happens when indexing elements with variables derived from calculations:
  ```cpp
  int count = 0; // count changes dynamically
  int index = val % count; // If count is 0, this triggers SIGFPE
  ```
- **Solution**: Check inputs and track indices to ensure you never divide or modulo by zero.
