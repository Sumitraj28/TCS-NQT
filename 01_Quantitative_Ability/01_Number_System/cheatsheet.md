# Number System — Cheat Sheet

## Summary Table

| Category | Formula / Theorem | Key Concept |
|----------|-------------------|-------------|
| HCF & LCM relation | $\text{HCF} \times \text{LCM} = A \times B$ | Product of two integers |
| Fractions HCF | $\text{HCF(Num)} / \text{LCM(Den)}$ | HCF of fractions |
| Fractions LCM | $\text{LCM(Num)} / \text{HCF(Den)}$ | LCM of fractions |
| Number of Factors | $\prod (a_i + 1)$ | Exponent combinations |
| Sum of Factors | $\prod \frac{p_i^{a_i+1}-1}{p_i-1}$ | Divisor sum |
| Trailing Zeros | $\sum \lfloor N/5^k \rfloor$ | Prime factor 5 count |
| Cyclicity periodicity | $N \bmod 4$ | Exponent cycles (1, 2, or 4) |

## Quick Modulo Properties
- $(A \times B) \bmod M = ((A \bmod M) \times (B \bmod M)) \bmod M$
- If $A \equiv -1 \pmod M$, then $A^k \equiv (-1)^k \pmod M$.
