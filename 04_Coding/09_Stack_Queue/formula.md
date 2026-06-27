# Stack & Queue — Formulas and Complexity Reference

## 1. Stack Complexity Reference (std::stack)

| Operation | Syntax | Time Complexity | Space Complexity |
|-----------|--------|-----------------|------------------|
| Push to top | `st.push(x)` | $O(1)$ | $O(1)$ |
| Pop from top | `st.pop()` | $O(1)$ | $O(1)$ |
| Access top | `st.top()` | $O(1)$ | $O(1)$ |
| Size of stack | `st.size()` | $O(1)$ | $O(1)$ |
| Check empty | `st.empty()` | $O(1)$ | $O(1)$ |

---

## 2. Queue Complexity Reference (std::queue)

| Operation | Syntax | Time Complexity | Space Complexity |
|-----------|--------|-----------------|------------------|
| Push to back | `q.push(x)` | $O(1)$ | $O(1)$ |
| Pop from front| `q.pop()` | $O(1)$ | $O(1)$ |
| Access front | `q.front()` | $O(1)$ | $O(1)$ |
| Access back | `q.back()` | $O(1)$ | $O(1)$ |
| Check empty | `q.empty()` | $O(1)$ | $O(1)$ |

---

## 3. Implementation Relations
- Queue using Stacks: Pop cost is $O(1)$ amortized (each element is pushed to `s1` once, popped from `s1` once, pushed to `s2` once, and popped from `s2` once).
- Stack using Queues: Push cost is $O(N)$ (rotate queue elements on push).
