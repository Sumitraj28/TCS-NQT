# Arrays — Practice: Basic (15 Questions)

> **Tags:** Each question has Difficulty / Expected Time / TCS Frequency

---

### Q1 — Find the Maximum Element
**Difficulty:** Easy | **Time:** 30s | **TCS Frequency:** High

Find the largest element in `arr = [3, 7, 1, 9, 4]`.

**Answer:** 9
**Explanation:** Iterate through array tracking `max = arr[0]`. At each element, update if `arr[i] > max`. Final max = 9.

---

### Q2 — Find the Second Largest Element
**Difficulty:** Easy | **Time:** 45s | **TCS Frequency:** High

Find the second largest in `arr = [12, 35, 1, 10, 34, 1]`.

**Answer:** 34
**Explanation:** Maintain `first = -INF, second = -INF`. For each element: if greater than first → shift first to second, update first. Else if greater than second and not equal to first → update second. Answer: 34.

---

### Q3 — Count Occurrences
**Difficulty:** Easy | **Time:** 20s | **TCS Frequency:** Medium

Count how many times 3 appears in `arr = [1, 3, 3, 2, 3, 4, 3]`.

**Answer:** 4
**Explanation:** Linear scan with a counter. Increment counter each time `arr[i] == 3`. Final count = 4.

---

### Q4 — Check If Array Is Sorted (Ascending)
**Difficulty:** Easy | **Time:** 30s | **TCS Frequency:** Medium

Is `arr = [1, 2, 4, 7, 9]` sorted in ascending order?

**Answer:** Yes
**Explanation:** Check every adjacent pair: `arr[i] <= arr[i+1]` for all i. If any pair violates, return false. Here all pairs satisfy: 1<2, 2<4, 4<7, 7<9 → sorted.

---

### Q5 — Reverse an Array
**Difficulty:** Easy | **Time:** 30s | **TCS Frequency:** Medium

Reverse `arr = [5, 3, 8, 1, 2]`.

**Answer:** `[2, 1, 8, 3, 5]`
**Explanation:** Two pointers at start (l=0) and end (r=4). Swap arr[l] and arr[r], then l++, r--. Repeat while l < r. Swaps: (5,2)→(3,1)→(8 stays middle).

---

### Q6 — Sum of All Elements
**Difficulty:** Easy | **Time:** 20s | **TCS Frequency:** Low

Find the sum of `arr = [2, 5, 1, 8, 3]`.

**Answer:** 19
**Explanation:** Accumulate: 0+2=2, +5=7, +1=8, +8=16, +3=19.

---

### Q7 — Find Missing Number in 1 to N
**Difficulty:** Easy | **Time:** 45s | **TCS Frequency:** High

`arr = [1, 2, 4, 5, 6]`, n=6. Find the missing number.

**Answer:** 3
**Explanation:** Expected sum = n(n+1)/2 = 6×7/2 = 21. Actual sum = 1+2+4+5+6 = 18. Missing = 21 − 18 = 3.

---

### Q8 — Count Even and Odd Numbers
**Difficulty:** Easy | **Time:** 25s | **TCS Frequency:** Low

In `arr = [4, 7, 2, 9, 6, 3]`, how many are even and how many odd?

**Answer:** Even: 3 (4, 2, 6), Odd: 3 (7, 9, 3)
**Explanation:** Check `arr[i] % 2 == 0` for even. Count both separately in one pass.

---

### Q9 — Left Rotate Array by 1
**Difficulty:** Easy | **Time:** 35s | **TCS Frequency:** Medium

Left rotate `arr = [1, 2, 3, 4, 5]` by 1 position.

**Answer:** `[2, 3, 4, 5, 1]`
**Explanation:** Store arr[0] = temp = 1. Shift all elements left: arr[i] = arr[i+1] for i from 0 to n-2. Place temp at arr[n-1] = 1.

---

### Q10 — Check if Target Exists (Linear Search)
**Difficulty:** Easy | **Time:** 20s | **TCS Frequency:** Low

Does 7 exist in `arr = [3, 5, 9, 7, 1]`?

**Answer:** Yes, at index 3
**Explanation:** Scan from left. At index 3, arr[3] = 7 = target. Return true.

---

### Q11 — Remove Duplicates from Sorted Array (Count Unique)
**Difficulty:** Easy | **Time:** 45s | **TCS Frequency:** High

`arr = [1, 1, 2, 3, 3, 4]`. How many unique elements are there?

**Answer:** 4 unique elements
**Explanation:** Use a write pointer `j=0`. For each i from 1 to n-1: if arr[i] != arr[j], write arr[i] at arr[++j]. Final unique count = j + 1 = 4.

---

### Q12 — Find the Minimum Element
**Difficulty:** Easy | **Time:** 25s | **TCS Frequency:** Low

Find the minimum in `arr = [8, 3, 11, 1, 7]`.

**Answer:** 1
**Explanation:** Initialize min = arr[0] = 8. Compare with each element: 3<8→min=3; 11>3; 1<3→min=1; 7>1. Final min = 1.

---

### Q13 — Check if Two Arrays Are Equal
**Difficulty:** Easy | **Time:** 35s | **TCS Frequency:** Medium

Are `a = [1, 2, 3]` and `b = [1, 2, 3]` equal?

**Answer:** Yes
**Explanation:** Check lengths first (both 3). Then compare element-wise: a[0]==b[0], a[1]==b[1], a[2]==b[2]. All match → equal.

---

### Q14 — First Index of a Target
**Difficulty:** Easy | **Time:** 25s | **TCS Frequency:** Medium

Find the first index of 5 in `arr = [2, 5, 3, 5, 8]`.

**Answer:** 1
**Explanation:** Linear scan: at index 1, arr[1] = 5. Return 1 immediately.

---

### Q15 — Sum of Even-Indexed Elements
**Difficulty:** Easy | **Time:** 30s | **TCS Frequency:** Low

Find sum of elements at even indices (0, 2, 4) in `arr = [3, 1, 4, 1, 5]`.

**Answer:** 12
**Explanation:** arr[0]=3, arr[2]=4, arr[4]=5. Sum = 3+4+5 = 12.
