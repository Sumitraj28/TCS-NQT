# Arrays — Common Mistakes (8 Specific Traps)

---

### Mistake 1 — Initializing maxSum = 0 in Kadane's

**What goes wrong:** For `nums = [-5, -1, -3]`, Kadane's returns 0 (wrong). The correct answer is -1 (least negative).

**Fix:** Initialize `maxSum = nums[0]` and `currentSum = nums[0]`, start loop at index 1.

```cpp
// WRONG:
int maxSum = 0;
// RIGHT:
int maxSum = nums[0], currentSum = nums[0];
for (size_t i = 1; i < nums.size(); ++i) { ... }
```

---

### Mistake 2 — Using int Instead of long long for Prefix Sums

**What goes wrong:** If `nums[i]` can be up to 10⁹ and array has 10⁵ elements, prefix sum can reach 10¹⁴ — well beyond `INT_MAX` (≈2.14×10⁹).

**Fix:** Declare prefix sum vector as `std::vector<long long>`.

---

### Mistake 3 — Not Taking std::abs() in Sign-Marking

**What goes wrong:** In the disappeared numbers trick, if `nums[3] = -7` (already marked), using it as an index without abs gives `idx = -7 - 1 = -8` → `ArrayIndexOutOfBoundsException` / Segmentation fault.

**Fix:** Always `int idx = std::abs(num) - 1;`.

---

### Mistake 4 — Wrong Sliding Window Boundary

**What goes wrong:** Sliding window of size k: when adding new element at `right = i`, the element leaving is at `i - k`, not `i - k + 1`.

```cpp
// WRONG (off by 1):
windowSum += nums[i] - nums[i - k + 1];
// RIGHT:
windowSum += nums[i] - nums[i - k];
```

---

### Mistake 5 — Not Handling k > n in Rotation

**What goes wrong:** Rotating by k=10 on vector of size n=7 — reversing ranges out of bounds causes crash.

**Fix:** `k = k % n;` before any rotation. Also handle `k == 0` (no rotation needed).

---

### Mistake 6 — Forgetting to Advance mid After Swap in Dutch National Flag

**What goes wrong:** When `nums[mid] == 2`, swapping with high and then incrementing `mid` causes the newly-placed element (from high) to be skipped without examination.

**Fix:** Only increment `mid` for cases 0 and 1, NOT for case 2.

---

### Mistake 7 — Using Division in Product Except Self (Zero Handling)

**What goes wrong:** `totalProduct / nums[i]` fails when any `nums[i] == 0` (division by zero).

**Fix:** Use the left-pass + right-pass approach with no division.

---

### Mistake 8 — Two Pointer on Unsorted Array for Pair Sum

**What goes wrong:** For `[3, 1, 4, 2]` and target=5: left=0(3), right=3(2), sum=5 → "found [3,2]". But this misses [1,4]. Also misses the fact that the two pointer assumes the array is sorted.

**Fix:** For unsorted arrays, use `std::unordered_map` for O(n) pair-finding. Only use two pointer after sorting (if indices don't matter).

---

### Mistake 9 — Prefix Sum Put Before Count (Wrong Order)

**What goes wrong:** In Subarray Sum = k, if you do `prefixCount[sum]++` BEFORE `count += prefixCount[sum - k]`, you might count the current position against itself when k=0.

**Fix:** Always update `count` first, then update the map:
```cpp
count += prefixCount[sum - k];
prefixCount[sum]++;
```

---

### Mistake 10 — Using INT_MIN as Sentinel for Third Max

**What goes wrong:** If `nums = [1, 2, INT_MIN]`, the third maximum is `INT_MIN`. But if you use `int` with `INT_MIN` as the "not seen" sentinel, you can't distinguish between "not set" and "actually equal to INT_MIN".

**Fix:** Use `long long` variables initialized to `LLONG_MIN`. Cast back to `int` only at the final return.
