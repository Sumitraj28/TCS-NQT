# Recursion — Practice: Medium (15 Questions)

---

### Q1 — Power of Three (Recursive)
Check if $N$ is a power of 3.
**Full Solution:**
```cpp
bool isPowerOfThree(int n) {
    if (n <= 0) return false;
    if (n == 1) return true;
    return n % 3 == 0 && isPowerOfThree(n / 3);
}
```

---

### Q2 — Climbing Stairs Recursive
**Full Solution:**
```cpp
int climbStairs(int n) {
    if (n <= 2) return n;
    return climbStairs(n - 1) + climbStairs(n - 2);
}
```

---

### Q3 — Tower of Hanoi Moves count
**Full Solution:**
```cpp
int hanoiCount(int n) {
    if (n == 0) return 0;
    return 2 * hanoiCount(n - 1) + 1;
}
```

---

### Q4 — Count Steps to Reduce to Zero
Given integer $N$, return steps to reduce to zero. If current is even, divide by 2; otherwise subtract 1.
**Full Solution:**
```cpp
int numberOfSteps(int num) {
    if (num == 0) return 0;
    return 1 + (num % 2 == 0 ? numberOfSteps(num / 2) : numberOfSteps(num - 1));
}
```

---

### Q5 — GCD (Recursive Euclidean)
**Full Solution:**
```cpp
int gcd(int a, int b) {
    return b == 0 ? a : gcd(b, a % b);
}
```

---

### Q6 — Print Pattern (Recursion without Loop)
Given $N$, subtract 5 iteratively until negative/zero, then add 5 until $N$.
**Full Solution:**
```cpp
#include <iostream>

void printPattern(int n, int curr, bool flag) {
    std::cout << curr << " ";
    if (!flag && n == curr) return;
    if (flag) {
        if (curr - 5 > 0) printPattern(n, curr - 5, true);
        else printPattern(n, curr - 5, false);
    } else {
        printPattern(n, curr + 5, false);
    }
}
```

---

### Q7 — Sum of digits of a base conversion
Find sum of digits of $N$ in base $B$ recursively.
**Full Solution:** `sum(n) = n % B + sum(n / B)`.

---

### Q8 — Count Consonants in String
**Full Solution:** Check first character and recurse for suffix.

---

### Q9 — Check if Prime recursively
**Full Solution:**
```cpp
bool checkPrime(int n, int i = 2) {
    if (n <= 2) return (n == 2);
    if (n % i == 0) return false;
    if (i * i > n) return true;
    return checkPrime(n, i + 1);
}
```

---

### Q10 — Tail Recursive Fibonacci
**Full Solution:**
```cpp
int fibTail(int n, int a = 0, int b = 1) {
    if (n == 0) return a;
    if (n == 1) return b;
    return fibTail(n - 1, b, a + b);
}
```

---

### Q11 — Find Minimum element recursively
**Full Solution:**
```cpp
int findMin(int arr[], int n) {
    if (n == 1) return arr[0];
    return std::min(arr[n - 1], findMin(arr, n - 1));
}
```

---

### Q12 — Subset Sum Problem (Recursive DFS)
Check if there exists a subset summing to $K$.
**Full Solution:**
```cpp
bool isSubsetSum(int arr[], int n, int sum) {
    if (sum == 0) return true;
    if (n == 0) return false;
    if (arr[n - 1] > sum) return isSubsetSum(arr, n - 1, sum);
    return isSubsetSum(arr, n - 1, sum) || isSubsetSum(arr, n - 1, sum - arr[n - 1]);
}
```

---

### Q13 — Decimal to Hexadecimal (Recursive)
**Full Solution:** Modulo division mapping digits.

---

### Q14 — Reverse Queue (Recursive)
**Full Solution:** Pop front, recurse, push back to stack bottom.

---

### Q15 — Predict the Winner (Simple Minimax recursive)
**Full Solution:**
```cpp
#include <vector>
#include <algorithm>

int maxScore(std::vector<int>& nums, int l, int r) {
    if (l == r) return nums[l];
    return std::max(nums[l] - maxScore(nums, l + 1, r), nums[r] - maxScore(nums, l, r - 1));
}
```
Ref: returns score differences.
