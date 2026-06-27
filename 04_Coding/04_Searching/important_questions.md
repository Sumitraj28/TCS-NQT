# Searching — Top 20 Important TCS NQT-Style Questions

> No duplicates with practice files. TCS-exam phrasing.

---

### IQ1 — Find the position of an element in an array of n elements.
**Difficulty:** Easy | **Time:** 30s | **TCS Frequency:** High
`arr = [10, 20, 30, 40, 50]`, find 30.
**Answer:** Index 2. Linear scan; or if sorted, binary search returns mid=2.

### IQ2 — Given sorted arr, check if target exists.
**Difficulty:** Easy | **Time:** 30s | **TCS Frequency:** High
`arr = [1,4,7,10,13]`, target=10.
**Answer:** Yes, index 3. Binary search: mid=2(7)<10→lo=3; mid=3(10)==10 ✓.

### IQ3 — Find the floor value of x in sorted array.
**Difficulty:** Medium | **Time:** 75s | **TCS Frequency:** High
`arr = [1,3,6,9,12]`, x=8. Largest element ≤ 8.
**Answer:** 6. Lower bound of 8 = index 2 (arr[2]=6... wait: lb of 8 = first i where arr[i]≥8 = 3 (arr[3]=9). Floor = arr[lb-1]=arr[2]=6.

### IQ4 — Find the ceiling value of x in sorted array.
**Difficulty:** Medium | **Time:** 75s | **TCS Frequency:** High
`arr = [1,3,6,9,12]`, x=8. Smallest element ≥ 8.
**Answer:** 9. Lower bound of 8 = index 3 (arr[3]=9). Ceiling = arr[3]=9.

### IQ5 — Count elements in range [lo, hi] in sorted array.
**Difficulty:** Medium | **Time:** 90s | **TCS Frequency:** High
`arr = [1,2,3,4,5,6,7]`, range=[3,5].
**Answer:** 3 (elements 3,4,5). upper_bound(5) - lower_bound(3) = 5 - 2 = 3.

### IQ6 — Search in a bitonic array (first increase then decrease).
**Difficulty:** Medium | **Time:** 150s | **TCS Frequency:** Medium
`arr = [1,3,8,12,4,2]`, target=12.
**Answer:** Index 3. Find peak (index 3, value 12). If target=peak, found. Else binary search left ascending half, then right descending half.

### IQ7 — Find number of occurrences of an element in a sorted array.
**Difficulty:** Easy | **Time:** 60s | **TCS Frequency:** High
`arr = [1,2,2,2,3,4]`, target=2.
**Answer:** 3. upper_bound(2)-lower_bound(2) = 4-1 = 3.

### IQ8 — Find the minimum element in a rotated sorted array.
**Difficulty:** Medium | **Time:** 90s | **TCS Frequency:** High
`arr = [6,7,1,2,3,4,5]`.
**Answer:** 1. Binary search: mid=3(2). nums[mid]<nums[hi]→hi=3. mid=1(7). 7>5→lo=2. mid=2(1). 1<5→hi=2. lo==hi=2, return 1.

### IQ9 — Find the maximum in rotated sorted array.
**Difficulty:** Medium | **Time:** 90s | **TCS Frequency:** Medium
`arr = [4,5,6,1,2,3]`.
**Answer:** 6. The maximum is at index `(minIdx - 1 + n) % n`. Min is at index 3 (value 1). Max = arr[(3-1+6)%6] = arr[2] = 6.

### IQ10 — Given n=100, what is the worst case number of comparisons in binary search?
**Difficulty:** Easy | **Time:** 15s | **TCS Frequency:** Medium
**Answer:** ⌈log₂(100)⌉ = 7 comparisons.

### IQ11 — Element appearing exactly once in sorted array where all others appear twice.
**Difficulty:** Medium | **Time:** 120s | **TCS Frequency:** High
`arr = [1,1,2,2,3,4,4,5,5]`. Find the single element.
**Answer:** 3. Binary search: at even index, if arr[i]==arr[i+1], single is in right half; else left half.

### IQ12 — Find pivot in rotated sorted array.
**Difficulty:** Medium | **Time:** 90s | **TCS Frequency:** High
`arr = [5,6,7,8,1,2,3]`. Find pivot (index where rotation happened, i.e., minimum element's index).
**Answer:** 4. Binary search for minimum: returns index 4 (value 1).

### IQ13 — Ternary search: find the maximum of a unimodal function.
**Difficulty:** Hard | **Time:** 150s | **TCS Frequency:** Low
Describe ternary search on `f(x) = -(x-5)²+25`. Max at x=5.
**Answer:** Divide [lo,hi] into thirds. Compare f(m1) and f(m2). If f(m1)<f(m2)→lo=m1 else hi=m2. Converges to x=5.

### IQ14 — Exponential search for 55 in an "infinite" sorted array.
**Difficulty:** Medium | **Time:** 120s | **TCS Frequency:** Low
Describe the exponential search process.
**Answer:** Check arr[1], arr[2], arr[4], arr[8], ... until arr[2^k] ≥ 55. Then binary search in [2^(k-1), 2^k]. Time O(log n).

### IQ15 — Total number of 1s in a binary matrix where each row is sorted.
**Difficulty:** Medium | **Time:** 120s | **TCS Frequency:** Medium
`matrix = [[0,0,1],[0,1,1],[1,1,1]]`. Count total 1s.
**Answer:** 1+2+3=6. For each row, use binary search to find first 1. Count = n - firstOneIndex.

### IQ16 — Find target in row-wise and column-wise sorted matrix.
**Difficulty:** Medium | **Time:** 120s | **TCS Frequency:** High
`matrix = [[1,4,7],[2,5,8],[3,6,9]]`, target=5.
**Answer:** Found at (1,1). Start top-right: (0,2)=7>5→col--; (0,1)=4<5→row++; (1,1)=5==5 ✓.

### IQ17 — Find missing number in sorted array 1..n with one missing.
**Difficulty:** Easy | **Time:** 60s | **TCS Frequency:** High
`arr = [1,2,3,5,6]`.
**Answer:** 4. Binary search: if arr[mid]==mid+1 → missing is in right half; else left. Or: n(n+1)/2 - sum(arr) = 21-17=4.

### IQ18 — Given sorted array of negatives and positives, find first positive.
**Difficulty:** Easy | **Time:** 45s | **TCS Frequency:** Medium
`arr = [-5,-3,-1,2,4,7]`.
**Answer:** 2, at index 3. Lower bound of 1 (first i where arr[i]≥1) = index 3.

### IQ19 — Ship packages in D days (minimum capacity).
**Difficulty:** Hard | **Time:** 240s | **TCS Frequency:** Medium
`weights=[1,2,3,4,5,6,7,8,9,10]`, D=5.
**Answer:** Binary search: lo=10(max), hi=55(sum). Simulate feasibility. Answer = 15.

### IQ20 — Find three numbers that sum to zero (not searching but uses binary search within two-pointer).
**Difficulty:** Medium | **Time:** 180s | **TCS Frequency:** High
`arr = [-4,-1,-1,0,1,2]`. Find all unique triplets summing to 0.
**Answer:** [[-4,2... wait: -4+1+... Try [-1,-1,2],[-4,1,3→no]. Correct: sort→[-4,-1,-1,0,1,2]. Fix first=-4: need pair summing to 4: (2+2=no, 1+... no). Fix first=-1(i=1): need pair=-1+1=0? [−1,0,1] ✓. Fix first=-1(i=2): same → skip dup. Fix first=0: need [1,-1]=[0,-1,1] dup.
**Answer:** [[-1,-1,2],[-1,0,1]]
