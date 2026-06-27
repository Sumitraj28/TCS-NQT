# Number System — Practice: Medium (15 Questions)

---

### Q1 — Divisibility by 11
Find the value of $X$ so that the number $5X74$ is divisible by 11.
**Answer:**
- Sum of odd position digits (from right): $4 + X$.
- Sum of even position digits: $7 + 5 = 12$.
- Difference: $|(4+X) - 12| = 0 \rightarrow X = 8$. (Or $|4+X - 12| = 11 \rightarrow X = 19$ (not possible)).
- Target: $X = 8$.

---

### Q2 — Unit Digit of Power
Find the last digit of $28^{67}$.
**Answer:**
- Base unit digit is 8.
- Power: $67 \bmod 4 = 3$.
- $8^3 = 512 \rightarrow$ last digit is **2**.

---

### Q3 — Trailing Zeros in 100!
Find trailing zeros in $100!$.
**Answer:** $\lfloor 100/5 \rfloor + \lfloor 100/25 \rfloor = 20 + 4 = 24$.

---

### Q4 — HCF of Fractions
Find HCF of $\frac{2}{3}, \frac{8}{9}, \frac{16}{81}$.
**Answer:**
$$\text{HCF} = \frac{\text{HCF}(2, 8, 16)}{\text{LCM}(3, 9, 81)} = \frac{2}{81}$$

---

### Q5 — Number of Factors
Find total number of factors of $180$.
**Answer:**
$180 = 2^2 \times 3^2 \times 5^1 \rightarrow F(180) = (2+1)(2+1)(1+1) = 3 \times 3 \times 2 = 18$ factors.

---

### Q6 — Product of Factors
Find product of all factors of $120$.
**Answer:**
- $120 = 2^3 \times 3^1 \times 5^1 \rightarrow F(120) = (3+1)(1+1)(1+1) = 16$ factors.
- Product $= 120^{16/2} = 120^8$.

---

### Q7 — Remainder with Large Power
Find the remainder when $2^{99}$ is divided by 10.
**Answer:** This is equivalent to finding the last digit of $2^{99}$.
- $99 \bmod 4 = 3$.
- $2^3 = 8$. Remainder is **8**.

---

### Q8 — Base Conversion
Convert decimal 250 to octal base.
**Answer:**
- $250 / 8 = 31$ remainder 2.
- $31 / 8 = 3$ remainder 7.
- $3 / 8 = 0$ remainder 3.
- Reading remainders upwards: $372_8$.

---

### Q9 — Prime Factors
How many distinct prime factors does $210$ have?
**Answer:** $210 = 2 \times 3 \times 5 \times 7 \rightarrow$ 4 distinct prime factors.

---

### Q10 — Remainder of Multiplication Sum
Find remainder when $1421 \times 1423 \times 1425$ is divided by 12.
**Answer:**
- $1421 \bmod 12 = 5$
- $1423 \bmod 12 = 7$
- $1425 \bmod 12 = 9$
- Combined remainder: $(5 \times 7 \times 9) \bmod 12 = 315 \bmod 12 = 3$.

---

### Q11 — Find least number divisible by 12, 15, 20
**Answer:**
LCM of 12, 15, 20:
- $12 = 2^2 \times 3$
- $15 = 3 \times 5$
- $20 = 2^2 \times 5$
- $\text{LCM} = 2^2 \times 3 \times 5 = 60$.

---

### Q12 — Coprime pair count
Which of the following are coprime pairs: (14, 35) or (18, 35)?
**Answer:** (18, 35) because $\text{HCF}(18, 35) = 1$, whereas $\text{HCF}(14, 35) = 7$.

---

### Q13 — Sum of Factors
Find sum of factors of 36.
**Answer:**
- $36 = 2^2 \times 3^2$.
- Sum $= (2^0 + 2^1 + 2^2)(3^0 + 3^1 + 3^2) = (1+2+4)(1+3+9) = 7 \times 13 = 91$.

---

### Q14 — Division remainder
A number when divided by 5 leaves a remainder of 3. What remainder is left when the square of that number is divided by 5?
**Answer:**
- Let number be $N \equiv 3 \pmod 5$.
- $N^2 \equiv 3^2 = 9 \equiv 4 \pmod 5$. Remainder is **4**.

---

### Q15 — Base Conversion to Decimal
Convert hex `2B` to decimal.
**Answer:** $2 \times 16^1 + 11 \times 16^0 = 32 + 11 = 43$.
