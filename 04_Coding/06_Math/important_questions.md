# Math — Top 20 Important TCS NQT-Style Questions

---

### IQ1 — Check if a number is prime.
**Answer:** Loop from 2 to $\sqrt{N}$. If any value divides $N$, return false.

---

### IQ2 — Compute GCD of two numbers.
**Answer:** Euclidean algorithm `gcd(a, b) = gcd(b, a % b)`.

---

### IQ3 — Compute LCM of two numbers.
**Answer:** `(a * b) / gcd(a, b)`.

---

### IQ4 — Reversing an integer.
**Answer:** Loop extraction `pop = x % 10`, then `rev = rev * 10 + pop`. Prevent 32-bit overflow.

---

### IQ5 — Check if number is a Palindrome.
**Answer:** Reverse number and check equality.

---

### IQ6 — Count divisors of a number.
**Answer:** Loop 1 to $\sqrt{N}$, increment count by 2 if $i$ divides $N$ (unless perfect square).

---

### IQ7 — Compute sum of first N natural numbers.
**Answer:** $\frac{N(N+1)}{2}$.

---

### IQ8 — Modular Exponentiation.
**Answer:** Binary exponentiation with modulo operations inside the loop.

---

### IQ9 — Check if number is an Armstrong number.
**Answer:** Sum of digits raised to power of digit count equals number.

---

### IQ10 — Find the missing number in 0..N.
**Answer:** Sum range $\frac{N(N+1)}{2}$ and subtract elements sum.

---

### IQ11 — Sieve of Eratosthenes.
**Answer:** Array initialization to true, mark multiples of primes starting from 2 to false.

---

### IQ12 — Print first N rows of Pascal's Triangle.
**Answer:** Construct vector of vectors row-by-row, summing elements from preceding row.

---

### IQ13 — N-th Fibonacci number.
**Answer:** Dynamic programming iteration $O(N)$ or matrix exponentiation $O(\log N)$.

---

### IQ14 — Check if number is Perfect.
**Answer:** Divisor sum excluding $N$ equals $N$.

---

### IQ15 — Leap Year Check.
**Answer:** `year % 400 == 0 || (year % 4 == 0 && year % 100 != 0)`.

---

### IQ16 — Decimal to Hexadecimal.
**Answer:** Modulo division by 16, mapping values 10-15 to 'A'-'F'.

---

### IQ17 — Find Prime Factors of N.
**Answer:** Divide by 2 while possible, then by odd values starting at 3 up to $\sqrt{N}$.

---

### IQ18 — N-th Catalan Number.
**Answer:** $\frac{1}{n+1} \binom{2n}{n}$.

---

### IQ19 — Happy Number Check.
**Answer:** Sum squares of digits, detect cycles using two pointers (slow/fast).

---

### IQ20 — Count set bits in an integer.
**Answer:** Brian Kernighan's bitwise algorithm: count occurrences of `n = n & (n - 1)`.
