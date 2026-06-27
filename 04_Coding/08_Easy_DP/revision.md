# Easy DP — Quick Revision

## Core Templates

### Fibonacci (Space-Optimized)
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

### Climbing Stairs
```cpp
int climb(int n) {
    if (n <= 2) return n;
    int a = 1, b = 2;
    for (int i = 3; i <= n; ++i) {
        int c = a + b;
        a = b; b = c;
    }
    return b;
}
```

### House Robber
```cpp
int rob(const std::vector<int>& nums) {
    int prev2 = 0, prev1 = 0;
    for (int num : nums) {
        int curr = std::max(prev1, prev2 + num);
        prev2 = prev1;
        prev1 = curr;
    }
    return prev1;
}
```

## Key Modulo Rule
`MOD = 1000000007;`
`dp[i] = (dp[i-1] + dp[i-2]) % MOD;`
