# Syllogism - Expected Questions

This file contains 15 TCS NQT-style expected questions ranging from beginner to advanced levels, designed to mirror recent patterns.

---

### **Q1.** 
**Statements:**
1. All computers are calculators.
2. All calculators are processors.

**Conclusions:**
I. All processors are computers.
II. Some processors are computers.

> 🎯 **Hint:** Look at the direction of the subset relationship.

<details><summary>✅ Solution</summary>

**Step-by-Step Solution:**
1. Let Computers = $C$, Calculators = $K$, and Processors = $P$.
2. The premises establish: $C \subseteq K$ and $K \subseteq P \implies C \subseteq P$.
3. For Conclusion I (All $P$ are $C$): This requires $P \subseteq C$. The minimal Venn shows $P$ is larger than $C$, so this is invalid.
4. For Conclusion II (Some $P$ are $C$): Since $C \subseteq P$ and $C \neq \emptyset$, the intersection $P \cap C = C \neq \emptyset$. Thus, some processors are computers is valid.

**Answer:** Only Conclusion II follows.
**Shortcut:** When going from inner to outer circle, "All" and "Some" are valid. When going from outer to inner circle, only "Some" is valid.
**Difficulty:** ⭐☆☆☆☆ | **Target Time:** 20 seconds
**Common Mistake:** Marking Conclusion I as valid by reversing the "All" relationship.

</details>

---

### **Q2.** 
**Statements:**
1. Some keys are locks.
2. No lock is a door.

**Conclusions:**
I. Some keys are not doors.
II. All keys can be doors.

> 🎯 **Hint:** Identify the common region that is restricted from entering the "doors" set.

<details><summary>✅ Solution</summary>

**Step-by-Step Solution:**
1. Let Keys = $K$, Locks = $L$, and Doors = $D$.
2. We have $K \cap L \neq \emptyset$ and $L \cap D = \emptyset$.
3. Let $x \in K \cap L$. Since $x \in L$, and no $L$ is $D$, $x$ cannot be in $D$.
4. This means there is at least one element in $K$ (the overlap with $L$) that is not in $D$, which satisfies $K \cap D' \neq \emptyset$. Thus, Conclusion I is valid.
5. For Conclusion II, since some keys are definitely not doors, it is impossible for all keys to be doors. Thus, Conclusion II is invalid.

**Answer:** Only Conclusion I follows.
**Shortcut:** "Some + No" combination between adjacent terms always yields a definite "Some-not" conclusion.
**Difficulty:** ⭐⭐☆☆☆ | **Target Time:** 35 seconds
**Common Mistake:** Missing the fact that the overlapping "keys-locks" region cannot touch doors, leading to marking Conclusion II as possible.

</details>

---

### **Q3.** 
**Statements:**
1. Some inputs are outputs.
2. Some outputs are signals.
3. No signal is a data.

**Conclusions:**
I. Some inputs are data.
II. No input is a data.

> 🎯 **Hint:** Check if the conclusions form a complementary pair with no direct constraints.

<details><summary>✅ Solution</summary>

**Step-by-Step Solution:**
1. Let Inputs = $I$, Outputs = $O$, Signals = $S$, and Data = $D$.
2. We have $I \cap O \neq \emptyset$, $O \cap S \neq \emptyset$, and $S \cap D = \emptyset$.
3. In the minimal Venn, $I$ and $D$ do not overlap, making Conclusion I false and Conclusion II appear true.
4. In an alternative Venn, we can draw $I$ and $D$ overlapping without violating any premises. This makes Conclusion I true and Conclusion II false.
5. Since they are individually invalid, share the same terms, and are a "Some + No" pair, they form an Either-Or relationship.

**Answer:** Either Conclusion I or II follows.
**Shortcut:** Complementary pair (Some + No) with identical terms and no direct constraints always results in "Either-Or".
**Difficulty:** ⭐⭐⭐☆☆ | **Target Time:** 45 seconds
**Common Mistake:** Marking "Only II follows" because they do not touch in the minimal Venn diagram.

</details>

---

### **Q4.** 
**Statements:**
1. Only a few cars are bikes.
2. All bikes are trucks.
3. No truck is a bus.

