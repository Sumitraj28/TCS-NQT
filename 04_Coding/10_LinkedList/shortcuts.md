# Linked List — Shortcuts & Patterns

## 1. Dummy Node Technique
Creating a dummy node simplifies edge cases (such as modifying the head node of a list, merging lists, or deleting nodes).
```cpp
ListNode* mergeTwoLists(ListNode* l1, ListNode* l2) {
    ListNode dummy(0); // local dummy node
    ListNode* tail = &dummy;
    while (l1 && l2) {
        if (l1->val < l2->val) {
            tail->next = l1;
            l1 = l1->next;
        } else {
            tail->next = l2;
            l2 = l2->next;
        }
        tail = tail->next;
    }
    tail->next = l1 ? l1 : l2;
    return dummy.next; // returns actual merged head
}
```

---

## 2. Slow & Fast Pointer (Runner Technique)
A versatile strategy used to solve multiple problems in one pass:
- Finding the middle: Move `fast` by 2, `slow` by 1.
- Cycle check: Move `fast` by 2, `slow` by 1.
- Find $K$-th node from end: Move `fast` by $K$ steps first, then move both together at 1 step speed until `fast` reaches `NULL`.
