# Number System — Coding Application (Connecting Math to Code)

This section maps numerical ability concepts (prime numbers, divisibility, power factors) to C++ coding problems.

---

## 1. Prime Numbers $\rightarrow$ Count Primes
**Concept Connection:** Prime classification and sifting.
**Sieve of Eratosthenes Connection:** Instead of checking each number up to $N$ individually using $O(\sqrt{N})$ tests (which takes $O(N\sqrt{N})$), we use the Sieve of Eratosthenes to find all primes in $O(N \log \log N)$ time by crossing out multiples of primes.

```cpp
#include <vector>

class Solution {
public:
    int countPrimes(int n) {
        if (n <= 2) return 0;
        std::vector<bool> isPrime(n, true);
        isPrime[0] = isPrime[1] = false;
        for (int i = 2; i * i < n; ++i) {
            if (isPrime[i]) {
                for (int j = i * i; j < n; j += i) {
                    isPrime[j] = false;
                }
            }
        }
        int count = 0;
        for (int i = 2; i < n; ++i) {
            if (isPrime[i]) count++;
        }
        return count;
    }
};
```
**Complexity:** Time $O(N \log \log N)$ | Space $O(N)$

---

## 2. Prime Factors $\rightarrow$ Ugly Number
**Concept Connection:** Prime factorization.
An ugly number is a positive integer whose prime factors are limited to 2, 3, and 5. We verify this by repeatedly dividing the number by these factors. If the final value is 1, it has no other prime factors.

```cpp
class Solution {
public:
    bool isUgly(int n) {
        if (n <= 0) return false;
        for (int factor : {2, 3, 5}) {
            while (n % factor == 0) {
                n /= factor;
            }
        }
        return n == 1;
    }
};
```
**Complexity:** Time $O(\log N)$ | Space $O(1)$

---

## 3. Powers of Prime $\rightarrow$ Power of Two
**Concept Connection:** Base 2 conversion and binary representation.
A number that is a power of 2 has exactly one set bit in binary representation (e.g. $4 = 100_2$, $8 = 1000_2$). We can perform this check in $O(1)$ using the bitwise operation `(n & (n - 1)) == 0`.

```cpp
class Solution {
public:
    bool isPowerOfTwo(int n) {
        return n > 0 && (n & (n - 1LL)) == 0;
    }
};
```
**Complexity:** Time $O(1)$ | Space $O(1)$
