# Syllogism — Complete Notes

---

## 1. Categorical Propositions (The Four Types)

Syllogisms consist of logical arguments with premises (statements) and conclusions. Statements are classified into four forms:

1.  **A-Type (Universal Positive):** *"All A are B"*
    *   Set implication: $A \subseteq B$.
2.  **E-Type (Universal Negative):** *"No A are B"*
    *   Set implication: $A \cap B = \emptyset$.
3.  **I-Type (Particular Positive):** *"Some A are B"*
    *   Set implication: $A \cap B \neq \emptyset$.
4.  **O-Type (Particular Negative):** *"Some A are not B"*
    *   Set implication: $A \setminus B \neq \emptyset$.

---

## 2. The Venn-Diagram Method

The safest and most intuitive method to solve syllogisms is the Venn diagram.

### Basic vs. Possible Diagrams
*   **Basic Diagram:** The simplest representation that satisfies the statements without assuming any extra intersections.
*   **Possible Diagrams:** Other valid diagrams that satisfy the statements (e.g., if "Some A are B", it is *possible* that "All A are B").
*   **Rule of Truth:**
    *   A **definite conclusion** is TRUE only if it is true in **all** possible Venn diagrams. If it fails in even one diagram, it is FALSE.
    *   A **possibility conclusion** (e.g., "Some A being B is a possibility") is TRUE if it is true in at least **one** possible Venn diagram.

---

## 3. Complementary Pairs (Either-Or Cases)

If two conclusions individually fail, they might form an "Either-Or" pair where one of them must be true.

### Conditions for "Either-Or"
All three conditions must be satisfied:
1.  Both conclusions must be **individually false/undetermined** (they cannot be definitely true).
2.  The subject and predicate of both conclusions must be the **same**.
3.  They must form a **complementary pair**:
    *   *Pair 1:* **Some** and **No** (e.g., "Some A are B" and "No A are B").
    *   *Pair 2:* **All** and **Some Not** (e.g., "All A are B" and "Some A are not B").
    *   *Note:* "All" and "No" is NOT a complementary pair.
