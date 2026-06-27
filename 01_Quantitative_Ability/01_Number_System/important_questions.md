# Number System — Top 20 Important TCS NQT-Style Questions

---

### IQ1 — Check divisibility of a number by 11.
**Answer:** Absolute difference between sum of digits at odd and even positions is 0 or a multiple of 11.

---

### IQ2 — Find the last digit of $34^{56}$.
**Answer:** Base is 4. Power $56 \bmod 4 = 0 \rightarrow$ use exponent 4. Last digit of $4^4 = 256 \rightarrow$ unit digit is **6**.

---

### IQ3 — Count factors of 240.
**Answer:** $240 = 2^4 \times 3^1 \times 5^1 \rightarrow F(240) = 5 \times 2 \times 2 = 20$.

---

### IQ4 — Find the number of trailing zeros in $80!$.
**Answer:** $\lfloor 80/5 \rfloor + \lfloor 80/25 \rfloor = 16 + 3 = 19$.

---

### IQ5 — Find HCF of $\frac{3}{4}$ and $\frac{6}{7}$.
**Answer:** $\frac{\text{HCF}(3, 6)}{\text{LCM}(4, 7)} = \frac{3}{28}$.

---

### IQ6 — Find LCM of $\frac{2}{3}$ and $\frac{4}{5}$.
**Answer:** $\frac{\text{LCM}(2, 4)}{\text{HCF}(3, 5)} = \frac{4}{1} = 4$.

---

### IQ7 — Find the remainder when $17^{200}$ is divided by 18.
**Answer:** $17 \equiv -1 \pmod{18}$. Therefore, $17^{200} \equiv (-1)^{200} = 1 \pmod{18}$. Remainder is **1**.

---

### IQ8 — Convert binary `11101` to decimal.
**Answer:** $16 + 8 + 4 + 1 = 29$.

---

### IQ9 — Convert octal `75` to binary.
**Answer:** Replace digits: $7 \rightarrow 111$, $5 \rightarrow 101 \rightarrow 111101_2$.

---

### IQ10 — If HCF of two numbers is 8 and LCM is 48, and one number is 16, find the other.
**Answer:** $\frac{H \times L}{A} = \frac{8 \times 48}{16} = 24$.

---

### IQ11 — Find sum of all factors of 45.
**Answer:** $45 = 3^2 \times 5^1 \rightarrow (1+3+9)(1+5) = 13 \times 6 = 78$.

---

### IQ12 — Find the product of all factors of 24.
**Answer:** $24 = 2^3 \times 3^1 \rightarrow F(24) = 8$. Product $= 24^{8/2} = 24^4$.

---

### IQ13 — Is 509 a prime number?
**Answer:** Yes. $\sqrt{509} \approx 22.5$. Check prime divisors up to 19: none divide 509.

---

### IQ14 — If a number leaves remainder 4 when divided by 7, what is the remainder when its triple is divided by 7?
**Answer:** $(4 \times 3) \bmod 7 = 12 \bmod 7 = 5$.

---

### IQ15 — Find base $x$ if $13_x \times 12_x = 216_x$.
**Answer:** $(x + 3)(x + 2) = 2x^2 + x + 6 \rightarrow x^2 + 5x + 6 = 2x^2 + x + 6 \rightarrow x^2 - 4x = 0 \rightarrow x = 4$. Base is **4**.

---

### IQ16 — Find number of prime factors of $30^5$.
**Answer:** $30^5 = (2 \times 3 \times 5)^5 = 2^5 \times 3^5 \times 5^5 \rightarrow$ 3 distinct prime factors.

---

### IQ17 — Find the remainder of $5^{99} \bmod 7$.
**Answer:** $5^1 \equiv 5, 5^2 \equiv 4, 5^3 \equiv 6, 5^4 \equiv 2, 5^5 \equiv 3, 5^6 \equiv 1 \pmod 7$.
- Power $99 \bmod 6 = 3$.
- Remainder is $5^3 \bmod 7 = 6$.

---

### IQ18 — Find HCF of $3^3 \times 5^2$ and $3^2 \times 5^4$.
**Answer:** $3^{\min(3,2)} \times 5^{\min(2,4)} = 3^2 \times 5^2 = 9 \times 25 = 225$.

---

### IQ19 — Find LCM of $2^4 \times 7^2$ and $2^2 \times 7^3$.
**Answer:** $2^{\max(4,2)} \times 7^{\max(2,3)} = 2^4 \times 7^3$.

---

### IQ20 — How many trailing zeros are in $1000!$?
**Answer:** $\lfloor 1000/5 \rfloor + \lfloor 1000/25 \rfloor + \lfloor 1000/125 \rfloor + \lfloor 1000/625 \rfloor = 200 + 40 + 8 + 1 = 249$.
