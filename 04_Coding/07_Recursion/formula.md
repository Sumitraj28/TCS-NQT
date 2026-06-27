# Recursion — Formulas and Relations

## 1. Fibonacci Recurrence
- Recurrence relation:
  $$F(n) = F(n-1) + F(n-2) \quad \text{for } n \geq 2$$
- Base cases: $F(0) = 0$, $F(1) = 1$.
- Closed-form (Binet's Formula):
  $$F(n) = \frac{\phi^n - \psi^n}{\sqrt{5}}$$
  where $\phi = \frac{1 + \sqrt{5}}{2} \approx 1.618$ and $\psi = \frac{1 - \sqrt{5}}{2} \approx -0.618$.
- Time complexity: $O(2^N)$ for standard recursion.

---

## 2. Factorial Recurrence
- Recurrence relation:
  $$T(n) = T(n-1) + O(1) \quad \text{where } F(n) = n \times F(n-1)$$
- Base case: $F(0) = 1$.
- Time complexity: $O(N)$ for recursion.

---

## 3. Tower of Hanoi Moves
- Recurrence relation:
  $$T(n) = 2T(n-1) + 1$$
- Base case: $T(0) = 0$, $T(1) = 1$.
- Closed-form solution:
  $$T(n) = 2^n - 1$$
- Time complexity: $O(2^N)$ for moves printing.
