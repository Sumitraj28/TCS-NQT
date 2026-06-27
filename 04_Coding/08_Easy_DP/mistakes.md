# Easy DP — Common Mistakes

## 1. DP Table Size Off-By-One
**Mistake:** Allocating size `N` instead of `N + 1` for a 1D DP table. Accessing `dp[N]` then causes index out of bounds.
**Fix:** Always declare arrays as `std::vector<int> dp(n + 1);`.

---

## 2. Integer Overflow
**Mistake:** Storing large numbers in standard `int` arrays. Fibonacci values grow exponentially and will overflow.
**Fix:** Apply modulo operations or use `long long`.

---

## 3. Wrong Order of Iteration
**Mistake:** In 0/1 Knapsack style problems (e.g. Partition Sum or Coin Change), iterating in the wrong direction can result in using the same item multiple times.
**Fix:** Loop backward for 0/1 Knapsack, and forward when items can be reused (Unbounded Knapsack / Coin Change).
