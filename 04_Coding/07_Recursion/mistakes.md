# Recursion — Common Mistakes

## 1. Stack Overflow
**Mistake:** Forgetting the base case, or writing a base case that is never met (e.g. subtracting from `n` when it is already negative, but base case checks `n == 0`).
**Fix:** Always ensure that arguments converge toward the base case with each recursive call.

---

## 2. Exponential Space Overhead
**Mistake:** Assuming recursive space complexity is $O(1)$. Every recursive call adds a stack frame. If recursion depth is $N$, space complexity is $O(N)$.
**Fix:** Use iteration or tail recursion if memory limits are strict.

---

## 3. Modifying References Inside DFS Loops
**Mistake:** Forgetting to backtrack (undo) changes made to array/vector parameters during recursive search.
**Fix:** Pop elements back after returning from the recursive call.
```cpp
temp.push_back(nums[i]);
backtrack(res, temp, nums, i + 1);
temp.pop_back(); // crucial undo step!
```
