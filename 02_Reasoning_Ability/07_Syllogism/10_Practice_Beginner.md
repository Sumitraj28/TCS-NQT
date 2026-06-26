# Syllogism - Practice Beginner (10 Questions)

Practice these 10 beginner-level questions to solidify your understanding of basic set overlaps and standard logical conversions.

---

### **Q1.** 
**Statements:**
1. All pens are markers.
2. All markers are crayons.

**Conclusions:**
I. All pens are crayons.
II. Some crayons are pens.

> 🎯 **Hint:** Draw nested circles.

<details><summary>✅ Solution</summary>

**Step-by-Step Solution:**
1. Let Pens = $P$, Markers = $M$, and Crayons = $C$.
2. Premise 1: $P \subseteq M$.
3. Premise 2: $M \subseteq C$.
4. Combining these gives $P \subseteq C$. Thus, Conclusion I (All pens are crayons) is valid.
5. Since $P \subseteq C$, the overlap between $C$ and $P$ is non-empty. Thus, Conclusion II (Some crayons are pens) is valid.

**Answer:** Both Conclusions I and II follow.
**Shortcut:** Nested circles $A \subseteq B \subseteq C$ always mean $A \subseteq C$ (All $A$ are $C$) and $C \cap A \neq \emptyset$ (Some $C$ are $A$).
**Difficulty:** ⭐☆☆☆☆ | **Target Time:** 20 seconds
**Common Mistake:** Thinking that "All pens are crayons" does not allow "Some crayons are pens." In logic, "All" implies "Some."

</details>

---

### **Q2.** 
**Statements:**
1. All cats are dogs.
2. Some dogs are tigers.

**Conclusions:**
I. Some cats are tigers.
II. No cat is a tiger.

> 🎯 **Hint:** Check if they share a direct link in the minimal Venn diagram.

<details><summary>✅ Solution</summary>

**Step-by-Step Solution:**
1. Let Cats = $C$, Dogs = $D$, and Tigers = $T$.
2. Premise 1: $C \subseteq D$.
3. Premise 2: $D \cap T \neq \emptyset$.
4. In the minimal Venn, $T$ overlaps with $D$ but does not touch $C$. Thus, Conclusion I is invalid.
5. In an alternative Venn, we can make $T$ overlap with $C$ without violating premises. Thus, Conclusion II is also invalid.
6. Since both are individually invalid, share the same terms, and are a `Some` + `No` pair, they form an Either-Or relationship.

**Answer:** Either Conclusion I or II follows.
**Shortcut:** "Some" + "No" complementary pair with identical terms.
**Difficulty:** ⭐⭐☆☆☆ | **Target Time:** 35 seconds
**Common Mistake:** Choosing "Only II follows" because cats and tigers do not overlap in the minimal Venn diagram.

</details>

---

### **Q3.** 
**Statements:**
1. No shirt is a pant.
2. No pant is a jacket.

**Conclusions:**
I. No shirt is a jacket.
II. Some shirts are jackets.

> 🎯 **Hint:** Look for direct connections between shirts and jackets.

<details><summary>✅ Solution</summary>

**Step-by-Step Solution:**
1. Let Shirts = $S$, Pants = $P$, and Jackets = $J$.
2. Premise 1: $S \cap P = \emptyset$.
3. Premise 2: $P \cap J = \emptyset$.
4. In the minimal Venn, all three sets are disjoint. So Conclusion I seems true, and II seems false.
5. However, there is no restriction preventing $S$ and $J$ from overlapping. We can draw an alternative Venn where $S \cap J \neq \emptyset$ while keeping both disjoint from $P$.
6. Thus, both are individually invalid and form a `No` + `Some` complementary pair.

**Answer:** Either Conclusion I or II follows.
**Shortcut:** Two negative premises between three variables always leave the outer variables unlinked, making them an Either-Or case if complementary conclusions are offered.
**Difficulty:** ⭐⭐☆☆☆ | **Target Time:** 30 seconds
**Common Mistake:** Concluding "No shirt is a jacket" is definitely true because no shirts are pants and no pants are jackets.

