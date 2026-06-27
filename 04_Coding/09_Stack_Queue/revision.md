# Stack & Queue — Quick Revision

## Core Templates

### Balanced Parentheses Check
```cpp
bool checkBalanced(const std::string& s) {
    std::stack<char> st;
    for (char c : s) {
        if (c == '(' || c == '{' || c == '[') st.push(c);
        else {
            if (st.empty()) return false;
            if (c == ')' && st.top() != '(') return false;
            if (c == '}' && st.top() != '{') return false;
            if (c == ']' && st.top() != '[') return false;
            st.pop();
        }
    }
    return st.empty();
}
```

### Monotonic Next Greater Element
```cpp
std::vector<int> nge(const std::vector<int>& arr) {
    int n = arr.size();
    std::vector<int> res(n, -1);
    std::stack<int> st;
    for (int i = 0; i < n; ++i) {
        while (!st.empty() && arr[st.top()] < arr[i]) {
            res[st.top()] = arr[i];
            st.pop();
        }
        st.push(i);
    }
    return res;
}
```

## Key Concept
- **Stack:** LIFO, expression parsing, backtracking, brackets.
- **Queue:** FIFO, level order traversal, buffer queue.
