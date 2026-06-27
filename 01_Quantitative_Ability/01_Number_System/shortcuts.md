# Number System — Shortcuts & Speedups

## 1. Modular Remainder Shortcuts
Instead of calculating large powers before finding remainders, calculate the remainder of the base first:
- *Example:* Find $(43^{10}) \bmod 6$.
  - First reduce base: $43 \bmod 6 = 1$.
  - Then $(1^{10}) \bmod 6 = 1$.

---

## 2. Divisibility check shortcuts
- **Divisibility by 9:** Sum digits. If the sum is a large number, sum the digits of that sum recursively.
  - *Example:* $9876543 \rightarrow 9+8+7+6+5+4+3 = 42 \rightarrow 4+2 = 6$. Not divisible.
- **Divisibility by 11:** Alternating sum difference. Keep subtracting and adding digits from left to right.

---

## 3. Fast Base Conversion
For base conversions to/from binary:
- **Octal to Binary:** Replace each octal digit with its 3-digit binary equivalent (e.g. $5_8 = 101_2$).
- **Hexadecimal to Binary:** Replace each hex digit with its 4-digit binary equivalent (e.g. $A_{16} = 1010_2$).
- This is much faster than dividing by 2 repeatedly.
