# Easy DP — Practice: Basic (15 Questions)

---

### Q1 — Declare DP Memoization Array
How to declare a 1D DP table initialized to -1 of size $N+1$?
**Answer:** `std::vector<int> dp(n + 1, -1);`

---

### Q2 — Fibonacci Space-Optimized
Write the code to find Fibonacci of $N$ in $O(1)$ space.
**Answer:**
```cpp
int fib(int n) {
    if (n <= 1) return n;
    int a = 0, b = 1;
    for (int i = 2; i <= n; ++i) {
        int c = a + b;
        a = b;
        b = c;
    }
    return b;
}
```

---

### Q3 — Base Cases of Climbing Stairs
**Answer:** `dp[1] = 1` (1 way to reach step 1), `dp[2] = 2` (2 ways to reach step 2).

---

### Q4 — State Transition of Tribonacci
What is the state transition formula for Tribonacci: $T(n) = T(n-1) + T(n-2) + T(n-3)$?
**Answer:** `dp[i] = dp[i - 1] + dp[i - 2] + dp[i - 3];`

---

### Q5 — Overlapping Subproblems
Define overlapping subproblems.
**Answer:** When recursive calls solve the exact same subproblems multiple times instead of generating unique tasks.

---

### Q6 — Optimal Substructure
Define optimal substructure.
**Answer:** A problem has optimal substructure if an optimal solution to the problem contains optimal solutions to its subproblems.

---

### Q7 — Difference between Top-Down and Bottom-Up
**Answer:** Top-Down is memoization (recursion + caching), Bottom-Up is tabulation (iteration building up from base cases).

---

### Q8 — Base Case of Min Cost Climbing Stairs
**Answer:** `dp[0] = cost[0]` and `dp[1] = cost[1]`.

---

### Q9 — Memoization Table Size
What should be the size of the memoization table to store states from $0$ to $N$?
**Answer:** `N + 1`.

---

### Q10 — Tribonacci Space-Optimized
**Answer:**
```cpp
int tribonacci(int n) {
    if (n == 0) return 0;
    if (n <= 2) return 1;
    int a = 0, b = 1, c = 1;
    for (int i = 3; i <= n; ++i) {
        int d = a + b + c;
        a = b; b = c; c = d;
    }
    return c;
}
```

---

### Q11 — Avoid Stack Overflow in Fibonacci
How does bottom-up tabulation avoid stack overflows?
**Answer:** It uses iteration (loops) instead of recursion, which avoids pushing stack frames onto the call stack.

---

### Q12 — Time Complexity of Memoized Fibonacci
**Answer:** $O(N)$ (each state is computed exactly once).

---

### Q13 — Space Complexity of Tabulated Fibonacci
**Answer:** $O(N)$ (if using an array of size $N+1$).

---

### Q14 — Modulo Arithmetic in DP additions
**Answer:** `dp[i] = (dp[i-1] + dp[i-2]) % MOD;`

---

### Q15 — Check if State is Calculated
What check is used in memoization to determine if `dp[i]` is already calculated?
**Answer:** `if (dp[i] != -1)` (assuming -1 represents uncalculated).
 Richmond.
