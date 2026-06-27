# Recursion — Complete Notes

## 1. What is Recursion?
Recursion is when a function calls itself. A recursive function requires two main components:
1. **Base Case:** The condition under which the recursion stops. Without this, it will result in infinite recursion and a Stack Overflow error.
2. **Recursive Case:** The division of the problem into smaller subproblems and the self-call.

---

## 2. Factorial (Recursive)
Mathematical recurrence: $F(n) = n \times F(n - 1)$ with base case $F(0) = 1$.

```cpp
long long factorial(int n) {
    if (n <= 1) return 1; // base case
    return n * factorial(n - 1); // recursive case
}
```
*Time Complexity: $O(N)$ | Space Complexity: $O(N)$ (call stack)*

---

## 3. Fibonacci Number (Recursive)
Mathematical recurrence: $F(n) = F(n - 1) + F(n - 2)$ with base cases $F(0) = 0$ and $F(1) = 1$.

```cpp
int fib(int n) {
    if (n <= 1) return n; // base cases
    return fib(n - 1) + fib(n - 2); // recursive case
}
```
*Time Complexity: $O(2^N)$ | Space Complexity: $O(N)$ (call stack)*

---

## 4. Sum of Digits (Recursive)
Mathematical recurrence: $\text{sum}(n) = (n \bmod 10) + \text{sum}(n / 10)$ with base case $\text{sum}(0) = 0$.

```cpp
int digitSum(int n) {
    if (n == 0) return 0; // base case
    return (n % 10) + digitSum(n / 10); // recursive case
}
```
*Time Complexity: $O(\log_{10} N)$ | Space Complexity: $O(\log_{10} N)$*

---

## 5. Tower of Hanoi
**Concept:** Move $N$ disks from source rod to destination rod using an auxiliary rod.
Rules:
1. Only one disk can be moved at a time.
2. A larger disk cannot be placed on top of a smaller disk.

**Recurrence:**
To move $N$ disks from Source ($A$) to Destination ($B$) using Auxiliary ($C$):
1. Move $N-1$ disks from $A$ to $C$ using $B$.
2. Move the $N$-th disk from $A$ to $B$.
3. Move $N-1$ disks from $C$ to $B$ using $A$.

Number of moves: $T(N) = 2T(N - 1) + 1 = 2^N - 1$.

**C++ Code (Optional/Explanation):**
```cpp
#include <iostream>

void towerOfHanoi(int n, char from_rod, char to_rod, char aux_rod) {
    if (n == 0) return;
    towerOfHanoi(n - 1, from_rod, aux_rod, to_rod);
    std::cout << "Move disk " << n << " from rod " << from_rod << " to rod " << to_rod << "\n";
    towerOfHanoi(n - 1, aux_rod, to_rod, from_rod);
}
```
*Time Complexity: $O(2^N)$ | Space Complexity: $O(N)$*