**Conclusions:**
I. All cars can never be bikes.
II. All cars can never be trucks.

> 🎯 **Hint:** Look at the exact meaning of "Only a few" and the boundary limits it places.

<details><summary>✅ Solution</summary>

**Step-by-Step Solution:**
1. Let Cars = $C$, Bikes = $B$, Trucks = $T$, and Buses = $S$.
2. Premise 1: $C \cap B \neq \emptyset$ and $C \cap B' \neq \emptyset$ (Some $C$ are not $B$).
3. Premise 2: $B \subseteq T$.
4. Evaluating Conclusion I: Since some cars are not bikes is a definite requirement, all cars can never be bikes. This is valid.
5. Evaluating Conclusion II: "All cars can never be trucks" means "All cars are trucks is impossible". Let us test if all cars *can* be trucks. If we draw all cars inside trucks (while keeping some cars outside bikes), no premise is violated. Thus, "All cars being trucks" is possible. This makes the claim "All cars can never be trucks" invalid.

**Answer:** Only Conclusion I follows.
**Shortcut:** "Only a few A are B" prevents all A from being B, but does not prevent all A from being a larger set containing B.
**Difficulty:** ⭐⭐⭐⭐☆ | **Target Time:** 60 seconds
**Common Mistake:** Assuming that because cars cannot be all bikes, they also cannot be all trucks.

</details>

---

### **Q5.** 
**Statements:**
1. Only circles are squares.
2. Some circles are triangles.
3. All triangles are hexagons.

**Conclusions:**
I. No square is a hexagon.
II. Some squares can be triangles.

> 🎯 **Hint:** The "Only" keyword makes the predicate set exclusive.

<details><summary>✅ Solution</summary>

**Step-by-Step Solution:**
1. Let Circles = $C$, Squares = $S$, Triangles = $T$, and Hexagons = $H$.
2. Premise 1 converts to: $S \subseteq C$, with the exclusive condition that $S$ cannot intersect with any set other than $C$.
3. Evaluating Conclusion I: Since $S$ is exclusive to $C$, it cannot intersect with $H$. Thus, "No square is a hexagon" is valid.
4. Evaluating Conclusion II: Since $S$ is exclusive to $C$, it can never intersect with $T$. Thus, the possibility "Some squares can be triangles" is invalid.

**Answer:** Only Conclusion I follows.
**Shortcut:** Any element inside the "Only" predicate (Squares) is locked. It can never overlap with any other group.
**Difficulty:** ⭐⭐⭐⭐☆ | **Target Time:** 50 seconds
**Common Mistake:** Marking Conclusion II as valid because squares and triangles are both inside circles.

</details>

---

### **Q6.** 
**Statements:**
1. Some tables are desks.
2. Some desks are chairs.
3. No chair is a bench.

**Conclusions:**
I. Some desks are not benches.
II. Some tables are not benches.

> 🎯 **Hint:** Look at the overlap between desks and chairs.

<details><summary>✅ Solution</summary>

**Step-by-Step Solution:**
1. Let Tables = $T$, Desks = $D$, Chairs = $C$, and Benches = $B$.
2. We have $T \cap D \neq \emptyset$, $D \cap C \neq \emptyset$, and $C \cap B = \emptyset$.
3. Evaluating Conclusion I: There is a region where $D$ and $C$ overlap. Since no element in $C$ can be in $B$, the elements in $D \cap C$ cannot be in $B$. Thus, some desks are not benches is valid.
4. Evaluating Conclusion II: In the minimal Venn, $T$ and $B$ are disjoint, but we can draw them completely overlapping or intersecting without violating premises. Since there is no direct link between $T$, $C$, and $B$, we cannot definitely say some tables are not benches. Thus, Conclusion II is invalid.

**Answer:** Only Conclusion I follows.
**Shortcut:** Find the intersection of the "Some" statement that touches the "No" statement. That intersection is guaranteed to be outside the negative set.
**Difficulty:** ⭐⭐⭐☆☆ | **Target Time:** 45 seconds
**Common Mistake:** Concluding that some tables are not benches because tables are far from benches in the drawing.

</details>

---

### **Q7.** 
**Statements:**
1. All stars are planets.
2. Some planets are moons.
3. No moon is a sun.
4. All suns are galaxies.

