# Easy DP — Previous Year Style Questions (TCS NQT)

---

### PYQ1 — N-th Fibonacci Number
**Difficulty:** Easy | **Time:** 45s | **TCS Frequency:** High
Find the $N$-th Fibonacci number.
**C++ Solution:**
```cpp
int fib(int n) {
    if (n <= 1) return n;
    int a = 0, b = 1;
    for (int i = 2; i <= n; ++i) {
        int c = a + b;
        a = b; b = c;
    }
    return b;
}
```

---

### PYQ2 — Climbing Stairs
**Difficulty:** Easy | **Time:** 60s | **TCS Frequency:** High
Count distinct ways to climb $N$ stairs.
**C++ Solution:** Bottom-up space-optimized variable transitions.

---

### PYQ3 — House Robber
**Difficulty:** Medium | **Time:** 90s | **TCS Frequency:** High
Maximize money robbed without adjacent alerts.
**C++ Solution:**
```cpp
#include <vector>
#include <algorithm>

int rob(std::vector<int>& nums) {
    int prev2 = 0, prev1 = 0;
    for (int num : nums) {
        int curr = std::max(prev1, prev2 + num);
        prev2 = prev1;
        prev1 = curr;
    }
    return prev1;
}
```

---

### PYQ4 — Min Cost Climbing Stairs
**Difficulty:** Medium | **Time:** 90s | **TCS Frequency:** High
**C++ Solution:** Compare min steps cost at each landing.

---

### PYQ5 — Decode Ways
**Difficulty:** Hard | **Time:** 120s | **TCS Frequency:** High
Determine total decodings for string digit letters.
**C++ Solution:** 1D DP table checking bounds.
