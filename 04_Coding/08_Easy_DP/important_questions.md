# Easy DP — Top 20 Important TCS NQT-Style Questions

---

### IQ1 — N-th Fibonacci Number.
**Answer:** State variable shifts: `c = a + b`.

---

### IQ2 — Climbing Stairs ways.
**Answer:** Same transition as Fibonacci with base cases `dp[1]=1`, `dp[2]=2`.

---

### IQ3 — House Robber maximum value.
**Answer:** `dp[i] = max(dp[i-1], dp[i-2] + nums[i])`.

---

### IQ4 — Min Cost Climbing Stairs.
**Answer:** `dp[i] = cost[i] + min(dp[i-1], dp[i-2])`.

---

### IQ5 — N-th Tribonacci Number.
**Answer:** Three variable shifts: `d = a + b + c`.

---

### IQ6 — Unique Paths in Grid.
**Answer:** `dp[i][j] = dp[i-1][j] + dp[i][j-1]`.

---

### IQ7 — Minimum Path Sum in Grid.
**Answer:** `dp[i][j] = grid[i][j] + min(dp[i-1][j], dp[i][j-1])`.

---

### IQ8 — Coin Change (Minimum Coins).
**Answer:** `dp[i] = min(dp[i], dp[i-coin] + 1)`.

---

### IQ9 — Partition Equal Subset Sum.
**Answer:** DP sum target matching for half of total sum.

---

### IQ10 — Longest Increasing Subsequence (LIS).
**Answer:** `dp[i] = max(dp[i], dp[j] + 1)` for $j < i, arr[j] < arr[i]$.

---

### IQ11 — Longest Common Subsequence (LCS).
**Answer:** `dp[i][j] = 1 + dp[i-1][j-1]` if match, else `max(dp[i-1][j], dp[i][j-1])`.

---

### IQ12 — Edit Distance.
**Answer:** Min of replacement, deletion, or insertion DP steps.

---

### IQ13 — House Robber II.
**Answer:** `max(rob(0..n-2), rob(1..n-1))`.

---

### IQ14 — Coin Change II (Total combinations).
**Answer:** `dp[i] += dp[i-coin]`.

---

### IQ15 — Decode Ways.
**Answer:** Count permutations of valid single and double digit splits.

---

### IQ16 — Word Break.
**Answer:** Boolean array search matched segments.

---

### IQ17 — Unique Paths II.
**Answer:** Unique paths with blocked states set to 0.

---

### IQ18 — Maximal Square.
**Answer:** `dp[i][j] = 1 + min({dp[i-1][j], dp[i][j-1], dp[i-1][j-1]})`.

---

### IQ19 — Counting Bits 1s.
**Answer:** `dp[i] = dp[i >> 1] + (i & 1)`.

---

### IQ20 — Divisor Game.
**Answer:** `n % 2 == 0`.
