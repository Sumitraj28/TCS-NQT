# Math — Previous Year Style Questions (TCS NQT)

---

### PYQ1 — Prime Range Queries
**Difficulty:** Medium | **Time:** 90s | **TCS Frequency:** High
Find the count of prime numbers in range $[L, R]$ (inclusive).
**C++ Solution:**
```cpp
#include <vector>

int countPrimesInRange(int L, int R) {
    if (R < 2) return 0;
    if (L < 2) L = 2;
    std::vector<bool> isPrime(R + 1, true);
    isPrime[0] = isPrime[1] = false;
    for (int p = 2; p * p <= R; ++p) {
        if (isPrime[p]) {
            for (int i = p * p; i <= R; i += p) isPrime[i] = false;
        }
    }
    int count = 0;
    for (int i = L; i <= R; ++i) {
        if (isPrime[i]) count++;
    }
    return count;
}
```

---

### PYQ2 — Greatest Common Divisor of Array
**Difficulty:** Easy | **Time:** 60s | **TCS Frequency:** High
Find the GCD of $N$ integers.
**C++ Solution:**
```cpp
int gcd(int a, int b) {
    return b == 0 ? a : gcd(b, a % b);
}
int findArrayGCD(const std::vector<int>& arr) {
    int res = arr[0];
    for (int num : arr) {
        res = gcd(res, num);
        if (res == 1) return 1;
    }
    return res;
}
```

---

### PYQ3 — Armstrong Numbers in Interval
**Difficulty:** Easy | **Time:** 60s | **TCS Frequency:** High
Check all Armstrong numbers in range $[L, R]$.
**C++ Solution:** Check each number by computing sum of digits raised to digit count.

---

### PYQ4 — Count trailing zeros in Factorial of N
**Difficulty:** Medium | **Time:** 60s | **TCS Frequency:** High
**C++ Solution:** Sum of $\lfloor N / 5^k \rfloor$ for $k \geq 1$.
```cpp
int countTrailingZeros(int n) {
    int count = 0;
    while (n >= 5) {
        count += n / 5;
        n /= 5;
    }
    return count;
}
```

---

### PYQ5 — Leap Year Check list
**Difficulty:** Easy | **Time:** 45s | **TCS Frequency:** High
Given a list of years, count the number of leap years.
**C++ Solution:** Use leap year divisibility rule in loop.
