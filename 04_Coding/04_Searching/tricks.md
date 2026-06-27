# Searching — Tricks, Traps, and TCS Patterns

## Trap 1 — Integer Overflow in Mid Calculation

**The trap:** `int mid = (lo + hi) / 2;` — if both lo and hi are near `INT_MAX`, their sum overflows to a negative number, giving a wrong (or negative) mid.

**Fix:** Always use `int mid = lo + (hi - lo) / 2;`

---

## Trap 2 — Wrong Loop Condition (`<=` vs `<`)

**The trap:** Using `while (lo <= hi)` for lower/upper bound returns wrong results; using `while (lo < hi)` for exact-match search causes missed final element.

**Fix:** 
- Exact match → `lo <= hi`, `hi = n-1`
- Bounds / Peak / Answer Space → `lo < hi`, `hi = n` (or `n-1` for peak)

---

## Trap 3 — Applying Binary Search on Unsorted Array

**The trap:** Candidate sees a search question and applies binary search without checking if the array is sorted. Gets wrong answers.

**Fix:** Binary search's correctness guarantee requires the **monotone property** — either sorted order or a condition that is strictly false then true (or vice versa).

---

## Trap 4 — Not Saving Result in First/Last Occurrence

**The trap:** On finding `arr[mid] == target`, returning `mid` immediately. This gives any occurrence, not necessarily first or last.

**Fix:**
- First occurrence: save `result = mid`, then `hi = mid - 1` (keep searching left)
- Last occurrence: save `result = mid`, then `lo = mid + 1` (keep searching right)

```cpp
// WRONG (first occurrence):
if (arr[mid] == target) return mid; // stops at any match
// RIGHT:
if (arr[mid] == target) { result = mid; hi = mid - 1; } // continue left
```

---

## Trap 5 — `hi = n` vs `hi = n-1`

**The trap:** Using `hi = arr.size() - 1` for lower/upper bound when the answer might be `arr.size()` (i.e., all elements are less than target → insert at the end). The loop terminates with `lo = hi = n-1` and misses returning `n`.

**Fix:** For lower bound and upper bound, use `hi = arr.size()` (not `arr.size() - 1`).

---

## Trap 6 — Built-in lower_bound Returns Iterator

**The trap:** `std::lower_bound` returns an iterator, not an integer index. Dereferencing it directly when target is not present might lead to reading next elements or undefined behavior if it equals `.end()`.

**Fix:** Always subtract `arr.begin()` to get the index, and check if it is within bounds before dereferencing:
```cpp
auto it = std::lower_bound(arr.begin(), arr.end(), target);
if (it != arr.end()) {
    int val = *it;
    int idx = it - arr.begin();
}
```

---

## Trap 7 — Peak Element: Checking Both Neighbors

**The trap:** Checking `arr[mid] > arr[mid-1] && arr[mid] > arr[mid+1]` can throw out-of-bounds errors at boundaries (mid=0 or mid=n-1).

**Fix:** The slope-following approach (`if (nums[mid] < nums[mid+1]) lo = mid + 1; else hi = mid;`) never accesses `mid-1` and handles boundaries naturally.

---

## TCS Pattern Recognition

| If the problem says... | Think... |
|-----------------------|---------|
| "array is sorted, find element" | Binary search |
| "find first/last position of x in sorted array" | First/Last occurrence |
| "how many times does x appear in sorted array" | `std::upper_bound` - `std::lower_bound` |
| "find peak element" | Peak binary search |
| "first version that is bad" | Answer-space binary search (minimize first True) |
| "minimum X such that condition holds" | Binary search on answer |
| "search in rotated sorted array" | Modified binary search (detect which half is sorted) |
| "unsorted array, find x" | Linear search or `std::unordered_map` |
