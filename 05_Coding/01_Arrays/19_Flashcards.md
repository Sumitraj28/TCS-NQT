# Array active-Recall Flashcards

Use these 20 flashcards to test your knowledge of array mechanics, patterns, and C++14 optimization tricks.

---

## 📊 Quick Concept Comparison

Before starting the cards, review the difference between these three terms:

| Term | Contiguous? | Order Preserved? | Total Count for Size $N$ | Example for $[1, 2, 3]$ |
| :--- | :--- | :--- | :--- | :--- |
| **Subarray** | Yes | Yes | $\frac{N(N+1)}{2}$ | $[1, 2]$, $[2, 3]$ |
| **Subsequence** | No | Yes | $2^N - 1$ (excluding empty) | $[1, 3]$ |
| **Subset** | No | No | $2^N$ | $\{3, 1\}$ |

---

## 📇 Flashcard Deck

### Card 1: Array Base Address Calculation
What is the formula to calculate the memory address of element $A[i]$ in a 1D array?
<details>
<summary>Reveal Answer</summary>

$$\text{Address}(A[i]) = \text{BaseAddress} + i \times \text{sizeof}(\text{DataType})$$
- **BaseAddress**: Starting memory location of the array.
- **i**: Index of the element (0-indexed).
- **sizeof(DataType)**: Byte size of an individual element (e.g., 4 bytes for `int`, 8 bytes for `double`).
</details>

---

### Card 2: Pointer Decay
What happens to a raw array when passed into a function as a parameter?
<details>
<summary>Reveal Answer</summary>

It decays into a pointer pointing to its first element (`arr` becomes `int*`).
- Inside the function, `sizeof(arr)` returns the pointer size (4 or 8 bytes) rather than the array's total size.
- **Solution**: Always pass the array size $N$ as a separate parameter: `void func(int* arr, int n)`.
</details>

---

### Card 3: Vector Capacity Growth
How does `std::vector` resize itself when it runs out of capacity?
<details>
<summary>Reveal Answer</summary>

It allocates a new contiguous block of memory (typically $1.5\times$ or $2\times$ the current size).
- It then copies the existing elements to the new block.
- It deletes the old memory block.
- This results in an amortized insertion time of $O(1)$ at the back, but individual insertions triggering resize take $O(N)$ time.
</details>

---

### Card 4: Element Deletion Shift Complexity
What is the worst-case time complexity of deleting an element from the middle of an array of size $N$?
<details>
<summary>Reveal Answer</summary>

**$O(N)$** time complexity.
- Memory is contiguous, so we cannot leave a gap.
- All elements to the right of the deleted index must be shifted one position to the left.
- Worst-case occurs when deleting the first element (index 0), requiring $N-1$ shifts.
</details>

---

### Card 5: Two-Pointer vs Sliding Window
When should you use Two-Pointers vs Sliding Window?
<details>
<summary>Reveal Answer</summary>

- **Two-Pointers**: Used on sorted arrays to search pairs or merge. Pointer movement depends on comparisons (e.g., `left` moves right, `right` moves left).
- **Sliding Window**: Used on contiguous subarrays. A window is expanded (by moving `right`) and shrunk (by moving `left`) to track a dynamic range matching a condition.
</details>

---

### Card 6: Kadane's Negatives Trap
What happens if Kadane's algorithm is initialized with `curr_max = 0` on an array containing only negative numbers?
<details>
<summary>Reveal Answer</summary>

It will incorrectly output `0` instead of the maximum negative element.
- **Correction**: Initialize both `max_so_far` and `curr_max` to the first element of the array `arr[0]`:
  ```cpp
  long long max_so_far = arr[0];
  long long curr_max = arr[0];
  ```
</details>

---

### Card 7: Modulo Arithmetic Overflow
Why do we calculate modulo operations during multiplication step-by-step rather than only at the end?
<details>
<summary>Reveal Answer</summary>

Intermediate products can exceed the maximum capacity of standard data types, causing integer overflow.
- **Rule**: Apply modulo after each multiplication:
  ```cpp
  long long res = 1;
  res = (res * arr[i]) % MOD;
  ```
</details>

---

### Card 8: In-place Array Rotation
What are the 3 reversal steps to rotate an array to the right by $K$ elements?
<details>
<summary>Reveal Answer</summary>

For size $N$ and rotation steps $K = K \pmod N$:
1. Reverse the entire array: `reverse(arr, arr + n)`
2. Reverse the first $K$ elements: `reverse(arr, arr + k)`
3. Reverse the remaining $N-K$ elements: `reverse(arr + k, arr + n)`
</details>

---

### Card 9: First Missing Positive (Cycle Sort Marker)
What is the core index-mapping array marker trick to find the first missing positive in $O(N)$ time and $O(1)$ space?
<details>
<summary>Reveal Answer</summary>

Put each element $X$ in its correct position `arr[X-1]` if $1 \le X \le N$ using swaps.
- Once sorted, scan the array.
- The first index $i$ where `arr[i] != i + 1` identifies the first missing positive as `i + 1`.
</details>

