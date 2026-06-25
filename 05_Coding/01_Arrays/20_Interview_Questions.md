# Array Coding Interview Questions & Tradeoffs

This file covers 10 conceptual and architectural interview questions about arrays, focusing on systems level, cache behavior, complexity, and algorithmic tradeoffs.

---

## 🗺️ Cache Locality Comparison

Dynamic 2D arrays can be allocated in two different ways in C++. Review their memory layouts and performance characteristics:

| Layout Strategy | Memory Visualization | Cache Friendly? | Access Index Instruction | Deallocation |
| :--- | :--- | :--- | :--- | :--- |
| **Pointer-to-Pointers** (`int**`) | Scattered 1D blocks linked by pointer array | ❌ No (double pointer hop, disjoint rows) | `arr[i][j]` | Loop over each row, then delete main pointer |
| **Flat 1D Vector** (`int*` or `vector<int>`) | Single contiguous block of size $R \times C$ |  Yes (elements stored consecutively) | `arr[i * cols + j]` | Single delete operation |

---

## 🗂️ Interview Questions & Answers

### Q1: Compare Static Arrays (`int arr[N]`) vs Dynamic Arrays (`std::vector`)
Explain the architectural differences, storage location, and allocation timing between the two.

**Answer:**
- **Static Arrays**: Allocated on the stack (unless global). Size must be known at compile-time. High performance with zero pointer overhead.
- **Dynamic Arrays (`std::vector`)**: Allocated on the heap. Size can change dynamically at runtime.
- **Performance Tradeoffs**: Stack allocation is fast (just updates stack pointer), but stack size is limited (typically 1MB to 8MB), risking Stack Overflow. Heap allocation is slower due to OS lookup, but holds large data blocks.

---

### Q2: Why is Search $O(N)$ in Unsorted Arrays but $O(\log N)$ in Sorted Arrays?
Derive the binary search recurrence relation to prove the logarithmic time complexity.

**Answer:**
- **Unsorted Array**: No relationship between elements. We must inspect every index in the worst case, leading to $O(N)$ comparisons.
- **Sorted Array**: Elements are ordered. Each check at midpoint $M$ discards half of the remaining elements.
- **Recurrence Derivation**:
  $$T(N) = T\left(\frac{N}{2}\right) + c$$
  Apply Master Theorem ($a=1$, $b=2$, $f(N) = \Theta(1)$):
  $$N^{\log_b a} = N^{\log_2 1} = N^0 = 1 = f(N)$$
  Thus, Case 2 applies:
  $$T(N) = \Theta(N^{\log_2 1} \log N) = \Theta(\log N)$$

---

### Q3: What is Pointer Decay and How Does it Affect Multi-dimensional Arrays?
Explain why `void print(int arr[][10])` requires column dimensions to be specified, but not rows.

**Answer:**
- When an array is passed to a function, it decays to a pointer to its first element.
- For a 1D array, `int arr[]` becomes `int*`.
- For a 2D array, `int arr[][10]` decays to a pointer to an array of 10 integers: `int (*arr)[10]`.
- The compiler needs the column size to perform address calculations:
  $$\text{Address}(A[i][j]) = \text{Base} + (i \times \text{Cols} + j) \times \text{sizeof}(int)$$
  Without knowing $\text{Cols}$ (columns), the compiler cannot locate $A[i][j]$.

---

### Q4: How do you Allocate a 2D Array Dynamically in C++? Compare flat 1D allocation vs array of pointers.
Provide the code snippets for both methods and discuss cache locality.

**Answer:**
- **Method A (Pointer to pointers):**
  ```cpp
  int** arr = new int*[rows];
  for (int i = 0; i < rows; i++) arr[i] = new int[cols];
  ```
  Rows are scattered across heap memory, resulting in cache misses.
- **Method B (Flat 1D mapped array):**
  ```cpp
  int* arr = new int[rows * cols];
  // Access element arr[i][j] via: arr[i * cols + j]
  ```
  This creates a single contiguous block, maximizing CPU cache line hits.

---

### Q5: Compare Prefix Sum + Hashing with Sliding Window for Subarray Sum
When does the sliding window approach fail?

