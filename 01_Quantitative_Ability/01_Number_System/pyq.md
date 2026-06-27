# Number System — Previous Year Questions (TCS NQT)

---

### PYQ1 — Digit Sum & Divisibility
**Difficulty:** Easy | **Time:** 60s | **TCS Frequency:** High
Find the value of $P$ for which $78P39$ is divisible by 9.
**Answer:** Sum of digits $= 7 + 8 + P + 3 + 9 = 27 + P$.
For $27 + P$ to be divisible by 9, $P$ must be $0$ or $9$. (Usually only one option is provided in the choices).

---

### PYQ2 — Remainder Problem
**Difficulty:** Medium | **Time:** 75s | **TCS Frequency:** High
Find the remainder when $2^{31}$ is divided by 5.
**Answer:**
- $2^1 \equiv 2, 2^2 \equiv 4, 2^3 \equiv 3, 2^4 \equiv 1 \pmod 5$ (cyclicity of 4).
- $31 \bmod 4 = 3$.
- Remainder is $2^3 \bmod 5 = 3$.

---

### PYQ3 — Trailing Zeros
**Difficulty:** Easy | **Time:** 45s | **TCS Frequency:** High
Find trailing zeros in $125!$.
**Answer:** $\lfloor 125/5 \rfloor + \lfloor 125/25 \rfloor + \lfloor 125/125 \rfloor = 25 + 5 + 1 = 31$ zeros.

---

### PYQ4 — Octal to Hexadecimal conversion
**Difficulty:** Medium | **Time:** 75s | **TCS Frequency:** Medium
Convert octal $237_8$ to hexadecimal.
**Answer:**
1. Octal to Binary: $2 \rightarrow 010$, $3 \rightarrow 011$, $7 \rightarrow 111 \rightarrow 010011111_2$.
2. Group into 4-bit nibbles from right:
   - `1111` $\rightarrow$ F
   - `1001` $\rightarrow$ 9
   - `0000` $\rightarrow$ 0
3. Hexadecimal value is $9\text{F}_{16}$.

---

### PYQ5 — LCM of fractions word problem
**Difficulty:** Medium | **Time:** 90s | **TCS Frequency:** High
Three bells toll at intervals of $\frac{2}{3}$ min, $\frac{3}{5}$ min, and $\frac{4}{7}$ min respectively. If they toll together now, after what time interval will they toll together next?
**Answer:**
LCM of fractions:
$$\text{LCM} = \frac{\text{LCM}(2, 3, 4)}{\text{HCF}(3, 5, 7)} = \frac{12}{1} = 12 \text{ minutes}$$
They will toll together next after 12 minutes.
