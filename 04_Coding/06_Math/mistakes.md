# Math — Common Mistakes

## 1. Prime Check Loops Starting from 1
**Mistake:** Starting the loop at index 1: `for (int i = 1; i * i <= n; i++)`. This will mark every number as composite since $N \bmod 1 == 0$.
**Fix:** Loop must start at 2.

---

## 2. Integer Overflow in LCM
**Mistake:** Calculating LCM using: `int lcm = (a * b) / gcd(a, b);`. If $a$ and $b$ are large, the multiplication `a * b` will overflow before the division.
**Fix:** Divide first: `int lcm = (a / gcd(a, b)) * b;`.

---

## 3. Negative Modulo Outcomes
**Mistake:** Expecting `(a - b) % m` to always yield positive values.
**Fix:** Add $m$ before the final modulo: `(a - b % m + m) % m`.

---

## 4. Wrong Sieve Bounds
**Mistake:** Running the Sieve outer loop up to $N$ instead of $\sqrt{N}$. While correct, it performs unnecessary operations and decreases speed.
**Fix:** Loop up to `i * i < n` or `i * i <= limit`.
