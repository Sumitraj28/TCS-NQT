# Stack & Queue — Common Mistakes

## 1. Popping from Empty Stack/Queue
**Mistake:** Calling `st.pop()`, `st.top()`, `q.pop()`, or `q.front()` without checking `empty()`. This leads to segmentation faults.
**Fix:** Always verify `!st.empty()` or `!q.empty()` first.

---

## 2. Queue using Stacks - Redundant Transfer
**Mistake:** Transferring elements from `s1` to `s2` on *every* pop/peek operation. This ruins the amortized $O(1)$ complexity.
**Fix:** Only transfer elements when `s2` is empty.

---

## 3. Monotonic Stack Element Type
**Mistake:** Storing array values instead of array indices in a monotonic stack when index tracking is needed.
**Fix:** Push indices onto the stack, and access array values using `arr[st.top()]`.
