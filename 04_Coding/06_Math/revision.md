# Math — Quick Revision

## Core Algorithms

### Euclidean GCD
```cpp
int gcd(int a, int b) { return b == 0 ? a : gcd(b, a % b); }
```

### Binary Exponentiation
```cpp
long long power(long long base, long long exp) {
    long long res = 1;
    while (exp > 0) {
        if (exp & 1) res *= base;
        base *= base;
        exp >>= 1;
    }
    return res;
}
```

### Sieve of Eratosthenes
```cpp
std::vector<bool> sieve(int n) {
    std::vector<bool> primes(n, true);
    primes[0] = primes[1] = false;
    for (int i = 2; i * i < n; ++i) {
        if (primes[i]) {
            for (int j = i * i; j < n; j += i) primes[j] = false;
        }
    }
    return primes;
}
```

## Formulas to Memorize
- LCM: `(a / gcd(a, b)) * b`
- Trailing Zeros in Factorial: Sum of $N / 5^i$
- Sum of Range: `(low + high) * (high - low + 1) / 2`
- Leap Year: `(y % 400 == 0) || (y % 4 == 0 && y % 100 != 0)`
