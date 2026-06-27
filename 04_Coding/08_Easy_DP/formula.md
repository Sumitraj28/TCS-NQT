# Easy DP — Formulas and Recurrences

## 1. Fibonacci recurrence
- Tabulation state transition:
  $$\text{dp}[i] = \text{dp}[i-1] + \text{dp}[i-2]$$
- Base cases: $\text{dp}[0] = 0, \text{dp}[1] = 1$.

---

## 2. Climbing Stairs recurrence
- State transition:
  $$\text{dp}[i] = \text{dp}[i-1] + \text{dp}[i-2]$$
- Base cases: $\text{dp}[1] = 1, \text{dp}[2] = 2$.
- (This is identical to Fibonacci sequence shifted by one index position).

---

## 3. Complexity comparison

| Paradigm | Time Complexity | Space Complexity |
|----------|-----------------|------------------|
| Plain Recursion | $O(2^N)$ | $O(N)$ (call stack) |
| Memoization | $O(N)$ | $O(N)$ (cache + call stack) |
| Tabulation | $O(N)$ | $O(N)$ (cache table) |
| Space-Optimized DP | $O(N)$ | $O(1)$ |
