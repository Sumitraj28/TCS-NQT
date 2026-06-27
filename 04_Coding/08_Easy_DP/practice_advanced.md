# Easy DP — Practice: Advanced / Prime Level (10 Questions)

---

### Q1 — House Robber II (Circular Houses)
Maximize robbery money when houses are arranged in a circle (first house is neighbor of last).
**Full Solution:**
Robbery target choice: either rob houses $0$ to $N-2$, or houses $1$ to $N-1$. Take the maximum of both outcomes using standard House Robber O(1) space logic.
```cpp
#include <vector>
#include <algorithm>

int robHelper(const std::vector<int>& nums, int start, int end) {
    int prev2 = 0, prev1 = 0;
    for (int i = start; i <= end; ++i) {
        int curr = std::max(prev1, prev2 + nums[i]);
        prev2 = prev1;
        prev1 = curr;
    }
    return prev1;
}

int robCircular(std::vector<int>& nums) {
    int n = nums.size();
    if (n == 1) return nums[0];
    return std::max(robHelper(nums, 0, n - 2), robHelper(nums, 1, n - 1));
}
```
**Complexity:** Time $O(N)$ | Space $O(1)$

---

### Q2 — Coin Change (Min Coins)
Find the fewest number of coins needed to make up a given amount.
**Full Solution:**
`dp[i] = min(dp[i], dp[i - coin] + 1)`.
```cpp
#include <vector>
#include <algorithm>

int coinChange(std::vector<int>& coins, int amount) {
    std::vector<int> dp(amount + 1, amount + 1);
    dp[0] = 0;
    for (int i = 1; i <= amount; ++i) {
        for (int coin : coins) {
            if (i - coin >= 0) {
                dp[i] = std::min(dp[i], dp[i - coin] + 1);
            }
        }
    }
    return dp[amount] > amount ? -1 : dp[amount];
}
```
**Complexity:** Time $O(\text{amount} \times \text{coins})$ | Space $O(\text{amount})$

---

### Q3 — Word Break
Check if string can be segmented into space-separated dictionary words.
**Full Solution:** Set elements indices to true if `dp[j] && dict.count(s[j..i])`.

---

### Q4 — Longest Increasing Subsequence (LIS)
Find length of longest increasing subsequence in array.
**Full Solution:**
`dp[i] = max(dp[i], dp[j] + 1)` for $j < i$ and $arr[j] < arr[i]$.
```cpp
#include <vector>
#include <algorithm>

int lengthOfLIS(std::vector<int>& nums) {
    if (nums.empty()) return 0;
    std::vector<int> dp(nums.size(), 1);
    int maxLen = 1;
    for (size_t i = 1; i < nums.size(); ++i) {
        for (size_t j = 0; j < i; ++j) {
            if (nums[i] > nums[j]) {
                dp[i] = std::max(dp[i], dp[j] + 1);
            }
        }
        maxLen = std::max(maxLen, dp[i]);
    }
    return maxLen;
}
```
*Time Complexity: $O(N^2)$ (can be optimized to $O(N \log N)$ with binary search).*

---

### Q5 — Unique Paths II (Grid with obstacles)
**Full Solution:** Skip processing paths from cells containing obstacle value 1.

---

### Q6 — Triangle Minimum Path Sum
Find min path sum from top to bottom of triangle array.
**Full Solution:** Bottom-up row reductions.

---

### Q7 — Maximal Square
Find largest square containing only 1s in a 2D binary matrix.
**Full Solution:**
`dp[i][j] = 1 + min({dp[i-1][j], dp[i][j-1], dp[i-1][j-1]})`.

---

### Q8 — Longest Palindromic Subsequence (LPS)
**Full Solution:** `LPS(s) = LCS(s, reverse(s))`.

---

### Q9 — Combination Sum IV
Find number of combinations that sum to target.
**Full Solution:**
```cpp
#include <vector>

int combinationSum4(std::vector<int>& nums, int target) {
    std::vector<unsigned int> dp(target + 1, 0);
    dp[0] = 1;
    for (int i = 1; i <= target; ++i) {
        for (int num : nums) {
            if (i - num >= 0) {
                dp[i] += dp[i - num];
            }
        }
    }
    return dp[target];
}
```

---

### Q10 — Best Time to Buy and Sell Stock with Cooldown
Maximize profit with stock buying/selling and a 1-day cooldown.
**Full Solution:** Maintain state variable arrays: `buy`, `sell`, and `cooldown`.
```cpp
#include <vector>
#include <algorithm>

int maxProfitCooldown(std::vector<int>& prices) {
    if (prices.size() <= 1) return 0;
    int n = prices.size();
    std::vector<int> buy(n, 0), sell(n, 0);
    buy[0] = -prices[0];
    buy[1] = std::max(-prices[0], -prices[1]);
    sell[1] = std::max(0, buy[0] + prices[1]);
    
    for (int i = 2; i < n; ++i) {
        sell[i] = std::max(sell[i - 1], buy[i - 1] + prices[i]);
        buy[i] = std::max(buy[i - 1], sell[i - 2] - prices[i]);
    }
    return sell[n - 1];
}
```
**Complexity:** Time $O(N)$ | Space $O(N)$
