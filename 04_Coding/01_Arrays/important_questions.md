# Arrays — Top 20 Important TCS NQT-Style Questions

> These are the most-repeated patterns from TCS NQT coding rounds based on community reports.
> No duplicates with practice_basic / medium / advanced files.
> Tags: Difficulty / Time / TCS Frequency

---

### IQ1 — Sum of Digits of Array Elements
**Difficulty:** Easy | **Time:** 45s | **TCS Frequency:** Medium

Given `arr = [12, 34, 56]`, find the sum of digits of all array elements combined.

**Answer:** Digits of 12=1+2=3; 34=3+4=7; 56=5+6=11. Total=21.
**Approach:** Convert each number to string or extract digits using `% 10` and `/ 10` loops.

---

### IQ2 — Element Appearing Odd Number of Times (XOR)
**Difficulty:** Easy | **Time:** 45s | **TCS Frequency:** High

`arr = [4, 3, 4, 4, 4, 3, 2]`. Find the element appearing an odd number of times.

**Answer:** 2
**Approach:** XOR all elements. XOR of any number with itself = 0. Only the element appearing odd times survives. `4^3^4^4^4^3^2 = 2`.

---

### IQ3 — Find the Pivot Index (Equilibrium Index)
**Difficulty:** Medium | **Time:** 90s | **TCS Frequency:** High

`arr = [1, 7, 3, 6, 5, 6]`. Find index where sum of left elements = sum of right elements.

**Answer:** 3 (left sum = 1+7+3=11; right sum = 5+6=11)
**Approach:** Total sum = 28. Scan left to right with leftSum. At index i: rightSum = totalSum − leftSum − arr[i]. Check leftSum == rightSum.

---

### IQ4 — Rearrange Array Alternating Positive and Negative
**Difficulty:** Medium | **Time:** 120s | **TCS Frequency:** High

`arr = [1, 2, -3, -4, 5, -6]`. Rearrange to alternate positive and negative (extra space allowed).

**Answer:** e.g., `[1, -3, 2, -4, 5, -6]`
**Approach:** Separate positives and negatives, then interleave.

---

### IQ5 — Count Inversions in Array
**Difficulty:** Hard | **Time:** 240s | **TCS Frequency:** Medium

`arr = [2, 4, 1, 3, 5]`. Count pairs (i,j) where i < j but arr[i] > arr[j].

**Answer:** 3 (pairs: (2,1), (4,1), (4,3))
**Approach:** Modified merge sort — count while merging. O(n log n).

---

### IQ6 — Leaders in an Array
**Difficulty:** Easy | **Time:** 60s | **TCS Frequency:** High

`arr = [16, 17, 4, 3, 5, 2]`. Find all leaders (elements greater than all elements to their right).

**Answer:** [17, 5, 2]
**Approach:** Scan from right to left, tracking rightMax. If arr[i] > rightMax, it's a leader. Update rightMax.

---

### IQ7 — Wave Array
**Difficulty:** Medium | **Time:** 90s | **TCS Frequency:** Medium

`arr = [3, 6, 5, 10, 7, 20]`. Arrange in wave form: arr[0] ≥ arr[1] ≤ arr[2] ≥ arr[3]...

**Answer:** `[6, 3, 10, 5, 20, 7]`
**Approach:** Sort the array. Swap every adjacent pair.

---

### IQ8 — Maximum Sum of Non-Adjacent Elements
**Difficulty:** Medium | **Time:** 120s | **TCS Frequency:** High

`arr = [3, 2, 7, 10]`. Maximum sum without picking adjacent elements.

**Answer:** 13 (3+10)
**Approach:** DP: `dp[i] = max(dp[i-1], dp[i-2] + arr[i])`.

---

### IQ9 — Chocolate Distribution Problem
**Difficulty:** Medium | **Time:** 120s | **TCS Frequency:** High

`arr = [7, 3, 12, 4, 9, 8, 11]`, m=3 (students). Distribute m packets minimizing max−min.

**Answer:** Sort → [3,4,7,8,9,11,12]. Window of size 3: min diff = 2 (for [7,8,9]).
**Approach:** Sort + sliding window of size m.

---

### IQ10 — Stock Span Problem
**Difficulty:** Medium | **Time:** 150s | **TCS Frequency:** Medium

`prices = [100, 80, 60, 70, 60, 75, 85]`. Find span of each day (days consecutively ≤ today).

