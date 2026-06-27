# Math — Practice: Basic (15 Questions)

---

### Q1 — Factorial of a Number
Calculate factorial of $N$.
**Answer:** $N! = 1 \times 2 \times 3 \times \dots \times N$.
```cpp
long long factorial(int n) {
    long long fact = 1;
    for (int i = 2; i <= n; ++i) fact *= i;
    return fact;
}
```

---

### Q2 — Check If Number Is Even
Check if a number is even.
**Answer:** `n % 2 == 0` or bitwise `(n & 1) == 0`.

---

### Q3 — Count Digits in Integer
**Answer:** Divide by 10 repeatedly until the number becomes 0.
```cpp
int count(int n) {
    int c = 0;
    while (n > 0) { c++; n /= 10; }
    return c;
}
```

---

### Q4 — Sum of First N Natural Numbers
**Answer:** $\frac{N(N+1)}{2}$.

---

### Q5 — GCD of Two Numbers
**Answer:** Use Euclidean division:
```cpp
int gcd(int a, int b) {
    return b == 0 ? a : gcd(b, a % b);
}
```

---

### Q6 — LCM of Two Numbers
**Answer:** `(a / gcd(a, b)) * b`.

---

### Q7 — Armstrong Number (3 digits)
**Answer:** Check if sum of cubes of digits is equal to the number.
```cpp
bool isArmstrong3(int n) {
    int sum = 0, temp = n;
    while (temp > 0) {
        int d = temp % 10;
        sum += d * d * d;
        temp /= 10;
    }
    return sum == n;
}
```

---

### Q8 — Absolute Value
How to find the absolute value of $X$ without using `abs()`?
**Answer:** `x < 0 ? -x : x`.

---

### Q9 — Swap Two Numbers Without Third Variable
**Answer:**
```cpp
a = a ^ b;
b = a ^ b;
a = a ^ b;
```

---

### Q10 — Leap Year Check
**Answer:**
```cpp
bool isLeap(int year) {
    return (year % 4 == 0 && year % 100 != 0) || (year % 400 == 0);
}
```

---

### Q11 — Power of Two Check (Loops)
**Answer:**
```cpp
bool isPowerOfTwo(int n) {
    if (n <= 0) return false;
    while (n % 2 == 0) n /= 2;
    return n == 1;
}
```

---

### Q12 — Add Digits Loop
Sum digits of a number once.
**Answer:**
```cpp
int getSum(int n) {
    int sum = 0;
    while (n > 0) { sum += n % 10; n /= 10; }
    return sum;
}
```

---

### Q13 — Decimal to Binary
Convert number to binary representation.
**Answer:**
```cpp
std::string toBinary(int n) {
    std::string s = "";
    while (n > 0) {
        s = std::to_string(n % 2) + s;
        n /= 2;
    }
    return s.empty() ? "0" : s;
}
```

---

### Q14 — Reverse Number (Basic)
Reverse number ignoring overflow.
**Answer:**
```cpp
int reverse(int n) {
    int rev = 0;
    while (n > 0) { rev = rev * 10 + n % 10; n /= 10; }
    return rev;
}
```

---

### Q15 — Perfect Square Check
Check if a number is a perfect square.
**Answer:**
```cpp
bool isSquare(int n) {
    int s = std::sqrt(n);
    return s * s == n;
}
```
