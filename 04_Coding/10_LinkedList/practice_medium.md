# Linked List — Practice: Medium (15 Questions)

---

### Q1 — Reverse Linked List
**Difficulty:** Medium | **Time:** 60s | **TCS Frequency:** High
**Full Solution:**
```cpp
ListNode* reverseList(ListNode* head) {
    ListNode* prev = nullptr;
    ListNode* curr = head;
    while (curr) {
        ListNode* temp = curr->next;
        curr->next = prev;
        prev = curr;
        curr = temp;
    }
    return prev;
}
```
**Complexity:** Time $O(N)$ | Space $O(1)$

---

### Q2 — Linked List Cycle Check
**Difficulty:** Medium | **Time:** 60s | **TCS Frequency:** High
**Full Solution:** Floyd's Tortoise and Hare pointers.

---

### Q3 — Middle of Linked List
**Difficulty:** Medium | **Time:** 60s | **TCS Frequency:** High
**Full Solution:** Slow & fast pointers.

---

### Q4 — Remove N-th Node From End of List
**Difficulty:** Medium | **Time:** 90s | **TCS Frequency:** High
Remove the $n$-th node from the end of the list and return its head.
**Full Solution (Two Pointers):**
```cpp
ListNode* removeNthFromEnd(ListNode* head, int n) {
    ListNode dummy(0);
    dummy.next = head;
    ListNode* first = &dummy;
    ListNode* second = &dummy;
    for (int i = 0; i <= n; ++i) first = first->next;
    while (first) {
        first = first->next;
        second = second->next;
    }
    ListNode* toDelete = second->next;
    second->next = second->next->next;
    delete toDelete;
    return dummy.next;
}
```
**Complexity:** Time $O(N)$ | Space $O(1)$

---

### Q5 — Merge Two Sorted Lists
Merge two sorted linked lists and return it as a sorted list.
**Full Solution:**
Use a dummy node and a tail pointer, advancing the list pointer with the smaller value.

---

### Q6 — Delete Node in a Linked List (given access only to that node)
Delete the node from list, guaranteed it is not the tail.
**Full Solution:** Copy data from next node to current node, then delete next node.
```cpp
void deleteNode(ListNode* node) {
    ListNode* temp = node->next;
    node->val = temp->val;
    node->next = temp->next;
    delete temp;
}
```

---

### Q7 — Remove Linked List Elements
Remove all elements with value `val`.
**Full Solution:** Use a dummy node pointing to head, deleting matched nodes.

---

### Q8 — Palindrome Linked List
Check if linked list is palindrome.
**Full Solution:** Find middle, reverse second half, compare both halves.
```cpp
bool isPalindrome(ListNode* head) {
    if (!head || !head->next) return true;
    ListNode *slow = head, *fast = head;
    while (fast && fast->next) {
        slow = slow->next;
        fast = fast->next->next;
    }
    // Reverse second half
    ListNode *prev = nullptr, *curr = slow;
    while (curr) {
        ListNode* temp = curr->next;
        curr->next = prev;
        prev = curr;
        curr = temp;
    }
    // Compare
    ListNode *p1 = head, *p2 = prev;
    while (p2) {
        if (p1->val != p2->val) return false;
        p1 = p1->next;
        p2 = p2->next;
    }
    return true;
}
```
**Complexity:** Time $O(N)$ | Space $O(1)$

---

### Q9 — Odd Even Linked List
Group all odd nodes together followed by even nodes.
**Full Solution:** Maintain `odd` and `even` heads, linking odds together and evens together, then attach even list to odd tail.

---

### Q10 — Remove Duplicates from Sorted List
**Full Solution:** Check if `curr->val == curr->next->val`. If so, skip next node.

---

### Q11 — Intersection of Two Linked Lists
Find node at which two lists intersect.
**Full Solution:** Use two pointers. When pointer reaches end, redirect to other list's head. They will meet at intersection node or `NULL`.

---

### Q12 — Add Two Numbers (Values represented by lists in reverse order)
**Full Solution:** Traverse both lists, calculating sum and carry values. Construct new list.

---

### Q13 — Sort List (Merge Sort on Lists)
**Difficulty:** Hard | **Time:** 120s | **TCS Frequency:** Medium
**Full Solution:** Find middle using slow/fast, split list, recursively sort halves, then merge.

---

### Q14 — Rotate List
Rotate list to the right by $K$ places.
**Full Solution:** Link tail node back to head node (making circular). Break loop at index position `length - (k % length)`.

---

### Q15 — Swap Nodes in Pairs
**Full Solution:**
```cpp
ListNode* swapPairs(ListNode* head) {
    if (!head || !head->next) return head;
    ListNode* nextNode = head->next;
    head->next = swapPairs(nextNode->next);
    nextNode->next = head;
    return nextNode;
}
```
**Complexity:** Time $O(N)$ | Space $O(N)$ stack
