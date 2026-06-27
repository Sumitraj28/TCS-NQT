# Searching — Common Mistakes

### Mistake 1 — Integer Overflow in Mid
`(lo + hi) / 2` overflows. Always use `lo + (hi - lo) / 2`.

### Mistake 2 — Wrong Loop: `<=` vs `<`
- Exact match → `lo <= hi`. Bounds/Peak → `lo < hi`. Mixing these causes infinite loops or missed elements.

### Mistake 3 — `hi = arr.size() - 1` for Lower/Upper Bound
Lower/upper bound can return `n` (all elements smaller than target). Use `hi = arr.size()`.

### Mistake 4 — Returning Mid Immediately for First Occurrence
On finding `arr[mid] == target`, you must continue searching left (`hi = mid - 1`) and save the result. Returning immediately gives an arbitrary occurrence.

### Mistake 5 — Dereferencing end() Iterator
`std::lower_bound` returns `arr.end()` if target is larger than all elements. Dereferencing it directly causes undefined behavior. Always check `if (it != arr.end())` first.

### Mistake 6 — Binary Searching Unsorted Array
Binary search assumes sorted (or monotone) input. On unsorted arrays, the result is unpredictable.

### Mistake 7 — Peak Element: Accessing `nums[mid+1]` Without Bound Check
If you use `lo <= hi` instead of `lo < hi`, `mid` can equal `hi = n-1`, making `nums[mid+1]` out of bounds.

### Mistake 8 — Not Handling `hi = mid` in Bounds/Peak (Causes Infinite Loop)
Using `hi = mid - 1` for lower bound or peak search excludes the answer. The loop may never converge. Use `hi = mid`.
