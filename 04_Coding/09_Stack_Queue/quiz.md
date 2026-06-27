# Stack & Queue — Quiz

## Rapid-Fire Q&A
1. **Which structure is suited to check balanced parentheses?**
   - **Answer:** Stack.
2. **What does LIFO stand for?**
   - **Answer:** Last In First Out.
3. **What is the amortized cost of popping from a Queue implemented using Stacks?**
   - **Answer:** $O(1)$ (because each element is moved at most once between the stacks).
4. **Which structure is typically used to implement BFS?**
   - **Answer:** Queue.
5. **How does a double-ended queue (deque) differ from a standard queue?**
   - **Answer:** A deque supports $O(1)$ insertions and deletions at both ends.
6. **What is the value of `st.top()` when the stack is empty in C++?**
   - **Answer:** Undefined behavior (segmentation fault).
7. **What is a monotonic stack?**
   - **Answer:** A stack that maintains its elements in sorted order (increasing or decreasing).
8. **In Unix path simplification, what does `..` represent?**
   - **Answer:** Moving up one level (pop from directory stack).
9. **What is print spooling an example of?**
   - **Answer:** FIFO queue scheduling.
10. **What is the time complexity of reversing a queue recursively?**
    - **Answer:** $O(N)$.

## True or False
1. **A queue allows random access to elements using indices.**
   - **Answer:** False.
2. **Standard BFS requires a stack.**
   - **Answer:** False (It requires a queue).
3. **Pushing onto a stack takes $O(N)$ time.**
   - **Answer:** False ($O(1)$).
4. **An expression in Postfix form does not require parentheses to show order of evaluation.**
   - **Answer:** True.
5. **A circular queue avoids wasting unused array slots left behind by dequeue operations.**
   - **Answer:** True.
