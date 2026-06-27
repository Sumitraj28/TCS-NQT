# Math — Complete Notes

## 1. Prime Number Check
A prime number is a number strictly greater than 1 that has no positive divisors other than 1 and itself.
To check if a number $N$ is prime, we only need to test divisors up to $\sqrt{N}$.

```cpp
bool isPrime(int n) {
    if (n <= 1) return false;
    if (n <= 3) return true;
    if (n % 2 == 0 || n % 3 == 0) return false;
    for (int i = 5; i * i <= n; i += 6) {
        if (n % i == 0 || n % (i + 2) == 0) return false;
    }
    return true;
}
```
*Time Complexity: $O(\sqrt{N})$ | Space Complexity: $O(1)$*

---

## 2. GCD and LCM (Euclidean Algorithm)
- **GCD (Greatest Common Divisor):** The largest positive integer that divides each of the integers.
- **LCM (Least Common Multiple):** $\text{LCM}(a, b) = \frac{|a \times b|}{\text{GCD}(a, b)}$

```cpp
int gcd(int a, int b) {
    while (b) {
        int temp = b;
        b = a % b;
        a = temp;
    }
    return a;
}

int lcm(int a, int b) {
    if (a == 0 || b == 0) return 0;
    return (a / gcd(a, b)) * b; // prevent overflow by dividing first
}
```
*Time Complexity: $O(\log(\min(a, b)))$ | Space Complexity: $O(1)$*

---

## 3. Factors of a Number
Find all positive divisors of $N$. Loop up to $\sqrt{N}$; if $i$ divides $N$, then both $i$ and $N/i$ are factors.

```cpp
#include <vector>
#include <algorithm>

std::vector<int> findFactors(int n) {
    std::vector<int> factors;
    for (int i = 1; i * i <= n; ++i) {
        if (n % i == 0) {
            factors.push_back(i);
            if (i * i != n) {
                factors.push_back(n / i);
            }
        }
    }
    std::sort(factors.begin(), factors.end());
    return factors;
}
```
*Time Complexity: $O(\sqrt{N})$ | Space Complexity: $O(\sqrt{N})$*

---

## 4. Power & Binary Exponentiation
Computes $x^n$ in $O(\log n)$ time instead of $O(n)$.

```cpp
double binaryPow(double x, long long n) {
    if (n < 0) {
        x = 1 / x;
        n = -n;
    }
    double result = 1.0;
    double current_product = x;
    while (n > 0) {
        if (n % 2 == 1) {
            result *= current_product;
        }
        current_product *= current_product;
        n /= 2;
    }
    return result;
}
```
*Time Complexity: $O(\log N)$ | Space Complexity: $O(1)$*

---

## 5. Digit Manipulation
Common tasks like extracting digits, reversing, sum of digits, and palindrome checks.

```cpp
// Count digits
int countDigits(int n) {
    if (n == 0) return 1;
    int count = 0;
    n = std::abs(n);
    while (n > 0) {
        count++;
        n /= 10;
    }
    return count;
}

// Sum of digits
int digitSum(int n) {
    int sum = 0;
    n = std::abs(n);
    while (n > 0) {
        sum += n % 10;
        n /= 10;
    }
    return sum;
}

// Reverse number (with overflow check)
int reverseNumber(int n) {
    int rev = 0;
    while (n != 0) {
        int pop = n % 10;
        n /= 10;
        if (rev > INT_MAX/10 || (rev == INT_MAX/10 && pop > 7)) return 0;
        if (rev < INT_MIN/10 || (rev == INT_MIN/10 && pop < -8)) return 0;
        rev = rev * 10 + pop;
    }
    return rev;
}

// Palindrome check
bool isPalindrome(int n) {
    if (n < 0) return false;
    return n == reverseNumber(n);
}
```

---

## 6. Armstrong and Perfect Numbers
- **Armstrong Number:** Sum of digits raised to the power of number of digits equals the number itself.
- **Perfect Number:** Equal to the sum of its positive proper divisors (excluding itself).

```cpp
#include <cmath>

bool isArmstrong(int n) {
    if (n < 0) return false;
    int numDigits = countDigits(n);
    int sum = 0, temp = n;
    while (temp > 0) {
        sum += std::pow(temp % 10, numDigits);
        temp /= 10;
    }
    return sum == n;
}

bool isPerfect(int n) {
    if (n <= 1) return false;
    int sum = 1;
    for (int i = 2; i * i <= n; ++i) {
        if (n % i == 0) {
            sum += i;
            if (i * i != n) sum += n / i;
        }
    }
    return sum == n;
}
```

---

## 7. Missing Number
Find the missing number in an array containing numbers from $0$ to $n$.
$\text{Sum}(0..n) = \frac{n(n+1)}{2}$. Sum elements and subtract from formula value.

```cpp
#include <vector>

int missingNumber(const std::vector<int>& nums) {
    int n = nums.size();
    long long expectedSum = (long long)n * (n + 1) / 2;
    long long actualSum = 0;
    for (int num : nums) actualSum += num;
    return expectedSum - actualSum;
}
```

---

## 8. Pascal's Triangle
Generates Pascal's triangle coefficients where element at $(r, c)$ is $C(r, c)$.

```cpp
#include <vector>

std::vector<std::vector<int>> generatePascal(int numRows) {
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
```
