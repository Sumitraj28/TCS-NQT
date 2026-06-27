# Math — Coding Application (Full Problem Solutions)

Every solution includes: Problem Statement → Approach → C++ code (line-by-line) → Complexity.

---

## Problem 1 — Count Primes
**LeetCode:** #204 | **Difficulty:** Medium | **TCS Frequency:** High

### Problem Statement
Given an integer `n`, return the number of prime numbers that are strictly less than `n`.

### Approach
Use the Sieve of Eratosthenes algorithm. Maintain a boolean array of size `n` initialized to true. Set composite numbers to false starting from the square of each prime.

### C++ Solution
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

## Problem 2 — Power of Two
**LeetCode:** #231 | **Difficulty:** Easy | **TCS Frequency:** High

### Problem Statement
Given an integer `n`, return `true` if it is a power of two. Otherwise, return `false`.

### Approach
A power of two has exactly one set bit in its binary representation. We can verify this in $O(1)$ using the bitwise operation `(n & (n - 1)) == 0` for `n > 0`.

### C++ Solution
```cpp
class Solution {
public:
    bool isPowerOfTwo(int n) {
        return n > 0 && (n & (n - 1LL)) == 0;
    }
};
```
**Complexity:** Time $O(1)$ | Space $O(1)$

---

## Problem 3 — Ugly Number
**LeetCode:** #263 | **Difficulty:** Easy | **TCS Frequency:** Medium

### Problem Statement
An ugly number is a positive integer whose prime factors are limited to 2, 3, and 5. Given an integer `n`, return `true` if `n` is an ugly number.

### Approach
Divide `n` iteratively by 2, 3, and 5 as long as it is divisible. If the final value is 1, return `true`.

### C++ Solution
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

## Problem 4 — Palindrome Number
**LeetCode:** #9 | **Difficulty:** Easy | **TCS Frequency:** High

### Problem Statement
Given an integer `x`, return `true` if `x` is a palindrome.

### Approach
Reverse the second half of the number and compare it with the first half to avoid integer overflow issues.

### C++ Solution
```cpp
class Solution {
public:
    bool isPalindrome(int x) {
        if (x < 0 || (x % 10 == 0 && x != 0)) return false;
        
        int revertedNumber = 0;
        while (x > revertedNumber) {
            revertedNumber = revertedNumber * 10 + x % 10;
            x /= 10;
        }
        
        return x == revertedNumber || x == revertedNumber / 10;
    }
};
```
**Complexity:** Time $O(\log_{10} N)$ | Space $O(1)$

---

## Problem 5 — Reverse Integer
**LeetCode:** #7 | **Difficulty:** Medium | **TCS Frequency:** High

### Problem Statement
Given a signed 32-bit integer `x`, return `x` with its digits reversed. If reversing `x` causes the value to go outside the signed 32-bit integer range, return 0.

### Approach
Extract digits one by one. Check for potential 32-bit overflow/underflow before multiplying the reversed value by 10.

### C++ Solution
```cpp
#include <climits>

class Solution {
public:
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
};
```
**Complexity:** Time $O(\log_{10} N)$ | Space $O(1)$

---

## Problem 6 — Add Digits
**LeetCode:** #258 | **Difficulty:** Easy | **TCS Frequency:** Medium

### Problem Statement
Given an integer `num`, repeatedly add all its digits until the result has only one digit, and return it.

### Approach
We can calculate the digital root of the number in $O(1)$ time using congruence modulo 9: `1 + (num - 1) % 9`.

### C++ Solution
```cpp
class Solution {
public:
    int addDigits(int num) {
        if (num == 0) return 0;
        return 1 + (num - 1) % 9;
    }
};
```
**Complexity:** Time $O(1)$ | Space $O(1)$

---

## Problem 7 — Happy Number
**LeetCode:** #202 | **Difficulty:** Easy | **TCS Frequency:** High

### Problem Statement
Determine if a number `n` is happy. A happy number is defined by replacing the number by the sum of the squares of its digits repeatedly until it equals 1, or it loops endlessly in a cycle.

### Approach
Use Floyd's Cycle-Finding Algorithm (Tortoise and Hare) to detect cycles.

### C++ Solution
```cpp
class Solution {
private:
    int getNext(int n) {
        int totalSum = 0;
        while (n > 0) {
            int d = n % 10;
            n /= 10;
            totalSum += d * d;
        }
        return totalSum;
    }
public:
    bool isHappy(int n) {
        int slow = n;
        int fast = getNext(n);
        while (fast != 1 && slow != fast) {
            slow = getNext(slow);
            fast = getNext(getNext(fast));
        }
        return fast == 1;
    }
};
```
**Complexity:** Time $O(\log N)$ | Space $O(1)$

---

## Problem 8 — Missing Number
**LeetCode:** #268 | **Difficulty:** Easy | **TCS Frequency:** High

### Problem Statement
Given an array `nums` containing `n` distinct numbers in the range `[0, n]`, return the only number in the range that is missing from the array.

### Approach
Use the summation formula $S = \frac{n(n+1)}{2}$ and subtract the sum of elements.

