# Math — Cheat Sheet

## C++ Code Snippets

```cpp
// GCD
int gcd(int a, int b) { return b == 0 ? a : gcd(b, a % b); }

// LCM
int lcm(int a, int b) { return (a / gcd(a, b)) * b; }

// Power of 2 check
bool isPowerOfTwo = n > 0 && (n & (n - 1)) == 0;

// Trailing Zeros in N!
int trailingZeros(int n) {
    int count = 0;
    while (n >= 5) { count += n / 5; n /= 5; }
    return count;
}

// Count Primes (Sieve)
std::vector<bool> isPrime(n, true);
for (int i = 2; i * i < n; ++i) {
    if (isPrime[i]) {
        for (int j = i * i; j < n; j += i) isPrime[j] = false;
    }
}
```

## Reference Table

| Formula / Concept | Code / Math expression | Complexity |
|-------------------|------------------------|------------|
| GCD(a, b) | `gcd(a, b)` | $O(\log(\min(a,b)))$ |
| Prime Check | Loop up to $\sqrt{N}$ | $O(\sqrt{N})$ |
| Exponentiation | Binary Exponentiation | $O(\log N)$ |
| Trailing Zeros | $\sum \lfloor n/5^k \rfloor$ | $O(\log_5 N)$ |
| Missing Number | Sum formula difference | $O(N)$ time, $O(1)$ space |
| Armstrong Check | Digits power sum | $O(\log_{10} N)$ |
| digital root | `1 + (n - 1) % 9` | $O(1)$ |