</details>

---

### **Q4.** 
**Statements:**
1. Some tables are chairs.
2. Some chairs are benches.

**Conclusions:**
I. Some tables are benches.
II. No table is a bench.

> 🎯 **Hint:** Check if there is a complementary pair.

<details><summary>✅ Solution</summary>

**Step-by-Step Solution:**
1. Let Tables = $T$, Chairs = $C$, and Benches = $B$.
2. Premise 1: $T \cap C \neq \emptyset$.
3. Premise 2: $C \cap B \neq \emptyset$.
4. Minimal Venn shows $T$ and $B$ are disjoint. So Conclusion I is invalid.
5. Alternative Venn allows $T$ and $B$ to overlap. So Conclusion II is invalid.
6. They share the same terms and are a `Some` + `No` pair.

**Answer:** Either Conclusion I or II follows.
**Shortcut:** "Some A are B" and "Some B are C" never yields a definite relation between A and C, but forms Either-Or for (Some, No) conclusions.
**Difficulty:** ⭐⭐☆☆☆ | **Target Time:** 30 seconds
**Common Mistake:** Missing the Either-Or relationship and marking "Neither follows."

</details>

---

### **Q5.** 
**Statements:**
1. All apples are bananas.
2. No banana is a cherry.

**Conclusions:**
I. No apple is a cherry.
II. Some cherries are apples.

> 🎯 **Hint:** If a container is disjoint from a set, what about the elements inside it?

<details><summary>✅ Solution</summary>

**Step-by-Step Solution:**
1. Let Apples = $A$, Bananas = $B$, and Cherries = $C$.
2. Premise 1: $A \subseteq B$.
3. Premise 2: $B \cap C = \emptyset$.
4. Since $A \subseteq B$ and $B$ has no common elements with $C$, $A$ can have no common elements with $C$. Thus, $A \cap C = \emptyset$. Conclusion I is valid.
5. Since $A \cap C = \emptyset$, Conclusion II is invalid.

**Answer:** Only Conclusion I follows.
**Shortcut:** $X \subseteq Y$ and $Y \cap Z = \emptyset \implies X \cap Z = \emptyset$.
**Difficulty:** ⭐☆☆☆☆ | **Target Time:** 20 seconds
**Common Mistake:** Drawing apples and cherries overlapping, which violates Premise 2.

</details>

---

### **Q6.** 
**Statements:**
1. Some cars are buses.
2. No bus is a train.

**Conclusions:**
I. Some cars are not trains.
II. Some trains are not cars.

> 🎯 **Hint:** Look at the portion of cars that overlaps with buses.

<details><summary>✅ Solution</summary>

