# Math — Formulas and Theorems

## 1. Prime Numbers
- **Prime Number Density (Prime Number Theorem):** The number of primes less than or equal to $N$ is approximately $\frac{N}{\ln N}$.
- **Sieve of Eratosthenes Complexity:** Time complexity is $O(N \log \log N)$.

---

## 2. GCD & LCM
- **Fundamental Formula:**
  $$\text{GCD}(a, b) \times \text{LCM}(a, b) = |a \times b|$$
- **Euclidean Algorithm (Subtraction version):**
  $$\text{GCD}(a, b) = \text{GCD}(a - b, b) \quad \text{for } a > b$$
- **Euclidean Algorithm (Modulo version):**
  $$\text{GCD}(a, b) = \text{GCD}(b, a \bmod b)$$

---

## 3. Divisors & Divisibility
- **Number of Divisors:** If prime factorization of $N = p_1^{a_1} \times p_2^{a_2} \times \dots$, then total divisors count is:
  $$d(N) = (a_1 + 1)(a_2 + 1)\dots$$
- **Sum of Divisors:**
  $$\sigma(N) = \frac{p_1^{a_1+1}-1}{p_1-1} \times \frac{p_2^{a_2+1}-1}{p_2-1} \dots$$

---

## 4. Arithmetic Sums
- **Sum of first $n$ natural numbers:**
  $$\sum_{i=1}^n i = \frac{n(n+1)}{2}$$
- **Sum of first $n$ odd numbers:**
  $$\sum_{i=1}^n (2i-1) = n^2$$
- **Sum of first $n$ squares:**
  $$\sum_{i=1}^n i^2 = \frac{n(n+1)(2n+1)}{6}$$

---

## 5. Modular Arithmetic Rules
- Addition: $(a + b) \bmod m = ((a \bmod m) + (b \bmod m)) \bmod m$
- Subtraction: $(a - b) \bmod m = ((a \bmod m) - (b \bmod m) + m) \bmod m$
- Multiplication: $(a \times b) \bmod m = ((a \bmod m) \times (b \bmod m)) \bmod m$
- Modular Exponentiation: $(a^b) \bmod m$ can be computed in $O(\log b)$ time.
