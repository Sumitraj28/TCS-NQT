# Recursion — Worked Examples

---

## Example 1 — Recursive Digit Sum

**Problem:** Find the sum of digits of $12345$ recursively.

**Trace:**
1. `digitSum(12345)` $\rightarrow$ returns `5 + digitSum(1234)`
2. `digitSum(1234)` $\rightarrow$ returns `4 + digitSum(123)`
3. `digitSum(123)` $\rightarrow$ returns `3 + digitSum(12)`
4. `digitSum(12)` $\rightarrow$ returns `2 + digitSum(1)`
5. `digitSum(1)` $\rightarrow$ returns `1 + digitSum(0)`
6. `digitSum(0)` $\rightarrow$ base case returns `0`.
- Accumulating sums: $0 + 1 + 2 + 3 + 4 + 5 = 15$.

**C++ Code:**
```cpp
int digitSum(int n) {
    if (n == 0) return 0;
    return (n % 10) + digitSum(n / 10);
}
```

---

## Example 2 — Tower of Hanoi for 3 Disks

**Problem:** Print disk movements to transfer 3 disks from rod A to rod B.

**Trace:**
1. `hanoi(3, 'A', 'B', 'C')`
2. `hanoi(2, 'A', 'C', 'B')` $\rightarrow$ `hanoi(1, 'A', 'B', 'C')` $\rightarrow$ **Move disk 1 from A to B**
3. **Move disk 2 from A to C**
4. `hanoi(1, 'B', 'C', 'A')` $\rightarrow$ **Move disk 1 from B to C**
5. **Move disk 3 from A to B**
6. `hanoi(2, 'C', 'B', 'A')` $\rightarrow$ `hanoi(1, 'C', 'A', 'B')` $\rightarrow$ **Move disk 1 from C to A**
7. **Move disk 2 from C to B**
8. `hanoi(1, 'A', 'B', 'C')` $\rightarrow$ **Move disk 1 from A to B**

---

## Example 3 — Climbing Stairs Recursion

**Problem:** Count distinct ways to climb 4 stairs.

**Trace:**
- `ways(4)` = `ways(3) + ways(2)`
- `ways(3)` = `ways(2) + ways(1)` = `2 + 1 = 3`
- `ways(2)` = `2` (base case)
- `ways(4)` = `3 + 2 = 5`.
- Returns 5.
