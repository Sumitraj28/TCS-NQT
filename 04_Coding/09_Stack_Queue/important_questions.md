# Stack & Queue — Top 20 Important TCS NQT-Style Questions

---

### IQ1 — Check balanced parentheses in a string.
**Answer:** Push opening brackets onto stack, pop on matching closing brackets.

---

### IQ2 — Find the next greater element for all array elements.
**Answer:** Monotonic decreasing stack traversed from right to left.

---

### IQ3 — Implement a queue using two stacks.
**Answer:** Push to stack 1, transfer elements to stack 2 when popping or peeking.

---

### IQ4 — Implement a stack using two queues.
**Answer:** Rotate queue elements on push to maintain LIFO ordering at queue front.

---

### IQ5 — Implement a stack that returns the minimum element in O(1).
**Answer:** Maintain a second stack storing minimum values.

---

### IQ6 — Evaluate a postfix expression (RPN).
**Answer:** Stack of operands, pop top two on operator, evaluate, push result back.

---

### IQ7 — Convert Infix to Postfix.
**Answer:** Use operator stack, checking operator precedence before pushing.

---

### IQ8 — Sliding Window Maximum.
**Answer:** Deque of indices, removing indices that are out of bounds or correspond to smaller values.

---

### IQ9 — Trapping Rain Water.
**Answer:** Monotonic decreasing height index stack to find bounded container areas.

---

### IQ10 — Largest Rectangle in Histogram.
**Answer:** Monotonic increasing index stack, calculating area when height drops.

---

### IQ11 — Reverse a string using a stack.
**Answer:** Push all characters onto stack, then pop them back into string.

---

### IQ12 — Simplify Directory Path.
**Answer:** Split path by `/`, process segments with stack (`..` pops, `.` skipped).

---

### IQ13 — Daily Temperatures.
**Answer:** Monotonic index stack keeping track of days until warmer temperature.

---

### IQ14 — Asteroid Collision.
**Answer:** Stack simulation, resolving collisions between positive and negative values.

---

### IQ15 — Validate Stack Sequences.
**Answer:** Greedily pop from stack when top matches current popped index element.

---

### IQ16 — Queue Reversal.
**Answer:** Push queue elements onto stack, then pop stack back to queue.

---

### IQ17 — Circular Queue Design.
**Answer:** Rear/front index pointers wrapping using modulo arithmetic.

---

### IQ18 — Design LRU Cache.
**Answer:** Map mapping keys to double-linked list node iterators.

---

### IQ19 — Remove K Digits.
**Answer:** Monotonic increasing stack, popping if top > incoming digit and $K > 0$.

---

### IQ20 — Check if queue elements can be sorted using another stack.
**Answer:** Push elements to stack if they are out of order, check sorted bounds on pop.
 Richmond.
