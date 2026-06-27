# Math — Tricks, Traps, and TCS-Specific Patterns

## Trap 1 — Reversal Integer Overflow
**The trap:** Reversing `1234567899` results in `9987654321`, which exceeds the maximum limit of a 32-bit signed integer (`2147483647`). This causes undefined behavior/wraparound in C++ if using simple `int`.

**Fix:** Use `long long` for storage during reversal, or pre-check limits before multiplying.
```cpp
if (rev > INT_MAX / 10 || (rev == INT_MAX / 10 && pop > 7)) return 0;
```

---

## Trap 2 — Negative Numbers in Modulo
**The trap:** In C++, `-5 % 3` returns `-2` instead of `1`.

**Fix:** Add divisor before modulo operation:
```cpp
int rem = (a % m + m) % m;
```

---

## Trap 3 — Floating Point Division Rounding Errors
**The trap:** Using `double` division `x / y` and casting to `int` can round down incorrectly due to precision issues (e.g. `29.999999` becoming `29` instead of `30`).

**Fix:** Perform integer calculations whenever possible. For rounding up division:
```cpp
int ceilDiv = (a + b - 1) / b; // works for a >= 0, b > 0
```

---

## Trap 4 — Armstrong Count Digits
**The trap:** Hardcoding digit count to 3. Armstrong numbers can have any number of digits (e.g., 1634 is Armstrong because $1^4 + 6^4 + 3^4 + 4^4 = 1634$).

**Fix:** Count digits first, and use that as the power exponent.
