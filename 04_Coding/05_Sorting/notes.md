# Sorting — Complete Notes

## 1. Bubble Sort

**Concept:** Repeatedly compare adjacent elements and swap if out of order. After each pass, the largest unsorted element "bubbles up" to its correct position.

```cpp
#include <vector>
#include <algorithm>

void bubbleSort(std::vector<int>& arr) {
    int n = arr.size();
    for (int i = 0; i < n - 1; i++) {
        bool swapped = false;
        for (int j = 0; j < n - 1 - i; j++) {
            if (arr[j] > arr[j + 1]) {
                std::swap(arr[j], arr[j + 1]);
                swapped = true;
            }
        }
        if (!swapped) break; // already sorted — early exit optimization
    }
}
```

**Properties:**
- Time: O(n²) worst/average, O(n) best (with early exit when already sorted)
- Space: O(1)
- Stable: Yes
- In-place: Yes

**When used in TCS:** Never in a coding problem (too slow). Understanding it is tested in MCQ format.

---

## 2. Selection Sort

**Concept:** In each pass, find the minimum element in the unsorted portion and place it at the start of that portion.

```cpp
#include <vector>
#include <algorithm>

void selectionSort(std::vector<int>& arr) {
    int n = arr.size();
    for (int i = 0; i < n - 1; i++) {
        int minIdx = i;
        for (int j = i + 1; j < n; j++) {
            if (arr[j] < arr[minIdx]) minIdx = j;
        }
        std::swap(arr[i], arr[minIdx]);
    }
}
```

**Properties:**
- Time: O(n²) always
- Space: O(1)
- Stable: No
- In-place: Yes
- Makes exactly n-1 swaps (minimum swaps to sort)

---

## 3. Insertion Sort

**Concept:** Build a sorted sub-array one element at a time. Each new element is inserted into its correct position within the sorted portion by shifting larger elements right.

```cpp
#include <vector>

void insertionSort(std::vector<int>& arr) {
    int n = arr.size();
    for (int i = 1; i < n; i++) {
        int key = arr[i];
        int j = i - 1;
        while (j >= 0 && arr[j] > key) {
            arr[j + 1] = arr[j];
            j--;
        }
        arr[j + 1] = key;
    }
}
```

**Properties:**
- Time: O(n²) worst, O(n) best (already sorted)
- Space: O(1)
- Stable: Yes
- In-place: Yes
- **Excellent for nearly-sorted arrays**

---

## 4. Built-in Sort Usage (C++ STL)

C++ STL provides highly optimized sorting functions in the `<algorithm>` library.

### standard `std::sort`
Uses **IntroSort** (a hybrid of QuickSort, HeapSort, and InsertionSort). It guarantees O(n log n) worst-case time complexity.
```cpp
#include <algorithm>
#include <vector>
#include <functional> // for std::greater

// Ascending
std::sort(arr.begin(), arr.end());

// Descending
std::sort(arr.begin(), arr.end(), std::greater<int>());
// Or using reverse iterators:
std::sort(arr.rbegin(), arr.rend());

// Sort a portion of vector: [first, last)
std::sort(arr.begin() + 2, arr.begin() + 5); // sorts indices 2, 3, and 4
```

### sorting with custom comparator (Lambda)
```cpp
// Sort pairs by second element ascending:
std::sort(pairs.begin(), pairs.end(), [](const std::pair<int, int>& a, const std::pair<int, int>& b) {
    return a.second < b.second;
});

// Sort intervals by start time:
std::sort(intervals.begin(), intervals.end(), [](const std::vector<int>& a, const std::vector<int>& b) {
    return a[0] < b[0];
});
```

### stable sorting (`std::stable_sort`)
If you need equal elements to maintain their relative original order, use `std::stable_sort` (uses Merge Sort internally, taking O(N log N) time and O(N) extra space).
```cpp
std::stable_sort(arr.begin(), arr.end());
```

---

## 5. Merge Sort (Concept + Trace)

**Concept:** Divide and conquer. Split array in half recursively until single elements. Merge pairs of sorted subarrays back together.

**Trace for [5, 2, 8, 1, 9, 3]:**
```
Split:       [5,2,8] | [1,9,3]
Split again: [5,2] [8] | [1,9] [3]
Split again: [5] [2]   | [1] [9]
Merge pairs: [2,5] [8] | [1,9] [3]
Merge:       [2,5,8]   | [1,3,9]
Merge:       [1,2,3,5,8,9]
```

**Properties:**
- Time: O(n log n) always
- Space: O(n)
- Stable: Yes
- Used for: External sorting, linked lists, count inversions

**Key TCS fact:** Merge Sort is the basis of counting inversions in O(n log n) time.

---

## 6. Quick Sort (Concept + Trace)

**Concept:** Pick a pivot. Partition array so all elements < pivot are left, all > pivot are right. Recursively sort both sides.

**Trace for [3, 6, 8, 10, 1, 2, 1] with pivot = arr[last] = 1:**
```
Partition around 1: [1, 1] | [3, 6, 8, 10, 2] (pivot=1 is at correct position)
Recursively sort left [1]: base case
Recursively sort right [3,6,8,10,2] with pivot=2:
  [2] | [3,6,8,10]
  Final: [1, 1, 2, 3, 6, 8, 10]
```

**Properties:**
- Time: O(n log n) average, O(n²) worst (sorted/reverse-sorted input with bad pivot choice)
- Space: O(log n) for recursion stack
- Stable: No
- In-place: Yes (no auxiliary array needed)

---

## TCS-Specific Sorting Applications

| Problem | Sorting Technique | Why |
|---------|------------------|-----|
| Sort Colors | Dutch National Flag (O(n), O(1)) | 3-way partition, not sort |
| Kth Largest | QuickSelect / std::priority_queue | No need to fully sort |
| Merge Intervals | Sort by start + linear merge | Sorting preprocessing |
| Meeting Rooms | Sort by start time | Greedy needs sorted order |
| Relative Sort | Custom comparator | Non-standard ordering |
| Find Pairs | Sort + Two Pointer | O(n log n) vs O(n²) |
