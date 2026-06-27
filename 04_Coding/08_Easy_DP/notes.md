# Easy DP — Complete Notes

## 1. What is Dynamic Programming?
Dynamic Programming is an optimization over plain recursion. If a problem has:
1. **Overlapping Subproblems:** Subproblems are calculated multiple times.
2. **Optimal Substructure:** Optimal solution to the problem can be constructed from optimal solutions to its subproblems.

Then we can store results of subproblems to avoid recalculating them.

---

## 2. Fibonacci Transition (Recursion $\rightarrow$ DP)

### Stage 1: Plain Recursion (Top-Down)
```cpp
int fib(int n) {
    if (n <= 1) return n;
    return fib(n - 1) + fib(n - 2);
}
```
- **Drawback:** Recalculates states. Time Complexity: $O(2^N)$ | Space Complexity: $O(N)$

### Stage 2: Memoization (Top-Down with cache)
Store the results of subproblems in an array (memo table) and check it before computing.
```cpp
#include <vector>

int solve(int n, std::vector<int>& memo) {
    if (n <= 1) return n;
    if (memo[n] != -1) return memo[n]; // return cached result
    return memo[n] = solve(n - 1, memo) + solve(n - 2, memo);
}

int fibMemo(int n) {
    std::vector<int> memo(n + 1, -1);
    return solve(n, memo);
}
```
- **Improvement:** Time Complexity: $O(N)$ | Space Complexity: $O(N)$ (memo table + call stack)

### Stage 3: Tabulation (Bottom-Up)
Build the table iteratively starting from base cases, eliminating recursive call stack overhead.
```cpp
#include <vector>

int fibTab(int n) {
    if (n <= 1) return n;
    std::vector<int> dp(n + 1);
    dp[0] = 0;
    dp[1] = 1;
    for (int i = 2; i <= n; ++i) {
        dp[i] = dp[i - 1] + dp[i - 2];
    }
    return dp[n];
}
```
- **Improvement:** Time Complexity: $O(N)$ | Space Complexity: $O(N)$ (no call stack)

### Stage 4: Space-Optimized DP
Since $F(n)$ only depends on $F(n-1)$ and $F(n-2)$, we only need to track the last two values.
```cpp
int fibOpt(int n) {
    if (n <= 1) return n;
    int prev2 = 0, prev1 = 1;
    for (int i = 2; i <= n; ++i) {
        int curr = prev1 + prev2;
        prev2 = prev1;
        prev1 = curr;
    }
    return prev1;
}
```
- **Improvement:** Time Complexity: $O(N)$ | Space Complexity: $O(1)$

---

## 3. Climbing Stairs Transition

### Stage 1: Recursion
```cpp
int climbStairs(int n) {
    if (n <= 2) return n;
    return climbStairs(n - 1) + climbStairs(n - 2);
}
```

### Stage 2: Memoization
```cpp
#include <vector>

int solve(int n, std::vector<int>& memo) {
    if (n <= 2) return n;
    if (memo[n] != -1) return memo[n];
    return memo[n] = solve(n - 1, memo) + solve(n - 2, memo);
}
```

### Stage 3: Tabulation
```cpp
#include <vector>

int climbStairsTab(int n) {
    if (n <= 2) return n;
    std::vector<int> dp(n + 1);
    dp[1] = 1;
    dp[2] = 2;
    for (int i = 3; i <= n; ++i) {
        dp[i] = dp[i - 1] + dp[i - 2];
    }
    return dp[n];
}
```

### Stage 4: Space-Optimized DP
```cpp
int climbStairsOpt(int n) {
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
*Time Complexity: $O(N)$ | Space Complexity: $O(1)$*
