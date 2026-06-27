# Linked List — Cheat Sheet

## Operations Summary

| Operation | C++ Code | Complexity |
|-----------|----------|------------|
| Traversal | `curr = curr->next;` | $O(N)$ |
| Reverse List | 3-pointers swap | $O(N)$ time, $O(1)$ space |
| Middle Node | slow/fast pointers | $O(N)$ time, $O(1)$ space |
| Detect Cycle | slow/fast pointers meeting | $O(N)$ time, $O(1)$ space |
| Delete Node | `prev->next = curr->next; delete curr;` | $O(1)$ (with references) |

## Key Patterns

```cpp
// Dummy node creation
ListNode dummy(0);
ListNode* tail = &dummy;

// Floyd's cycle meeting point check
ListNode *slow = head, *fast = head;
while (fast && fast->next) {
    slow = slow->next;
    fast = fast->next->next;
    if (slow == fast) { ... }
}
```
