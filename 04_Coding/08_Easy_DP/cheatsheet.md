# Easy DP — Cheat Sheet

## C++ Code Snippets

```cpp
// Memoization setup
std::vector<int> memo(n + 1, -1);

// Space-optimized Fibonacci
int a = 0, b = 1;
for (int i = 2; i <= n; ++i) {
    int c = a + b;
    a = b; b = c;
}

// House Robber Space-Optimized
int p2 = 0, p1 = 0;
for (int num : nums) {
    int c = std::max(p1, p2 + num);
    p2 = p1; p1 = c;
}
```

## Key Guidelines

- **Always verify base cases:** `n = 0`, `n = 1` are common crash points.
- **Modulo additions:** Remember `(a + b) % MOD` for large numbers.
- **Space Optimization:** If transition only depends on a fixed window of past steps, optimize the table into variables.
