# Recursion — Quick Revision

## Core Templates

### Recursive Factorial
```cpp
long long fact(int n) {
    return n <= 1 ? 1 : n * fact(n - 1);
}
```

### Recursive Fibonacci
```cpp
int fib(int n) {
    return n <= 1 ? n : fib(n - 1) + fib(n - 2);
}
```

### Tower of Hanoi Core
```cpp
void hanoi(int n, char from, char to, char aux) {
    if (n == 0) return;
    hanoi(n - 1, from, aux, to);
    // move N from from to to
    hanoi(n - 1, aux, to, from);
}
```

## Key Things to Remember
- Base cases are mandatory.
- Space complexity depends on maximum call stack depth.
- Standard recursive Fibonacci is $O(2^N)$ time and $O(N)$ space.
