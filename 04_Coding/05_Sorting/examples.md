# Sorting — 5 Worked Examples

---

## Example 1 — Bubble Sort Trace

**Problem:** Sort `arr = [5, 1, 4, 2]` using Bubble Sort.

**Trace:**
- **Pass 1:**
  - Compare (5, 1) → swap → `[1, 5, 4, 2]`
  - Compare (5, 4) → swap → `[1, 4, 5, 2]`
  - Compare (5, 2) → swap → `[1, 4, 2, 5]` (5 is sorted at the end)
- **Pass 2:**
  - Compare (1, 4) → no swap
  - Compare (4, 2) → swap → `[1, 2, 4, 5]` (4 is sorted)
- **Pass 3:**
  - Compare (1, 2) → no swap (no swaps in this pass, early exit)

**Result:** `[1, 2, 4, 5]`

---

## Example 2 — Selection Sort Trace

**Problem:** Sort `arr = [29, 10, 14, 37]` using Selection Sort.

**Trace:**
- **Pass 1 (i=0):** min index = 1 (val 10). Swap arr[0] and arr[1] → `[10, 29, 14, 37]`
- **Pass 2 (i=1):** min index = 2 (val 14). Swap arr[1] and arr[2] → `[10, 14, 29, 37]`
- **Pass 3 (i=2):** min index = 2 (val 29). No swap needed → `[10, 14, 29, 37]`
- Array sorted.

**Result:** `[10, 14, 29, 37]`

---

## Example 3 — Insertion Sort Trace

**Problem:** Sort `arr = [8, 5, 2, 9]` using Insertion Sort.

**Trace:**
- **i=1 (key=5):** Compare 8 > 5 → shift 8 → `[8, 8, 2, 9]` → insert key → `[5, 8, 2, 9]`
- **i=2 (key=2):** Compare 8 > 2 → shift 8, Compare 5 > 2 → shift 5 → `[5, 5, 8, 9]` → insert key → `[2, 5, 8, 9]`
- **i=3 (key=9):** Compare 8 < 9 → no shift → `[2, 5, 8, 9]`
- Array sorted.

**Result:** `[2, 5, 8, 9]`

---

## Example 4 — Custom Object Sort (Intervals)

**Problem:** Sort intervals `[[1,3], [8,10], [2,6]]` by start time in C++.

**C++ Code:**
```cpp
#include <vector>
#include <algorithm>

void sortIntervals(std::vector<std::vector<int>>& intervals) {
    std::sort(intervals.begin(), intervals.end(), [](const std::vector<int>& a, const std::vector<int>& b) {
        return a[0] < b[0];
    });
}
```

**Trace:**
- Input: `[[1,3], [8,10], [2,6]]`
- Compare starts: 1 < 8 (order OK), 8 > 2 (swap needed), 1 < 2 (order OK).
- Sorted: `[[1,3], [2,6], [8,10]]`

---

## Example 5 — Counting Sort with Negative Values

**Problem:** Sort `arr = [3, -2, 0, -2, 1]` using Counting Sort.

**Trace:**
- Find range: min = -2, max = 3. Range size = 3 - (-2) + 1 = 6.
- Offset = -min = 2.
- Array elements offset: `arr` becomes index-ready as `[5, 0, 2, 0, 3]`.
- Count array of size 6: `count = [2, 0, 1, 1, 0, 1]` (representing count of values -2, -1, 0, 1, 2, 3).
- Reconstruct using counts:
  - count[0]=2 times → val = 0-2 = -2. Array: `[-2, -2]`
  - count[2]=1 time → val = 2-2 = 0. Array: `[-2, -2, 0]`
  - count[3]=1 time → val = 3-2 = 1. Array: `[-2, -2, 0, 1]`
  - count[5]=1 time → val = 5-2 = 3. Array: `[-2, -2, 0, 1, 3]`

**Result:** `[-2, -2, 0, 1, 3]`
