# Searching — Previous Year Style Questions

---

### PYQ1 — Binary Search Return Value
**Difficulty:** Easy | **Time:** 30s | **Frequency:** High

What does Java's `Arrays.binarySearch(arr, x)` return if x is not found in the sorted array `arr = [1,3,5,7]` and x=4?

**Answer:** `-(insertionPoint) - 1`. InsertionPoint for 4 = 2 (between 3 and 5). Return = -(2)-1 = **-3**.
**Faster method:** Directly apply the formula: `-(lb) - 1` where lb = lowerBound(arr, x).

---

### PYQ2 — Count Elements in Range
**Difficulty:** Medium | **Time:** 90s | **Frequency:** High

`arr = [2,3,3,5,7,7,7,8,9]`. How many elements are in range [3, 7] (inclusive)?

**Answer:** 6 (elements: 3,3,5,7,7,7). upper_bound(7) - lower_bound(3) = 7 - 1 = 6.
**Faster method:** One linear scan O(n) or two binary searches O(log n). Use binary search.

---

### PYQ3 — First and Last Occurrence
**Difficulty:** Medium | **Time:** 120s | **Frequency:** High

`arr = [5,7,7,8,8,10]`, target=8. Find first and last occurrence.

**Answer:** First=3, Last=4.
- First: lo=0,hi=5,mid=2(7)<8→lo=3; mid=4(8)==8, result=4,hi=3; mid=3(8)==8, result=3,hi=2; lo>hi→first=3.
- Last: similar but move lo=mid+1 on match. Result=4.

---

### PYQ4 — Search in Rotated Array
**Difficulty:** Medium | **Time:** 120s | **Frequency:** High

`arr = [6,7,8,1,2,3,4,5]`, target=3. Which index?

**Answer:** Index 5.
Trace: lo=0,hi=7,mid=3(1). Right half [1..5] sorted. target=3 in [1,5]→lo=4. lo=4,hi=7,mid=5(3)==3. **return 5**.

---

### PYQ5 — Binary Search Complexity
**Difficulty:** Easy | **Time:** 15s | **Frequency:** Medium

For binary search on 1000 elements, worst case comparisons?

**Answer:** ⌈log₂(1000)⌉ = 10 comparisons (since 2¹⁰=1024 > 1000).

---

### PYQ6 — Lower Bound Application
**Difficulty:** Medium | **Time:** 90s | **Frequency:** High

`arr = [1,2,4,4,4,7,8]`. How many elements are strictly less than 4?

**Answer:** 2 (elements 1, 2). This equals `lowerBound(arr, 4) = 2`.

---

### PYQ7 — Find Peak in Bitonic Array
**Difficulty:** Medium | **Time:** 120s | **Frequency:** Medium

`arr = [1,4,8,5,3]`. Find the peak element.

**Answer:** Index 2 (value 8). Binary search: mid=2(8). nums[2]=8 > nums[3]=5 → hi=2. lo=2==hi=2 → return 2.

---

### PYQ8 — When Does Binary Search Fail?
**Difficulty:** Easy | **Time:** 20s | **Frequency:** Medium

Give two conditions under which binary search gives wrong results.

**Answer:**
1. Array is NOT sorted — binary search assumes sorted order.
2. Integer overflow: `(lo + hi) / 2` overflows when both are near MAX_VALUE. Fix: `lo + (hi-lo)/2`.

---

### PYQ9 — Minimum in Rotated Sorted Array With Duplicates
**Difficulty:** Hard | **Time:** 180s | **Frequency:** Medium

`arr = [3,3,1,3]`. Find minimum.

**Answer:** 1.
Modified binary search: if nums[mid] == nums[hi], hi-- (can't determine which side). If nums[mid] > nums[hi]: lo=mid+1. Else hi=mid.
lo=0,hi=3,mid=1(3)==nums[3](3)→hi=2. lo=0,hi=2,mid=1(3)>nums[2](1)→lo=2. lo==hi=2, nums[2]=1.

---

### PYQ10 — Count 1s in Binary Sorted Array
**Difficulty:** Easy | **Time:** 45s | **Frequency:** High

`arr = [0,0,0,0,1,1,1]`. Count 1s using binary search.

**Answer:** 3. Lower bound of 1 = 4. Count = 7 - 4 = 3.
**Python:** `n - bisect.bisect_left(arr, 1)`

