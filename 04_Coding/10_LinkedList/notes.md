# Linked List — Complete Notes

## 1. What is a Linked List?
A Linked List is a dynamic linear data structure composed of nodes.
```cpp
struct ListNode {
    int val;
    ListNode *next;
    ListNode(int x) : val(x), next(NULL) {}
};
```

**Key properties:**
- **Dynamic Size:** Can grow or shrink at runtime without relocation overhead.
- **Insert/Delete at known node:** $O(1)$ pointer updates.
- **Random access:** Not supported (must traverse from head node).
- **Extra memory:** Requires storing pointers.

---

## 2. Traversal
Iterate through the nodes from `head` until `NULL`.
```cpp
void traverse(ListNode* head) {
    ListNode* curr = head;
    while (curr != NULL) {
        // process curr->val
        curr = curr->next;
    }
}
```
*Time Complexity: $O(N)$ | Space Complexity: $O(1)$*

---

## 3. Reversal
To reverse a singly linked list, we keep track of three pointers: `prev` (initially `NULL`), `curr` (initially `head`), and `nextTemp` (stores `curr->next` before breaking link).

```cpp
ListNode* reverseList(ListNode* head) {
    ListNode* prev = NULL;
    ListNode* curr = head;
    while (curr != NULL) {
        ListNode* nextTemp = curr->next; // save next
        curr->next = prev;               // reverse link
        prev = curr;                     // move prev
        curr = nextTemp;                 // move curr
    }
    return prev; // new head
}
```
*Time Complexity: $O(N)$ | Space Complexity: $O(1)$*

---

## 4. Cycle Detection (Floyd's Tortoise and Hare)
Move two pointers at different speeds: `slow` by 1 step and `fast` by 2 steps. If there is a cycle, the `fast` pointer will eventually meet the `slow` pointer inside the loop.

```cpp
bool hasCycle(ListNode *head) {
    if (head == NULL || head->next == NULL) return false;
    ListNode *slow = head;
    ListNode *fast = head;
    while (fast != NULL && fast->next != NULL) {
        slow = slow->next;
        fast = fast->next->next;
        if (slow == fast) return true; // cycle detected
    }
    return false; // no cycle
}
```
*Time Complexity: $O(N)$ | Space Complexity: $O(1)$*
