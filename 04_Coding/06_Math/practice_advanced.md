# Math — Practice: Advanced / Prime Level (10 Questions)

---

### Q1 — Sieve of Eratosthenes Range Query
Find primes in a range $[L, R]$ where $R \leq 10^9$ and $R - L \leq 10^5$.
**Full Solution (Segmented Sieve):**
First find all primes up to $\sqrt{R}$ using a standard sieve. Use these primes to mark composites in a segment array of size $R - L + 1$.
```cpp
#include <vector>
#include <cmath>
#include <iostream>

std::vector<int> segmentedSieve(long long L, long long R) {
    long long limit = std::sqrt(R);
    std::vector<bool> isPrime(limit + 1, true);
    std::vector<int> primes;
    for (int p = 2; p * p <= limit; p++) {
        if (isPrime[p]) {
            for (int i = p * p; i <= limit; i += p) isPrime[i] = false;
        }
    }
    for (int p = 2; p <= limit; p++) {
        if (isPrime[p]) primes.push_back(p);
    }
    
    std::vector<bool> dummy(R - L + 1, true);
    for (int p : primes) {
        long long sm = (L / p) * p;
        if (sm < L) sm += p;
        if (sm == p) sm += p; // skip marking prime itself if inside range
        for (long long i = sm; i <= R; i += p) {
            dummy[i - L] = false;
        }
    }
    std::vector<int> result;
    for (long long i = L; i <= R; ++i) {
        if (i == 1) continue;
        if (dummy[i - L]) result.push_back(i);
    }
    return result;
}
```
**Complexity:** Time $O((R - L + 1) \log \log R + \sqrt{R})$ | Space $O(R - L + 1)$

---

### Q2 — Ugly Number II
Find the $n$-th ugly number.
**Full Solution (DP with three pointers):**
```cpp
#include <vector>
#include <algorithm>

int nthUglyNumber(int n) {
    std::vector<int> dp(n);
    dp[0] = 1;
    int i2 = 0, i3 = 0, i5 = 0;
    for (int i = 1; i < n; ++i) {
        int next = std::min({dp[i2] * 2, dp[i3] * 3, dp[i5] * 5});
        dp[i] = next;
        if (next == dp[i2] * 2) i2++;
        if (next == dp[i3] * 3) i3++;
        if (next == dp[i5] * 5) i5++;
    }
    return dp[n - 1];
}
```
**Complexity:** Time $O(N)$ | Space $O(N)$

---

### Q3 — Modular Exponentiation
Compute $(a^b) \bmod c$.
**Full Solution:**
```cpp
long long modPower(long long base, long long exp, long long mod) {
    long long res = 1;
    base = base % mod;
    while (exp > 0) {
        if (exp & 1) res = (res * base) % mod;
        base = (base * base) % mod;
        exp >>= 1;
    }
    return res;
}
```

---

### Q4 — Count Primes Digit Divisibility
Count numbers in range $[L, R]$ divisible by all their non-zero digits.
**Full Solution:** Loop through and check remainder against each digit.

---

### Q5 — GCD of Array Elements
Compute GCD of all elements in an array.
**Full Solution:** Use Euclidean GCD iteratively.
```cpp
int findGCD(std::vector<int>& nums) {
    int result = nums[0];
    for (int num : nums) {
        result = gcd(result, num);
        if (result == 1) return 1;
    }
    return result;
}
```

---

### Q6 — Euler's Totient Function
Compute $\phi(N)$ (count of numbers $1..N$ coprime to $N$).
**Full Solution:** $\phi(N) = N \prod (1 - 1/p)$ for all prime factors $p$.
```cpp
int phi(int n) {
    int result = n;
    for (int i = 2; i * i <= n; ++i) {
        if (n % i == 0) {
            while (n % i == 0) n /= i;
            result -= result / i;
        }
    }
    if (n > 1) result -= result / n;
    return result;
}
```

---

### Q7 — Super Pow
Compute $a^{b} \bmod 1337$ where $b$ is a very large integer given as an array of digits.
**Full Solution:** Use property $a^b \bmod c = (a^{b \bmod \phi(c)}) \bmod c$ or recursively.

---

### Q8 — Check if Number is Fibonacci Member
Check if $N$ is a Fibonacci number.
**Full Solution:** $N$ is Fibonacci if and only if one of $5N^2 + 4$ or $5N^2 - 4$ is a perfect square.
```cpp
bool isSquare(long long x) {
    long long s = std::sqrt(x);
    return s * s == x;
}
bool isFibonacci(int n) {
    long long val1 = 5LL * n * n + 4;
    long long val2 = 5LL * n * n - 4;
    return isSquare(val1) || isSquare(val2);
}
```

---

### Q9 — N-th Catalan Number
**Full Solution:** $C_n = \frac{1}{n+1} \binom{2n}{n}$. Compute combinations using long arithmetic.

---

### Q10 — Prime Factorization Queries (using SPF Sieve)
Respond to multiple prime factorization queries in $O(\log N)$ time.
**Full Solution:** Precompute smallest prime factor (SPF) array up to $10^6$.
```cpp
#include <vector>

const int MAXN = 1000001;
int spf[MAXN];

void sieveSPF() {
    for (int i = 1; i < MAXN; ++i) spf[i] = i;
    for (int i = 2; i * i < MAXN; ++i) {
        if (spf[i] == i) {
            for (int j = i * i; j < MAXN; j += i) {
                if (spf[j] == j) spf[j] = i;
            }
        }
    }
}

std::vector<int> getFactorization(int x) {
    std::vector<int> factors;
    while (x > 1) {
        factors.push_back(spf[x]);
        x /= spf[x];
    }
    return factors;
}
```
