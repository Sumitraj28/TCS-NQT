# Syllogism - Past Year Questions (PYQs)

These past year questions from the 2023-2025 TCS NQT papers demonstrate real exam patterns, traps, and speed shortcuts.

---

## 📌 PYQ 1: "Only a Few" & Possibility (TCS NQT 2024)

*   **Question**: 
    **Statements:**
    1. Only a few blue are green.
    2. All green are yellow.
    
    **Conclusions:**
    I. Some blue are yellow.
    II. All yellow can be blue.
*   **Pattern ID**: `TCS_NQT_2024_SYLL_01`
*   **Approach**: Map "Only a few" as both $Some$ and $Some\ Not$. Check relationships in the minimal Venn and then test the possibility for all yellow being blue.
*   **Solution**:
    1.  Premise 1 states: $\text{Blue} \cap \text{Green} \neq \emptyset$ and $\text{Blue} \cap \text{Green}' \neq \emptyset$.
    2.  Premise 2 states: $\text{Green} \subseteq \text{Yellow}$.
    3.  Evaluating Conclusion I: Since $\text{Blue}$ overlaps with $\text{Green}$, and all $\text{Green}$ is inside $\text{Yellow}$, $\text{Blue}$ must overlap with $\text{Yellow}$ in the region where it overlaps with $\text{Green}$. Thus, $\text{Some blue are yellow}$ is **valid**.
    4.  Evaluating Conclusion II: Can we fit all $\text{Yellow}$ inside $\text{Blue}$? Let $\text{Blue} = \{1, 2, 3\}$, $\text{Green} = \{1\}$, $\text{Yellow} = \{1, 2\}$. Here, $\text{Yellow} \subseteq \text{Blue}$ is true. Does it violate the premises? 
        *   Only a few blue are green? Yes, some blue are green ($\{1\}$) and some are not ($\{2, 3\}$).
        *   All green are yellow? Yes ($\{1\} \subseteq \{1, 2\}$).
        *   Since no premise is violated, "All yellow can be blue" is **valid**.
*   **Shortcut**: "Only a few $A$ are $B$" blocks all $A$ from entering $B$, but does not block all $B$ from entering $A$. Since all green is yellow, yellow can also enter $A$ completely.
*   **Variation & Trap**: If Conclusion II was "All blue can be yellow," this would be a trap. Since some blue is NOT green, and green is the only restriction, could all blue be yellow? Yes! The only thing blue cannot be is all green. So all blue can be yellow is actually valid. But if it was "All blue can be green," it would be **invalid** (blocked by "Only a few").

---

## 📌 PYQ 2: Three-Statement Either-Or Case (TCS NQT 2023)

*   **Question**: 
    **Statements:**
    1. Some keys are locks.
    2. Some locks are doors.
    3. No door is a window.
    
    **Conclusions:**
    I. Some keys are windows.
    II. No key is a window.
*   **Pattern ID**: `TCS_NQT_2023_SYLL_02`
*   **Approach**: Identify if the conclusions form a complementary pair containing identical variables that are individually invalid in the minimal Venn diagram.
*   **Solution**:
    1.  Draw the minimal Venn diagram: `Keys` overlaps with `Locks`, `Locks` overlaps with `Doors`, and `Doors` is disjoint from `Windows`.
    2.  Evaluate Conclusion I: In the minimal Venn, `Keys` and `Windows` do not overlap. Thus, Conclusion I is invalid.
    3.  Evaluate Conclusion II: In the minimal Venn, `Keys` and `Windows` do not overlap, making this appear valid. However, we can easily draw an alternative Venn diagram where `Keys` overlaps with `Windows` without violating any premises. Thus, Conclusion II is not definitely true, making it invalid.
    4.  Both conclusions are individually invalid, share the same terms (`keys` and `windows`), and form a `Some` + `No` pair. Hence, they form an **Either-Or** relation.
*   **Shortcut**: When you see `Some X are Y` and `No X is Y` in conclusions, and they do not have a direct relation defined in the premises, immediately mark them as **Either-Or**.
*   **Variation & Trap**: If the statements were altered such that `All keys are doors`, then `Keys` would be constrained by the `No door is a window` rule. In that case, no key could overlap with windows, making "No key is a window" definitely valid, breaking the Either-Or relationship.

---

## 📌 PYQ 3: The "Only" Constraint Trap (TCS NQT 2024)

*   **Question**:
    **Statements:**
    1. Only tables are chairs.
    2. No table is a couch.
    
    **Conclusions:**
    I. No chair is a couch.
    II. Some tables are chairs.
*   **Pattern ID**: `TCS_NQT_2024_SYLL_03`
*   **Approach**: Convert "Only tables are chairs" to "All chairs are tables" with the exclusive boundary condition: `Chairs` cannot intersect with any other set.
*   **Solution**:
    1.  Convert Premise 1: $\text{Chairs} \subseteq \text{Tables}$. Crucially, chairs can *only* belong to tables and nothing else.
    2.  Evaluate Conclusion I: Since chairs are subset of tables, and no table is a couch ($\text{Tables} \cap \text{Couches} = \emptyset$), chairs cannot touch couches. Thus, "No chair is a couch" is **valid**.
    3.  Evaluate Conclusion II: Since chairs exist inside tables, there must be an overlap between tables and chairs. Thus, "Some tables are chairs" is **valid**.
*   **Shortcut**: "Only $A$ are $B$" means $B$ is exclusively inside $A$. Therefore, $B$ will automatically have a negative relation ("No $B$ is...") with any set that is disjoint from $A$.
*   **Variation & Trap**: If we added a third statement "Some tables are wooden," a common trap conclusion is "Some chairs can be wooden." Under the "Only" constraint, chairs can never overlap with any set other than tables. Thus, "Some chairs can be wooden" is **invalid** (an absolute trap!).
