# Math — Practice: Medium (15 Questions)

---

### Q1 — Count Primes Less Than N
**Difficulty:** Medium | **Time:** 90s | **TCS Frequency:** High
Count primes strictly less than $N$.
**Full Solution:**
```cpp
#include <vector>

int countPrimes(int n) {
    if (n <= 2) return 0;
    std::vector<bool> isPrime(n, true);
    isPrime[0] = isPrime[1] = false;
    for (int i = 2; i * i < n; ++i) {
        if (isPrime[i]) {
            for (int j = i * i; j < n; j += i) isPrime[j] = false;
        }
    }
    int count = 0;
    for (int i = 2; i < n; ++i) if (isPrime[i]) count++;
    return count;
}
```
**Complexity:** Time $O(N \log \log N)$ | Space $O(N)$

---

### Q2 — Palindrome Number
**Difficulty:** Medium | **Time:** 60s | **TCS Frequency:** High
Check if number is a palindrome without extra space.
**Full Solution:**
```cpp
bool isPalindrome(int x) {
    if (x < 0 || (x % 10 == 0 && x != 0)) return false;
    int rev = 0;
    while (x > rev) {
        rev = rev * 10 + x % 10;
        x /= 10;
    }
    return x == rev || x == rev / 10;
}
```
**Complexity:** Time $O(\log_{10} N)$ | Space $O(1)$

---

### Q3 — Reverse Integer (With Overflow Checks)
**Difficulty:** Medium | **Time:** 90s | **TCS Frequency:** High
**Full Solution:**
```cpp
#include <climits>

int reverse(int x) {
    int rev = 0;
    while (x != 0) {
        int pop = x % 10;
        x /= 10;
        if (rev > INT_MAX/10 || (rev == INT_MAX/10 && pop > 7)) return 0;
        if (rev < INT_MIN/10 || (rev == INT_MIN/10 && pop < -8)) return 0;
        rev = rev * 10 + pop;
    }
    return rev;
}
```
**Complexity:** Time $O(\log N)$ | Space $O(1)$

---

### Q4 — Sieve of Eratosthenes (Prime Factors)
**Difficulty:** Medium | **Time:** 90s | **TCS Frequency:** High
Find all prime factors of a number.
**Full Solution:**
```cpp
#include <vector>

std::vector<int> getPrimeFactors(int n) {
    std::vector<int> factors;
    for (int i = 2; i * i <= n; ++i) {
        if (n % i == 0) {
            factors.push_back(i);
            while (n % i == 0) n /= i;
        }
    }
    if (n > 1) factors.push_back(n);
    return factors;
}
```
**Complexity:** Time $O(\sqrt{N})$ | Space $O(\text{factors})$

---

### Q5 — Ugly Number
**Difficulty:** Medium | **Time:** 60s | **TCS Frequency:** Medium
**Full Solution:** Divide iteratively by 2, 3, and 5.
```cpp
bool isUgly(int n) {
    if (n <= 0) return false;
    for (int d : {2, 3, 5}) while (n % d == 0) n /= d;
    return n == 1;
}
```
**Complexity:** Time $O(\log N)$ | Space $O(1)$

---

### Q6 — Happy Number
**Difficulty:** Medium | **Time:** 90s | **TCS Frequency:** High
**Full Solution:** Floyd's Tortoise and Hare cycle detection.
```cpp
int getNext(int n) {
    int sum = 0;
    while (n > 0) { int d = n % 10; sum += d * d; n /= 10; }
    return sum;
}
bool isHappy(int n) {
    int slow = n, fast = getNext(n);
    while (fast != 1 && slow != fast) {
        slow = getNext(slow);
        fast = getNext(getNext(fast));
    }
    return fast == 1;
}
```
**Complexity:** Time $O(\log N)$ | Space $O(1)$

---

### Q7 — Armstrong Numbers in Range
**Difficulty:** Medium | **Time:** 90s | **TCS Frequency:** Medium
Find all Armstrong numbers between two limits.
**Full Solution:** For each number, count digits and check sum of powers.

---

### Q8 — Pascal's Triangle Row Generators
**Difficulty:** Medium | **Time:** 90s | **TCS Frequency:** High
Given index row, generate Pascal's row.
**Full Solution:**
```cpp
#include <vector>

std::vector<int> getPascalRow(int rowIndex) {
    std::vector<int> row(rowIndex + 1, 1);
    long long val = 1;
    for (int i = 1; i < rowIndex; ++i) {
        val = val * (rowIndex - i + 1) / i;
        row[i] = val;
    }
    return row;
}
```
**Complexity:** Time $O(N)$ | Space $O(1)$ auxiliary

---

### Q9 — Add Digits O(1)
**Difficulty:** Medium | **Time:** 60s | **TCS Frequency:** Medium
Add digits until single digit remains.
**Full Solution:**
```cpp
int addDigits(int num) {
    return num == 0 ? 0 : 1 + (num - 1) % 9;
}
```
**Complexity:** Time $O(1)$ | Space $O(1)$

---

### Q10 — Missing Number (XOR method)
**Difficulty:** Medium | **Time:** 60s | **TCS Frequency:** High
**Full Solution:**
```cpp
#include <vector>

int missingNumberXOR(const std::vector<int>& nums) {
    int res = nums.size();
    for (int i = 0; i < nums.size(); ++i) {
        res ^= i ^ nums[i];
    }
    return res;
}
```
**Complexity:** Time $O(N)$ | Space $O(1)$

---

### Q11 — Power of Three check O(1)
**Difficulty:** Medium | **Time:** 60s | **TCS Frequency:** Medium
**Full Solution:** Check if the maximum 32-bit power of 3 divides the number.
```cpp
bool isPowerOfThree(int n) {
    return n > 0 && 1162261467 % n == 0;
}
```

---

### Q12 — Binary Exponentiation
**Difficulty:** Medium | **Time:** 90s | **TCS Frequency:** High
**Full Solution:**
```cpp
double myPow(double x, long long n) {
    if (n < 0) { x = 1 / x; n = -n; }
    double res = 1;
    while (n > 0) {
        if (n & 1) res *= x;
        x *= x;
        n >>= 1;
    }
    return res;
}
```

---

### Q13 — Sieve of Eratosthenes (Prime Numbers list)
**Difficulty:** Medium | **Time:** 90s | **TCS Frequency:** High
Get all prime numbers up to $N$.
**Full Solution:** Sieve boolean table.

---

### Q14 — Count Factors of a Number
**Difficulty:** Medium | **Time:** 75s | **TCS Frequency:** High
**Full Solution:** Loop up to $\sqrt{N}$ and count pairs.

---

### Q15 — Perfect Number Check
**Difficulty:** Medium | **Time:** 75s | **TCS Frequency:** Medium
**Full Solution:** Sum proper divisors up to $\sqrt{N}$.
```cpp
bool isPerfect(int num) {
    if (num <= 1) return false;
    int sum = 1;
    for (int i = 2; i * i <= num; ++i) {
        if (num % i == 0) {
            sum += i;
            if (i * i != num) sum += num / i;
        }
    }
    return sum == num;
}
```
