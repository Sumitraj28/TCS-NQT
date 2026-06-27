# Number System — Common Mistakes

## 1. Cyclicity remainder of 0
**Mistake:** Stating that the last digit is $X^0 = 1$ when $Y \bmod 4 == 0$ in unit digit calculation.
**Fix:** Treat a remainder of 0 as a power exponent of **4**.

---

## 2. Using fractions formula backwards
**Mistake:** Using $\text{HCF} = \frac{\text{LCM of Numerators}}{\text{HCF of Denominators}}$ for HCF of fractions.
**Fix:**
- HCF of Fractions = $\frac{\text{HCF of Numerators}}{\text{LCM of Denominators}}$
- LCM of Fractions = $\frac{\text{LCM of Numerators}}{\text{HCF of Denominators}}$

---

## 3. Negative remainder modulations
**Mistake:** Retaining negative remainder answers (e.g. $-3 \bmod 7 = -3$).
**Fix:** Add modulo base divisor to get standard positive remainder values (e.g. $-3 + 7 = 4$).
