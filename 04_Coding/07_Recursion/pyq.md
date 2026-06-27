# Recursion — Previous Year Style Questions (TCS NQT)

---

### PYQ1 — N-th Fibonacci Number
**Difficulty:** Easy | **Time:** 60s | **TCS Frequency:** High
Find the $N$-th Fibonacci number.
**C++ Solution:**
```cpp
int fib(int n) {
    if (n <= 1) return n;
    return fib(n - 1) + fib(n - 2);
}
```

---

### PYQ2 — Sum of Digits of a Number
**Difficulty:** Easy | **Time:** 45s | **TCS Frequency:** High
**C++ Solution:**
```cpp
int digitSum(int n) {
    if (n == 0) return 0;
    return (n % 10) + digitSum(n / 10);
}
```

---

### PYQ3 — Print Pattern without Loop
**Difficulty:** Medium | **Time:** 90s | **TCS Frequency:** High
Print $N, N-5, N-10 \dots$ up to negative or zero, then print numbers in reverse.
**C++ Solution:** Recursively subtract 5, print value, then print when returning.

---

### PYQ4 — Tower of Hanoi
**Difficulty:** Medium | **Time:** 90s | **TCS Frequency:** Medium
Solve Tower of Hanoi and print disk movements.
**C++ Solution:** Standard 3-step recursive function.

---

### PYQ5 — Subset Sum Check
**Difficulty:** Hard | **Time:** 120s | **TCS Frequency:** Medium
Check if subset sums to $K$.
**C++ Solution:**
```cpp
bool solve(int arr[], int n, int target) {
    if (target == 0) return true;
    if (n == 0) return false;
    if (arr[n - 1] > target) return solve(arr, n - 1, target);
    return solve(arr, n - 1, target) || solve(arr, n - 1, target - arr[n - 1]);
}
```
