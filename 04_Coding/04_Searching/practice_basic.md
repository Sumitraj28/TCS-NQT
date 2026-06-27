# Searching — Practice: Basic (15 Questions)

> Tags: Difficulty / Expected Time / TCS Frequency

---

### Q1 — Linear Search
**Difficulty:** Easy | **Time:** 20s | **TCS Frequency:** Medium
Find the index of 9 in `arr = [5, 3, 9, 1, 7]`.
**Answer:** Index 2. Linear scan: at index 2, arr[2]=9.

---

### Q2 — Binary Search Found
**Difficulty:** Easy | **Time:** 30s | **TCS Frequency:** High
Find 15 in sorted `arr = [2, 5, 10, 15, 20]`.
**Answer:** Index 3. lo=0,hi=4,mid=2(10)<15→lo=3; lo=3,hi=4,mid=3(15)==15→return 3.

---

### Q3 — Binary Search Not Found
**Difficulty:** Easy | **Time:** 30s | **TCS Frequency:** Medium
Find 8 in sorted `arr = [1, 3, 6, 10, 14]`.
**Answer:** -1 (not found). Trace: mid=2(6)<8→lo=3; mid=3(10)>8→hi=2; lo>hi → return -1.

---

### Q4 — Number of Iterations
**Difficulty:** Easy | **Time:** 20s | **TCS Frequency:** Medium
How many comparisons does binary search make in the worst case for n=16?
**Answer:** ⌈log₂(16)⌉ = 4 comparisons.

---

### Q5 — Sorted Array: Find Insert Position
**Difficulty:** Easy | **Time:** 45s | **TCS Frequency:** High
Where would you insert 6 in `arr = [1, 3, 5, 7, 9]` to maintain sorted order?
**Answer:** Index 3. Lower bound of 6: first i where arr[i] >= 6. arr[3]=7 >= 6 (and arr[2]=5 < 6). Insert at index 3.

---

### Q6 — Count Comparisons (Linear)
**Difficulty:** Easy | **Time:** 15s | **TCS Frequency:** Low
In linear search on `arr = [4, 8, 2, 9, 3]`, how many comparisons to find 9?
**Answer:** 4 comparisons (check 4, 8, 2, 9 → found at comparison 4).

---

### Q7 — Binary Search: n=1
**Difficulty:** Easy | **Time:** 15s | **TCS Frequency:** Low
Binary search on `arr = [7]`, target=7.
**Answer:** Found at index 0. lo=0, hi=0, mid=0, arr[0]==7.

---

### Q8 — Find Maximum in Sorted Array
**Difficulty:** Easy | **Time:** 15s | **TCS Frequency:** Low
In a sorted ascending array, where is the maximum?
**Answer:** At `arr[n-1]` — last index. No search needed, just access.

---

### Q9 — Find Smallest Element ≥ x
**Difficulty:** Easy | **Time:** 45s | **TCS Frequency:** High
In `arr = [1, 4, 6, 8, 10]`, find smallest element ≥ 5.
**Answer:** 6 (at index 2). Lower bound of 5 = index 2 (arr[2]=6 ≥ 5).

---

### Q10 — Check if Sorted
**Difficulty:** Easy | **Time:** 30s | **TCS Frequency:** Medium
Is `arr = [1, 2, 5, 4, 7]` sorted? (Linear scan check)
**Answer:** No. At index 2→3: arr[2]=5 > arr[3]=4 violates ascending order.

---

### Q11 — Binary Search Range
**Difficulty:** Easy | **Time:** 30s | **TCS Frequency:** Medium
For `arr = [2, 4, 6, 8, 10]`, target=3, what does binary search return?
**Answer:** -1 (not present). lo=0,hi=4,mid=2(6)>3→hi=1; mid=0(2)<3→lo=1; mid=1(4)>3→hi=0; lo>hi → -1.

---

### Q12 — Sentinel Linear Search
**Difficulty:** Easy | **Time:** 30s | **TCS Frequency:** Low
In sentinel linear search, a copy of the target is placed at the end. Why?
**Answer:** Eliminates the need for `i < n` boundary check in the loop — the sentinel guarantees the loop terminates. Reduces comparisons by ~half.

---

### Q13 — Lower Bound Result
**Difficulty:** Easy | **Time:** 45s | **TCS Frequency:** High
`arr = [1, 2, 4, 4, 6]`. Lower bound of 4?
**Answer:** 2. First index where arr[i] >= 4. arr[2]=4 ≥ 4 and arr[1]=2 < 4.

---

### Q14 — Upper Bound Result
**Difficulty:** Easy | **Time:** 45s | **TCS Frequency:** High
`arr = [1, 2, 4, 4, 6]`. Upper bound of 4?
**Answer:** 4. First index where arr[i] > 4. arr[4]=6 > 4.

---

### Q15 — Count Occurrences Using Bounds
**Difficulty:** Easy | **Time:** 60s | **TCS Frequency:** High
`arr = [1, 2, 4, 4, 4, 6]`. How many times does 4 appear?
**Answer:** 3. upper_bound(4)=5, lower_bound(4)=2. Count = 5-2 = 3.
