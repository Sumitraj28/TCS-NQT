# Searching — Formulas and Complexity Reference

## Time and Space Complexities

| Algorithm | Best | Average | Worst | Space |
|-----------|------|---------|-------|-------|
| Linear Search | O(1) | O(n) | O(n) | O(1) |
| Binary Search | O(1) | O(log n) | O(log n) | O(1) iterative |
| Binary Search (recursive) | O(1) | O(log n) | O(log n) | O(log n) stack |
| Lower Bound | O(1) | O(log n) | O(log n) | O(1) |
| Upper Bound | O(1) | O(log n) | O(log n) | O(1) |
| First Occurrence | O(1) | O(log n) | O(log n) | O(1) |
| Last Occurrence | O(1) | O(log n) | O(log n) | O(1) |

---

## Key Formulas

### Number of iterations in binary search
```
After k iterations, search space = n / 2^k
Search ends when n / 2^k = 1  →  k = log₂(n)
Maximum iterations = ⌈log₂(n)⌉
```

Example: n=1024 → log₂(1024) = 10 iterations maximum.

### Mid-point calculation (overflow-safe)
```
mid = lo + (hi - lo) / 2
```
NOT: `mid = (lo + hi) / 2`  ← can overflow when both > 10⁹ in Java/C++

### Count of a value in sorted array
```
count = upperBound(arr, x) - lowerBound(arr, x)
```

### Insert position (0-indexed) for value x in sorted array
```
insertPos = lowerBound(arr, x)
```

### Number of elements less than x in sorted array
```
count_less_than_x = lowerBound(arr, x)
```

### Number of elements ≤ x in sorted array
```
count_leq_x = upperBound(arr, x)
```

---

## Binary Search Decision Table

| Condition | Template to use |
|-----------|----------------|
| Find exact target | Standard: `if arr[mid]==target return mid` |
| Find first index where `arr[i] >= x` | Lower Bound |
| Find first index where `arr[i] > x` | Upper Bound |
| Find first occurrence of x | First Occurrence (save mid, go left) |
| Find last occurrence of x | Last Occurrence (save mid, go right) |
| Find any peak | Find Peak Element |
| Find minimum answer satisfying a condition | Binary Search on Answer Space |

---

## Binary Search: Loop Termination Conditions

| Situation | Loop Condition | hi initialization | Final Answer |
|-----------|---------------|-------------------|-------------|
| Exact match | `lo <= hi` | `arr.size() - 1` | return mid or -1 |
| Lower bound | `lo < hi` | `arr.size()` | return lo |
| Upper bound | `lo < hi` | `arr.size()` | return lo |
| Peak element | `lo < hi` | `arr.size() - 1` | return lo |
| Answer space | `lo < hi` | `maxAnswer` | return lo |

> The choice of `<=` vs `<` in the loop and whether `hi = n` or `hi = n-1` completely determines the correctness of the result. Getting this wrong is the #1 binary search bug.

---

## Quick-Revision Formula Table

| Formula | Meaning |
|---------|---------|
| `mid = lo + (hi - lo) / 2` | Safe midpoint |
| `lowerBound(arr, x)` | First i where arr[i] >= x |
| `upperBound(arr, x)` | First i where arr[i] > x |
| `upper - lower` | Count of x in sorted arr |
| `⌈log₂(n)⌉` | Max binary search iterations |
| `feasible(lo)` where `lo == hi` | Answer-space binary search terminates |
