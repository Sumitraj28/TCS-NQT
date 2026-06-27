# Stack & Queue — Previous Year Style Questions (TCS NQT)

---

### PYQ1 — Balanced Parentheses
**Difficulty:** Easy | **Time:** 45s | **TCS Frequency:** High
Check if bracket configurations are valid.
**C++ Solution:** Push openers to stack, pop on matching closers.

---

### PYQ2 — Next Greater Element
**Difficulty:** Medium | **Time:** 75s | **TCS Frequency:** High
Compute NGE for array values.
**C++ Solution:** Monotonic decreasing stack.

---

### PYQ3 — Implement Queue using Stacks
**Difficulty:** Easy | **Time:** 60s | **TCS Frequency:** High
Implement FIFO queue using two stacks.
**C++ Solution:** Push to `s1`, pop/peek from `s2` after transferring.

---

### PYQ4 — Reverse Queue
**Difficulty:** Easy | **Time:** 45s | **TCS Frequency:** High
Reverse a queue using an auxiliary stack.
**C++ Solution:**
```cpp
#include <queue>
#include <stack>

void reverseQueue(std::queue<int>& q) {
    std::stack<int> st;
    while (!q.empty()) {
        st.push(q.front());
        q.pop();
    }
    while (!st.empty()) {
        q.push(st.top());
        st.pop();
    }
}
```

---

### PYQ5 — Sliding Window Maximum
**Difficulty:** Hard | **Time:** 120s | **TCS Frequency:** High
Find maximum elements in sliding windows of size $K$.
**C++ Solution:** Monotonic index deque traversal.
