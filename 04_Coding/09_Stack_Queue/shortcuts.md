# Stack & Queue — Shortcuts & Quick Reference

## 1. Monotonic Stack Template
Used for finding the nearest smaller/greater element in $O(N)$:
```cpp
#include <stack>
#include <vector>

std::vector<int> nextGreater(const std::vector<int>& arr) {
    int n = arr.size();
    std::vector<int> nge(n, -1);
    std::stack<int> st; // stores indices
    for (int i = 0; i < n; ++i) {
        while (!st.empty() && arr[st.top()] < arr[i]) {
            nge[st.top()] = arr[i];
            st.pop();
        }
        st.push(i);
    }
    return nge;
}
```

---

## 2. Fast Bracket Match Mapping
Instead of multiple `if/else` checks for bracket types, use a character array or map check:
```cpp
char getOpen(char c) {
    if (c == ')') return '(';
    if (c == '}') return '{';
    if (c == ']') return '[';
    return '\0';
}
```
Inside stack loop:
```cpp
if (getOpen(c)) {
    if (st.empty() || st.top() != getOpen(c)) return false;
    st.pop();
} else st.push(c);
```
