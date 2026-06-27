# Sorting — Quiz

## 10 Q&A Flashcard Pairs

**Q1:** What algorithm does C++ `std::sort` use?
**A1:** It uses IntroSort — a hybrid algorithm of QuickSort, HeapSort, and InsertionSort. It guarantees O(N log N) worst-case time complexity.

**Q2:** Why does a custom comparator using `<=` crash `std::sort`?
**A2:** It violates the strict weak ordering requirement. When elements are equal, both `a <= b` and `b <= a` return true, causing `std::sort` to loop infinitely or access out-of-bounds memory. Always use `<` or `>`.

**Q3:** What is the worst-case space complexity of Merge Sort?
**A3:** O(N) — because it requires an auxiliary array of size N to merge sorted subarrays.

**Q4:** In what scenario is Insertion Sort highly efficient?
**A4:** When the array is already sorted or nearly sorted. It runs in O(N) time under this condition.

**Q5:** What is the difference between stable and unstable sorting?
**A5:** Stable sorting preserves the relative order of equal elements. Unstable sorting may rearrange them.

**Q6:** How can we find the Kth largest element in O(N) average time without sorting?
**A6:** Use `std::nth_element` (QuickSelect) in C++.

**Q7:** What is the minimum number of swaps required to sort an array of N distinct elements in the worst case?
**A7:** It can be calculated using graph cycles. If cycle sizes are `c_1, c_2, ...`, the minimum swaps is `sum(c_i - 1)`.

**Q8:** When should you use `std::stable_sort` instead of `std::sort`?
**A8:** When you need to preserve the relative order of equal elements (e.g. sorting by last name, then sorting by department).

**Q9:** In the Dutch National Flag algorithm, why is `mid` NOT incremented when `nums[mid] == 2`?
**A9:** The element swapped from `high` to `mid` is unexamined. We must evaluate it in the next loop iteration.

**Q10:** What is the time complexity of Counting Sort?
**A10:** O(N + K) where N is the number of elements and K is the range of values.

---

## 5 True / False Statements

**TF1:** Quick Sort is a stable sorting algorithm.
**→ FALSE.** Quick Sort partitions elements around a pivot, which swaps elements over long distances and can change the relative order of equal values.

**TF2:** Selection Sort makes exactly N-1 swaps in all cases.
**→ TRUE.** In each of the N-1 passes, Selection Sort performs exactly one swap to place the minimum element in its correct position.

**TF3:** `std::nth_element` sorts the entire array.
**→ FALSE.** It only places the element at index `k` in its correct sorted position, guaranteeing that elements before `k` are ≤ `k` and elements after `k` are ≥ `k`. The rest of the array remains unsorted.

**TF4:** In C++, `std::stable_sort` has O(N log N) worst-case time complexity.
**→ TRUE.** It uses Merge Sort internally to guarantee O(N log N) time and stability.

**TF5:** Bubble Sort is an in-place sorting algorithm.
**→ TRUE.** It only requires O(1) auxiliary space for swapping elements.
