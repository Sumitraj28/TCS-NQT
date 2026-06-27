# Recursion — Practice: Basic (15 Questions)

---

### Q1 — Factorial of N
Implement recursive factorial.
**Answer:**
```cpp
int fact(int n) {
    if (n <= 1) return 1;
    return n * fact(n - 1);
}
```

---

### Q2 — Fibonacci Term
Implement recursive Fibonacci term.
**Answer:**
```cpp
int fib(int n) {
    if (n <= 1) return n;
    return fib(n - 1) + fib(n - 2);
}
```

---

### Q3 — Recursive Digit Sum
**Answer:**
```cpp
int digitSum(int n) {
    if (n == 0) return 0;
    return (n % 10) + digitSum(n / 10);
}
```

---

### Q4 — Count Digits Recursively
**Answer:**
```cpp
int countDigits(int n) {
    if (n == 0) return 0;
    return 1 + countDigits(n / 10);
}
```

---

### Q5 — Sum of Array Elements Recursively
**Answer:**
```cpp
int sumArray(int arr[], int n) {
    if (n <= 0) return 0;
    return arr[n - 1] + sumArray(arr, n - 1);
}
```

---

### Q6 — Print 1 to N
Print numbers from 1 to $N$ recursively.
**Answer:**
```cpp
void print1ToN(int n) {
    if (n == 0) return;
    print1ToN(n - 1);
    std::cout << n << " ";
}
```

---

### Q7 — Print N to 1
**Answer:**
```cpp
void printNTo1(int n) {
    if (n == 0) return;
    std::cout << n << " ";
    printNTo1(n - 1);
}
```

---

### Q8 — Power of Base (Iterative/Recursive)
Calculate $x^n$.
**Answer:**
```cpp
double power(double x, int n) {
    if (n == 0) return 1;
    return x * power(x, n - 1);
}
```

---

### Q9 — Find Max in Array Recursively
**Answer:**
```cpp
int findMax(int arr[], int n) {
    if (n == 1) return arr[0];
    return std::max(arr[n - 1], findMax(arr, n - 1));
}
```

---

### Q10 — Reverse String Recursively
**Answer:**
```cpp
void reverse(std::string& s, int l, int r) {
    if (l >= r) return;
    std::swap(s[l], s[r]);
    reverse(s, l + 1, r - 1);
}
```

---

### Q11 — Find Length of String Recursively
**Answer:**
```cpp
int strLength(const char* s) {
    if (*s == '\0') return 0;
    return 1 + strLength(s + 1);
}
```

---

### Q12 — Binary Search (Recursive)
**Answer:**
```cpp
int binSearch(int arr[], int l, int r, int x) {
    if (l > r) return -1;
    int mid = l + (r - l) / 2;
    if (arr[mid] == x) return mid;
    if (arr[mid] > x) return binSearch(arr, l, mid - 1, x);
    return binSearch(arr, mid + 1, r, x);
}
```

---

### Q13 — Sum of Natural Numbers
Compute sum up to $N$.
**Answer:**
```cpp
int sum(int n) {
    if (n <= 1) return n;
    return n + sum(n - 1);
}
```

---

### Q14 — Is Array Sorted
**Answer:**
```cpp
bool isSorted(int arr[], int n) {
    if (n <= 1) return true;
    return arr[n - 1] >= arr[n - 2] && isSorted(arr, n - 1);
}
```

---

### Q15 — Check Palindrome String
**Answer:**
```cpp
bool isPal(const std::string& s, int l, int r) {
    if (l >= r) return true;
    return s[l] == s[r] && isPal(s, l + 1, r - 1);
}
```
