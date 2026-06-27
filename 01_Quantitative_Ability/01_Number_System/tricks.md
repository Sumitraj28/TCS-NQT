# Number System — Tricks, Traps, and TCS Patterns

## Trap 1 — Neglecting Modulo Cycle boundary
**The trap:** In cyclicity problems, when power is exactly divisible by 4 (i.e. $Y \bmod 4 == 0$), substituting power as 0 gives $X^0 = 1$, which is incorrect.

**Fix:** If $Y \bmod 4 == 0$, treat the power exponent as **4** instead of 0.
- *Example:* Find unit digit of $2^8$.
  - $8 \bmod 4 = 0 \rightarrow$ use power 4.
  - $2^4 = 16 \rightarrow$ unit digit is **6**. (Using power 0 would give $2^0 = 1$, which is wrong).

---

## Trap 2 — Factor Count for Perfect Squares
**The trap:** A perfect square has an odd number of factors. If a question asks to write $N$ as a product of two factors, the formula is:
- If $N$ is not a perfect square: $\frac{F(N)}{2}$
- If $N$ is a perfect square: $\frac{F(N) + 1}{2}$ (if factors can be identical) or $\frac{F(N) - 1}{2}$ (if distinct).

---

## Trap 3 — Trailing Zeros count base
**The trap:** Assuming trailing zeros is just $N/5$. For large factorials, powers like $5^2$ (25) contribute an extra factor of 5, which must be added.

**Fix:** Always use Legendre's summation: $\lfloor N/5 \rfloor + \lfloor N/25 \rfloor + \lfloor N/125 \rfloor \dots$
