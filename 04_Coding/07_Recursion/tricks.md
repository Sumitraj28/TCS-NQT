# Recursion — Tricks, Traps, and TCS-Specific Patterns

## Trap 1 — Missing Base Case (Stack Overflow)
**The trap:** Writing a recursive function without a proper base case, or a base case that cannot be reached. This fills up the call stack space and crashes the program with a Stack Overflow.

**Fix:** Ensure every branch of execution has a clear path to a base case.
```cpp
// WRONG:
int factorial(int n) {
    return n * factorial(n - 1); // no base case!
}
```

---

## Trap 2 — Global Variable Side-Effects
**The trap:** Using global variables within recursive calls. In multi-test-case environments like the TCS compiler, global variables do not auto-reset between runs, leading to cumulative calculation errors.

**Fix:** Pass variables as reference parameters, or reset global state before each run.

---

## Trap 3 — Exponential Call Trees
**The trap:** Solving overlapping subproblems using plain recursion (e.g. `fib(n - 1) + fib(n - 2)`). For $n \geq 45$, this will exceed standard execution limits (TLE).

**Fix:** Transition to Dynamic Programming / Memoization when subproblems overlap.
