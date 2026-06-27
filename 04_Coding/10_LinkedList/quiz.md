# Linked List — Quiz

## Rapid-Fire Q&A
1. **Can we access elements of a singly linked list in $O(1)$ time by index?**
   - **Answer:** No, it requires $O(N)$ sequential traversal.
2. **What does Floyd's Tortoise and Hare algorithm detect?**
   - **Answer:** Cycles in a linked list.
3. **If a list has a cycle, will the fast pointer bypass the slow pointer without meeting it?**
   - **Answer:** No, they are guaranteed to meet inside the cycle loop.
4. **How many pointer adjustments are needed to insert a node in a singly linked list?**
   - **Answer:** Two.
5. **What is the advantage of using a dummy node?**
   - **Answer:** It simplifies boundary checks at the head of the list.
6. **In a doubly linked list, what member variable pointers does each node contain?**
   - **Answer:** `next` and `prev`.
7. **What is the time complexity of merging two sorted linked lists?**
   - **Answer:** $O(N_1 + N_2)$.
8. **What is the space complexity of reversing a linked list iteratively?**
   - **Answer:** $O(1)$.
9. **How do you find the node where a cycle begins?**
   - **Answer:** Reset the slow pointer to head after detection and advance both slow and fast pointers 1 step at a time until they meet.
10. **Why must we call `delete` in C++ when removing nodes?**
    - **Answer:** To prevent heap memory leaks.

## True or False
1. **A singly linked list can be traversed in both directions.**
   - **Answer:** False (only forward).
2. **Finding the length of a linked list requires $O(N)$ time.**
   - **Answer:** True.
3. **Inserting a node at the head of a list is an $O(N)$ operation.**
   - **Answer:** False ($O(1)$).
4. **Floyd's Cycle detection runs in $O(N)$ time and $O(1)$ space.**
   - **Answer:** True.
5. **A circular linked list's last node points to NULL.**
   - **Answer:** False (it points back to head).
 Richmond.