**Answer:**
- **Sliding Window**: Uses two pointers to define a range. It expands and contracts based on whether the current sum is smaller or larger than the target.
- **Prefix Sum + Hash Map**: Stores cumulative sum at each index. If `curr_sum - target` exists in the hash map, we found a matching subarray.
- **When Sliding Window Fails**: It fails when the array contains **negative numbers**. Moving the right pointer can decrease the sum, and moving the left pointer can increase it, breaking the monotonic growth rule. The prefix sum hash map handles negatives correctly.

---

### Q6: How does Kadane's Algorithm track indices of the Maximum Subarray Sum?
Provide the C++14 code implementation.

**Answer:**
To track indices, update the starting index whenever the current subarray sum resets, and capture the indices whenever a new global maximum is found:

```cpp
#include <iostream>
#include <vector>
#include <algorithm>

using namespace std;

void findMaxSubarray(const vector<int>& arr) {
    long long max_so_far = arr[0];
    long long curr_max = arr[0];
    int start = 0, end = 0, temp_start = 0;

    for (size_t i = 1; i < arr.size(); i++) {
        if (arr[i] > curr_max + arr[i]) {
            curr_max = arr[i];
            temp_start = i; // Reset subarray start index
        } else {
            curr_max += arr[i];
        }

        if (curr_max > max_so_far) {
            max_so_far = curr_max;
            start = temp_start;
            end = i;
        }
    }
    cout << "Max Sum: " << max_so_far << "\n";
    cout << "Indices: [" << start << ", " << end << "]\n";
}
```

---

### Q7: Explain the Dutch National Flag Algorithm (Sort 012)
Why is it better than standard sorting, and how does it maintain three partition pointers?

**Answer:**
- Standard sorting takes $O(N \log N)$ time.
- The Dutch National Flag algorithm solves it in $O(N)$ time and $O(1)$ space using three pointers: `low`, `mid`, and `high`.
- **Pointer Rules**:
  - Elements before `low` are 0s.
  - Elements between `low` and `mid-1` are 1s.
  - Elements after `high` are 2s.
- **Step Example**:
  If `arr[mid] == 0`, swap `arr[mid]` and `arr[low]`, increment `low++` and `mid++`.
  If `arr[mid] == 1`, increment `mid++`.
  If `arr[mid] == 2`, swap `arr[mid]` and `arr[high]`, decrement `high--` (do not increment `mid`, as the swapped element must be checked).

---

### Q8: Compare `std::map` vs `std::unordered_map` for Array Element Counts
What are the time and space complexity differences under high hash-collision conditions?

**Answer:**
- **`std::map`**:
  - Time: $O(N \log N)$ to insert $N$ keys.
  - Space: $O(N)$ node pointers.
  - Benefit: Elements are kept sorted.
- **`std::unordered_map`**:
  - Time: $O(N)$ average case. If all elements hash to the same bucket (worst-case hash collision), time degrades to $O(N^2)$.
  - Space: $O(N)$ bucket array + linked list nodes.

---

### Q9: Explain the Cycle Sort pattern for Finding Missing Numbers
How does it achieve $O(N)$ time with $O(1)$ auxiliary space?

**Answer:**
- Cycle sort uses the property that elements are contiguous integers in the range $[1, N]$.
- We iterate through the array. If the current element `arr[i]` is in range $[1, N]$ and not at its correct index (`arr[i] != arr[arr[i] - 1]`), we swap it to its target index.
- Since each swap places at least one element in its correct position, the loop runs at most $2N$ times, giving $O(N)$ time.
- Space is $O(1)$ because we only swap elements within the input array.

---

### Q10: How does Dynamic Array Doubling affect Memory Fragmentation?
Why is a growth factor of 1.5 sometimes preferred over 2?

**Answer:**
- When size exceeds capacity, `std::vector` allocates a new block of size $\text{Capacity} \times \text{Factor}$.
- If growth factor is $2$: New capacities are $1, 2, 4, 8, 16, 32 \dots$
  The sum of previous capacities is:
  $$\sum_{i=0}^{k-1} 2^i = 2^k - 1 < 2^k$$
  This means the newly requested block is always larger than all previously freed memory combined. The allocator cannot reuse freed memory, leading to heap fragmentation.
- If growth factor is $1.5$, older blocks can be combined and reused by the allocator after a few resizes, improving memory locality.
