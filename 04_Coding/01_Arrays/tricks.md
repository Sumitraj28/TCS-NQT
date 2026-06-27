# Arrays — Tricks, Traps, and TCS-Specific Patterns

## Trap 1 — Off-By-One in Sliding Window

**The trap:** When sliding a window of size `k`, the new element enters at index `i` and the old one exits at index `i - k`. Getting this wrong by 1 gives wrong answers on every window.

**Fix:** Always verify: if `i` is the rightmost index of the current window, left boundary is `i - k + 1` and the element leaving is at `i - k`.

```cpp
// RIGHT: windowSum += nums[i] - nums[i - k];
// WRONG: windowSum += nums[i] - nums[i - k + 1];
```

---

## Trap 2 — Kadane's With All-Negative Arrays

**The trap:** Initializing `maxSum = 0` gives wrong answer when all elements are negative (answer should be the least-negative element, not 0).

**Fix:** Initialize `maxSum = nums[0]` and `currentSum = nums[0]`, then start the loop from index 1.

```cpp
// WRONG (fails all-negative input):
int maxSum = 0;
// RIGHT:
int maxSum = nums[0], currentSum = nums[0];
for (size_t i = 1; i < nums.size(); ++i) { ... }
```

---

## Trap 3 — Two Pointer Requires Sorted Array

**The trap:** Applying two-pointer to find a pair with given sum on an **unsorted** array. This gives wrong answers.

**Fix:** Either sort first (and note that sorting changes indices — if indices are needed, use hash table instead), or use `std::unordered_map` for O(n) unsorted solution.

---

## Trap 4 — Integer Overflow in Prefix Sum

**The trap:** Array values can be large (e.g., up to 10⁹), and sum of 10⁵ such values exceeds `INT_MAX` (2.14 × 10⁹).

**Fix:** Use `long long` for prefix sums whenever values × count could exceed 2 × 10⁹.

```cpp
std::vector<long long> prefix(n + 1, 0); // not std::vector<int>
```

---

## Trap 5 — Rotation Modulo

**The trap:** Rotating by `k` when `k >= n` causes index out of bounds or incorrect result.

**Fix:** Always apply `k = k % n` before any rotation logic.

```cpp
k = k % nums.size(); // if k == 0, no rotation needed
if (k == 0) return;
```

---

## Trap 6 — In-Place Sign-Marking Corrupts Input

**The trap:** The in-place marking trick (negating `nums[idx]` to mark visited) breaks if you read `nums[idx]` after marking without taking `std::abs()`.

**Fix:** Always use `int idx = std::abs(num) - 1;` — take abs of the value before using it as an index, because a previously marked element will be negative.

```cpp
for (int num : nums) {
    int idx = std::abs(num) - 1;  // ← std::abs is critical here
    if (nums[idx] > 0) nums[idx] = -nums[idx];
}
```

---

## Trap 7 — Dutch National Flag: mid Stops, high Moves

**The trap:** When `nums[mid] == 2`, you swap with `high` and decrement `high` — but do NOT increment `mid`. The swapped-in element at `mid` is not yet examined.

**Fix:** Only increment `mid` for cases 0 and 1, not for case 2.

```cpp
if      (nums[mid] == 0) { std::swap(nums[low], nums[mid]); low++; mid++; }
else if (nums[mid] == 1) { mid++; }                         // mid moves
else                     { std::swap(nums[mid], nums[high]); high--; }       // mid stays!
```

---

## Trap 8 — Subarray Sum = k Fails with Sorting

**The trap:** If you sort the array before solving "subarray sum = k", you destroy the ordering, which is required for subarrays to be contiguous.

**Fix:** Never sort for subarray problems. Use prefix sum + `std::unordered_map` (works for negative numbers too).

---

## Trap 9 — Product Except Self: Don't Use Division

**The trap:** The intuitive solution divides total product by each element — but fails when the array contains zeros (division by zero).

**Fix:** Use left-pass × right-pass without any division.

---

## Trap 10 — Third Maximum: long long Not int

**The trap:** If the array contains `INT_MIN`, using `int` for the "not seen" sentinel fails because `INT_MIN` could be a valid array element.

**Fix:** Use `long long` initialized to `LLONG_MIN` as the sentinel:

```cpp
long long first = LLONG_MIN, second = LLONG_MIN, third = LLONG_MIN;
```

---

## TCS-Specific Pattern Spotting

| Keyword in Problem | Pattern to Use |
|-------------------|---------------|
| "contiguous subarray with maximum sum" | Kadane's |
| "subarray with sum equal to k" | Prefix Sum + std::unordered_map |
| "maximum sum of subarray of size k" | Sliding Window (fixed) |
| "smallest subarray with sum ≥ k" | Sliding Window (variable) |
| "pair with sum" (sorted) | Two Pointer |
| "two numbers that add to target" (unsorted) | std::unordered_map |
| "missing number in 1 to n" | Sum formula or XOR |
| "0s, 1s, 2s sort" | Dutch National Flag |
| "rotate array" | Reverse method |
| "product except self" | Left × Right pass |
