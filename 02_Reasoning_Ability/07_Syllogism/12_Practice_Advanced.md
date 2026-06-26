# Syllogism - Practice Advanced (8 Questions)

Master these 8 advanced-level questions featuring "Only a few", "Only", four-statement chains, and complex logical constraints.

---

### **Q1.** 
**Statements:**
1. Only a few blue are green.
2. Only green are yellow.
3. All blue are pink.
4. No pink is black.

**Conclusions:**
I. No yellow is black.
II. All pink can never be green.

> 🎯 **Hint:** Convert the "Only" statement and track the exclusivity of yellow.

<details><summary>✅ Solution</summary>

**Step-by-Step Solution:**
1. Let Blue = $B$, Green = $G$, Yellow = $Y$, Pink = $P$, and Black = $K$.
2. Premise 1: $B \cap G \neq \emptyset$ and $B \cap G' \neq \emptyset$ (Some $B$ are not $G$).
3. Premise 2: Only $G$ are $Y \implies Y \subseteq G$. Crucially, $Y$ cannot overlap with any other set besides $G$.
4. Premise 3: $B \subseteq P$.
5. Premise 4: $P \cap Black = \emptyset$.
6. Evaluating Conclusion I: Since $Y$ is exclusive to $G$, and black is a separate set, can they overlap? No. The exclusivity of $Y$ means it cannot overlap with black. Thus, "No yellow is black" is valid.
7. Evaluating Conclusion II: "All pink can never be green" means "All pink is green is impossible." Let us test if all pink *can* be green ($P \subseteq G$). 
    *   If $P \subseteq G$, then since $B \subseteq P$, we would have $B \subseteq G$.
    *   However, Premise 1 states "Only a few blue are green", which requires some $B$ to be outside $G$ ($B \cap G' \neq \emptyset$).
    *   Since $B \subseteq P$, if all $P$ were inside $G$, all $B$ would also be inside $G$, violating Premise 1.
    *   Therefore, all pink can never be green. Valid.

**Answer:** Both Conclusions I and II follow.
**Shortcut:** If $X \subseteq Y$, then any negative constraint on $X$ ($X \not\subseteq Z$) also prevents $Y$ from being subset of $Z$ ($Y \not\subseteq Z$).
**Difficulty:** ⭐⭐⭐⭐⭐ | **Target Time:** 90 seconds
**Common Mistake:** Forgetting that "Only green are yellow" locks yellow from intersecting black, or missing the transitivity of "Only a few blue are green" to the pink set.

</details>

---

### **Q2.** 
**Statements:**
1. Only tables are chairs.
2. Only a few tables are desks.
3. No desk is a bench.

**Conclusions:**
I. Some chairs being desks is a possibility.
II. All tables can be desks.

> 🎯 **Hint:** Apply the exclusivity of chairs.

<details><summary>✅ Solution</summary>

**Step-by-Step Solution:**
1. Let Tables = $T$, Chairs = $C$, Desks = $D$, and Benches = $B$.
2. Premise 1: $C \subseteq T$, with $C$ exclusive to $T$ (cannot overlap with $D$ or $B$).
3. Premise 2: Only a few $T$ are $D \implies T \cap D \neq \emptyset$ and $T \cap D' \neq \emptyset$.
4. Premise 3: $D \cap B = \emptyset$.
5. Evaluating Conclusion I: Since $C$ is exclusive to $T$, it can never overlap with $D$. Thus, "Some chairs being desks is a possibility" is invalid.
6. Evaluating Conclusion II: "Only a few tables are desks" means some tables must remain outside desks. Thus, all tables can never be desks. Invalid.

**Answer:** Neither Conclusion I nor II follows.
**Shortcut:** "Only A is B" locks B from touching any set. "Only a few A are B" prevents A from being fully inside B.
**Difficulty:** ⭐⭐⭐⭐☆ | **Target Time:** 50 seconds
**Common Mistake:** Allowing chairs to overlap with desks under the "possibility" conclusion.

</details>

---

### **Q3.** 
**Statements:**
1. Only a few inputs are outputs.
2. Some outputs are signals.
3. All signals are data.
4. No data is a network.

**Conclusions:**
I. Some outputs are not networks.
II. All inputs can be networks.

> 🎯 **Hint:** Trace the path from outputs through signals and data to networks.

<details><summary>✅ Solution</summary>

**Step-by-Step Solution:**
1. Let Inputs = $I$, Outputs = $O$, Signals = $S$, Data = $D$, and Networks = $N$.
2. We have:
    *   Only a few $I$ are $O \implies I \cap O \neq \emptyset$.
    *   $O \cap S \neq \emptyset$.
    *   $S \subseteq D$.
    *   $D \cap N = \emptyset$.
3. Evaluating Conclusion I: Since $S \subseteq D$ and $D \cap N = \emptyset$, we have $S \cap N = \emptyset$. Since some outputs are signals ($O \cap S \neq \emptyset$), those outputs that are signals can never be networks. Thus, "Some outputs are not networks" is valid.
4. Evaluating Conclusion II: Can we draw all inputs inside networks? 
    *   If all inputs are inside networks ($I \subseteq N$), then since $I \cap O \neq \emptyset$, some networks would overlap with outputs.
    *   Does this violate any premises? We know outputs cannot overlap with networks in the $S$ region, but they can overlap in other regions.
    *   However, if $I \subseteq N$, then since $I \cap O \neq \emptyset$, the overlap region $I \cap O$ must be inside $N$.
    *   Since $N \cap D = \emptyset$, this overlap region cannot touch $D$. This is perfectly fine (we can keep $I \cap O$ outside $S$ and $D$).
    *   Thus, we can draw all inputs inside networks. The possibility is valid.

**Answer:** Both Conclusions I and II follow.
**Shortcut:** "Some + All + No" chain creates a "Some-not" relation between outputs and networks. However, inputs are not constrained by this chain, so they can enter networks completely.
**Difficulty:** ⭐⭐⭐⭐⭐ | **Target Time:** 80 seconds
**Common Mistake:** Assuming that because outputs cannot be all networks, inputs also cannot be all networks.

</details>

---

### **Q4.** 
**Statements:**
1. Only a few keys are locks.
2. No lock is a door.
3. Some doors are windows.

**Conclusions:**
I. All keys can never be locks.
II. Some keys are not doors.

> 🎯 **Hint:** Look at the dual constraints of "Only a few" and the "No" statement.

<details><summary>✅ Solution</summary>

**Step-by-Step Solution:**
1. Let Keys = $K$, Locks = $L$, Doors = $D$, and Windows = $W$.
2. Premise 1: Only a few $K$ are $L \implies K \cap L \neq \emptyset$ and $K \cap L' \neq \emptyset$.
3. Premise 2: $L \cap D = \emptyset$.
4. Premise 3: $D \cap W \neq \emptyset$.
5. Evaluating Conclusion I: Since "Some keys are not locks" ($K \cap L' \neq \emptyset$) is a required premise, it is impossible for all keys to be locks. Thus, they can never be locks. Valid.
6. Evaluating Conclusion II: Since some keys are locks ($K \cap L \neq \emptyset$), and no lock is a door ($L \cap D = \emptyset$), those keys that are locks can never be doors. Thus, "Some keys are not doors" is valid.

**Answer:** Both Conclusions I and II follow.
**Shortcut:** "Only a few A are B" immediately makes "All A can be B" invalid, which validates "All A can never be B".
**Difficulty:** ⭐⭐⭐⭐☆ | **Target Time:** 60 seconds
**Common Mistake:** Missing the deduction that keys overlapping with locks are blocked from doors, leading to marking Conclusion II as invalid.

</details>

---

### **Q5.** 
**Statements:**
1. All red are blue.
2. Some blue are green.
3. No green is yellow.
4. Some yellow are pink.

**Conclusions:**
I. Some blue are not yellow.
II. All blue being yellow is a possibility.

> 🎯 **Hint:** Look at the overlap between blue and green.

<details><summary>✅ Solution</summary>

**Step-by-Step Solution:**
1. Let Red = $R$, Blue = $B$, Green = $G$, Yellow = $Y$, and Pink = $P$.
2. We have $R \subseteq B$, $B \cap G \neq \emptyset$, $G \cap Y = \emptyset$, and $Y \cap P \neq \emptyset$.
3. Evaluating Conclusion I: There are elements of $B$ in $G$. Since no green is yellow, these elements of $B$ can never be yellow. Thus, "Some blue are not yellow" is valid.
4. Evaluating Conclusion II: Since some blue are definitely not yellow, all blue can never be yellow. The possibility is invalid.

**Answer:** Only Conclusion I follows.
**Shortcut:** "Some B are G" + "No G is Y" $\implies$ "Some B are not Y" (definite truth). This immediately kills the possibility "All B can be Y".
**Difficulty:** ⭐⭐⭐⭐☆ | **Target Time:** 55 seconds
**Common Mistake:** Thinking all blue can be yellow because red can be yellow.

</details>

---

### **Q6.** 
**Statements:**
1. Only red is black.
2. No red is pink.
3. Some pink are green.

**Conclusions:**
I. No black is green.
II. Some green can be black.

> 🎯 **Hint:** Analyze the exclusive domain of black.

<details><summary>✅ Solution</summary>

**Step-by-Step Solution:**
1. Let Red = $R$, Black = $B$, Pink = $P$, and Green = $G$.
2. Premise 1 converts to: $B \subseteq R$, with $B$ exclusive to $R$ (cannot overlap with any other set).
3. Premise 2: $R \cap P = \emptyset$.
4. Premise 3: $P \cap G \neq \emptyset$.
5. Evaluating Conclusion I: Since $B$ is exclusive to $R$, it cannot touch any set other than $R$. Hence, $B$ cannot touch $G$. "No black is green" is valid.
6. Evaluating Conclusion II: Since black cannot touch any other set, "Some green can be black" is invalid.

**Answer:** Only Conclusion I follows.
**Shortcut:** Under the "Only A is B" rule, B can never overlap with any set C.
**Difficulty:** ⭐⭐⭐⭐☆ | **Target Time:** 45 seconds
**Common Mistake:** Thinking green can overlap with black because green is not directly linked to red.

</details>

---

### **Q7.** 
**Statements:**
1. Only a few A are B.
2. No B is C.
3. All C are D.
4. Some D are E.

**Conclusions:**
I. Some A are not D is a possibility.
II. All A being D is a possibility.

> 🎯 **Hint:** Test the possibility bounds for A and D.

<details><summary>✅ Solution</summary>

**Step-by-Step Solution:**
1. We have:
    *   Only a few A are B $\implies A \cap B \neq \emptyset$.
    *   No B is C $\implies B \cap C = \emptyset$.
    *   $C \subseteq D$.
    *   $D \cap E \neq \emptyset$.
2. Let us test Conclusion II first: Can we draw all A inside D ($A \subseteq D$)?
    *   We need $A \cap B \neq \emptyset$ and $B \cap C = \emptyset$ and $C \subseteq D$.
    *   If $A \subseteq D$, then the elements of $A \cap B$ are inside $D$. 
    *   Since $B \cap C = \emptyset$, these elements are outside $C$, which is fine because $C \subseteq D$ allows elements in $D$ to be outside $C$.
    *   No premise is violated. Thus, "All A being D is a possibility" is valid.
3. Evaluating Conclusion I: "Some A are not D is a possibility."
    *   In the minimal Venn, $A$ and $D$ do not overlap except potentially if we force them.
    *   Since they are not required to overlap completely, we can easily draw a diagram where some elements of $A$ are outside $D$.
    *   Thus, "Some A are not D is a possibility" is valid.

**Answer:** Both Conclusions I and II follow.
**Shortcut:** Since there is no negative constraint directly between A and D, both "All can be" and "Some are not" possibilities are valid.
**Difficulty:** ⭐⭐⭐⭐⭐ | **Target Time:** 85 seconds
**Common Mistake:** Concluding that since all A can be D, "Some A are not D is a possibility" must be false. Possibilities are independent.

</details>

---

### **Q8.** 
**Statements:**
1. Only a few fruits are sweet.
2. Only a few sweet are sour.
3. No sour is bitter.

**Conclusions:**
I. All sweet can be fruits.
II. All sweet can be bitter.

> 🎯 **Hint:** "Only a few A are B" allows all B to be A.

<details><summary>✅ Solution</summary>

**Step-by-Step Solution:**
1. Let Fruits = $F$, Sweet = $W$, Sour = $R$, and Bitter = $B$.
2. Premise 1: Only a few $F$ are $W \implies F \cap W' \neq \emptyset$.
3. Premise 2: Only a few $W$ are $R \implies W \cap R' \neq \emptyset$ (All $W$ cannot be $R$).
4. Premise 3: $R \cap B = \emptyset$.
5. Evaluating Conclusion I: Can we fit all sweet inside fruits ($W \subseteq F$)? Yes, the restriction is that all fruits cannot be sweet, not vice-versa. So this is valid.
6. Evaluating Conclusion II: Can we fit all sweet inside bitter ($W \subseteq B$)?
    *   If $W \subseteq B$, then since $W \cap R \neq \emptyset$ (from Premise 2), some elements of $B$ would have to overlap with $R$.
    *   However, Premise 3 states $R \cap B = \emptyset$.
    *   This is a contradiction. Thus, all sweet can never be bitter. Invalid.

**Answer:** Only Conclusion I follows.
**Shortcut:** If $X \cap Y \neq \emptyset$, then all $X$ cannot enter a set $Z$ if $Z \cap Y = \emptyset$.
**Difficulty:** ⭐⭐⭐⭐⭐ | **Target Time:** 80 seconds
**Common Mistake:** Missing the fact that sweet overlaps with sour, which prevents all sweet from entering bitter (since bitter and sour are disjoint).

</details>
