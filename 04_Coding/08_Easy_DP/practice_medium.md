# Easy DP — Practice: Medium (15 Questions)

---

### Q1 — Min Cost Climbing Stairs
**Difficulty:** Medium | **Time:** 90s | **TCS Frequency:** High
Find min cost to reach top of stairs.
**Full Solution:**
```cpp
#include <vector>
#include <algorithm>

int minCostClimbingStairs(std::vector<int>& cost) {
    int n = cost.size();
    int prev2 = cost[0], prev1 = cost[1];
    for (int i = 2; i < n; ++i) {
        int curr = cost[i] + std::min(prev1, prev2);
        prev2 = prev1;
        prev1 = curr;
    }
    return std::min(prev1, prev2);
}
```
**Complexity:** Time $O(N)$ | Space $O(1)$

---

### Q2 — House Robber
**Difficulty:** Medium | **Time:** 120s | **TCS Frequency:** High
Maximize money robbed without robbing adjacent houses.
**Full Solution:**
`dp[i] = max(dp[i-1], dp[i-2] + nums[i])`.
```cpp
#include <vector>
#include <algorithm>

int rob(std::vector<int>& nums) {
    if (nums.empty()) return 0;
    int n = nums.size();
    if (n == 1) return nums[0];
    int prev2 = 0, prev1 = nums[0];
    for (int i = 1; i < n; ++i) {
        int curr = std::max(prev1, prev2 + nums[i]);
        prev2 = prev1;
        prev1 = curr;
    }
    return prev1;
}
```
**Complexity:** Time $O(N)$ | Space $O(1)$

---

### Q3 — N-th Tribonacci Number
**Difficulty:** Medium | **Time:** 60s | **TCS Frequency:** High
**Full Solution:** Space optimized 3-variable shifts.

---

### Q4 — Maximum Sum of Non-Adjacent Elements
**Difficulty:** Medium | **Time:** 90s | **TCS Frequency:** High
(Identical problem statement to House Robber).

---

### Q5 — Decoding Ways (1D DP)
Given string digit representation, find number of ways to decode it ('A'=1, 'B'=2... 'Z'=26).
**Full Solution:**
```cpp
#include <string>
#include <vector>

int numDecodings(std::string s) {
    if (s.empty() || s[0] == '0') return 0;
    int n = s.length();
    std::vector<int> dp(n + 1, 0);
    dp[0] = 1;
    dp[1] = 1;
    for (int i = 2; i <= n; ++i) {
        if (s[i - 1] != '0') dp[i] += dp[i - 1];
        int twoDigit = std::stoi(s.substr(i - 2, 2));
        if (twoDigit >= 10 && twoDigit <= 26) dp[i] += dp[i - 2];
    }
    return dp[n];
}
```
**Complexity:** Time $O(N)$ | Space $O(N)$

---

### Q6 — Unique Paths (2D grid DP basics)
Given $M \times N$ grid, find unique paths from top-left to bottom-right.
**Full Solution:**
`dp[i][j] = dp[i-1][j] + dp[i][j-1]`.
```cpp
#include <vector>

int uniquePaths(int m, int n) {
    std::vector<int> dp(n, 1);
    for (int i = 1; i < m; ++i) {
        for (int j = 1; j < n; ++j) {
            dp[j] += dp[j - 1];
        }
    }
    return dp[n - 1];
}
```
**Complexity:** Time $O(M \times N)$ | Space $O(N)$

---

### Q7 — Minimum Path Sum
Given $M \times N$ grid containing non-negative numbers, find path minimizing sum.
**Full Solution:**
`dp[i][j] = grid[i][j] + min(dp[i-1][j], dp[i][j-1])`.

---

### Q8 — Divisor Game
**Difficulty:** Medium | **Time:** 60s | **TCS Frequency:** Medium
**Full Solution:** Returns `n % 2 == 0`.

---

### Q9 — Integer Break
**Difficulty:** Medium | **Time:** 90s | **TCS Frequency:** Medium
**Full Solution:** Break integer to maximize product of parts.

---

### Q10 — Coin Change II (Ways to make change)
**Difficulty:** Medium | **Time:** 120s | **TCS Frequency:** High
Find total combinations that sum up to amount.
**Full Solution:**
```cpp
#include <vector>

int change(int amount, std::vector<int>& coins) {
    std::vector<int> dp(amount + 1, 0);
    dp[0] = 1;
    for (int coin : coins) {
        for (int i = coin; i <= amount; ++i) {
            dp[i] += dp[i - coin];
        }
    }
    return dp[amount];
}
```
**Complexity:** Time $O(\text{amount} \times \text{coins})$ | Space $O(\text{amount})$

---

### Q11 — Perfect Squares
**Difficulty:** Medium | **Time:** 120s | **TCS Frequency:** Medium
Find least number of perfect square numbers that sum to $N$.
**Full Solution:**
`dp[i] = min(dp[i], dp[i - j*j] + 1)`.

---

### Q12 — Partition Equal Subset Sum
**Difficulty:** Medium | **Time:** 120s | **TCS Frequency:** High
Check if array can be partitioned into two subsets with equal sum.
**Full Solution:** 0/1 Knapsack style target search for `sum / 2`.

---

### Q13 — Longest Palindromic Substring (DP approach)
**Difficulty:** Medium | **Time:** 120s | **TCS Frequency:** High
**Full Solution:** 2D boolean table tracking if `s[i..j]` is palindrome.

---

### Q14 — Arithmetic Slices
**Difficulty:** Medium | **Time:** 90s | **TCS Frequency:** Medium
Find number of arithmetic slices in array.
**Full Solution:** Track consecutive differences.

---

### Q15 — Counting Bits
**Difficulty:** Medium | **Time:** 90s | **TCS Frequency:** High
**Full Solution:**
`dp[i] = dp[i / 2] + (i % 2)`.
```cpp
#include <vector>

std::vector<int> countBits(int n) {
    std::vector<int> dp(n + 1, 0);
    for (int i = 1; i <= n; ++i) {
        dp[i] = dp[i >> 1] + (i & 1);
    }
    return dp;
}
```
**Complexity:** Time $O(N)$ | Space $O(N)$
