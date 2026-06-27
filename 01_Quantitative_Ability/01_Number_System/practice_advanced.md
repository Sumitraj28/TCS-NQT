# Number System — Practice: Advanced (10 Questions)

---

### Q1 — Chinese Remainder Theorem basics
Find the smallest number that leaves a remainder of 2 when divided by 3, and a remainder of 3 when divided by 5.
**Answer:**
- $N \equiv 2 \pmod 3 \rightarrow N \in \{2, 5, 8, 11, 14 \dots\}$
- $N \equiv 3 \pmod 5 \rightarrow N \in \{3, 8, 13 \dots\}$
- Smallest common value is **8**.
- General solution: $8 + 15k$ for integer $k$.

---

### Q2 — Euler's Totient Theorem for Remainders
Find the remainder when $3^{100}$ is divided by 10.
**Answer:**
- $\phi(10) = 10 \times (1 - 1/2) \times (1 - 1/5) = 4$.
- Since HCF(3, 10) = 1, by Euler's Theorem: $3^4 \equiv 1 \pmod{10}$.
- $3^{100} = (3^4)^{25} \equiv 1^{25} \equiv 1 \pmod{10}$. Remainder is **1**.

---

### Q3 — Divisibility range
How many numbers between 100 and 300 are divisible by both 4 and 6?
**Answer:**
- Divisible by both 4 and 6 $\rightarrow$ divisible by $\text{LCM}(4, 6) = 12$.
- First term $\ge 100$: 108.
- Last term $\le 300$: 300.
- Count $N$ in Arithmetic Progression: $300 = 108 + (N - 1)12 \rightarrow 192 = (N-1)12 \rightarrow N-1 = 16 \rightarrow N = 17$.

---

### Q4 — Perfect Square Factors
Find the number of factors of 3600 that are perfect squares.
**Answer:**
- $3600 = 2^4 \times 3^2 \times 5^2$.
- For a factor to be a perfect square, all exponents in its prime factorization must be even:
  - Exponent of 2 can be chosen from $\{0, 2, 4\}$ (3 choices).
  - Exponent of 3 can be chosen from $\{0, 2\}$ (2 choices).
  - Exponent of 5 can be chosen from $\{0, 2\}$ (2 choices).
- Total perfect square factors = $3 \times 2 \times 2 = 12$.

---

### Q5 — Finding Last Two Digits
Find the last two digits of $2^{100}$.
**Answer:**
- This is equivalent to finding $2^{100} \bmod 100$.
- Note: $2^{10} = 1024 \equiv 24 \pmod{100}$.
- $2^{20} = (2^{10})^2 \equiv 24^2 = 576 \equiv 76 \pmod{100}$.
- Note: Any power of 76 ends in 76 (i.e. $76^k \equiv 76 \pmod{100}$).
- $2^{100} = (2^{20})^5 \equiv 76^5 \equiv 76 \pmod{100}$.
- Last two digits are **76**.

---

### Q6 — Trailing Zeros in base 12
Find trailing zeros of $50!$ in base 12.
**Answer:**
- $12 = 2^2 \times 3^1$. The number of zeros is determined by the limiting factor, which is either 3 or 4 ($2^2$).
- Exponent of 3 in $50!$:
  $\lfloor 50/3 \rfloor + \lfloor 50/9 \rfloor + \lfloor 50/27 \rfloor = 16 + 5 + 1 = 22$.
- Exponent of 2 in $50!$:
  $\lfloor 50/2 --> 25 \rfloor + \lfloor 50/4 --> 12 \rfloor + \lfloor 50/8 --> 6 \rfloor + \lfloor 50/16 --> 3 \rfloor + \lfloor 50/32 --> 1 \rfloor = 47$.
  - Exponent of $2^2$: $\lfloor 47/2 \rfloor = 23$.
- Limiting value is 22. Trailing zeros count is **22**.

---

### Q7 — GCD of large integers
If $a = 2^{30} - 1$ and $b = 2^{45} - 1$, find HCF(a, b).
**Answer:**
Use the property: $\text{HCF}(x^m - 1, x^n - 1) = x^{\text{HCF}(m, n)} - 1$.
$$\text{HCF}(2^{30} - 1, 2^{45} - 1) = 2^{\text{HCF}(30, 45)} - 1 = 2^{15} - 1$$

---

### Q8 — Base Conversion Sums
If $123_x + 45_x = 171_x$, find base $x$.
**Answer:**
- Expand terms: $(x^2 + 2x + 3) + (4x + 5) = x^2 + 7x + 1$
- $x^2 + 6x + 8 = x^2 + 7x + 1 \rightarrow x = 7$.
- Base is **7**.

---

### Q9 — Number of Coprime values less than N
Find the number of integers less than 100 that are coprime to 100.
**Answer:**
Euler's Totient function $\phi(100) = 100 \times (1 - 1/2) \times (1 - 1/5) = 100 \times 1/2 \times 4/5 = 40$.

---

### Q10 — Sum of Odd Factors
Find the sum of odd factors of 120.
**Answer:**
- $120 = 2^3 \times 3^1 \times 5^1$.
- To get odd factors, exclude all factors containing powers of 2 (i.e. only use $2^0$).
- Sum $= 2^0 \times (3^0 + 3^1)(5^0 + 5^1) = 1 \times (1+3)(1+5) = 4 \times 6 = 24$.
