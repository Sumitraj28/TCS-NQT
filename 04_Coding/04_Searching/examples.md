# Searching — 5 Worked Examples

---

## Example 1 — Standard Binary Search

**Problem:** Find the index of target=11 in `arr = [2, 5, 8, 11, 15, 23, 30]`.

| Step | lo | hi | mid | arr[mid] | Decision |
|------|----|----|-----|----------|---------|
| 1 | 0 | 6 | 3 | 11 | == target → **FOUND at 3** |

**Answer:** Index 3.
**Explanation:** Single step because mid happened to be target. In worst case (7 elements), we'd need ⌈log₂7⌉ = 3 steps.

---

## Example 2 — Lower Bound

**Problem:** `arr = [1, 3, 5, 5, 5, 7, 9]`. Find lower bound (first index ≥ 5).

| lo | hi | mid | arr[mid] | Condition | Action |
|----|----|----|---------|-----------|--------|
| 0 | 7 | 3 | 5 | ≥ 5 → possible answer | hi = 3 |
| 0 | 3 | 1 | 3 | < 5 → can't be | lo = 2 |
| 2 | 3 | 2 | 5 | ≥ 5 → possible answer | hi = 2 |
| 2 | 2 | — | — | lo == hi | DONE |

**Answer:** Lower bound = 2 (first occurrence of 5 is at index 2). ✓

---

## Example 3 — Count of Occurrences

**Problem:** How many times does 5 appear in `arr = [1, 3, 5, 5, 5, 7, 9]`?

- Lower bound of 5 = 2 (from Example 2)
- Upper bound of 5 = first index where arr[i] > 5 = 5 (index of 7)
- **Count = upper − lower = 5 − 2 = 3** ✓

(Verify: arr[2]=5, arr[3]=5, arr[4]=5 → 3 occurrences ✓)

---

## Example 4 — First Occurrence (with duplicates)

**Problem:** `arr = [2, 4, 4, 4, 4, 7]`. Find the first occurrence of 4.

| lo | hi | mid | arr[mid] | Decision |
|----|----|----|---------|---------|
| 0 | 5 | 2 | 4 | == target → result=2, hi=1 |
| 0 | 1 | 0 | 2 | < target → lo=1 |
| 1 | 1 | 1 | 4 | == target → result=1, hi=0 |
| lo=1 > hi=0 | | | | DONE |

**Answer:** First occurrence at index 1. ✓

---

## Example 5 — Binary Search on Answer Space

**Problem:** `arr = [10, 4, 2, 7, 6]`, `days = 3`. Find minimum shipping capacity such that all packages can be shipped within 3 days (packages must be shipped in order; any day's total ≤ capacity).

**Answer space:** capacity ranges from max(arr)=10 to sum(arr)=29.

**Feasibility check (can we ship in 3 days with capacity cap):**
```
Simulate: current_day_weight = 0, days_used = 1
For each package: if adding it exceeds cap → new day (days_used++). Add to current.
Return days_used <= 3.
```

**Binary search:**
- lo=10, hi=29, mid=19: simulate → [10,4,2]=16<19, then [7,6]=13<19, done in 2 days ≤ 3 → feasible → hi=19
- lo=10, hi=19, mid=14: simulate → [10,4]=14, then [2,7]=9, then [6]=6, 3 days ≤ 3 → feasible → hi=14
- lo=10, hi=14, mid=12: simulate → [10]=10, [4,2]=6, [7,6]=13>12 → new day → [6]=6, 4 days > 3 → not feasible → lo=13
- lo=13, hi=14, mid=13: simulate → [10]=10, [4,2]=6, [7,6]=13 ≤ 13, 3 days ≤ 3 → feasible → hi=13
- lo=13, hi=13 → DONE

**Answer:** 13
