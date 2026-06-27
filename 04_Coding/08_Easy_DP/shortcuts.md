# Easy DP — Shortcuts & Optimization Speedups

## 1. Space Optimization Shortcut
If the transition only uses values from a fixed window of previous steps:
- If depending on `i - 1` and `i - 2` $\rightarrow$ use 2 variables (`prev1`, `prev2`) instead of full array.
- If depending on `i - 1`, `i - 2`, `i - 3` $\rightarrow$ use 3 variables.
- This changes space complexity from $O(N)$ to $O(1)$.

---

## 2. Array Memoization initialization
Initialize memoization cache vectors using the faster C++ fill syntax rather than loops:
```cpp
std::vector<int> memo(n + 1, -1);
```

---

## 3. Fast Bitwise Modulo in DP
If the problem asks for answer modulo $2^k$, we can do bitwise AND operations:
```cpp
// Instead of: result = sum % 1024;
// Use:
result = sum & 1023;
```
*(This is faster than standard remainder division).*
