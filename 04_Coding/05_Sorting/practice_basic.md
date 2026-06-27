# Sorting — Practice: Basic (15 Questions)

> Tags: Difficulty / Expected Time / TCS Frequency

---

### Q1 — Find Min/Max Element
**Difficulty:** Easy | **Time:** 15s | **TCS Frequency:** High
Find the minimum element in `arr = [5, 2, 8, 1, 9]`.
**Answer:** 1. Scan once or sort and access `arr[0]`.

---

### Q2 — Bubble Sort Swap Count
**Difficulty:** Easy | **Time:** 30s | **TCS Frequency:** Medium
How many swaps in Pass 1 of Bubble Sort for `arr = [4, 3, 2, 1]`?
**Answer:** 3 swaps. (4,3)→(4,2)→(4,1) resulting in `[3, 2, 1, 4]`.

---

### Q3 — Selection Sort Swap Count
**Difficulty:** Easy | **Time:** 30s | **TCS Frequency:** Medium
How many swaps are performed in total by Selection Sort on `arr = [4, 3, 2, 1]`?
**Answer:** Exactly 3 swaps (for n=4, it does n-1 swaps).
1. Swap 4 and 1 → `[1, 3, 2, 4]`
2. Swap 3 and 2 → `[1, 2, 3, 4]`
3. Swap 3 and 3 (no-op or self-swap) → 3 swaps.

---

### Q4 — Insertion Sort Shift Count
**Difficulty:** Easy | **Time:** 45s | **TCS Frequency:** Medium
For `arr = [1, 3, 2, 4]`, how many shifts are made during Insertion Sort?
**Answer:** 1 shift (value 3 is shifted right to insert 2).

---

### Q5 — Stable Sorting Check
**Difficulty:** Easy | **Time:** 20s | **TCS Frequency:** Low
Which of these is a stable sorting algorithm: Selection Sort, Quick Sort, Merge Sort?
**Answer:** Merge Sort.

---

### Q6 — In-Place Sort Definition
**Difficulty:** Easy | **Time:** 15s | **TCS Frequency:** Low
Does Merge Sort sort in-place?
**Answer:** No, it requires O(n) auxiliary space to merge subarrays.

---

### Q7 — Sort Vector Ascending
**Difficulty:** Easy | **Time:** 20s | **TCS Frequency:** High
What is the C++ STL one-liner to sort vector `v` ascending?
**Answer:** `std::sort(v.begin(), v.end());`

---

### Q8 — Sort Vector Descending
**Difficulty:** Easy | **Time:** 20s | **TCS Frequency:** High
What is the C++ STL one-liner to sort vector `v` descending?
**Answer:** `std::sort(v.rbegin(), v.rend());`

---

### Q9 — Number of Comparisons in Merge Sort
**Difficulty:** Easy | **Time:** 20s | **TCS Frequency:** Low
What is the worst-case time complexity of Merge Sort?
**Answer:** O(n log n) always.

---

### Q10 — Quick Sort Worst-Case Input
**Difficulty:** Easy | **Time:** 30s | **TCS Frequency:** Medium
When does Quick Sort exhibit O(n²) time complexity?
**Answer:** When the pivot choice is poor (e.g. choosing the last element as pivot on a sorted or reverse-sorted array).

---

### Q11 — Find if Array Is Sorted
**Difficulty:** Easy | **Time:** 20s | **TCS Frequency:** High
How to verify if a vector is sorted in C++?
**Answer:** `std::is_sorted(v.begin(), v.end());`

---

### Q12 — Counting Sort Range
**Difficulty:** Easy | **Time:** 30s | **TCS Frequency:** High
When is Counting Sort preferred over Comparison-based Sort?
**Answer:** When elements are integers bounded in a small range [0, k] where k = O(n).

---

### Q13 — Sort Strings by Length
**Difficulty:** Easy | **Time:** 45s | **TCS Frequency:** Medium
How to sort a vector of strings by length in C++?
**Answer:**
```cpp
std::sort(v.begin(), v.end(), [](const std::string& a, const std::string& b) {
    return a.length() < b.length();
});
```

---

### Q14 — Binary Search Pre-requisite
**Difficulty:** Easy | **Time:** 15s | **TCS Frequency:** High
What must be done to an array before performing binary search?
**Answer:** The array must be sorted.

---

### Q15 — Sort Check After Partition
**Difficulty:** Easy | **Time:** 30s | **TCS Frequency:** Low
In Quick Sort, after the first partition, is the pivot element in its final sorted position?
**Answer:** Yes, the partition guarantees the pivot is placed exactly where it belongs in the final sorted array.
