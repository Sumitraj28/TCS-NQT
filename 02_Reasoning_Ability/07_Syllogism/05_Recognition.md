# Syllogism - Pattern Recognition Guide

Use this chart to instantly map common English terms and quantifiers used in TCS NQT exams to their mathematical equivalents.

---

## 📊 1. Quantifier Pattern Recognition Chart

| If the statement contains... | Logical Quantifier | Mathematical Representation | Venn Overlap Rule |
| :--- | :--- | :--- | :--- |
| "Every", "Each", "Any", "100%" | **All** | $A \subseteq B$ | Draw $A$ completely inside $B$. |
| "At least some", "Most", "Many", "Generally", "Frequently", "Almost all", "A few" | **Some** | $A \cap B \neq \emptyset$ | Draw $A$ and $B$ overlapping. |
| "None", "Not a single", "No one", "0%" | **No** | $A \cap B = \emptyset$ | Draw $A$ and $B$ disjoint, connected by a crossed line. |
| "Only A are B" | **All B are A** | $B \subseteq A$ | Draw $B$ completely inside $A$ and cross out $B$'s overlap with others. |
| "Only a few A are B" | **Some + Some Not** | $A \cap B \neq \emptyset$ and $A \cap B' \neq \emptyset$ | Draw overlap, and add a dot in $A$ with a barred line to $B$. |

---

## 🎯 2. Conclusion Recognition & Action Rules

Use these rules to instantly determine the correct verification strategy:

```
IF Conclusion has...
 │
 ├─► "Can be" or "Is a possibility"
 │    └─► Action: Try to draw ANY valid Venn diagram where the condition is met.
 │                If you can draw even one, conclusion is VALID.
 │
 ├─► "Can never be" (e.g., "All A can never be B")
 │    └─► Action: Check if "All A are B" is possible. 
 │                If "All A are B" is IMPOSSIBLE, the conclusion is VALID.
 │
 ├─► Definite statements (e.g., "Some A are B", "No A is B")
 │    └─► Action: Check in the Minimal Venn Diagram. 
 │                If it fails in the Minimal Venn, it is INVALID.
 │
 └─► "At least" prefix (e.g., "At least some A are B")
      └─► Action: Treat simply as "Some A are B" (ignore "At least").
```

### Real-Example Demonstration
*   **Given Conclusion**: "All cats can never be dogs."
*   **Strategy**: 
    1. Try to make "All cats are dogs" (Possibility test).
    2. If the statements include "Only a few cats are dogs," then we know at least some cats must *never* be dogs.
    3. Thus, "All cats are dogs" is impossible.
    4. Hence, "All cats can never be dogs" is **valid**.
