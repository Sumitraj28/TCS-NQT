# Syllogism - Visual Guides & Solving Models

Use these decision-making trees, sequence flowcharts, and comparison tables to quickly select the correct deduction method and identify complementary pairs under exam pressure.

---

## 🌳 1. Decision Tree: Evaluating "Either-Or" (Complementary Pairs)

When two conclusions are individually invalid, use this decision tree to determine if they form an **Either-Or** case:

```
                  Are both conclusions individually invalid?
                                     |
                         +-----------+-----------+
                         | No                    | Yes
                  [Regular Analysis]      Do they share the SAME 
                                          Subject and Predicate?
                                                 |
                                     +-----------+-----------+
                                     | No                    | Yes
                              [Regular Analysis]     Are they one of these
                                                     Complementary Pairs?
                                                             |
                            +--------------------------------+--------------------------------+
                            |                                |                                |
                     (Some + No)                     (All + Some Not)                 (Some + Some Not)
                            |                                |                                |
                      Does order matter?             Does order matter?               Does order matter?
                            |                                |                                |
                      No (A-B/B-A ok)                 Yes (Must be A-B/A-B)            No (A-B/B-A ok)
                            |                                |                                |
                  [✅ EITHER-OR Case]               [✅ EITHER-OR Case]              [✅ EITHER-OR Case]
```

---

## 🔄 2. Solving Flowchart: Venn Diagram Deduction Sequence

This sequence ensures zero false positives when evaluating complex or possibility-based conclusions:

```
                    [Start: Read Premises]
                              │
                              ▼
                ┌───────────────────────────┐
                │ Draw Minimal Overlap Venn │
                │ (Satisfy premises only)   │
                └─────────────┬─────────────┘
                              │
                              ▼
                ┌───────────────────────────┐
                │ Evaluate Conclusion on    │
                │ Minimal Venn Diagram      │
                └─────────────┬─────────────┘
                              │
             ┌────────────────┴────────────────┐
             ▼                                 ▼
    [Does it FAIL in Minimal?]        [Does it PASS in Minimal?]
             │                                 │
             ├────────────────────────┐        ├────────────────────────┐
             ▼                        ▼        ▼                        ▼
     [Is it Definite?]      [Is it Possibility?] [Is it Definite?]      [Is it Possibility?]
             │                        │        │                        │
             ▼                        ▼        ▼                        ▼
        INVALID               Try Alternative     Try Alternative          VALID
      (Done with              Venn to make PASS   Venn to make FAIL       (Done with
       this one)              │                │                       this one)
                              ▼                ▼
                     [Can it pass?]    [Can it fail?]
                       /        \        /        \
                     Yes         No    Yes         No
                     /            \    /            \
                 VALID      INVALID INVALID        VALID
```

---

## 📊 3. Comparison Table: Venn Diagram vs. Rules-Based Method

Use this table to choose the best strategy based on the question structure:

| Evaluation Metric | Venn Diagram Method (Recommended) | Rules-Based (50/100) Method |
| :--- | :--- | :--- |
| **Logic Basis** | Visual set-overlap representation | Quantitative mapping of terms |
| **Ideal For** | Possibility cases & "Only a few" questions | Simple, standard categorical syllogisms |
| **Setup Time** | 10–15 seconds (to sketch) | 5 seconds (to label terms) |
| **Complexity Limit**| Handles $4+$ variables easily | Difficult to apply beyond 3 variables |
| **Accuracy Rate** | $100\%$ if minimal/maximal conditions met | Prone to error with modern NQT traps |
| **Rule of Thumb** | *If question has "Possibility/Can be" $\rightarrow$ Draw Venn.* | *If statements are direct and standard $\rightarrow$ Use Rules.* |
