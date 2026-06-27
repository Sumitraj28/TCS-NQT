# Recursion — Cheat Sheet

## C++ Code Snippets

```cpp
// FACTORIAL
long long fact(int n) { return n <= 1 ? 1 : n * fact(n - 1); }

// FIBONACCI
int fib(int n) { return n <= 1 ? n : fib(n - 1) + fib(n - 2); }

// SUM OF DIGITS
int sumDig(int n) { return n == 0 ? 0 : (n % 10) + sumDig(n / 10); }

// TOWER OF HANOI
void hanoi(int n, char s, char d, char a) {
    if (n == 0) return;
    hanoi(n - 1, s, a, d);
    std::cout << "Move disk " << n << " from " << s << " to " << d << "\n";
    hanoi(n - 1, a, d, s);
}
```

## Key Complexities

| Algorithm | Recurrence relation | Time Complexity | Space Complexity |
|-----------|---------------------|-----------------|------------------|
| Factorial | $T(N) = T(N-1) + O(1)$ | $O(N)$ | $O(N)$ (stack) |
| Fibonacci | $T(N) = T(N-1) + T(N-2)$ | $O(2^N)$ | $O(N)$ (stack) |
| Hanoi | $T(N) = 2T(N-1) + O(1)$ | $O(2^N)$ | $O(N)$ (stack) |
| Digit Sum | $T(N) = T(N/10) + O(1)$ | $O(\log_{10} N)$ | $O(\log_{10} N)$ |