**Conclusions:**
I. Some planets are not suns.
II. Some galaxies are not moons.

> 🎯 **Hint:** Look for the elements in Moons and Suns that are restricted.

<details><summary>✅ Solution</summary>

**Step-by-Step Solution:**
1. Let Stars = $S$, Planets = $P$, Moons = $M$, Suns = $U$, and Galaxies = $G$.
2. Overlaps: $S \subseteq P$, $P \cap M \neq \emptyset$, $M \cap U = \emptyset$, and $U \subseteq G$.
3. Evaluating Conclusion I: The overlapping region $P \cap M$ cannot touch $U$ (since $M \cap U = \emptyset$). Hence, there are some planets (in the $P \cap M$ region) that are not suns. This is valid.
4. Evaluating Conclusion II: Since $U \subseteq G$, and $U \cap M = \emptyset$, the elements in $U$ are inside $G$ but outside $M$. Thus, those elements are galaxies that are not moons. This makes Conclusion II valid.

**Answer:** Both Conclusions I and II follow.
**Shortcut:** "All X are Y" combined with "No X is Z" always implies "Some Y are not Z" (via the subset $X$).
**Difficulty:** ⭐⭐⭐⭐☆ | **Target Time:** 75 seconds
**Common Mistake:** Missing the fact that galaxies contain all suns, and since no sun is a moon, the suns inside galaxies are guaranteed not to be moons.

</details>

---

### **Q8.** 
**Statements:**
1. Only a few fruits are sweet.
2. Only a few sweet are sour.
3. No sour is bitter.

**Conclusions:**
I. All fruits can be sweet.
II. All sweet can be sour.

> 🎯 **Hint:** "Only a few" is a one-way restriction.

<details><summary>✅ Solution</summary>

**Step-by-Step Solution:**
1. Let Fruits = $F$, Sweet = $W$, Sour = $R$, and Bitter = $B$.
2. Premise 1: Only a few $F$ are $W \implies F \cap W' \neq \emptyset$ (All $F$ cannot be $W$).
3. Premise 2: Only a few $W$ are $R \implies W \cap R' \neq \emptyset$ (All $W$ cannot be $R$).
4. Evaluating Conclusion I: Since some fruits must remain outside sweet, it is impossible for all fruits to be sweet. Invalid.
5. Evaluating Conclusion II: Since some sweet must remain outside sour, it is impossible for all sweet to be sour. Invalid.

**Answer:** Neither Conclusion I nor II follows.
**Shortcut:** "Only a few X are Y" automatically invalidates "All X can be Y".
**Difficulty:** ⭐⭐⭐☆☆ | **Target Time:** 40 seconds
**Common Mistake:** Thinking that "Only a few" allows "All" under some possibility scenarios.

</details>

---

### **Q9.** 
**Statements:**
1. Each student is a learner.
2. Every learner is an explorer.

**Conclusions:**
I. All students are explorers.
II. Some explorers are students.

> 🎯 **Hint:** Map "Each" and "Every" to their standard logical quantifier.

<details><summary>✅ Solution</summary>

**Step-by-Step Solution:**
1. "Each" and "Every" translate to **All**.
2. Premise 1: $\text{Students} \subseteq \text{Learners}$.
3. Premise 2: $\text{Learners} \subseteq \text{Explorers}$.
4. Combining both: $\text{Students} \subseteq \text{Explorers}$.
5. Evaluating Conclusion I: Since $\text{Students} \subseteq \text{Explorers}$, this is valid.
6. Evaluating Conclusion II: Since $\text{Students} \subseteq \text{Explorers}$, the intersection is non-empty, so some explorers are students is valid.

**Answer:** Both Conclusions I and II follow.
**Shortcut:** Standard nested circles: $A \subseteq B \subseteq C \implies A \subseteq C$ and $C \cap A \neq \emptyset$.
**Difficulty:** ⭐⭐☆☆☆ | **Target Time:** 25 seconds
**Common Mistake:** Getting confused by the words "Each" and "Every" and treating them as particular statements.

</details>

---

### **Q10.** 
**Statements:**
1. 0% of papers are books.
2. 100% of books are files.
3. Almost all files are folders.

**Conclusions:**
I. Some folders are books.
II. No folder is a book.

