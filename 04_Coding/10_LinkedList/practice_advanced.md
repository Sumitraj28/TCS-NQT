# Linked List — Practice: Advanced / Prime Level (10 Questions)

---

### Q1 — Linked List Cycle II
Find the exact node where the cycle begins.
**Full Solution:**
First detect cycle using Floyd's Tortoise and Hare. When they meet, reset the `slow` pointer to `head`, keeping the `fast` pointer at the meeting node. Move both pointers at 1 step speed. They will meet at the start of the cycle.
```cpp
class Solution {
public:
    ListNode *detectCycle(ListNode *head) {
        if (!head || !head->next) return nullptr;
        ListNode *slow = head, *fast = head;
        bool hasCycle = false;
        while (fast && fast->next) {
            slow = slow->next;
            fast = fast->next->next;
            if (slow == fast) {
                hasCycle = true;
                break;
            }
        }
        if (!hasCycle) return nullptr;
        slow = head;
        while (slow != fast) {
            slow = slow->next;
            fast = fast->next;
        }
        return slow;
    }
};
```
**Complexity:** Time $O(N)$ | Space $O(1)$

---

### Q2 — Reverse Nodes in k-Group
Reverse nodes of linked list $K$ at a time and return its modified head.
**Full Solution:**
```cpp
class Solution {
public:
    ListNode* reverseKGroup(ListNode* head, int k) {
        ListNode* curr = head;
        int count = 0;
        while (curr && count < k) {
            curr = curr->next;
            count++;
        }
        if (count == k) {
            ListNode* prev = nullptr;
            ListNode* nextTemp = nullptr;
            curr = head;
            for (int i = 0; i < k; ++i) {
                nextTemp = curr->next;
                curr->next = prev;
                prev = curr;
                curr = nextTemp;
            }
            if (nextTemp) {
                head->next = reverseKGroup(nextTemp, k);
            }
            return prev;
        }
        return head;
    }
};
```
**Complexity:** Time $O(N)$ | Space $O(N/K)$ stack depth

---

### Q3 — Merge k Sorted Lists
Merge $K$ sorted linked lists.
**Full Solution:** Use a min-heap (priority queue) containing heads of all lists. Extract min element, push its next node to heap, and link to result list.

---

### Q4 — Copy List with Random Pointer
Copy list where nodes contain a random pointer to any node in list or null.
**Full Solution:**
Create new nodes and insert them adjacent to original nodes (e.g. `1 -> 1' -> 2 -> 2'`). Connect random pointers for new nodes. Split lists.

---

### Q5 — Flatten a Multilevel Doubly Linked List
**Full Solution:** Traverse nodes. When finding child nodes, recursively flatten list, adjusting next/prev pointers.

---

### Q6 — Partition List
Given value $X$, partition list such that nodes less than $X$ come before nodes $\geq X$.
**Full Solution:** Maintain two lists (one for nodes $< X$, one for nodes $\geq X$) and merge them at the end.

---

### Q7 — Remove Duplicates from Sorted List II
Remove all nodes that have duplicate numbers, leaving only unique numbers.
**Full Solution:** Use dummy node, skipping all matching duplicate nodes.

---

### Q8 — Reorder List
Reorder list to `L0 -> Ln -> L1 -> Ln-1...`
**Full Solution:** Find middle, split list, reverse second half, merge lists alternately.

---

### Q9 — Flattening a Linked List (vertical links)
Given list of nodes where each node contains a child pointer list, flatten into sorted singly list.
**Full Solution:** Recursively merge current list with flattened next list.

---

### Q10 — LRU Cache Node linking
Explain how double linked lists are used in LRU Cache.
**Answer:** Nodes are moved to head on access in $O(1)$. Eviction removes from tail in $O(1)$.
