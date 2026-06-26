# Syllogism - Timed Practice (10 Questions)

Test your speed under exam conditions. Try to solve each question within its specified target time.

---

### **Q1.** 
**Statements:**
1. All computers are laptops.
2. Some laptops are tablets.
3. No tablet is a phone.

**Conclusions:**
I. Some laptops are not phones.
II. All laptops can be phones.

> 🎯 **Hint:** Look at the overlap between laptops and tablets.

<details><summary>✅ Solution</summary>

**Step-by-Step Solution:**
1. Overlaps: $\text{Computers} \subseteq \text{Laptops}$, $\text{Laptops} \cap \text{Tablets} \neq \emptyset$, and $\text{Tablets} \cap \text{Phones} = \emptyset$.
2. Evaluating Conclusion I: The laptops that are tablets ($\text{Laptops} \cap \text{Tablets}$) cannot be phones because no tablet is a phone. Thus, "Some laptops are not phones" is valid.
3. Evaluating Conclusion II: Since some laptops are definitely not phones, all laptops can never be phones. Invalid.

**Answer:** Only Conclusion I follows.
**Shortcut:** "Some + No" combination yields a definite "Some not" conclusion.
**Difficulty:** ⭐⭐⭐☆☆ | **Target Time:** 45 seconds
**Common Mistake:** Forgetting that the tablet-laptop overlap is restricted from entering phones.

</details>

---

### **Q2.** 
**Statements:**
1. Only circles are squares.
2. All circles are rings.

**Conclusions:**
I. No square is a ring.
II. Some squares can be rings.

> 🎯 **Hint:** Look at the subset relationships.

<details><summary>✅ Solution</summary>

**Step-by-Step Solution:**
1. Premise 1 converts to: $\text{Squares} \subseteq \text{Circles}$, with squares exclusive to circles.
2. Premise 2: $\text{Circles} \subseteq \text{Rings}$.
3. Combining gives: $\text{Squares} \subseteq \text{Circles} \subseteq \text{Rings} \implies \text{Squares} \subseteq \text{Rings}$.
4. Since all squares are rings, Conclusion I is invalid.
5. Since all squares are already rings, the possibility "Some squares can be rings" is technically valid (or definitely true).

**Answer:** Only Conclusion II follows.
**Shortcut:** $X \subseteq Y \subseteq Z \implies X \subseteq Z$.
**Difficulty:** ⭐⭐☆☆☆ | **Target Time:** 35 seconds
**Common Mistake:** Marking Conclusion I as valid due to confusing the exclusivity of squares.

</details>

---

### **Q3.** 
**Statements:**
1. Only a few blue are green.
2. No green is yellow.

**Conclusions:**
I. All blue can be yellow.
II. Some blue are not yellow.

> 🎯 **Hint:** Look at the overlap between blue and green.

<details><summary>✅ Solution</summary>

**Step-by-Step Solution:**
1. Premise 1: $\text{Blue} \cap \text{Green} \neq \emptyset$.
2. Premise 2: $\text{Green} \cap \text{Yellow} = \emptyset$.
3. Since some blue are green, those blue elements cannot touch yellow. Thus, "Some blue are not yellow" is valid.
4. Since some blue are definitely not yellow, all blue can never be yellow. Invalid.

**Answer:** Only Conclusion II follows.
**Shortcut:** "Only a few" implies "Some", which combines with "No" to form a definite "Some not".
**Difficulty:** ⭐⭐⭐☆☆ | **Target Time:** 40 seconds
**Common Mistake:** Missing the fact that "Some blue are not yellow" is definitely true.

</details>

---

### **Q4.** 
**Statements:**
1. Some tables are desks.
2. Some desks are chairs.
3. Some chairs are benches.

**Conclusions:**
I. Some tables are benches.
II. No table is a bench.

> 🎯 **Hint:** Look at the chain of particular statements.

<details><summary>✅ Solution</summary>

**Step-by-Step Solution:**
1. In the minimal Venn, all circles overlap in a chain, and the end items (`Tables` and `Benches`) do not touch.
2. Since they do not touch in the minimal Venn, both are individually invalid.
3. They share the same terms and form a `Some` + `No` pair.

**Answer:** Either Conclusion I or II follows.
**Shortcut:** Complementary pair with no direct relationships.
**Difficulty:** ⭐⭐☆☆☆ | **Target Time:** 30 seconds
**Common Mistake:** Marking "Neither follows" because both are individually false.

</details>

---

### **Q5.** 
**Statements:**
1. No shirt is a pant.
2. No pant is a jacket.
3. No jacket is a coat.

**Conclusions:**
I. No shirt is a coat.
II. Some shirts are coats.

> 🎯 **Hint:** Look for negative restrictions between shirts and coats.

<details><summary>✅ Solution</summary>

**Step-by-Step Solution:**
1. There is no direct negative statement between shirts and coats.
2. Thus, in the minimal Venn they are disjoint (Conclusion I seems true, II seems false).
3. In an alternative Venn, they can overlap (Conclusion I becomes false, II becomes true).
4. Both are individually invalid and form a `No` + `Some` pair.

**Answer:** Either Conclusion I or II follows.
**Difficulty:** ⭐⭐☆☆☆ | **Target Time:** 35 seconds
**Common Mistake:** Marking Conclusion I as valid.

