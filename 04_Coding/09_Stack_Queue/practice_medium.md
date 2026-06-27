# Stack & Queue — Practice: Medium (15 Questions)

---

### Q1 — Valid Parentheses
**Difficulty:** Medium | **Time:** 90s | **TCS Frequency:** High
Check if bracket combinations are valid.
**Full Solution:**
```cpp
#include <stack>
#include <string>

bool isValid(std::string s) {
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
**Complexity:** Time $O(N)$ | Space $O(N)$

---

### Q2 — Next Greater Element I
**Difficulty:** Medium | **Time:** 90s | **TCS Frequency:** High
**Full Solution:** Use monotonic decreasing stack and hash map lookup.

---

### Q3 — Implement Queue using Stacks
**Difficulty:** Medium | **Time:** 90s | **TCS Frequency:** High
**Full Solution:** Two stacks (`s1` and `s2`), transfer on pop/peek.

---

### Q4 — Implement Stack using Queues
**Difficulty:** Medium | **Time:** 90s | **TCS Frequency:** Medium
Implement LIFO stack using FIFO queues.
**Full Solution:** On push, push to queue, then rotate all preceding elements to back.
```cpp
#include <queue>

class MyStack {
private:
    std::queue<int> q;
public:
    void push(int x) {
        q.push(x);
        for (int i = 0; i < (int)q.size() - 1; ++i) {
            q.push(q.front());
            q.pop();
        }
    }
    void pop() { q.pop(); }
    int top() { return q.front(); }
    bool empty() { return q.empty(); }
};
```
**Complexity:** Push $O(N)$ | Pop $O(1)$ | Space $O(N)$

---

### Q5 — Min Stack
Design a stack that supports push, pop, top, and retrieving the minimum element in $O(1)$ time.
**Full Solution:** Maintain an auxiliary stack storing the minimum value up to the current state.
```cpp
#include <stack>
#include <algorithm>

class MinStack {
private:
    std::stack<int> s;
    std::stack<int> min_s;
public:
    void push(int val) {
        s.push(val);
        if (min_s.empty() || val <= min_s.top()) min_s.push(val);
    }
    void pop() {
        if (s.top() == min_s.top()) min_s.pop();
        s.pop();
    }
    int top() { return s.top(); }
    int getMin() { return min_s.top(); }
};
```
**Complexity:** All operations $O(1)$ | Space $O(N)$

---

### Q6 — Simplify Path
Simplify standard Unix-style absolute path string (e.g. `"/home//foo/"` $\rightarrow$ `"/home/foo"`).
**Full Solution:** Split string by `/`, parse tokens, push to stack of strings. Pop on `..`, skip `.` or empty tokens.

---

### Q7 — Evaluate Reverse Polish Notation (Postfix)
Evaluate math expressions in postfix notation (e.g. `["2", "1", "+", "3", "*"]` $\rightarrow$ `9`).
**Full Solution:** Use stack of operands. Pop twice when encountering operator, perform operation, push result.

---

### Q8 — Generate Binary Numbers from 1 to N
**Full Solution:** Use a queue of strings. Push `"1"`. Loop $N$ times: pop front string $S$, print it, then enqueue $S + \text{"0"}$ and $S + \text{"1"}$.

---

### Q9 — Reverse First K Elements of Queue
**Full Solution:** Dequeue $K$ elements to stack, pop them back to queue, then rotate remaining $N - K$ elements.

---

### Q10 — Design Circular Queue
**Full Solution:** Array implementation with front and rear pointers, wrapping around using modulo arithmetic `(index + 1) % size`.

---

### Q11 — Next Greater Element II (Circular array)
**Difficulty:** Medium | **Time:** 120s | **TCS Frequency:** High
Find next greater element in circular array.
**Full Solution:** Loop indices from $2N - 1$ down to 0, using monotonic stack tracking values modulo $N$.

---

### Q12 — Monotonic Queue (Max Sliding Window basics)
Find the maximum element in each sliding window of size $K$.
**Full Solution:** Use `std::deque` storing indices. Remove indices out of bounds and indices of smaller values.

---

### Q13 — Online Stock Span
**Full Solution:** Monotonic stack storing pairs of `(price, span)`. If current price $\geq$ stack top, accumulate spans and pop.

---

### Q14 — Reverse Stack using Recursion
**Full Solution:** Pop top, recursively reverse remaining stack, then insert popped item at the stack bottom.

---

### Q15 — Validate Stack Sequences
Given push and pop sequences, check if they are valid stack operations.
**Full Solution:** Push elements sequentially. Greedily pop from stack as long as stack top matches current pop element.
```cpp
#include <vector>
#include <stack>

bool validateStackSequences(std::vector<int>& pushed, std::vector<int>& popped) {
    std::stack<int> st;
    int j = 0;
    for (int x : pushed) {
        st.push(x);
        while (!st.empty() && st.top() == popped[j]) {
            st.pop();
            j++;
        }
    }
    return st.empty();
}
```
**Complexity:** Time $O(N)$ | Space $O(N)$
