# Syllogism - Progressive Solved Examples

This guide provides step-by-step solutions to typical TCS NQT syllogism patterns, progressing from basic deductions to advanced possibility-based systems.

---

## 🟢 1. Easy Level: Universal & Particular Standard Model

### Problem Statement
*   **Premises:**
    1. All papers are books.
    2. Some books are journals.
*   **Conclusions:**
    I. Some papers are journals.
    II. Some journals are books.

Difficulty: ⭐⭐☆☆☆ | Target Time: 35 seconds

---

### Minimal Venn Diagram

```
+-----------------------------+
| Books                       |
|   +---------------+         |       +---------------+
|   | Papers        |         |       | Journals      |
|   +---------------+         |       |               |
+-----------------------------+       +---------------+
               |                             |
               +----------(Overlap)----------+
```

---

### Step-by-Step Logic Analysis

1.  **Map the Premises:**
    *   Premise 1: $\text{Papers} \subseteq \text{Books}$.
    *   Premise 2: $\text{Books} \cap \text{Journals} \neq \emptyset$.
2.  **Evaluate Conclusion I (Some papers are journals):**
    *   Check overlap: The minimal diagram shows `Papers` and `Journals` do not touch.
    *   Since it fails in the minimal diagram, it is **invalid** as a definite conclusion.
3.  **Evaluate Conclusion II (Some journals are books):**
    *   By Premise 2, $\text{Books} \cap \text{Journals} \neq \emptyset$.
    *   Since intersection is commutative, $\text{Journals} \cap \text{Books} \neq \emptyset$.
    *   Therefore, some journals are books is **valid**.

*   **Correct Answer**: Only Conclusion II follows.
*   **Common Mistake**: Assuming `Papers` and `Journals` must overlap because they both intersect with `Books`. This is a classic "undistributed middle" error.

---

## 🟡 2. Medium Level: Three Premises with Either-Or complementary pair

### Problem Statement
*   **Premises:**
    1. Some bags are suitcases.
    2. All suitcases are trunks.
    3. No trunk is a box.
*   **Conclusions:**
    I. Some bags are boxes.
    II. No bag is a box.

Difficulty: ⭐⭐⭐☆☆ | Target Time: 50 seconds

---

### Minimal Venn Diagram

```
+-----------------------------------+
| Trunks                            |
|   +---------------------------+   |       +-----------+
|   | Suitcases                 |   |       | Boxes     |
|   +---------------------------+   |       +-----------+
+-----------------------------------+             |
               |                                  |
   +-----------+-----------+                      |
   | Bags                  |                      |
   +-----------------------+                      |
               |                                  |
               +------------(No Link)-------------+
```

---

### Step-by-Step Logic Analysis

1.  **Evaluate Conclusion I (Some bags are boxes):**
    *   In the minimal Venn diagram, `Bags` and `Boxes` are completely disjoint.
    *   Hence, Conclusion I fails in the minimal diagram and is **invalid**.
2.  **Evaluate Conclusion II (No bag is a box):**
    *   In the minimal Venn diagram, `Bags` and `Boxes` do not overlap, which makes Conclusion II appear true.
    *   Now, test an alternative diagram: we can stretch the `Bags` circle to overlap with `Boxes` without violating the premises (as long as `Boxes` does not touch `Suitcases` or `Trunks`).
    *   Since we can draw a valid diagram where `Bags` and `Boxes` overlap, the definite claim "No bag is a box" is **invalid**.
3.  **Apply Either-Or Checklist:**
    *   Condition 1: Both conclusions are individually invalid? **Yes** (both failed).
    *   Condition 2: Do they share the same subject and predicate? **Yes** (`Bags` and `Boxes`).
    *   Condition 3: Are they a complementary pair? **Yes** (`Some` + `No`).

*   **Correct Answer**: Either Conclusion I or II follows.
*   **Common Mistake**: Marking "Only II follows" because they don't touch in the first drawing. Always verify if you can force an overlap.

---

## 🔴 3. Hard Level: "Only a Few" with Multi-Variable Possibility

### Problem Statement
*   **Premises:**
    1. Only a few students are writers.
    2. All writers are readers.
    3. No reader is a driver.
*   **Conclusions:**
    I. All students being writers is a possibility.
    II. Some students are not drivers.
    III. Some writers can be drivers.

Difficulty: ⭐⭐⭐⭐⭐ | Target Time: 80 seconds

---

### Minimal Venn Diagram

```
                 +-----------------------------------+
                 | Readers                           |
+----------------+---------------+                   |       +-----------+
| Students       | (xxx)         | Writers           |       | Drivers   |
|  +----------+  +---------------+                   |       +-----------+
|  |  No Wrt  |  |                                   |             |
|  +----------+  +-----------------------------------+             |
+----------------+                                                 |
        |                                                          |
        +───────────────────────────(No Link)──────────────────────+
```

---

### Step-by-Step Logic Analysis

1.  **Analyze Premise 1 (Only a few students are writers):**
    *   This implies two statements:
        $$\text{Students} \cap \text{Writers} \neq \emptyset$$
        $$\text{Students} \cap \text{Writers}' \neq \emptyset \quad (\text{Some students are not writers})$$
2.  **Evaluate Conclusion I (All students being writers is a possibility):**
    *   For all students to be writers, the set of students must be a subset of writers ($\text{Students} \subseteq \text{Writers}$).
    *   However, Premise 1 requires $\text{Students} \cap \text{Writers}' \neq \emptyset$.
    *   This contradiction makes the possibility **impossible**. Conclusion I is **invalid**.
3.  **Evaluate Conclusion II (Some students are not drivers):**
    *   From Premise 2, $\text{Writers} \subseteq \text{Readers}$.
    *   From Premise 1, $\text{Students} \cap \text{Writers} \neq \emptyset$.
    *   Thus, there is a common region containing students who are writers.
    *   Since these students are writers, they must be readers ($\text{Writers} \subseteq \text{Readers}$).
    *   Since no reader is a driver ($\text{Readers} \cap \text{Drivers} = \emptyset$), these overlapping student-readers can never be drivers.
    *   Therefore, there is a portion of students that is guaranteed not to be drivers. Conclusion II is **valid**.
4.  **Evaluate Conclusion III (Some writers can be drivers):**
    *   We are given $\text{Writers} \subseteq \text{Readers}$ and $\text{Readers} \cap \text{Drivers} = \emptyset$.
    *   This implies $\text{Writers} \cap \text{Drivers} = \emptyset$. No writer can ever be a driver.
    *   Thus, the possibility is **invalid**.

*   **Correct Answer**: Only Conclusion II follows.
*   **Common Mistake**: Forgetting that "Only a few" has a built-in negative constraint, which blocks the "All is a possibility" conclusion.
