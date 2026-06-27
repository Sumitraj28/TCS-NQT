# Recursion — Shortcuts & Recursion-to-Iteration Rules

## 1. Tail Recursion Optimization
If the recursive call is the last statement executed inside the function, the compiler can reuse the current stack frame.
Example of tail-recursive factorial (accumulators):
```cpp
long long tailFactorial(int n, long long accumulator = 1) {
    if (n <= 1) return accumulator;
    return tailFactorial(n - 1, n * accumulator);
}
```

---

## 2. Fast Fibonacci Matrix Exponentiation
Instead of recursive $O(2^N)$ or dynamic programming $O(N)$, Fibonacci can be calculated in $O(\log N)$ using:
$$\begin{pmatrix} F(n+1) & F(n) \\ F(n) & F(n-1) \end{pmatrix} = \begin{pmatrix} 1 & 1 \\ 1 & 0 \end{pmatrix}^n$$

---

## 3. Digit Sum In Recursion
We can sum digits without loop variables by returning `n % 10 + digitSum(n / 10)` which naturally processes right-to-left.
