# Sorting — Common Mistakes

### Mistake 1 — Violating Strict Weak Ordering in Comparators
Using `<=` or `>=` inside custom sorting comparators instead of strict `<` or `>` comparisons. This can cause memory corruption (segmentation fault) or infinite recursion in `std::sort`.
```cpp
// WRONG (CRASH DANGER):
std::sort(v.begin(), v.end(), [](int a, int b) { return a <= b; });

// RIGHT:
std::sort(v.begin(), v.end(), [](int a, int b) { return a < b; });
```

---

### Mistake 2 — Sorting the Entire Array for Kth Largest Element
Fully sorting a vector of size N to get only one element (e.g. at index N-k). Takes O(N log N) time, which causes TLE on large arrays.
**Fix:** Use `std::nth_element` which takes O(N) average time.

---

### Mistake 3 — Counting Sort with Negative Values
Attempting to map negative array values directly to count frequencies using array indices (`count[arr[i]]`). This results in negative indices and crash / segmentation fault.
**Fix:** Apply a minimum value offset to all indices.

---

### Mistake 4 — Assuming `std::sort` is Stable
Relying on `std::sort` to preserve the original relative order of equal elements. `std::sort` is not stable.
**Fix:** Use `std::stable_sort`.

---

### Mistake 5 — Comparator Subtract Overflow
Using subtraction to sort (e.g., `return a - b < 0`). If `a` is large positive and `b` is large negative, `a - b` overflows and returns incorrect sorting order.
**Fix:** Always use explicit comparison operator `<`.

---

### Mistake 6 — Forgetting to Increment mid in Case 0 (Dutch National Flag)
In the Dutch National Flag algorithm, when `arr[mid] == 0`, swapping with low but forgetting to increment `mid`.
**Fix:** Swap and increment both: `std::swap(nums[low++], nums[mid++]);`

---

### Mistake 7 — Incrementing mid in Case 2 (Dutch National Flag)
Incrementing `mid` after swapping with high. The swapped element from high is unexamined and could be 0, 1, or 2. Incrementing `mid` skips examining it.
**Fix:** Swap and decrement high only: `std::swap(nums[mid], nums[high--]);` (do NOT increment `mid`).
