# Syllogism - FAQ

Frequently asked questions and clarification on conceptual doubts for the TCS NQT Syllogism topic.

---

### **Q1. What is the practical difference between "Only A is B" and "All B are A"?**
*   **Answer**: While both map to the subset relation $B \subseteq A$, "Only A is B" carries an additional **exclusivity constraint**. In "Only A is B," $B$ can **never** overlap with any other third set $C$. In contrast, "All B are A" allows $B$ to overlap with other sets in possibility diagrams.

### **Q2. If "All A are B" is given, does the conclusion "Some A are B" follow?**
*   **Answer**: Yes. Under the classical rules of syllogism applied in the TCS NQT, "All" implies "Some." If every member of set A has a property, any sub-selection of set A must also have that property.

### **Q3. How should I draw the minimal Venn diagram for "Only a few A are B"?**
*   **Answer**: 
    1. Draw circles $A$ and $B$ overlapping.
    2. Place a dot or mark in the part of $A$ that is outside $B$, and draw a line with a cross ($\times$) to $B$. This visually reminds you that this portion of $A$ can **never** enter $B$.

### **Q4. What is the rule of thumb when all premises are negative (e.g., "No A is B" and "No B is C")?**
*   **Answer**: Two negative premises yield **no definite conclusion** between the outer terms ($A$ and $C$). However, look out for the conclusions: if they offer a complementary pair (e.g., "Some A are C" and "No A is C"), the answer will be **Either-Or**. Otherwise, it is **Neither-Nor**.

### **Q5. Why can't we convert "Some A are not B" directly to "Some B are not A"?**
*   **Answer**: The set-theory representation is $A \cap B' \neq \emptyset$. This tells us there is an element in $A$ outside $B$, but tells us nothing about whether there is an element in $B$ outside $A$ (e.g., if $B \subseteq A$, then all $B$ are $A$, so there are no elements in $B$ outside $A$, yet some $A$ are not $B$ remains true).

### **Q6. Does "At least some" have a different logical representation than "Some"?**
*   **Answer**: No. "At least some" is identical to "Some." Both represent $A \cap B \neq \emptyset$. The phrase "At least" is filler text used to distract students.

### **Q7. Under what condition does a "Possibility" conclusion become invalid?**
*   **Answer**: A possibility conclusion is invalid if and only if making it true would directly violate one or more of the given premises. If it can be drawn in even a single valid Venn diagram, it is valid.

### **Q8. How can I manage my time when a question has 4 premises and 3 conclusions?**
*   **Answer**: 
    1. Translate special terms ("Only", "Only a few") instantly.
    2. Sketch a single, clean Minimal Venn diagram.
    3. Evaluate definite conclusions on it. If they fail, mark them invalid.
    4. For any invalid conclusions, check if they share terms and form an Either-Or pair.
    5. For possibility conclusions, quickly check if they violate any negative constraints.
