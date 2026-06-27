# Math — Worked Examples

---

## Example 1 — Prime Number Check

**Problem:** Determine if $N = 37$ is prime.

**Trace:**
1. $\sqrt{37} \approx 6.08$. Loop test values up to 6.
2. Check 2: $37 \bmod 2 = 1 \neq 0$
3. Check 3: $37 \bmod 3 = 1 \neq 0$
4. Check 5: $37 \bmod 5 = 2 \neq 0$
5. All checks passed. 37 is Prime!

**C++ Code:**
```cpp
bool isPrime(int n) {
    if (n <= 1) return false;
    for (int i = 2; i * i <= n; ++i) {
        if (n % i == 0) return false;
    }
    return true;
}
```

---

## Example 2 — Binary Exponentiation

**Problem:** Compute $3^5$.

**Trace:**
- Initialize `result = 1`, `base = 3`, `power = 5`.
- `power = 5` (odd) $\rightarrow$ `result = result * base = 3`. `base = base * base = 9`. `power = 2`.
- `power = 2` (even) $\rightarrow$ `base = base * base = 81`. `power = 1`.
- `power = 1` (odd) $\rightarrow$ `result = result * base = 3 * 81 = 243`. `base = base * base = 6561`. `power = 0`.
- Loop terminates. Return `243`.

**C++ Code:**
```cpp
long long power(long long base, long long exp) {
    long long res = 1;
    while (exp > 0) {
        if (exp % 2 == 1) res *= base;
        base *= base;
        exp /= 2;
    }
    return res;
}
```

---

## Example 3 — Happy Number Check

**Problem:** Check if $N = 19$ is a Happy Number.

**Trace:**
1. $1^2 + 9^2 = 1 + 81 = 82$
2. $8^2 + 2^2 = 64 + 4 = 68$
3. $6^2 + 8^2 = 36 + 64 = 100$
4. $1^2 + 0^2 + 0^2 = 1$.
5. Reached 1! Returns true.

---

## Example 4 — Pascal's Row Element

**Problem:** Compute row 4 of Pascal's Triangle (0-indexed).

**Trace:**
- `col 0 = 1`
- `col 1 = C(4, 1) = 1 * (4/1) = 4`
- `col 2 = C(4, 2) = 4 * (3/2) = 6`
- `col 3 = C(4, 3) = 6 * (2/3) = 4`
- `col 4 = C(4, 4) = 4 * (1/4) = 1`
- Row elements: `[1, 4, 6, 4, 1]`.

---

## Example 5 — Perfect Number Check

**Problem:** Check if $N = 28$ is a Perfect Number.

**Trace:**
1. Proper divisors of 28: 1, 2, 4, 7, 14.
2. Sum of divisors: $1 + 2 + 4 + 7 + 14 = 28$.
3. Sum equals 28. Returns true.