---

### Card 10: Fast I/O Syntax
What are the two lines of code that optimize C++ input/output speeds for NQT platforms?
<details>
<summary>Reveal Answer</summary>

```cpp
ios_base::sync_with_stdio(false);
cin.tie(NULL);
```
- Line 1 disables synchronization between C and C++ standard streams.
- Line 2 unties `cin` from `cout`, preventing automatic flushes before inputs.
</details>

---

### Card 11: `std::sort` Complexity
What is the worst-case and average-case time complexity of `std::sort` in C++ STL?
<details>
<summary>Reveal Answer</summary>

- **Average Case**: $O(N \log N)$
- **Worst Case**: $O(N \log N)$
- **Reason**: C++ STL `std::sort` implements **IntroSort** (a hybrid algorithm of QuickSort, HeapSort, and InsertionSort), which switches to HeapSort if QuickSort's recursion depth exceeds limits, avoiding the $O(N^2)$ worst case.
</details>

---

### Card 12: Map vs Unordered Map Lookups
What are the time complexities of element lookup in `std::map` vs `std::unordered_map`?
<details>
<summary>Reveal Answer</summary>

- **`std::map`**: $O(\log N)$ (implemented using Self-Balancing Red-Black Trees).
- **`std::unordered_map`**: $O(1)$ average case, $O(N)$ worst case (due to hash collisions).
</details>

---

### Card 13: Vector vs Deque Memory Layout
How does the memory layout of `std::vector` compare to `std::deque`?
<details>
<summary>Reveal Answer</summary>

- **`std::vector`**: Single contiguous memory block.
- **`std::deque`**: Split contiguous memory blocks (chunks) linked via a central map directory. It allows $O(1)$ insertions at both front and back, but lacks strict contiguous layout.
</details>

---

### Card 14: Pointer Arithmetic
If `int* ptr` points to memory address `2000`, what is the value of `ptr + 3`?
<details>
<summary>Reveal Answer</summary>

**`2012`**
- In pointer arithmetic, adding $X$ shifts the pointer by $X \times \text{sizeof(Type)}$ bytes.
- Since `sizeof(int) = 4` bytes:
  $$\text{Address} = 2000 + (3 \times 4) = 2012$$
</details>

---

### Card 15: Binary Search Prerequisite
What must be true about an array before you can perform a binary search on it?
<details>
<summary>Reveal Answer</summary>

The array must be **sorted** relative to the search key.
- Without a sorted layout, we cannot discard half the search space based on comparisons.
</details>

---

### Card 16: Prefix Sum Array Utility
If `prefix[i] = arr[0] + arr[1] + ... + arr[i]`, how do you find the sum of subarray `arr[L...R]` in $O(1)$ time?
<details>
<summary>Reveal Answer</summary>

- If $L = 0$: `prefix[R]`
- If $L > 0$: `prefix[R] - prefix[L - 1]`
- **Derivation**:
  $$\sum_{i=L}^{R} A[i] = \sum_{i=0}^{R} A[i] - \sum_{i=0}^{L-1} A[i] = \text{prefix}[R] - \text{prefix}[L-1]$$
</details>

---

### Card 17: Pass Vector By Reference
Why should you pass vectors to helper functions by reference (`vector<int>& v`) rather than value (`vector<int> v`)?
<details>
<summary>Reveal Answer</summary>

Passing by value creates a full deep copy of the vector.
- This takes $O(N)$ time and auxiliary space.
- Passing by reference (`vector<int>&`) passes the address of the original vector, taking $O(1)$ time.
</details>

---

### Card 18: Vector `.reserve()` vs `.resize()`
What is the difference between `v.reserve(100)` and `v.resize(100)`?
<details>
<summary>Reveal Answer</summary>

- **`v.reserve(100)`**: Allocates memory for 100 elements but does not construct any objects. The size (`v.size()`) remains unchanged.
- **`v.resize(100)`**: Changes the vector size to 100, constructing default-initialized elements if expanding.
</details>

---

### Card 19: Find Equilibrium Index
What is the condition formula for an index $i$ to be an equilibrium index of an array?
<details>
<summary>Reveal Answer</summary>

$$\text{LeftSum} = \text{RightSum}$$
- Can be calculated in $O(N)$ time by maintaining a running left sum and subtracting current element from total sum:
  $$\text{RightSum} = \text{TotalSum} - \text{LeftSum} - A[i]$$
</details>

---

### Card 20: Array Element Swapping without Temp Variable
How can you swap `a` and `b` in-place using arithmetic or XOR without using a temporary variable?
<details>
<summary>Reveal Answer</summary>

Using XOR:
```cpp
a = a ^ b;
b = a ^ b; // b becomes (a ^ b) ^ b = a
a = a ^ b; // a becomes (a ^ b) ^ a = b
```
*Note*: This only works if `a` and `b` point to different memory locations. If they refer to the same index (`&arr[i] == &arr[j]`), XOR swap will zero the value.
</details>