### C++ Solution
```cpp
#include <vector>
#include <numeric>

class Solution {
public:
    int missingNumber(std::vector<int>& nums) {
        int n = nums.size();
        int expectedSum = n * (n + 1) / 2;
        int actualSum = std::accumulate(nums.begin(), nums.end(), 0);
        return expectedSum - actualSum;
    }
};
```
**Complexity:** Time $O(N)$ | Space $O(1)$

---

## Problem 9 — Perfect Number
**LeetCode:** #507 | **Difficulty:** Easy | **TCS Frequency:** Medium

### Problem Statement
A perfect number is a positive integer that is equal to the sum of its positive divisors, excluding the number itself. Given an integer `n`, return `true` if `n` is a perfect number.

### Approach
Find factors up to $\sqrt{N}$ and sum them up.

### C++ Solution
```cpp
class Solution {
public:
    bool checkPerfectNumber(int num) {
        if (num <= 1) return false;
        int sum = 1;
        for (int i = 2; i * i <= num; ++i) {
            if (num % i == 0) {
                sum += i;
                if (i * i != num) {
                    sum += num / i;
                }
            }
        }
        return sum == num;
    }
};
```
**Complexity:** Time $O(\sqrt{N})$ | Space $O(1)$

---

## Problem 10 — Pascal's Triangle
**LeetCode:** #118 | **Difficulty:** Easy | **TCS Frequency:** High

### Problem Statement
Given an integer `numRows`, return the first `numRows` of Pascal's triangle.

### Approach
Initialize the matrix rows. The value at `[i][j]` is the sum of `[i-1][j-1]` and `[i-1][j]`.

### C++ Solution
```cpp
#include <vector>

class Solution {
public:
    std::vector<std::vector<int>> generate(int numRows) {
        std::vector<std::vector<int>> triangle;
        for (int i = 0; i < numRows; ++i) {
            std::vector<int> row(i + 1, 1);
            for (int j = 1; j < i; ++j) {
                row[j] = triangle[i - 1][j - 1] + triangle[i - 1][j];
            }
            triangle.push_back(row);
        }
        return triangle;
    }
};
```
**Complexity:** Time $O(N^2)$ | Space $O(N^2)$

---

## Problem 11 — Pascal's Triangle II
**LeetCode:** #119 | **Difficulty:** Easy | **TCS Frequency:** Medium

### Problem Statement
Given an integer `rowIndex`, return the `rowIndex`-th (0-indexed) row of Pascal's triangle.

### Approach
Generate elements using the combination formula $C(n, k) = C(n, k-1) \times \frac{n-k+1}{k}$ to do it in $O(N)$ time and $O(1)$ auxiliary space.

### C++ Solution
```cpp
#include <vector>

class Solution {
public:
    std::vector<int> getRow(int rowIndex) {
        std::vector<int> row(rowIndex + 1, 1);
        long long val = 1;
        for (int i = 1; i < rowIndex; ++i) {
            val = val * (rowIndex - i + 1) / i;
            row[i] = val;
        }
        return row;
    }
};
```
**Complexity:** Time $O(N)$ | Space $O(1)$ auxiliary

---

## Problem 12 — Count Odd Numbers in an Interval Range
**LeetCode:** #1523 | **Difficulty:** Easy | **TCS Frequency:** High

### Problem Statement
Given two non-negative integers `low` and `high`. Return the count of odd numbers between `low` and `high` (inclusive).

### Approach
The number of odds between $1$ and $X$ is $\frac{X + 1}{2}$. The count between `low` and `high` is $\text{odds}(high) - \text{odds}(low - 1)$.

### C++ Solution
```cpp
class Solution {
public:
    int countOdds(int low, int high) {
        return (high + 1) / 2 - low / 2;
    }
};
```
**Complexity:** Time $O(1)$ | Space $O(1)$

---

## Problem 13 — Power of Three
**LeetCode:** #326 | **Difficulty:** Easy | **TCS Frequency:** Medium

### Problem Statement
Given an integer `n`, return `true` if it is a power of three.

### Approach
In a 32-bit signed integer, the maximum power of 3 is $3^{19} = 1162261467$. Since 3 is a prime number, any power of 3 must divide $3^{19}$.

### C++ Solution
```cpp
class Solution {
public:
    bool isPowerOfThree(int n) {
        return n > 0 && 1162261467 % n == 0;
    }
};
```
**Complexity:** Time $O(1)$ | Space $O(1)$

---

## Problem 14 — Pow(x, n)
**LeetCode:** #50 | **Difficulty:** Medium | **TCS Frequency:** High

### Problem Statement
Implement `pow(x, n)`, which calculates `x` raised to the power `n` (i.e., $x^n$).

### Approach
Implement binary exponentiation, using recursion or iteration, while handling potential integer overflow for `n = INT_MIN` by casting to `long long`.

### C++ Solution
```cpp
class Solution {
public:
    double myPow(double x, int n) {
        long long N = n;
        if (N < 0) {
            x = 1 / x;
            N = -N;
        }
        double ans = 1.0;
        double current_product = x;
        while (N > 0) {
            if (N % 2 == 1) {
                ans *= current_product;
            }
            current_product *= current_product;
            N /= 2;
        }
        return ans;
    }
};
```
**Complexity:** Time $O(\log N)$ | Space $O(1)$