**Step-by-Step Solution:**
1. Let Cars = $C$, Buses = $B$, and Trains = $T$.
2. We have $C \cap B \neq \emptyset$ and $B \cap T = \emptyset$.
3. Evaluating Conclusion I: There are elements in $C$ that are also in $B$. Since no elements in $B$ can be in $T$, those elements of $C$ cannot be in $T$. Thus, "Some cars are not trains" is valid.
4. Evaluating Conclusion II: We can draw all trains inside cars (as long as they don't touch buses). Thus, "Some trains are not cars" is not definitely true. Invalid.

**Answer:** Only Conclusion I follows.
**Shortcut:** "Some + No" between $C \to B \to T$ yields "Some $C$ are not $T$".
**Difficulty:** ⭐⭐☆☆☆ | **Target Time:** 35 seconds
**Common Mistake:** Reversing the particular negative to conclude "Some trains are not cars."

</details>

---

### **Q7.** 
**Statements:**
1. All roads are paths.
2. Some paths are highways.

**Conclusions:**
I. Some roads are highways.
II. All roads are highways.

> 🎯 **Hint:** Check the minimal Venn overlap.

<details><summary>✅ Solution</summary>

**Step-by-Step Solution:**
1. Let Roads = $R$, Paths = $P$, and Highways = $H$.
2. Premise 1: $R \subseteq P$.
3. Premise 2: $P \cap H \neq \emptyset$.
4. In the minimal Venn, $R$ and $H$ do not overlap. Thus, Conclusion I is invalid.
5. Since "Some roads are highways" is invalid, "All roads are highways" is also invalid in the definite sense.

**Answer:** Neither Conclusion I nor II follows.
**Shortcut:** "All" + "Some" with a middle term does not guarantee any relationship between the outer terms.
**Difficulty:** ⭐☆☆☆☆ | **Target Time:** 15 seconds
**Common Mistake:** Assuming that because roads are paths, and some paths are highways, some roads must be highways.

</details>

---

### **Q8.** 
**Statements:**
1. No window is a door.
2. Some doors are walls.

**Conclusions:**
I. Some walls are not windows.
II. No wall is a window.

> 🎯 **Hint:** Check the intersection of the doors that are walls.

<details><summary>✅ Solution</summary>

**Step-by-Step Solution:**
1. Let Windows = $W$, Doors = $D$, and Walls = $A$.
2. We have $W \cap D = \emptyset$ and $D \cap A \neq \emptyset$.
3. Evaluating Conclusion I: The walls that are doors ($D \cap A$) cannot be windows because no door is a window. Thus, "Some walls are not windows" is valid.
4. Evaluating Conclusion II: We can easily draw a Venn where some walls are windows (outside the door set). So "No wall is a window" is not definitely true. Invalid.

**Answer:** Only Conclusion I follows.
**Shortcut:** "No A is B" + "Some B are C" $\implies$ "Some C are not A."
**Difficulty:** ⭐⭐☆☆☆ | **Target Time:** 30 seconds
**Common Mistake:** Marking Conclusion II as valid because doors and windows are disjoint.

</details>

---

### **Q9.** 
**Statements:**
1. Each key is a metal.
2. Every metal is heavy.

**Conclusions:**
I. Some heavy are keys.
II. All keys are heavy.

> 🎯 **Hint:** Convert "Each" and "Every" to standard logical operators.

<details><summary>✅ Solution</summary>

**Step-by-Step Solution:**
1. Conversions:
    *   Each key is a metal $\implies$ All keys are metals ($K \subseteq M$).
    *   Every metal is heavy $\implies$ All metals are heavy ($M \subseteq H$).
2. Combining gives: $K \subseteq M \subseteq H \implies K \subseteq H$.
3. Evaluating Conclusion I: Since $K \subseteq H$, they must overlap. Thus, "Some heavy are keys" is valid.
4. Evaluating Conclusion II: Since $K \subseteq H$, "All keys are heavy" is valid.

**Answer:** Both Conclusions I and II follow.
**Shortcut:** Nested circles mean $A \subseteq B \subseteq C \implies A \subseteq C$ and $C \cap A \neq \emptyset$.
**Difficulty:** ⭐☆☆☆☆ | **Target Time:** 15 seconds
**Common Mistake:** Treating "Each" or "Every" as "Some."

</details>

---

### **Q10.** 
**Statements:**
1. All maps are guides.
2. No guide is a book.

**Conclusions:**
I. Some maps are books.
II. No map is a book.

> 🎯 **Hint:** Check if maps are fully contained inside guides.

<details><summary>✅ Solution</summary>

**Step-by-Step Solution:**
1. Let Maps = $M$, Guides = $G$, and Books = $B$.
2. We have $M \subseteq G$ and $G \cap B = \emptyset$.
3. Since $M \subseteq G$ and $G$ has no overlap with $B$, $M$ cannot overlap with $B$. Thus, $M \cap B = \emptyset$.
4. Evaluating Conclusion I: Some maps are books is invalid.
5. Evaluating Conclusion II: No map is a book is valid.

**Answer:** Only Conclusion II follows.
**Shortcut:** If $X \subseteq Y$ and $Y \cap Z = \emptyset \implies X \cap Z = \emptyset$.
**Difficulty:** ⭐☆☆☆☆ | **Target Time:** 20 seconds
**Common Mistake:** Drawing maps overlapping with books.

</details>
