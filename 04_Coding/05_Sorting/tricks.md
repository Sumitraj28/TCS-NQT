# Sorting — Tricks, Traps, and TCS-Specific Patterns

## Trap 1 — Custom Comparator: Strict Weak Ordering

**The trap:** Writing a comparator using `≤` or `≥` instead of `<` or `>`. C++ STL algorithms require the comparator to define a **strict weak ordering**. If you use `≤` (e.g. `a <= b`), when comparing `a` and `b` where `a == b`, both `a <= b` and `b <= a` return true. This violates the strict weak ordering requirement, resulting in undefined behavior, which can cause a runtime crash (segmentation fault) or infinite loop in `std::sort`.

**Fix:** Always use `<` or `>` in your comparators. Never use `<=` or `>=`.

```cpp
// CRASH RISK (contains <=):
std::sort(arr.begin(), arr.end(), [](int a, int b) { return a <= b; });

// SAFE (strict <):
std::sort(arr.begin(), arr.end(), [](int a, int b) { return a < b; });
```

---

## Trap 2 — Unnecessary Full Sorting

**The trap:** Fully sorting an array when you only need the top k elements or the kth element (e.g., Kth Largest Element). Sorting takes O(N log N) time, which might TLE (Time Limit Exceeded) if N is large.

**Fix:** Use `std::nth_element` (QuickSelect) which runs in O(N) average time, or use a min-heap / max-heap (`std::priority_queue`) of size K which runs in O(N log K).

```cpp
// O(N) instead of O(N log N)
std::nth_element(arr.begin(), arr.begin() + k, arr.end());
```

---

## Trap 3 — Stability Requirements

**The trap:** Using `std::sort` when the problem requires relative order preservation. `std::sort` uses IntroSort which is not stable.

**Fix:** Use `std::stable_sort` (which uses Merge Sort internally) to preserve original relative order of equal elements.

---

## Trap 4 — Counting Sort Index Shift

**The trap:** Applying counting sort directly when values include negative numbers. Since array indices cannot be negative, accessing `count[arr[i]]` will crash.

**Fix:** Find the minimum element in the array (`minVal`). Offset all indices by `abs(minVal)` during counting, and shift them back when reconstructing the array.

```cpp
int minVal = *std::min_element(arr.begin(), arr.end());
// offset = -minVal
// count[arr[i] + offset]++;
```

---

## Trap 5 — Overflow in Comparator subtraction

**The trap:** Writing a comparator using `a - b` (e.g., `return a - b < 0;` or similar Java style translated to C++). If `a` is a large positive number and `b` is a large negative number, `a - b` will overflow, producing incorrect results.

**Fix:** Always use explicit comparison operators (`a < b`).

```cpp
// WRONG (overflow risk):
bool compare(int a, int b) { return (a - b) < 0; }

// RIGHT:
bool compare(int a, int b) { return a < b; }
```

---

## TCS Pattern Recognition

| Keyword in Problem | Sorting Technique |
|-------------------|------------------|
| "sort elements in range [0, 1, 2]" | Dutch National Flag (O(n) time, O(1) space) |
| "merge intervals" | Sort by start time + linear traversal |
| "minimum platforms / train arrival" | Sort arrival and departure separately |
| "kth largest element" | `std::nth_element` or Heap |
| "relative sorting" | Custom comparator using index map |
| "count inversions" | Modified Merge Sort |
| "minimum swaps to sort" | Cycle decomposition using graph concept |
