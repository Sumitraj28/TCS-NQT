# Linked List — Formulas and Complexity Reference

## 1. Single Linked List Complexity

| Operation | Best Case | Worst/Average Case |
|-----------|-----------|--------------------|
| Access element | $O(1)$ (head) | $O(N)$ (must traverse) |
| Insert at head | $O(1)$ | $O(1)$ |
| Insert at tail (with tail pointer) | $O(1)$ | $O(1)$ |
| Insert at tail (no tail pointer) | $O(N)$ | $O(N)$ |
| Delete at head | $O(1)$ | $O(1)$ |
| Delete middle node | $O(1)$ (given pointer to node) | $O(N)$ (if searching) |

---

## 2. Cycle Detection Relationships (Floyd's Algorithm)
If the cycle length is $C$, and distance from head to start of cycle is $D$:
- Pointers meet after slow pointer covers some distance $X \leq D + C$.
- Finding cycle start: After they meet, move slow pointer back to `head`, and keep fast pointer at meeting point. Move both at 1 step speed. They will meet at the start of the cycle.
- Time Complexity: $O(D + C) \approx O(N)$.
- Space Complexity: $O(1)$.
