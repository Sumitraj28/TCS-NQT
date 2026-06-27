# Linked List — Coding Application (Full Problem Solutions)

---

## Problem 1 — Reverse Linked List
**LeetCode:** #206 | **Difficulty:** Easy | **TCS Frequency:** High

### Problem Statement
Given the `head` of a singly linked list, reverse the list, and return the reversed list.

### Approach
Use three pointers (`prev`, `curr`, `nextTemp`) to change the direction of `next` pointers iteratively.

### C++ Solution
```cpp
class Solution {
public:
    ListNode* reverseList(ListNode* head) {
        ListNode* prev = nullptr;
        ListNode* curr = head;
        while (curr != nullptr) {
            ListNode* nextTemp = curr->next;
            curr->next = prev;
            prev = curr;
            curr = nextTemp;
        }
        return prev;
    }
};
```
**Complexity:** Time $O(N)$ | Space $O(1)$

---

## Problem 2 — Linked List Cycle
**LeetCode:** #141 | **Difficulty:** Easy | **TCS Frequency:** High

### Problem Statement
Given `head`, the head of a linked list, determine if the linked list has a cycle in it.

### Approach
Use Floyd's Tortoise and Hare algorithm. Move a `slow` pointer by 1 step and a `fast` pointer by 2 steps. If they meet, a cycle exists.

### C++ Solution
```cpp
class Solution {
public:
    bool hasCycle(ListNode *head) {
        if (!head || !head->next) return false;
        ListNode* slow = head;
        ListNode* fast = head;
        while (fast && fast->next) {
            slow = slow->next;
            fast = fast->next->next;
            if (slow == fast) return true;
        }
        return false;
    }
};
```
**Complexity:** Time $O(N)$ | Space $O(1)$

---

## Problem 3 — Middle of the Linked List
**LeetCode:** #876 | **Difficulty:** Easy | **TCS Frequency:** High

### Problem Statement
Given the `head` of a singly linked list, return the middle node of the linked list. If there are two middle nodes, return the second middle node.

### Approach
Use the two-pointer approach (slow/fast pointers). Move `slow` by 1 step and `fast` by 2 steps. When `fast` reaches the end, `slow` will be at the middle.

### C++ Solution
```cpp
class Solution {
public:
    ListNode* middleNode(ListNode* head) {
        ListNode* slow = head;
        ListNode* fast = head;
        while (fast && fast->next) {
            slow = slow->next;
            fast = fast->next->next;
        }
        return slow;
    }
};
```
**Complexity:** Time $O(N)$ | Space $O(1)$
 obituary.
