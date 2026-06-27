# Number System — Complete Notes

---

## 1. Classification of Numbers
- **Natural Numbers ($\mathbb{N}$):** $1, 2, 3, \dots$
- **Whole Numbers ($\mathbb{W}$):** $0, 1, 2, \dots$
- **Integers ($\mathbb{Z}$):** $\dots, -2, -1, 0, 1, 2, \dots$
- **Prime Numbers:** Numbers $> 1$ with only two factors (1 and itself).
- **Composite Numbers:** Numbers $> 1$ with more than two factors.

---

## 2. Divisibility Rules

- **Divisibility by 2:** The last digit must be even ($0, 2, 4, 6, 8$).
- **Divisibility by 3:** The sum of all digits must be divisible by 3.
  - *Example:* $375 \rightarrow 3+7+5 = 15$ (divisible by 3).
- **Divisibility by 4:** The number formed by the last two digits must be divisible by 4.
  - *Example:* $1424 \rightarrow 24$ (divisible by 4).
- **Divisibility by 5:** The last digit must be either $0$ or $5$.
- **Divisibility by 6:** The number must be divisible by both 2 and 3.
- **Divisibility by 8:** The number formed by the last three digits must be divisible by 8.
  - *Example:* $3120 \rightarrow 120$ (divisible by 8).
- **Divisibility by 9:** The sum of all digits must be divisible by 9.
  - *Example:* $981 \rightarrow 9+8+1 = 18$ (divisible by 9).
- **Divisibility by 11:** The absolute difference between the sum of digits at odd positions and the sum of digits at even positions must be either $0$ or a multiple of 11.
  - *Example:* $121 \rightarrow (1+1) - (2) = 0$ (divisible by 11).

---

## 3. Remainders & Modular Arithmetic
When $a$ is divided by $m$, the remainder $r$ satisfies $0 \leq r < m$, denoted as $a \equiv r \pmod m$.

### Rules of Modular Arithmetic
1. **Addition Rule:**
   $$(A + B) \bmod M = ((A \bmod M) + (B \bmod M)) \bmod M$$
2. **Multiplication Rule:**
   $$(A \times B) \bmod M = ((A \bmod M) \times (B \bmod M)) \bmod M$$
3. **Power Rule:**
   $$(A^B) \bmod M = ((A \bmod M)^B) \bmod M$$

---

## 4. Cyclicity of Last Digits
The last digit of $X^Y$ repeats in a periodic cycle of length at most 4.

| Unit Digit of Base | Cyclicity Cycle | Cycle Length |
|--------------------|-----------------|--------------|
| 0, 1, 5, 6 | Same digit always | 1 |
| 4 | $4, 6, 4, 6 \dots$ | 2 |
| 9 | $9, 1, 9, 1 \dots$ | 2 |
| 2 | $2, 4, 8, 6, 2 \dots$ | 4 |
| 3 | $3, 9, 7, 1, 3 \dots$ | 4 |
| 7 | $7, 9, 3, 1, 7 \dots$ | 4 |
| 8 | $8, 4, 2, 6, 8 \dots$ | 4 |

### Calculation Steps
1. Find the remainder $r = Y \bmod 4$. If $r = 0$, treat it as power of 4.
2. Find the last digit of $\text{Base}^r$. This matches the last digit of $X^Y$.
   - *Example:* Last digit of $23^{35}$?
     - Unit digit of base is 3. Power is 35.
     - $35 \bmod 4 = 3$.
     - $3^3 = 27$. Unit digit is **7**.

---

## 5. LCM and HCF

### HCF (Highest Common Factor / GCD)
1. **Prime Factorization Method:** Find prime factorization of numbers. HCF is the product of the lowest power of all common prime factors.
   - *Example:* HCF of 12 and 18:
     $12 = 2^2 \times 3^1$, $18 = 2^1 \times 3^2$
     $\text{HCF} = 2^1 \times 3^1 = 6$.
2. **Division Method (Euclidean):** Divide the larger number by the smaller one. Then divide the previous divisor by the remainder. Repeat until the remainder is 0. The last divisor is the HCF.

### LCM (Least Common Multiple)
1. **Prime Factorization Method:** Product of the highest power of all prime factors involved.
   - *Example:* LCM of 12 and 18:
     $\text{LCM} = 2^2 \times 3^2 = 36$.
2. **Common Division Method:** Write numbers in a row, divide by prime numbers until all numbers become 1. Multiply the divisors.

---

## 6. Factors & Prime Factorization
Every composite number $N$ can be uniquely expressed as:
$$N = p_1^{a_1} \times p_2^{a_2} \times \dots \times p_k^{a_k}$$
where $p_i$ are distinct prime numbers.

### Formulas
- **Number of Factors:**
  $$F(N) = (a_1 + 1)(a_2 + 1)\dots(a_k + 1)$$
- **Sum of Factors:**
  $$S(N) = \left(\frac{p_1^{a_1+1}-1}{p_1-1}\right) \times \left(\frac{p_2^{a_2+1}-1}{p_2-1}\right) \dots$$
- **Product of Factors:**
  $$P(N) = N^{\frac{F(N)}{2}}$$

---

## 7. Trailing Zeros in a Factorial
The number of trailing zeros in $N!$ is determined by the exponent of prime factor 5 in $N!$, calculated using **Legendre's Formula**:
$$\text{Trailing Zeros} = \lfloor N/5 \rfloor + \lfloor N/25 \rfloor + \lfloor N/125 \rfloor + \dots$$
- *Example:* Trailing zeros in $100!$:
  $\lfloor 100/5 \rfloor + \lfloor 100/25 \rfloor = 20 + 4 = 24$.

---

## 8. Base Conversion Basics
- **Decimal to Base B:** Divide by $B$ repeatedly, recording remainders from bottom to top.
- **Base B to Decimal:** Multiply each digit by $B^p$ where $p$ is the positional index from the right (0-indexed).
  - *Example:* Binary `1101` to Decimal:
    $1 \times 2^3 + 1 \times 2^2 + 0 \times 2^1 + 1 \times 2^0 = 8 + 4 + 0 + 1 = 13$.