**Answer:** `[1, 1, 1, 2, 1, 4, 6]`
**Approach:** Monotonic stack. Push indices. For each price, pop while prices[stack.top] ≤ current price. Span = i − stack.top (or i+1 if stack empty).

---

### IQ11 — Maximum Difference (arr[j] − arr[i], j > i)
**Difficulty:** Easy | **Time:** 60s | **TCS Frequency:** High

`arr = [2, 3, 10, 6, 4, 8, 1]`. Find maximum arr[j]−arr[i] where j > i.

**Answer:** 8 (arr[0]=2, arr[2]=10)
**Approach:** Track minSoFar. At each j: diff = arr[j]−minSoFar; update max diff; update minSoFar.

---

### IQ12 — Merge Overlapping Intervals
**Difficulty:** Medium | **Time:** 150s | **TCS Frequency:** High

`intervals = [[1,3],[2,6],[8,10],[15,18]]`. Merge overlapping intervals.

**Answer:** `[[1,6],[8,10],[15,18]]`
**Approach:** Sort by start. Merge when next start ≤ current end. Update end = max(currentEnd, nextEnd).

---

### IQ13 — Find Duplicate Number (Only One, Without Extra Space)
**Difficulty:** Medium | **Time:** 120s | **TCS Frequency:** High

`nums = [1,3,4,2,2]`. Find the duplicate (only one duplicate, values in [1,n]).

**Answer:** 2
**Approach (Floyd's Cycle Detection):** Treat as linked list — index → value as next node. Find cycle, find entry point of cycle. Entry = duplicate.

---

### IQ14 — Minimum Platforms Required (Train Schedule)
**Difficulty:** Hard | **Time:** 200s | **TCS Frequency:** Medium

`arrival = [900,940,950,1100,1500,1800]`, `departure = [910,1200,1120,1130,1900,2000]`. Min platforms?

**Answer:** 3
**Approach:** Sort both. Two pointer: count active trains at any moment. At arrival event: platforms++, update max. At departure: platforms--.

---

### IQ15 — K-th Largest Element
**Difficulty:** Medium | **Time:** 120s | **TCS Frequency:** High

`arr = [3,2,1,5,6,4]`, k=2. Find the 2nd largest element.

**Answer:** 5
**Approach:** Min-heap (`std::priority_queue`) of size k: maintain heap. Or use QuickSelect O(n) average.

---

### IQ16 — Count Subarrays with Product Less Than k
**Difficulty:** Medium | **Time:** 150s | **TCS Frequency:** Low

`nums = [10,5,2,6]`, k=100. Count subarrays where product < 100.

**Answer:** 8
**Approach:** Sliding window: right expands, left shrinks when product ≥ k. Each valid right position adds (right − left + 1) subarrays.

---

### IQ17 — Smallest Subarray with All Distinct Elements
**Difficulty:** Hard | **Time:** 200s | **TCS Frequency:** Low

`arr = [7,3,7,3,1,3,4,1]`. Find length of smallest subarray containing all distinct elements.

**Distinct elements:** {7,3,1,4} = 4 distinct. Find minimum window containing all 4.
**Answer:** 5 (subarray [3,1,3,4,1])
**Approach:** Sliding window with `std::unordered_map` tracking current frequency. Shrink left when all distinct are covered.

---

### IQ18 — Find the Repeating and Missing Number
**Difficulty:** Hard | **Time:** 240s | **TCS Frequency:** Medium

`arr = [4,3,6,2,1,1]`, n=6. Find the repeating (1) and missing (5) numbers.

**Answer:** Repeating=1, Missing=5
**Approach:** Let repeating=a, missing=b. Sum equation: actual_sum − expected_sum = a−b. SumOfSquares equation: gives a+b. Solve the system.

---

### IQ19 — Longest Consecutive Sequence
**Difficulty:** Medium | **Time:** 150s | **TCS Frequency:** High

`arr = [100,4,200,1,3,2]`. Find length of the longest consecutive elements sequence.

**Answer:** 4 (sequence 1,2,3,4)
**Approach:** `std::unordered_set`. For each number, if num−1 is NOT in set (it's a sequence start), count consecutive numbers forward. O(n).

---

### IQ20 — Number of Subarrays with Zero Sum
**Difficulty:** Medium | **Time:** 120s | **TCS Frequency:** High

`arr = [4, 2, -3, 1, 6]`. Count subarrays with sum = 0.

**Answer:** 1 (subarray [2, -3, 1])
**Approach:** Prefix sum + `std::unordered_map`. Count += freq[prefixSum] for each step. freq = {0:1} initially.
