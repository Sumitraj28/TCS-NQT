# Sorting — Quick Revision

## Core Complexities

| Algorithm | Worst | Average | Space | Stable |
|-----------|-------|---------|-------|--------|
| Bubble Sort | O(n²) | O(n²) | O(1) | Yes |
| Selection Sort | O(n²) | O(n²) | O(1) | No |
| Insertion Sort | O(n²) | O(n²) | O(1) | Yes |
| Merge Sort | O(n log n) | O(n log n) | O(n) | Yes |
| Quick Sort | O(n²) | O(n log n) | O(log n) | No |
| Heap Sort | O(n log n) | O(n log n) | O(1) | No |
| std::sort | O(n log n) | O(n log n) | O(log n) | No |
| std::stable_sort | O(n log n) | O(n log n) | O(n) | Yes |

---

## C++ STL Sort Shortcuts

```cpp
#include <algorithm>

std::sort(v.begin(), v.end());                         // Ascending
std::sort(v.rbegin(), v.rend());                       // Descending
std::stable_sort(v.begin(), v.end());                  // Stable Sort

// Kth Element in O(N) average time
std::nth_element(v.begin(), v.begin() + k, v.end());
int kthSmallest = v[k];

// Custom Sort (Lambda comparator must use strict < or >)
std::sort(intervals.begin(), intervals.end(), [](const auto& a, const auto& b){
    return a[0] < b[0];
});
```

---

## Key Mistakes to Avoid
1. **Never use `<=` or `>=` in comparators** — strict weak ordering violation.
2. **Never sort fully for Kth Largest** — use `std::nth_element` or heaps.
3. **Use std::stable_sort** if relative ordering of equal elements must be preserved.
4. **Do NOT increment mid in Case 2 of Dutch National Flag** (swap with high).
