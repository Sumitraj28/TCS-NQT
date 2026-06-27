# HashMap — Quiz

## 10 Q&A Flashcard Pairs

**Q1:** What is the average and worst-case lookup complexity of `std::unordered_map`?
**A1:** Average: O(1). Worst-case: O(N) (happens when all elements collide into the same hash bucket).

**Q2:** Why does `std::unordered_map<std::pair<int, int>, int>` fail to compile?
**A2:** C++ standard library does not provide a default hash function for `std::pair`. Use `std::map` instead, which only requires the `<` operator.

**Q3:** What is the side effect of checking key presence using `if (map[key] == 0)`?
**A3:** It implicitly inserts `key` with a default value of 0 into the map if it was absent, consuming extra memory.

**Q4:** What does the `second` boolean value returned by `set.insert(x)` represent?
**A4:** It evaluates to `true` if `x` was successfully inserted (did not exist in the set), and `false` if `x` was already present.

**Q5:** Why do we seed the prefix sum map with `[0] = 1` before solving the Subarray Sum = K problem?
**A5:** To detect subarrays starting at index 0 whose sum is exactly equal to K (e.g. prefixSum − K = 0).

**Q6:** In the "longest subarray sum equals K" pattern, why do we only insert prefix sums if they are not already present in the map?
**A6:** To preserve the leftmost index of the prefix sum, which maximizes the calculated subarray length `i - leftmostIndex`.

**Q7:** What is the underlying data structure of C++ `std::map`?
**A7:** A self-balancing Binary Search Tree (specifically, a Red-Black Tree).

**Q8:** How do you sort a map by its values?
**A8:** Copy map elements into a `std::vector<std::pair<Key, Value>>` and sort the vector using a custom comparator.

**Q9:** What is the worst-case space complexity of a Hash Map containing N elements?
**A9:** O(N) — since it stores N key-value pairs.

**Q10:** How do you find the first non-repeating element in an array in O(N) time?
**A10:** Build a frequency map of elements, then traverse the array from left to right, returning the first element whose frequency in the map is 1.

---

## 5 True / False Statements

**TF1:** `std::unordered_map` maintains elements sorted by key.
**→ FALSE.** Elements in `std::unordered_map` are stored in arbitrary bucket order. `std::map` is the one that keeps elements sorted by key.

**TF2:** Inserting an element into `std::map` takes O(log N) time.
**→ TRUE.** Since it is based on a balanced binary search tree, all operations take O(log N) time.

**TF3:** `std::unordered_set` can store duplicate values.
**→ FALSE.** Sets only store unique values. Duplicate insertions are ignored.

**TF4:** In C++, `map.count(key)` returns the frequency value associated with the key.
**→ FALSE.** It returns `1` if the key exists, and `0` if not. To get the value, use `map[key]` or `find()->second`.

**TF5:** Clearing a map (`map.clear()`) releases all allocated memory and sets size to 0.
**→ TRUE.** All elements are deleted and `size()` becomes 0.
