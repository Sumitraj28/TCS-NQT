# Linked List — Quick Revision

## Core Templates

### Singly Linked List Reversal
```cpp
ListNode* reverse(ListNode* head) {
    ListNode *prev = nullptr, *curr = head;
    while (curr) {
        ListNode* temp = curr->next;
        curr->next = prev;
        prev = curr;
        curr = temp;
    }
    return prev;
}
```

### Floyd's Cycle Check
```cpp
bool checkCycle(ListNode* head) {
    ListNode *slow = head, *fast = head;
    while (fast && fast->next) {
        slow = slow->next;
        fast = fast->next->next;
        if (slow == fast) return true;
    }
    return false;
}
```

### Middle of List
```cpp
ListNode* getMiddle(ListNode* head) {
    ListNode *slow = head, *fast = head;
    while (fast && fast->next) {
        slow = slow->next;
        fast = fast->next->next;
    }
    return slow;
}
```

## Key Facts
- Access time is $O(N)$.
- Dynamic allocation.
- Floyd's cycle start recovery reset slow pointer to head.
