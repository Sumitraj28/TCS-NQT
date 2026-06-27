# Linked List — Tricks, Traps, and TCS-Specific Patterns

## Trap 1 — Dereferencing NULL Pointers
**The trap:** Writing traversal loops or updates like `curr->next->val` without first checking if `curr` or `curr->next` is `NULL`. This causes a segmentation fault crash.

**Fix:** Always verify pointers before accessing member variables:
```cpp
if (curr && curr->next) {
    // safe to access curr->next->val
}
```

---

## Trap 2 — Losing the Rest of the List During Update
**The trap:** Updating `curr->next = prev` before saving the original `curr->next` reference. This isolates the remaining nodes from the traversal.

**Fix:** Save the next node pointer in a temporary variable first:
```cpp
ListNode* nextTemp = curr->next;
curr->next = prev;
curr = nextTemp;
```

---

## Trap 3 — Memory Leaks
**The trap:** In C++, deleting a node pointer (e.g. `prev->next = curr->next`) without calling `delete curr;`. The node continues to occupy heap memory.

**Fix:** Explicitly free deleted nodes:
```cpp
ListNode* temp = curr;
prev->next = curr->next;
delete temp;
```
*(This is important in C++ compared to garbage-collected languages).*