</details>

---

### **Q6.** 
**Statements:**
1. All A are B.
2. All B are C.
3. All C are D.

**Conclusions:**
I. All A are D.
II. Some D are A.

> 🎯 **Hint:** Draw nested circles.

<details><summary>✅ Solution</summary>

**Step-by-Step Solution:**
1. $A \subseteq B \subseteq C \subseteq D \implies A \subseteq D$.
2. Thus, "All A are D" is valid.
3. Since $A \subseteq D$, the intersection $D \cap A = A \neq \emptyset$. Thus, "Some D are A" is valid.

**Answer:** Both Conclusions I and II follow.
**Difficulty:** ⭐☆☆☆☆ | **Target Time:** 20 seconds
**Common Mistake:** Thinking "Some D are A" is invalid because all A are D.

</details>

---

### **Q7.** 
**Statements:**
1. Only a few fruits are sweet.
2. Only a few sweet are sour.

**Conclusions:**
I. All fruits can be sweet.
II. All sweet can be fruits.

> 🎯 **Hint:** "Only a few" is a one-way restriction.

<details><summary>✅ Solution</summary>

**Step-by-Step Solution:**
1. Premise 1: Only a few $F$ are $W \implies F \cap W' \neq \emptyset$ (All $F$ cannot be $W$).
2. Thus, Conclusion I is invalid.
3. However, there is no restriction preventing all $W$ from being inside $F$. We can draw $W \subseteq F$ while keeping some $F$ outside $W$. Thus, Conclusion II is valid.

**Answer:** Only Conclusion II follows.
**Shortcut:** "Only a few A are B" prevents All A from being B, but allows All B to be A.
**Difficulty:** ⭐⭐⭐☆☆ | **Target Time:** 45 seconds
**Common Mistake:** Marking both as invalid.

</details>

---

### **Q8.** 
**Statements:**
1. All red are blue.
2. No blue is green.
3. Some green are yellow.

**Conclusions:**
I. Some yellow are not red.
II. Some red are not green.

> 🎯 **Hint:** Look at the relationship between red, blue, and green.

<details><summary>✅ Solution</summary>

**Step-by-Step Solution:**
1. We have $R \subseteq B$, $B \cap G = \emptyset$, and $G \cap Y \neq \emptyset$.
2. Since $R \subseteq B$ and $B \cap G = \emptyset \implies R \cap G = \emptyset$.
3. Evaluating Conclusion I: The yellow elements that are in green cannot be blue, and thus cannot be red. So "Some yellow are not red" is valid.
4. Evaluating Conclusion II: Since red and green are completely disjoint, "Some red are not green" is definitely true (valid).

**Answer:** Both Conclusions I and II follow.
**Difficulty:** ⭐⭐⭐☆☆ | **Target Time:** 45 seconds
**Common Mistake:** Marking Conclusion II as invalid because no red is green. In logic, "No" implies "Some not."

</details>

---

### **Q9.** 
**Statements:**
1. Some inputs are devices.
2. No device is a screen.
3. All screens are monitors.

**Conclusions:**
I. Some monitors are not devices.
II. All inputs being screens is a possibility.

> 🎯 **Hint:** Trace the screen-monitor containment.

<details><summary>✅ Solution</summary>

**Step-by-Step Solution:**
1. We have $I \cap D \neq \emptyset$, $D \cap S = \emptyset$, and $S \subseteq M$.
2. Evaluating Conclusion I: The monitors that are screens ($S$) cannot touch devices. Thus, those monitors are not devices. Valid.
3. Evaluating Conclusion II: Since some inputs are devices ($I \cap D \neq \emptyset$), and no device is a screen ($D \cap S = \emptyset$), those input-devices can never be screens. Thus, all inputs cannot be screens. Invalid.

**Answer:** Only Conclusion I follows.
**Difficulty:** ⭐⭐⭐☆☆ | **Target Time:** 50 seconds
**Common Mistake:** Concluding that all inputs can be screens by ignoring the input-device overlap.

</details>

---

### **Q10.** 
**Statements:**
1. Only tables are chairs.
2. No table is a desk.
3. Some desks are benches.

**Conclusions:**
I. No chair is a bench.
II. Some tables being benches is a possibility.

> 🎯 **Hint:** Remember the exclusivity of chairs.

<details><summary>✅ Solution</summary>

**Step-by-Step Solution:**
1. Premise 1: $\text{Chairs} \subseteq \text{Tables}$ (Chairs cannot touch any other set).
2. Premise 2: $\text{Tables} \cap \text{Desks} = \emptyset$.
3. Premise 3: $\text{Desks} \cap \text{Benches} \neq \emptyset$.
4. Evaluating Conclusion I: Since chairs are exclusive to tables, they can never touch benches. Valid.
5. Evaluating Conclusion II: There is no constraint preventing tables and benches from overlapping (as long as tables don't touch desks). Thus, this possibility is valid.

**Answer:** Both Conclusions I and II follow.
**Difficulty:** ⭐⭐⭐⭐☆ | **Target Time:** 55 seconds
**Common Mistake:** Thinking chairs can overlap with benches because benches overlap with desks.

</details>
