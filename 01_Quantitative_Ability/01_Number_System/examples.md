# Number System — Worked Examples

---

## Example 1 — Divisibility Check by 11

**Problem:** Is $85976$ divisible by 11?

**Trace:**
1. Sum of digits at odd positions (from right, 1-indexed):
   - 1st digit: 6
   - 3rd digit: 9
   - 5th digit: 8
   - Sum = $6 + 9 + 8 = 23$.
2. Sum of digits at even positions:
   - 2nd digit: 7
   - 4th digit: 5
   - Sum = $7 + 5 = 12$.
3. Difference = $|23 - 12| = 11$.
4. Since 11 is divisible by 11, the number 85976 is divisible by 11.

---

## Example 2 — Cyclicity of Last Digit

**Problem:** Find the last digit of $37^{122}$.

**Trace:**
1. Base unit digit is 7.
2. Power is 122.
3. Calculate power modulo 4: $122 \bmod 4 = 2$.
4. Calculate $7^2 = 49$.
5. The last digit is **9**.

---

## Example 3 — Finding Number of Factors

**Problem:** Find the number of factors of 360.

**Trace:**
1. Prime factorization of 360:
   $$360 = 2^3 \times 3^2 \times 5^1$$
2. Number of factors formula:
   $$F(360) = (3 + 1)(2 + 1)(1 + 1) = 4 \times 3 \times 2 = 24 \text{ factors}$$

---

## Example 4 — Trailing Zeros in $50!$

**Problem:** How many trailing zeros are in $50!$?

**Trace:**
1. $\lfloor 50/5 \rfloor = 10$
2. $\lfloor 50/25 \rfloor = 2$
3. $\lfloor 50/125 \rfloor = 0$
4. Total trailing zeros = $10 + 2 = 12$.
