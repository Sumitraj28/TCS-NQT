# Sorting — Top 20 Important TCS NQT-Style Questions

---

### IQ1 — Sort an array of size n containing only 0, 1, and 2.
**Difficulty:** Easy | **Time:** 60s | **TCS Frequency:** High
**Answer:** Use Dutch National Flag (3-way partition). Pointers: low, mid, high.

---

### IQ2 — Find the minimum swaps required to sort an array.
**Difficulty:** Medium | **Time:** 120s | **TCS Frequency:** High
**Answer:** Graph cycle decomposition: `sum(cycle_size - 1)`.

---

### IQ3 — Merge two sorted arrays without extra space.
**Difficulty:** Hard | **Time:** 180s | **TCS Frequency:** High
**Answer:** Gap Method (Shell Sort variant) or compare from right of A and left of B and sort.

---

### IQ4 — Find the Kth largest element in an unsorted array.
**Difficulty:** Medium | **Time:** 90s | **TCS Frequency:** High
**Answer:** Use `std::nth_element` or Min-Heap of size k.

---

### IQ5 — Sort an array according to the order defined by another array.
**Difficulty:** Medium | **Time:** 120s | **TCS Frequency:** High
**Answer:** Relative Sort using custom comparator with rank map.

---

### IQ6 — Group Anagrams.
**Difficulty:** Medium | **Time:** 120s | **TCS Frequency:** High
**Answer:** For each string, sort chars to create key, group in hash map.

---

### IQ7 — Count inversions in an array.
**Difficulty:** Hard | **Time:** 240s | **TCS Frequency:** High
**Answer:** Modified Merge Sort: count split inversions during merge.

---

### IQ8 — Find if two arrays are anagrams of each other.
**Difficulty:** Easy | **Time:** 30s | **TCS Frequency:** High
**Answer:** Sort both and check equality; or frequency hash map.

---

### IQ9 — Check if an array can be sorted with one swap.
**Difficulty:** Medium | **Time:** 75s | **TCS Frequency:** Medium
**Answer:** Find misplaced elements. Count indices i where `arr[i] > arr[i+1]`. If > 2 indices, impossible.

---

### IQ10 — Sort array by parity (even first, then odd).
**Difficulty:** Easy | **Time:** 45s | **TCS Frequency:** High
**Answer:** Two pointer swap.

---

### IQ11 — Find the maximum product of three numbers in an array.
**Difficulty:** Medium | **Time:** 90s | **TCS Frequency:** High
**Answer:** Sort. Max product = max(arr[n-1]*arr[n-2]*arr[n-3], arr[0]*arr[1]*arr[n-1]).

---

### IQ12 — Merge overlapping intervals.
**Difficulty:** Medium | **Time:** 120s | **TCS Frequency:** High
**Answer:** Sort intervals by start time and merge.

---

### IQ13 — Sort string characters.
**Difficulty:** Easy | **Time:** 30s | **TCS Frequency:** High
**Answer:** `std::sort(s.begin(), s.end());`

---

### IQ14 — Activity Selection Problem (Greedy).
**Difficulty:** Medium | **Time:** 120s | **TCS Frequency:** High
**Answer:** Sort activities by end time. Select greedily.

---

### IQ15 — Find pairs in array with sum closest to zero.
**Difficulty:** Medium | **Time:** 120s | **TCS Frequency:** Medium
**Answer:** Sort + Two Pointer (move left or right based on sum sign).

---

### IQ16 — Find triplet with given sum.
**Difficulty:** Medium | **Time:** 120s | **TCS Frequency:** High
**Answer:** Sort + fix one element + Two Pointer for remaining.

---

### IQ17 — Minimum platforms required for trains.
**Difficulty:** Hard | **Time:** 180s | **TCS Frequency:** High
**Answer:** Sort arrivals and departures separately. Traverse with two pointers.

---

### IQ18 — Maximum length chain of pairs.
**Difficulty:** Medium | **Time:** 120s | **TCS Frequency:** Medium
**Answer:** Sort pairs by second element ascending. Greedy selection.

---

### IQ19 — Sort array elements by absolute difference with key x.
**Difficulty:** Medium | **Time:** 90s | **TCS Frequency:** Medium
**Answer:** Custom comparator: `std::sort(v.begin(), v.end(), [x](int a, int b) { return std::abs(a-x) < std::abs(b-x); });`

---

### IQ20 — Frequency Sort (sort descending by count).
**Difficulty:** Medium | **Time:** 120s | **TCS Frequency:** High
**Answer:** Custom comparator using hash map.
```
