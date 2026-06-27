# Linked List — Top 20 Important TCS NQT-Style Questions

---

### IQ1 — Reverse a singly linked list.
**Answer:** Iteratively swap pointer directions using `prev`, `curr`, and `next` variables.

---

### IQ2 — Detect a cycle in a linked list.
**Answer:** Floyd's Tortoise and Hare slow/fast pointer check.

---

### IQ3 — Find the middle of a linked list.
**Answer:** Move slow pointer by 1, fast pointer by 2. Slow pointer stops at middle.

---

### IQ4 — Remove N-th node from end of linked list.
**Answer:** Maintain gap of $N$ nodes between two pointers, then delete next node of slower pointer.

---

### IQ5 — Find intersection of two linked lists.
**Answer:** Redirect pointer to other list's head on reaching end. Pointers meet at intersection.

---

### IQ6 — Merge two sorted linked lists.
**Answer:** Compare node values iteratively, appending smaller node to result list using dummy head.

---

### IQ7 — Check if linked list is a palindrome.
**Answer:** Reverse second half of list and compare with first half.

---

### IQ8 — Find cycle start node in linked list.
**Answer:** After slow/fast meet, reset slow to head. Move both 1 step at a time until they meet.

---

### IQ9 — Remove duplicate nodes from sorted linked list.
**Answer:** Skip next node if it matches current node value.

---

### IQ10 — Delete node from list given reference to that node only.
**Answer:** Copy next node's value into current node, then delete next node.

---

### IQ11 — Group odd and even nodes in list.
**Answer:** Maintain separate lists for odd/even indices and link them.

---

### IQ12 — Rotate list right by K.
**Answer:** Form circular list, traverse `length - (k % length)` nodes, break circular link.

---

### IQ13 — Reverse nodes in groups of K.
**Answer:** Recursively reverse group segments of size $K$, updating links.

---

### IQ14 — Add two numbers represented by linked lists.
**Answer:** Sum node digits, maintain carry values, construct new list.

---

### IQ15 — Swap nodes in pairs.
**Answer:** Recursively swap adjacent pairs of pointers.

---

### IQ16 — Reorder list.
**Answer:** Split in half, reverse second half, merge lists alternately.

---

### IQ17 — Flatten a multilevel doubly linked list.
**Answer:** DFS traverse nodes, adjusting pointer links when children exist.

---

### IQ18 — Partition list around X.
**Answer:** Split nodes into two lists (smaller than $X$ vs larger) and link.

---

### IQ19 — Merge K sorted lists.
**Answer:** Maintain pointers or min-heap containing heads of all $K$ lists.

---

### IQ20 — Remove duplicates from sorted list II.
**Answer:** Skip entire matching groups of duplicates using dummy node.
 Richmond.
