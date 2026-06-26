# Syllogism - Common Mistakes & Traps

Avoid these logical fallacies and traps that frequently appear in TCS NQT exams.

---

## 🚨 1. The Particular Negative Reversal Trap

> [!WARNING]
> **Logical Fallacy**: Assuming that "Some $A$ are not $B$" implies "Some $B$ are not $A$." 
> In formal logic, the particular negative statement $A \cap B' \neq \emptyset$ cannot be converted.

### The Contrast

```
INCORRECT DEDUCTION
"Some students are not graduates" ──► "Some graduates are not students" (INVALID)
```

```
CORRECT VENN MODEL
+-----------------------------------+
| Graduates                         |
|   +---------------------------+   |
|   | Students                  |   |
|   +---------------------------+   |
+-----------------------------------+
```
*   **Proof**: In the diagram above, all students are inside graduates, so "Some students are not graduates" is false, but "Some graduates are not students" is true (the outer ring). Thus, the conversion is not mutually symmetric.

---

## 🚨 2. The "Either-Or" Term Alignment Trap

> [!IMPORTANT]
> **Complementary Pair Constraint**: In the **All + Some Not** complementary pair, the Subject and Predicate must align in the exact same order. If they are crossed, they do not form an Either-Or case.

### Comparison of Cases

| Conclusion Pair | Order of Terms | Valid Either-Or? |
| :--- | :--- | :--- |
| I. All $A$ are $B$<br>II. Some $A$ are not $B$ | Parallel: $A \to B$ and $A \to B$ | **✅ YES** |
| I. All $A$ are $B$<br>II. Some $B$ are not $A$ | Crossed: $A \to B$ and $B \to A$ | **❌ NO** (Cannot be Either-Or) |

### Demonstration
*   **Statements**: "Some dogs are pets. Some pets are wild."
*   **Conclusions**:
    1. All dogs are wild.
    2. Some wild are not dogs.
*   **Result**: Even though both are individually false and contain the same terms (`dogs`, `wild`), the order is crossed. Thus, they do **not** form an Either-Or case.

---

## 🚨 3. The "Only a Few" Possibility Trap

> [!CAUTION]
> **The Hidden Constraint**: "Only a few $A$ are $B$" contains a hidden negative constraint: "Some $A$ are not $B$." This constraint completely invalidates any "All $A$ can be $B$" possibility.

### Concept Check
*   **Statement**: "Only a few cars are electric."
*   **Conclusion**: "All cars can be electric."
*   **Analysis**:
    *   "Only a few" means a fraction of cars must *never* be electric.
    *   Therefore, the possibility of all cars being electric is blocked.
    *   The conclusion is **invalid**.
*   **Rule**: If "Only a few $A$ are $B$" is given, then $\text{All } A \text{ can be } B$ is **always invalid**. However, $\text{All } B \text{ can be } A$ is **still valid**.