> 🎯 **Hint:** Convert percentages and "Almost all" to standard terms first.

<details><summary>✅ Solution</summary>

**Step-by-Step Solution:**
1. Conversions:
    *   0% of papers are books $\implies$ No paper is a book.
    *   100% of books are files $\implies$ All books are files.
    *   Almost all files are folders $\implies$ Some files are folders.
2. Let Papers = $P$, Books = $B$, Files = $F$, and Folders = $D$.
3. We have $P \cap B = \emptyset$, $B \subseteq F$, and $F \cap D \neq \emptyset$.
4. In the minimal Venn, $D$ and $B$ do not overlap, making Conclusion I false and Conclusion II appear true.
5. In an alternative Venn, we can easily overlap $D$ and $B$ without violating any premises. Thus, both are individually invalid.
6. They share the same terms and are a "Some + No" pair, forming an Either-Or case.

**Answer:** Either Conclusion I or II follows.
**Shortcut:** "Almost all" translates to "Some", and "0%" translates to "No". Standard Either-Or rules apply.
**Difficulty:** ⭐⭐⭐☆☆ | **Target Time:** 45 seconds
**Common Mistake:** Treating "Almost all" as "All", which would lead to a different (incorrect) conclusion.

</details>

---

### **Q11.** 
**Statements:**
1. Some dogs are cats.
2. No cat is a cow.
3. Some cows are horses.

**Conclusions:**
I. Some dogs are horses.
II. Some horses are not cats.

> 🎯 **Hint:** Look at the relationship between horses, cows, and cats.

<details><summary>✅ Solution</summary>

**Step-by-Step Solution:**
1. Let Dogs = $D$, Cats = $C$, Cows = $O$, and Horses = $H$.
2. We have $D \cap C \neq \emptyset$, $C \cap O = \emptyset$, and $O \cap H \neq \emptyset$.
3. Evaluating Conclusion I: In the minimal Venn, $D$ and $H$ do not overlap. Invalid.
4. Evaluating Conclusion II: Since some horses are cows ($O \cap H \neq \emptyset$), and no cow is a cat ($O \cap C = \emptyset$), the horses that are cows can never be cats. Thus, "Some horses are not cats" is valid.

**Answer:** Only Conclusion II follows.
**Shortcut:** "Some + No" relation creates a guaranteed "Some-not" for the intersecting portion.
**Difficulty:** ⭐⭐⭐☆☆ | **Target Time:** 40 seconds
**Common Mistake:** Missing the "Some horses are not cats" deduction because horses and cats look disjoint in the drawing.

</details>

---

### **Q12.** 
**Statements:**
1. Only red is black.
2. All red are pink.
3. Some pink are green.

**Conclusions:**
I. Some black can be green.
II. All black can be pink.

> 🎯 **Hint:** Red is the exclusive container of black.

<details><summary>✅ Solution</summary>

