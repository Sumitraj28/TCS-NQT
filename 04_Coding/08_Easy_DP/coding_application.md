# Easy DP — Coding Application (Full Problem Solutions)

---

## Problem 1 — Fibonacci Number (DP Version)
**LeetCode:** #509 | **Difficulty:** Easy | **TCS Frequency:** High

### Problem Statement
Given `n`, calculate the $n$-th Fibonacci number $F(n)$ using dynamic programming.

### Approach
Use bottom-up tabulation or space-optimized variables to build the solution iteratively in $O(N)$ time and $O(1)$ space.

### C++ Solution
```cpp
class Solution {
public:
    int fib(int n) {
        if (n <= 1) return n;
        int prev2 = 0, prev1 = 1;
        for (int i = 2; i <= n; ++i) {
            int curr = prev1 + prev2;
            prev2 = prev1;
            prev1 = curr;
        }
        return prev1;
    }
};
```
**Complexity:** Time $O(N)$ | Space $O(1)$

---

## Problem 2 — Climbing Stairs (DP Version)
**LeetCode:** #70 | **Difficulty:** Easy | **TCS Frequency:** High

### Problem Statement
Determine how many distinct ways you can climb a staircase of `n` steps, where you can climb 1 or 2 steps at a time.

### Approach
Use space-optimized dynamic programming where the number of ways to reach step `i` is the sum of ways to reach step `i-1` and `i-2`.

### C++ Solution
```cpp
class Solution {
public:
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
};
```
**Complexity:** Time $O(N)$ | Space $O(1)$
