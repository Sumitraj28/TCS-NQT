# Syllogism - 5-Minute Revision Notes

Quick reference guide for pre-exam review. Scan these rules to avoid common traps and speed up deduction.

---

## 🔄 1. Standard Conversions Cheat Sheet

Use this table to make instant deductions directly from premises without drawing:

| Given Premise | Direct Valid Conclusion | Common Exam Trap (Invalid!) |
| :--- | :--- | :--- |
| **All A are B** | Some B are A | All B are A |
| **No A is B** | No B is A, Some A are not B | Some A are B |
| **Some A are B** | Some B are A | All A are B |
| **Some A are not B** | None | Some B are not A |

---

## ⚡ 2. Modern Quantifier Translation Rules

Convert special keywords to standard forms immediately:

> [!NOTE]
> *   **"Each" / "Every" / "Any" / "100%"** $\implies$ **All** ($A \subseteq B$)
> *   **"Almost all" / "Many" / "Most" / "Generally" / "A few"** $\implies$ **Some** ($A \cap B \neq \emptyset$)
> *   **"None" / "Not a single" / "0%"** $\implies$ **No** ($A \cap B = \emptyset$)
> *   **"Only A is B"** $\implies$ **All B are A** ($B \subseteq A$, with $B$ exclusive to $A$)
> *   **"Only a few A are B"** $\implies$ **Some A are B** $\mathbf{AND}$ **Some A are not B** ($A \cap B \neq \emptyset$ and $A \cap B' \neq \emptyset$)

---

## ⚖️ 3. "Either-Or" (Complementary Pairs) Checklist

Both conclusions must satisfy all 3 conditions to form an **Either-Or** case:

```
1. Both conclusions are individually INVALID in the minimal Venn diagram.
2. Both conclusions share the same Subject and Predicate terms.
3. They form one of the following pairs:
   - (Some + No) ────► Order of terms does not matter (A-B or B-A is OK).
   - (All + Some Not) ─► Order of terms MUST match exactly (e.g., All A... / Some A not...).
   - (Some + Some Not) ─► Order of terms does not matter.
```

---

## 🚨 4. Exclusivity & Possibility Traps

*   **Vacuous Possibility**: If a definite conclusion is already **true**, its possibility version ("Some A being B is a possibility") is marked **valid** (or vacuously true).
*   **Only-A-is-B Barrier**: If "Only A is B" is given, then $B$ can **never** overlap with any third set $C$. Any possibility statement attempting to link $B$ with another set is **invalid**.
*   **Only-a-few-A-are-B Barrier**: If "Only a few A are B" is given, then the possibility "All A can be B" is **always invalid**. However, "All B can be A" is **still valid**.
