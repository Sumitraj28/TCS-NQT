# Arrays — Quiz (Rapid-Fire Flashcards)

## 10 Q&A Flashcard Pairs

---

**Q1:** What is the time complexity of Kadane's algorithm?
**A1:** O(n) time, O(1) space — single pass, constant extra memory.

---

**Q2:** What is the bug if you initialize `maxSum = 0` in Kadane's and all elements are negative?
**A2:** You return 0 instead of the correct (least-negative) answer. Always initialize with `nums[0]`.

---

**Q3:** For prefix sum array `pre[]` where `pre[i+1] = pre[i] + nums[i]`, what formula gives the sum of elements from index l to r (0-indexed, inclusive)?
**A3:** `pre[r+1] - pre[l]`

---

**Q4:** In a sliding window of fixed size k, what single expression updates the window sum when the window moves one step right?
**A4:** `windowSum += nums[i] - nums[i - k]`  (add new right element, remove old left element)

---

**Q5:** What is the core idea of Boyer-Moore Voting Algorithm?
**A5:** Maintain a candidate and a counter. Increment for a match, decrement for a non-match. When counter hits 0, switch candidate. The majority element (>n/2) always survives.

---

**Q6:** What must you do BEFORE rotating an array by k positions to handle k ≥ n?
**A6:** Compute `k = k % n`. This is mandatory to prevent out-of-bounds and to avoid no-op rotations.

---

**Q7:** Why does the Dutch National Flag algorithm NOT increment `mid` when `nums[mid] == 2`?
**A7:** Because the element swapped from position `high` to `mid` has not been examined yet — it could be 0, 1, or 2 and needs to be processed in the next iteration.

---

**Q8:** What data type should you use for prefix sums in C++ when array values can be up to 10⁹ and n can be up to 10⁵?
**A8:** `long long` — since 10⁹ × 10⁵ = 10¹⁴, which far exceeds `INT_MAX` (~2.14×10⁹).

---

**Q9:** In the in-place sign-marking technique to find disappeared numbers, why must you use `std::abs(num)` when computing the index?
**A9:** Because previously-visited elements may have been negated. Without `std::abs`, the negative value would give an incorrect (or negative) array index causing out-of-bounds/segmentation fault.

---

**Q10:** For "Product of Array Except Self", why can't you use the total product divided by each element?
**A10:** Division fails when any element is 0 (division by zero). The left-pass × right-pass method avoids division entirely and handles zeros correctly.

---

## 5 True / False Statements

**TF1:** In Kadane's algorithm, when `currentSum + nums[i] < nums[i]`, it means `currentSum` is negative.
**→ TRUE.** If `currentSum < 0`, starting fresh at `nums[i]` alone is better.

---

**TF2:** Two-pointer on an unsorted array can correctly find all pairs with a given sum.
**→ FALSE.** Two-pointer (opposite ends) only works correctly on a SORTED array. For unsorted, use `std::unordered_map`.

---

**TF3:** The prefix sum of an array with all zeros is all zeros.
**→ TRUE.** `prefix[i] = prefix[i-1] + 0 = 0` for all i.

---

**TF4:** Rotating an array right by k positions is equivalent to rotating it left by (n-k) positions.
**→ TRUE.** Right by k = Left by (n-k). Both produce the same result.

---

**TF5:** The Dutch National Flag algorithm requires exactly one pass through the array.
**→ TRUE.** All three pointers (low, mid, high) together scan the array exactly once. Each element is processed at most twice.
