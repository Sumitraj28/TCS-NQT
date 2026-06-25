---
title: "Arrays - Complexity Analysis"
section: "Coding"
---

# Array Complexity Analysis Reference

This document provides a complete complexity reference for static and dynamic array operations.

---

## 1. Operations Complexity Table

| Operation | Time (Best) | Time (Average) | Time (Worst) | Space Complexity |
| :--- | :---: | :---: | :---: | :---: |
| **Access by Index** | $O(1)$ | $O(1)$ | $O(1)$ | $O(1)$ |
| **Linear Search** | $O(1)$ | $O(N)$ | $O(N)$ | $O(1)$ |
| **Binary Search** | $O(1)$ | $O(\log N)$ | $O(\log N)$ | $O(1)$ |
| **Insert at End** | $O(1)$ | $O(1)$ | $O(N)$ | $O(1)$ |
| **Insert at Start/Mid**| $O(N)$ | $O(N)$ | $O(N)$ | $O(1)$ |
| **Delete from End** | $O(1)$ | $O(1)$ | $O(1)$ | $O(1)$ |
| **Delete from Start/Mid**| $O(N)$ | $O(N)$ | $O(N)$ | $O(1)$ |

---

## 2. Why is each Complexity what it is?

### A. Access by Index is $O(1)$
Because an array is allocated contiguously in memory, the location of any index `i` is calculated mathematically in a single CPU instruction using the base address:
$$\text{Address} = \text{Base} + i \times \text{Size}$$
No scanning or loop is needed.

### B. Insert at End is $O(1)$ Average but $O(N)$ Worst Case
For static arrays, inserting at the end is always $O(1)$ if space exists. For dynamic arrays (`std::vector` in C++), insertion is $O(1)$ average. However, if the array is full, it must allocate a new block of size $2N$ and copy all elements over, which takes $O(N)$ time. Because this copy occurs rarely (only when capacity doubles), the *amortized* cost remains $O(1)$.

### C. Insert/Delete in the Middle is $O(N)$
If you insert or delete an element at index `i`, all elements to its right must be shifted to the left or right to keep the memory contiguous. In the worst case (inserting at index 0), we must shift all $N$ elements, taking $O(N)$ time.

### D. Search is $O(N)$ (Linear) vs $O(\log N)$ (Binary)
*   **Linear Search**: In the worst case, the target element is at the very end of the array or not present at all, requiring us to check all $N$ items sequentially.
*   **Binary Search**: Requires a sorted array. By checking the midpoint, we can discard half the remaining search space at each step. The size of the search space shrinks as $N \rightarrow N/2 \rightarrow N/4 \dots \rightarrow 1$, taking $\log_2(N)$ steps.
