# Stack & Queue — Cheat Sheet

## Operations Summary

| Container | Operation | Method | Complexity |
|-----------|-----------|--------|------------|
| `std::stack` | Push | `push(x)` | $O(1)$ |
| `std::stack` | Pop | `pop()` | $O(1)$ |
| `std::stack` | Peek | `top()` | $O(1)$ |
| `std::queue` | Enqueue | `push(x)` | $O(1)$ |
| `std::queue` | Dequeue | `pop()` | $O(1)$ |
| `std::queue` | Front | `front()` | $O(1)$ |

## Key Templates

```cpp
// Check empty stack before popping
if (!st.empty()) {
    char val = st.top();
    st.pop();
}

// Monotonic Next Greater Element
while (!st.empty() && arr[st.top()] < arr[i]) {
    res[st.top()] = arr[i];
    st.pop();
}
st.push(i);
```
