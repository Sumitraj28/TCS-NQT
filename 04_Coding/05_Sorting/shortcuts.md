# Sorting — Shortcuts (C++ STL)

## C++ STL Sort Shortcuts

### 1. `std::sort`
Sorts a vector ascending or descending.
```cpp
#include <algorithm>
#include <vector>

std::sort(arr.begin(), arr.end());                      // ascending
std::sort(arr.rbegin(), arr.rend());                    // descending
```

### 2. `std::stable_sort`
Maintains relative order of equal elements.
```cpp
#include <algorithm>

std::stable_sort(arr.begin(), arr.end());
```

### 3. Sort Array / Vector of Pairs / Intervals
Sort by first column ascending:
```cpp
std::sort(intervals.begin(), intervals.end(), [](const std::vector<int>& a, const std::vector<int>& b) {
    return a[0] < b[0];
});
```

Sort by first column ascending, and by second column descending on a tie:
```cpp
std::sort(matrix.begin(), matrix.end(), [](const std::vector<int>& a, const std::vector<int>& b) {
    if (a[0] != b[0]) return a[0] < b[0];
    return a[1] > b[1];
});
```

### 4. `std::nth_element` (QuickSelect)
Finds the kth smallest element in O(n) average time without fully sorting the range.
```cpp
#include <algorithm>

// Rearranges elements so that the element at index k is the kth smallest element,
// and all elements before it are smaller than or equal to it.
std::nth_element(arr.begin(), arr.begin() + k, arr.end());
int kthSmallest = arr[k];
```

### 5. `std::partial_sort`
Sorts the first k elements of the range, leaving the rest unsorted.
```cpp
#include <algorithm>

// Sorts the first k elements of arr, arr[0..k-1] will contain the k smallest sorted elements.
std::partial_sort(arr.begin(), arr.begin() + k, arr.end());
```

---

## 30-Second Algorithm Selection Guide

```
Is n > 10,000?
├── YES → Use built-in sort std::sort (O(n log n) guaranteed)
└── NO  → Can use any; std::sort still preferred

Is stability required?
├── YES → std::stable_sort (O(n log n) Merge Sort variant)
└── NO  → std::sort (O(n log n) IntroSort variant)

Is space O(1) required?
├── YES → std::sort (uses IntroSort) or Insertion Sort (for small n)
└── NO  → std::stable_sort

Is input nearly sorted?
└── YES → Insertion Sort (O(n) best case) or std::stable_sort

Are values in a small range [0..k]?
└── YES → Counting Sort (O(n+k)) — faster than comparison-based

Need kth element without full sort?
└── YES → std::nth_element (O(n) average) or std::priority_queue
```

## Comparator Sign Convention

```cpp
// Comparator returns true if 'a' should come BEFORE 'b', false otherwise.
// ASCENDING:  [](int a, int b) { return a < b; }
// DESCENDING: [](int a, int b) { return a > b; }
```
