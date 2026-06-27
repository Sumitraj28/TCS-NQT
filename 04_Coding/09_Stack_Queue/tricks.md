# Stack & Queue — Tricks, Traps, and TCS-Specific Patterns

## Trap 1 — Accessing Top/Front on Empty Structures
**The trap:** Calling `st.top()`, `q.front()`, `st.pop()`, or `q.pop()` when the container is empty. This causes a segmentation fault or undefined behavior.

**Fix:** Always verify `!st.empty()` or `!q.empty()` before accessing.
```cpp
// WRONG:
char top = st.top(); st.pop();

// RIGHT:
if (!st.empty()) {
    char top = st.top();
    st.pop();
}
```

---

## Trap 2 — Monotonic Stack index vs value
**The trap:** Pushing the *values* of the array elements onto the stack when you actually need to find the *indices* of the next greater/smaller elements.

**Fix:** Push **indices** to the stack. You can always retrieve the value using `arr[st.top()]`.

---

## Trap 3 — Memory Limits in BFS
**The trap:** In BFS, queue size can grow exponentially to $O(W)$ where $W$ is the maximum width of the tree/graph. Unchecked queue insertion of visited nodes can result in Out of Memory (OOM) errors.

**Fix:** Mark nodes as visited *immediately* upon pushing to the queue, not when popping them.
