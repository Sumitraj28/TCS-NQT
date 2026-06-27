# Math — Shortcuts & Calculation Speedups

## 1. Fast Digit Extraction
Instead of string conversions, use mathematical modulo and division loops:
- Last digit: `n % 10`
- Remove last digit: `n /= 10`
- This is roughly 10x faster than `std::to_string(n)`.

---

## 2. Check for Power of 2
Instead of loops, use bitwise AND:
```cpp
bool isPowerOfTwo = (n > 0) && ((n & (n - 1)) == 0);
```

---

## 3. Modular Subtraction Shortcut
To avoid negative results in modular subtraction:
```cpp
int diff = (a - b) % MOD;
if (diff < 0) diff += MOD;
```
Better: `int diff = (a - b % MOD + MOD) % MOD;`

---

## 4. Integer Square Root Check
To check if a number is a perfect square without floating point rounding errors:
```cpp
long long sq = std::sqrt(n);
bool isPerfectSquare = (sq * sq == n);
```

---

## 5. Division by Modulo
To compute $(a / b) \bmod m$, we cannot do $(a \bmod m) / (b \bmod m)$. Instead, we use Fermat's Little Theorem (when $m$ is prime):
$$b^{-1} \equiv b^{m-2} \pmod m$$
Thus, $(a / b) \equiv a \times b^{m-2} \pmod m$.
