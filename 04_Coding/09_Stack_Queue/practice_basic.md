# Stack & Queue — Practice: Basic (15 Questions)

---

### Q1 — Declare Stack in C++
How to declare a stack of integers?
**Answer:** `std::stack<int> st;`

---

### Q2 — Declare Queue in C++
How to declare a queue of strings?
**Answer:** `std::queue<std::string> q;`

---

### Q3 — Check for Empty Stack
What function checks if a stack `st` is empty?
**Answer:** `st.empty()` (returns a boolean value).

---

### Q4 — Access Top Element of Stack
**Answer:** `st.top()` (does not remove the element).

---

### Q5 — Remove Element from Queue
What function removes the oldest element from a queue `q`?
**Answer:** `q.pop()` (returns `void`).

---

### Q6 — Access Front Element of Queue
**Answer:** `q.front()`.

---

### Q7 — Access Back Element of Queue
**Answer:** `q.back()`.

---

### Q8 — LIFO vs FIFO
Explain LIFO vs FIFO.
**Answer:** LIFO (Last In First Out) is for stacks; FIFO (First In First Out) is for queues.

---

### Q9 — Size of Stack
**Answer:** `st.size()`.

---

### Q10 — Standard Stack Header
Which library header is required to use `std::stack` in C++?
**Answer:** `#include <stack>`

---

### Q11 — Queue Push Syntax
How do you push element `5` onto a queue `q`?
**Answer:** `q.push(5);`

---

### Q12 — Stack Pop Return Value
Does C++ `st.pop()` return the popped element?
**Answer:** No, it returns `void`. You must call `st.top()` first.

---

### Q13 — Initialize Stack with Array
**Answer:**
```cpp
std::stack<int> st;
for (int num : arr) st.push(num);
```

---

### Q14 — Double-ended Queue Type
What C++ STL container represents a double-ended queue supporting $O(1)$ push/pop at both ends?
**Answer:** `std::deque`

---

### Q15 — Check Queue Size
**Answer:** `q.size()`.
