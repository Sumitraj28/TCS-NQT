# Easy DP — Worked Examples

---

## Example 1 — Climbing Stairs (Bottom-Up DP)

**Problem:** Find number of ways to climb 5 stairs.

**Trace:**
1. Base cases: `dp[1] = 1`, `dp[2] = 2`
2. `dp[3] = dp[2] + dp[1] = 2 + 1 = 3`
3. `dp[4] = dp[3] + dp[2] = 3 + 2 = 5`
4. `dp[5] = dp[4] + dp[3] = 5 + 3 = 8`
- Total ways = 8.

**C++ Code:**
```cpp
int climbStairs(int n) {
    if (n <= 2) return n;
    int prev2 = 1, prev1 = 2;
    for (int i = 3; i <= n; ++i) {
        int curr = prev1 + prev2;
        prev2 = prev1;
        prev1 = curr;
    }
    return prev1;
}
```

---

## Example 2 — Min Cost Climbing Stairs

**Problem:** `cost = [10, 15, 20]`. Find minimum cost to reach the top.

**Trace:**
- Let `dp[i]` be the min cost to reach step `i`.
- `dp[0] = cost[0] = 10`
- `dp[1] = cost[1] = 15`
- For step 2 (top of cost list):
  `dp[2] = cost[2] + min(dp[1], dp[0]) = 20 + min(15, 10) = 30`
- To reach the final top (beyond cost list):
  `min(dp[n-1], dp[n-2]) = min(dp[2], dp[1])`? Let's check:
  - We can start at index 0 or index 1.
  - Let `dp[i]` be min cost to reach top from step `i`.
  - `dp[i] = cost[i] + min(dp[i-1], dp[i-2])`
  - `dp[0] = 10`, `dp[1] = 15`
  - `dp[2] = cost[2] + min(dp[1], dp[0]) = 20 + 10 = 30`
  - Top is index 3: `min(dp[2], dp[1]) = min(30, 15) = 15`.

**C++ Code:**
```cpp
#include <vector>
#include <algorithm>

int minCostClimbingStairs(std::vector<int>& cost) {
    int n = cost.size();
    int prev2 = cost[0];
    int prev1 = cost[1];
    for (int i = 2; i < n; ++i) {
        int curr = cost[i] + std::min(prev1, prev2);
        prev2 = prev1;
        prev1 = curr;
    }
    return std::min(prev1, prev2);
}
```
*Time Complexity: $O(N)$ | Space Complexity: $O(1)$*
