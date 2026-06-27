# Sorting — Formulas and Complexity Reference

## Algorithm Comparison Table

| Algorithm | Best | Average | Worst | Space | Stable | In-Place |
|-----------|------|---------|-------|-------|--------|---------|
| Bubble Sort | O(n) | O(n²) | O(n²) | O(1) | ✅ Yes | ✅ Yes |
| Selection Sort | O(n²) | O(n²) | O(n²) | O(1) | ❌ No | ✅ Yes |
| Insertion Sort | O(n) | O(n²) | O(n²) | O(1) | ✅ Yes | ✅ Yes |
| Merge Sort | O(n log n) | O(n log n) | O(n log n) | O(n) | ✅ Yes | ❌ No |
| Quick Sort | O(n log n) | O(n log n) | O(n²) | O(log n) | ❌ No | ✅ Yes |
| Heap Sort | O(n log n) | O(n log n) | O(n log n) | O(1) | ❌ No | ✅ Yes |
| Counting Sort | O(n+k) | O(n+k) | O(n+k) | O(k) | ✅ Yes | ❌ No |
| std::sort (IntroSort) | O(n log n) | O(n log n) | O(n log n) | O(log n) | ❌ No | ✅ Yes |
| std::stable_sort | O(n log n) | O(n log n) | O(n log n) | O(n) | ✅ Yes | ❌ No |

---

## Key Formulas

### Number of comparisons (worst case)
```
Bubble Sort:    n(n-1)/2  comparisons,  n(n-1)/2 swaps (worst)
Selection Sort: n(n-1)/2  comparisons,  n-1 swaps (always exactly n-1)
Insertion Sort: n(n-1)/2  comparisons,  n(n-1)/2 shifts (worst)
Merge Sort:     n log n   comparisons
Quick Sort:     n log n   comparisons (average), n² (worst)
```

### Merge Sort Recurrence
```
T(n) = 2T(n/2) + O(n)
By Master Theorem: T(n) = O(n log n)
```

### Quick Sort Recurrence (average)
```
T(n) = T(n/2) + T(n/2) + O(n)   [balanced pivot]
     = O(n log n)

T(n) = T(n-1) + O(n)             [worst case: sorted input, pivot=last]
     = O(n²)
```

---

## Stability Definition

A sorting algorithm is **stable** if equal elements maintain their relative original order.

**Why it matters:** When sorting objects by one key, stable sort preserves previous sort order on other keys.

**Stable:** Bubble, Insertion, Merge, std::stable_sort, Counting  
**Not Stable:** Selection, Quick, Heap, std::sort

---

## Counting Sort (for bounded integer ranges)

```cpp
// If values are in [0, k]:
// 1. Count occurrences: count[v]++
// 2. Compute prefix sums: count[i] += count[i-1]
// 3. Build output: output[--count[arr[i]]] = arr[i]
```
Time: O(n + k), Space: O(k)

---

## Quick Reference

| Need | Use |
|------|-----|
| Any sorting need, n ≤ 10⁵ | `std::sort()` |
| Stable sort | `std::stable_sort()` |
| Nearly sorted, small n | Insertion Sort |
| Guaranteed O(n log n) | Merge Sort |
| Count inversions | Modified Merge Sort |
| Kth element without full sort | std::nth_element (QuickSelect O(N)) |
| Sort 0s, 1s, 2s | Dutch National Flag O(n) |
| Custom comparator | Lambda in std::sort |
