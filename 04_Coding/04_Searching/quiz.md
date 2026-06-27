# Searching — Quiz

## 10 Q&A Flashcard Pairs

**Q1:** What is the safe mid formula in binary search?
**A1:** `mid = lo + (hi - lo) / 2` — prevents integer overflow when lo and hi are both large.

**Q2:** For exact-match binary search, what loop condition and hi initialization are correct?
**A2:** `while (lo <= hi)`, `hi = n - 1` (closed interval on both ends).

**Q3:** For lower bound (first i where arr[i] ≥ x), what loop condition and hi initialization are correct?
**A3:** `while (lo < hi)`, `hi = n` (answer can be n if all elements < x).

**Q4:** How do you find the count of element x in a sorted array using binary search?
**A4:** `count = upperBound(arr, x) - lowerBound(arr, x)`. This is O(2 log n) = O(log n).

**Q5:** In `findPeakElement`, when `nums[mid] < nums[mid+1]`, where is the peak?
**A5:** In the right half (including mid+1). Set `lo = mid + 1`.

**Q6:** What is the maximum number of API calls made by First Bad Version binary search for n=10?
**A6:** ⌈log₂(10)⌉ = 4 calls.

**Q7:** In the answer-space binary search template, when `feasible(mid)` returns true, do you set `hi = mid` or `hi = mid - 1`?
**A7:** `hi = mid` — mid itself could be the answer; we must not exclude it.

**Q8:** What do `std::lower_bound` and `std::upper_bound` return in C++?
**A8:** They return iterators. To convert to a 0-based integer index, subtract the beginning iterator: `it - arr.begin()`.

**Q9:** What is the difference between linear search and sentinel linear search?
**A9:** Sentinel eliminates the `i < n` boundary check by placing a copy of target at arr[n]. Reduces number of comparisons per iteration from 2 to 1.

**Q10:** Why does binary search on a rotated sorted array still work in O(log n)?
**A10:** At each mid, one half is always sorted. We can determine in O(1) whether the target is in the sorted half. Eliminating one half per step maintains O(log n).

---

## 5 True / False Statements

**TF1:** Binary search requires the array to be sorted in ascending order only.
**→ FALSE.** Binary search works on any sorted order (ascending or descending) as long as the monotone property holds. For descending, flip the comparison.

**TF2:** Lower bound of x returns the index of the first occurrence of x in the array.
**→ FALSE** (partially). Lower bound returns the first index where `arr[i] ≥ x`. If x is present, this is indeed the first occurrence. But if x is not present, it returns the insertion point.

**TF3:** The Find Peak Element problem has a unique solution.
**→ FALSE.** The problem asks for ANY peak. Multiple peaks may exist; the algorithm returns one of them.

**TF4:** In C++, `std::lower_bound` on a range of size N takes O(log N) comparisons.
**→ TRUE.** For random access iterators (like vector/array), it runs in O(log N) time.

**TF5:** First Bad Version binary search uses exactly log₂(n) API calls in every case.
**→ FALSE.** It uses AT MOST ⌈log₂(n)⌉ calls (worst case).