**Step-by-Step Solution:**
1. Let Red = $R$, Black = $B$, Pink = $P$, and Green = $G$.
2. Premise 1 converts to: $B \subseteq R$, with $B$ having no overlap with any other set except $R$.
3. Premise 2 states: $R \subseteq P$.
4. Evaluating Conclusion I: Since $B$ is exclusive to $R$, it can never overlap with $G$ (which is outside $R$'s exclusive control). Thus, Conclusion I is invalid.
5. Evaluating Conclusion II: Since $B \subseteq R$ and $R \subseteq P$, we have $B \subseteq P$ definitely. Since it is already definitely true, the possibility "All black can be pink" is technically valid (since truth implies possibility in standard NQT rules).

**Answer:** Only Conclusion II follows.
**Shortcut:** "Only A is B" means B cannot touch anything except A. Since A is inside C, B is also inside C. So B is related to C, but B cannot touch any third set D.
**Difficulty:** ⭐⭐⭐⭐☆ | **Target Time:** 55 seconds
**Common Mistake:** Allowing Black to touch Green under a possibility assumption.

</details>

---

### **Q13.** 
**Statements:**
1. All pens are pencils.
2. Some pencils are markers.
3. No marker is a chalk.
4. Some chalks are boards.

**Conclusions:**
I. Some boards are not markers.
II. Some pencils are not chalks.

> 🎯 **Hint:** Trace the negative relationships starting from Chalks.

<details><summary>✅ Solution</summary>

**Step-by-Step Solution:**
1. Let Pens = $P$, Pencils = $E$, Markers = $M$, Chalks = $C$, and Boards = $B$.
2. We have $P \subseteq E$, $E \cap M \neq \emptyset$, $M \cap C = \emptyset$, and $C \cap B \neq \emptyset$.
3. Evaluating Conclusion I: Since some boards are chalks ($C \cap B \neq \emptyset$), and no chalk is a marker ($C \cap M = \emptyset$), the boards that are chalks cannot be markers. Thus, "Some boards are not markers" is valid.
4. Evaluating Conclusion II: Since some pencils are markers ($E \cap M \neq \emptyset$), and no marker is a chalk ($M \cap C = \emptyset$), those pencils that are markers can never be chalks. Thus, "Some pencils are not chalks" is valid.

**Answer:** Both Conclusions I and II follow.
**Shortcut:** Find the elements inside the "Some" set that overlap with the "No" set. They are guaranteed to be outside the opposite set.
**Difficulty:** ⭐⭐⭐⭐☆ | **Target Time:** 70 seconds
**Common Mistake:** Drawing separate Venn diagrams and missing the overlapping deduction.

</details>

---

### **Q14.** 
**Statements:**
1. Only a few A are B.
2. No B is C.
3. Some C are D.

**Conclusions:**
I. Some A are not C is a possibility.
II. All A being C is a possibility.

> 🎯 **Hint:** Look at the overlap between A and B, and its relation with C.

<details><summary>✅ Solution</summary>

**Step-by-Step Solution:**
1. We have:
    *   Only a few A are B $\implies A \cap B \neq \emptyset$.
    *   No B is C $\implies B \cap C = \emptyset$.
2. This means the portion of $A$ that overlaps with $B$ ($A \cap B$) cannot be in $C$.
3. Therefore, $A \cap C' \neq \emptyset$ (Some $A$ are not $C$ is definitely true).
4. Evaluating Conclusion I: Since "Some $A$ are not $C$" is definitely true, the possibility statement is valid (or in strict classical logic, a definite truth makes a possibility valid).
5. Evaluating Conclusion II: Since some $A$ are definitely not $C$ (due to the $A \cap B$ overlap), all $A$ can never be $C$. Thus, Conclusion II is invalid.

**Answer:** Only Conclusion I follows.
**Shortcut:** If $X$ is definitely true, then "All cannot be" is true, making "All is a possibility" invalid.
**Difficulty:** ⭐⭐⭐☆☆ | **Target Time:** 45 seconds
**Common Mistake:** Thinking all A can be C because B is the only set disjoint from C.

</details>

---

### **Q15.** 
**Statements:**
1. All red are blue.
2. Some blue are not green.
3. All green are yellow.

**Conclusions:**
I. Some red are not green.
II. All red being green is a possibility.

> 🎯 **Hint:** Does the "Some not" relation on the outer circle affect the inner circle?

<details><summary>✅ Solution</summary>

**Step-by-Step Solution:**
1. Let Red = $R$, Blue = $B$, Green = $G$, and Yellow = $Y$.
2. We have $R \subseteq B$, $B \cap G' \neq \emptyset$, and $G \subseteq Y$.
3. Evaluating Conclusion I: The elements of $B$ that are not in $G$ could lie entirely outside $R$. In the minimal Venn, we can make all $R$ overlap with $G$. Thus, "Some red are not green" is not definitely true. Invalid.
4. Evaluating Conclusion II: Can we draw all $R$ inside $G$? Yes, we can make $R \subseteq G$, and still have some other part of $B$ outside $G$ to satisfy Premise 2. Since this diagram is valid, the possibility holds. Valid.

**Answer:** Only Conclusion II follows.
**Shortcut:** A "Some not" constraint on a larger set (Blue) does not restrict a smaller subset (Red) unless the constraint specifically targets the subset.
**Difficulty:** ⭐⭐⭐⭐☆ | **Target Time:** 60 seconds
**Common Mistake:** Concluding that "Some red are not green" is valid because some blue are not green.

</details>
