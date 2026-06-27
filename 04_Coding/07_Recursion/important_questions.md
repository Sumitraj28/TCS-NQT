# Recursion — Top 20 Important TCS NQT-Style Questions

---

### IQ1 — Recursively reverse a string.
**Answer:** Swap characters at start/end, call recursively with `left+1` and `right-1`.

---

### IQ2 — Compute factorial of N.
**Answer:** Return `n * fact(n - 1)` with base case `n <= 1`.

---

### IQ3 — Compute N-th Fibonacci number recursively.
**Answer:** Return `fib(n - 1) + fib(n - 2)`.

---

### IQ4 — Recursive sum of array elements.
**Answer:** Return `arr[n - 1] + sumArray(arr, n - 1)`.

---

### IQ5 — Find GCD recursively.
**Answer:** `gcd(a, b) = gcd(b, a % b)`.

---

### IQ6 — Sum of digits recursively.
**Answer:** `(n % 10) + digitSum(n / 10)`.

---

### IQ7 — Power calculation recursively.
**Answer:** `x * power(x, n - 1)`.

---

### IQ8 — Check if array is sorted recursively.
**Answer:** `arr[n - 1] >= arr[n - 2] && isSorted(arr, n - 1)`.

---

### IQ9 — Tower of Hanoi moves count.
**Answer:** $2^N - 1$.

---

### IQ10 — Find maximum element in array recursively.
**Answer:** `max(arr[n-1], findMax(arr, n-1))`.

---

### IQ11 — Check palindrome string recursively.
**Answer:** `s[l] == s[r] && isPal(s, l + 1, r - 1)`.

---

### IQ12 — Print numbers 1 to N recursively.
**Answer:** Recurse `print(n - 1)`, then print `n`.

---

### IQ13 — Print numbers N to 1 recursively.
**Answer:** Print `n`, then recurse `print(n - 1)`.

---

### IQ14 — Count digits recursively.
**Answer:** `1 + count(n / 10)`.

---

### IQ15 — Predict the Winner recursive helper.
**Answer:** Returns `max(nums[l] - score(l+1, r), nums[r] - score(l, r-1))`.

---

### IQ16 — Letter Combinations of Phone Number.
**Answer:** Backtracking search over digits map mapping to character letters.

---

### IQ17 — Generate Parentheses count.
**Answer:** Check `open < max` and `close < open` bounds recursively.

---

### IQ18 — Josephus survivor position.
**Answer:** `(josephus(n - 1, k) + k) % n`.

---

### IQ19 — Subset sum match.
**Answer:** `dfs(n - 1, sum) || dfs(n - 1, sum - arr[n - 1])`.

---

### IQ20 — Binary Search recursive bounds.
**Answer:** Check middle, split search range.
