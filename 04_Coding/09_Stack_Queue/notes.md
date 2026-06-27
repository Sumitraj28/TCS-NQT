# Stack & Queue — Complete Notes

## 1. Stack Basics
A Stack is a linear data structure that follows the **Last In, First Out (LIFO)** principle. The last element added is the first one to be removed.

**Core operations:**
- `push(x)`: Adds element $x$ to top of stack. $O(1)$
- `pop()`: Removes element from top of stack. $O(1)$
- `top()`: Accesses top element. $O(1)$
- `empty()`: Returns true if stack is empty. $O(1)$

**When to use a Stack:**
- **Reversing:** Reversing string elements or linked list nodes.
- **Matching/Parsing:** Evaluating expressions, balancing parentheses, HTML tags.
- **DFS / Backtracking:** Storing traversal path or recursive calls.
- **Monotonic properties:** Finding next greater/smaller elements.

---

## 2. Queue Basics
A Queue is a linear data structure that follows the **First In, First Out (FIFO)** principle. The first element added is the first one to be removed.

**Core operations:**
- `push(x)`: Adds element $x$ to back (rear) of queue. $O(1)$
- `pop()`: Removes element from front of queue. $O(1)$
- `front()`: Accesses front element. $O(1)$
- `empty()`: Returns true if queue is empty. $O(1)$

**When to use a Queue:**
- **Scheduling/Buffering:** Print spooling, task scheduling (CPU/disk queues).
- **BFS (Breadth-First Search):** Finding shortest path in unweighted graphs or trees level-by-level.
- **Sliding Window:** Tracking history of elements within a moving boundary.

---

## 3. Implementation Transitions
### Queue using Stacks
To implement a queue using two stacks `s1` and `s2`:
- **Push:** Push to `s1` ($O(1)$).
- **Pop/Peek:** If `s2` is empty, move all elements from `s1` to `s2` (which reverses their order, making it LIFO $\rightarrow$ FIFO). Pop from `s2` ($O(1)$ amortized).

```cpp
#include <stack>

class MyQueue {
private:
    std::stack<int> s1, s2;
    void transfer() {
        if (s2.empty()) {
            while (!s1.empty()) {
                s2.push(s1.top());
                s1.pop();
            }
        }
    }
public:
    void push(int x) { s1.push(x); }
    int pop() {
        transfer();
        int val = s2.top();
        s2.pop();
        return val;
    }
    int peek() {
        transfer();
        return s2.top();
    }
    bool empty() {
        return s1.empty() && s2.empty();
    }
};
```
