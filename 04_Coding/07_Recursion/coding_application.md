# Recursion — Coding Application (Full Problem Solutions)

---

## Problem 1 — Fibonacci Number (Recursive Version)
**LeetCode:** #509 | **Difficulty:** Easy | **TCS Frequency:** High

### Problem Statement
The Fibonacci numbers, commonly denoted $F(n)$, form a sequence called the Fibonacci sequence, such that each number is the sum of the two preceding ones, starting from 0 and 1. Given `n`, calculate $F(n)$.

### Approach
Use the recursive relation: $F(n) = F(n-1) + F(n-2)$ with base cases $F(0) = 0$ and $F(1) = 1$. Note: This recursive version has exponential time complexity.

### C++ Solution
```cpp
class Solution {
public:
    int fib(int n) {
        if (n <= 1) return n;
        return fib(n - 1) + fib(n - 2);
    }
};
```
**Complexity:** Time $O(2^N)$ | Space $O(N)$ (call stack depth)

---

## Problem 2 — Climbing Stairs (Recursive Version)
**LeetCode:** #70 | **Difficulty:** Easy | **TCS Frequency:** High

### Problem Statement
You are climbing a staircase. It takes `n` steps to reach the top. Each time you can either climb 1 or 2 steps. In how many distinct ways can you climb to the top?

### Approach
To reach step `n`, you could have come from step `n-1` (by taking 1 step) or step `n-2` (by taking 2 steps). Hence, the total ways $W(n) = W(n-1) + W(n-2)$. The base cases are $W(1) = 1$ and $W(2) = 2$.
Note: The plain recursive version has $O(2^N)$ complexity and will Time Limit Exceeded (TLE) on LeetCode/TCS compiler for large $N$.

### C++ Solution
```cpp
class Solution {
public:
    int climbStairs(int n) {
        if (n <= 2) return n;
        return climbStairs(n - 1) + climbStairs(n - 2);
    }
};
```
**Complexity:** Time $O(2^N)$ | Space $O(N)$ (call stack depth)
