# Easy DP — Tricks, Traps, and TCS-Specific Patterns

## Trap 1 — Index Out of Bounds in Base Cases
**The trap:** Writing a bottom-up loop starting at index `2` or `3` without allocating enough size for the DP table when $N$ is small (e.g. `n = 0` or `n = 1`).
Example: `dp[1] = 1; dp[2] = 2;` will crash if $N = 1$ because the array size is only 2 (indices 0 and 1).

**Fix:** Add explicit checks at the beginning of the function for $N < 2$, or allocate `n + 2` size.
```cpp
if (n <= 2) return n;
```

---

## Trap 2 — Integer Overflow
**The trap:** Fibonacci values grow exponentially. $F(47)$ overflows standard 32-bit signed integers, and $F(93)$ overflows 64-bit integers.
TCS questions often ask to return the answer modulo $10^9+7$ to prevent this.

**Fix:** Apply modulo at each addition step:
```cpp
dp[i] = (dp[i - 1] + dp[i - 2]) % 1000000007;
```

---

## Trap 3 — Memoization Table Uninitialized
**The trap:** Forgetting to initialize the memoization table with a marker value (like `-1`) that represents an unvisited state.

**Fix:** Always use a unique default value that cannot be a valid computed answer.
