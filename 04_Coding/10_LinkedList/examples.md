# Linked List — Worked Examples

---

## Example 1 — Reversing a Singly Linked List

**Problem:** Reverse list `1 -> 2 -> 3 -> NULL`.

**Trace:**
- Initialize `prev = NULL`, `curr = head (node 1)`.
- **Iteration 1:**
  - `nextTemp = curr->next (node 2)`.
  - `curr->next = prev (NULL)`.
  - `prev = curr (node 1)`.
  - `curr = nextTemp (node 2)`.
  - List state: `1 -> NULL` and `2 -> 3 -> NULL`.
- **Iteration 2:**
  - `nextTemp = curr->next (node 3)`.
  - `curr->next = prev (node 1)`.
  - `prev = curr (node 2)`.
  - `curr = nextTemp (node 3)`.
  - List state: `2 -> 1 -> NULL` and `3 -> NULL`.
- **Iteration 3:**
  - `nextTemp = curr->next (NULL)`.
  - `curr->next = prev (node 2)`.
  - `prev = curr (node 3)`.
  - `curr = nextTemp (NULL)`.
  - List state: `3 -> 2 -> 1 -> NULL`.
- Loop finishes. Returns `prev (node 3)`.

---

## Example 2 — Middle of Linked List

**Problem:** Find the middle of `1 -> 2 -> 3 -> 4 -> 5 -> NULL`.

**Trace:**
- Initialize `slow = head (node 1)`, `fast = head (node 1)`.
- **Step 1:** `slow = slow->next (node 2)`, `fast = fast->next->next (node 3)`.
- **Step 2:** `slow = slow->next (node 3)`, `fast = fast->next->next (node 5)`.
- **Step 3:** `fast->next` is `NULL`. Loop terminates.
- Returns `slow (node 3)`.
- *For even size list `1 -> 2 -> 3 -> 4 -> 5 -> 6 -> NULL`: slow ends at node 4 (correct second middle).*
