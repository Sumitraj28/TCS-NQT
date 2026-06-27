# Linked List — Common Mistakes

## 1. Accessing Member variables of NULL Pointers
**Mistake:** Calling `curr->val` or `curr->next` when `curr` is `nullptr`. This causes segmentation faults.
**Fix:** Always verify `if (curr != nullptr)` before accessing fields.

---

## 2. Losing Head Reference
**Mistake:** Reversing or traversing the list using the original `head` pointer variable directly, which loses the reference to the list's beginning.
**Fix:** Use a temporary pointer variable (e.g. `curr = head`) to traverse, keeping `head` unchanged.

---

## 3. Creating Cycles accidentally during Updates
**Mistake:** Pointing nodes back to previous list elements without breaking existing links, creating an infinite loop cycle.
**Fix:** Explicitly set target links to `nullptr` or the new next node.
