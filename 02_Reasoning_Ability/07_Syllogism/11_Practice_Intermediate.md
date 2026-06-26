# Syllogism - Practice Intermediate (10 Questions)

Practice these 10 intermediate-level questions featuring three premises, possibility statements, and Either-Or cases.

---

### **Q1.** 
**Statements:**
1. All shirts are pants.
2. Some pants are jackets.
3. No jacket is a coat.

**Conclusions:**
I. Some pants are not coats.
II. All pants being coats is a possibility.

> 🎯 **Hint:** Look at the overlap between pants and jackets, and its relation with coats.

<details><summary>✅ Solution</summary>

**Step-by-Step Solution:**
1. Let Shirts = $S$, Pants = $P$, Jackets = $J$, and Coats = $C$.
2. We have $S \subseteq P$, $P \cap J \neq \emptyset$, and $J \cap C = \emptyset$.
3. Evaluating Conclusion I: There are elements in $P$ that overlap with $J$. Since no element of $J$ can be in $C$, these overlapping elements of $P$ can never be in $C$. Thus, "Some pants are not coats" is valid.
4. Evaluating Conclusion II: Since some pants are definitely not coats, it is impossible for all pants to be coats. Thus, Conclusion II is invalid.

**Answer:** Only Conclusion I follows.
**Shortcut:** "Some + No" combination yields a definite "Some not" conclusion, which immediately invalidates the corresponding "All is a possibility" claim.
**Difficulty:** ⭐⭐⭐☆☆ | **Target Time:** 40 seconds
**Common Mistake:** Marking Conclusion II as possible because pants is a large set.

</details>

---

### **Q2.** 
**Statements:**
1. Some inputs are devices.
2. All devices are systems.
3. No system is a network.

**Conclusions:**
I. Some inputs are systems.
II. No device is a network.

> 🎯 **Hint:** Trace the subset relations.

<details><summary>✅ Solution</summary>

**Step-by-Step Solution:**
1. Let Inputs = $I$, Devices = $D$, Systems = $S$, and Networks = $N$.
2. We have $I \cap D \neq \emptyset$, $D \subseteq S$, and $S \cap N = \emptyset$.
3. Evaluating Conclusion I: Since $I \cap D \neq \emptyset$ and $D \subseteq S$, the elements of $I$ in $D$ must also be in $S$. Thus, $I \cap S \neq \emptyset$. Valid.
4. Evaluating Conclusion II: Since $D \subseteq S$ and $S \cap N = \emptyset$, $D$ can have no overlap with $N$. Thus, "No device is a network" is valid.

**Answer:** Both Conclusions I and II follow.
**Shortcut:** If $X \subseteq Y$ and $Y \cap Z = \emptyset \implies X \cap Z = \emptyset$.
**Difficulty:** ⭐⭐⭐☆☆ | **Target Time:** 35 seconds
**Common Mistake:** Missing the fact that "No device is a network" is definitely true.

</details>

---

### **Q3.** 
**Statements:**
1. All red are blue.
2. No blue is green.
3. Some green are yellow.

**Conclusions:**
I. Some yellow are not blue.
II. Some red can be green.

> 🎯 **Hint:** Look at the relationship between yellow, green, and blue.

<details><summary>✅ Solution</summary>

**Step-by-Step Solution:**
1. Let Red = $R$, Blue = $B$, Green = $G$, and Yellow = $Y$.
2. We have $R \subseteq B$, $B \cap G = \emptyset$, and $G \cap Y \neq \emptyset$.
3. Evaluating Conclusion I: The elements of $Y$ that are in $G$ cannot be in $B$ because $G \cap B = \emptyset$. Thus, those yellow elements are not blue. Valid.
4. Evaluating Conclusion II: Since $R \subseteq B$ and $B \cap G = \emptyset$, we have $R \cap G = \emptyset$. Red and green can never overlap, so this possibility is invalid.

**Answer:** Only Conclusion I follows.
**Shortcut:** "Some + No" combination between green and blue creates a guaranteed "Some yellow are not blue" relationship.
**Difficulty:** ⭐⭐⭐☆☆ | **Target Time:** 45 seconds
**Common Mistake:** Marking Conclusion II as valid under the assumption that "possibility" makes everything true.

</details>

---

### **Q4.** 
**Statements:**
1. No keys are locks.
2. Some locks are doors.
3. All doors are windows.

**Conclusions:**
I. All keys being windows is a possibility.
II. All windows being keys is a possibility.

> 🎯 **Hint:** Check which elements of windows are locked out of keys.

<details><summary>✅ Solution</summary>

**Step-by-Step Solution:**
1. Let Keys = $K$, Locks = $L$, Doors = $D$, and Windows = $W$.
2. We have $K \cap L = \emptyset$, $L \cap D \neq \emptyset$, and $D \subseteq W$.
3. Evaluating Conclusion I: Can we draw all keys inside windows? Yes, we can make $K \subseteq W$ (outside the lock set) without violating any premises. Valid.
4. Evaluating Conclusion II: Can we draw all windows inside keys? Since $L \cap D \neq \emptyset$ and $D \subseteq W$, there are some windows that are doors, which are also locks. Since no lock can touch keys ($K \cap L = \emptyset$), those window-lock elements can never enter keys. Thus, all windows can never be keys. Invalid.

**Answer:** Only Conclusion I follows.
**Shortcut:** A subset relation ($D \subseteq W$) combined with a negative overlap ($L \cap K = \emptyset$ where $L \cap D \neq \emptyset$) blocks the larger set $W$ from fully entering $K$, but does not block $K$ from fully entering $W$.
**Difficulty:** ⭐⭐⭐⭐☆ | **Target Time:** 60 seconds
**Common Mistake:** Thinking that since all keys can be windows, all windows must also be able to be keys (reversal error).

</details>

---

### **Q5.** 
**Statements:**
1. Some tables are chairs.
2. Some chairs are desks.
3. No desk is a bench.

**Conclusions:**
I. Some tables are benches.
II. No table is a bench.

> 🎯 **Hint:** Check if there is any direct connection or if they form an Either-Or case.

<details><summary>✅ Solution</summary>

**Step-by-Step Solution:**
1. Let Tables = $T$, Chairs = $C$, Desks = $D$, and Benches = $B$.
2. We have $T \cap C \neq \emptyset$, $C \cap D \neq \emptyset$, and $D \cap B = \emptyset$.
3. Evaluating Conclusion I: In the minimal Venn, $T$ and $B$ do not overlap. Invalid.
4. Evaluating Conclusion II: We can easily draw $T$ and $B$ overlapping without violating any premises. Invalid.
5. They share the same terms and are a `Some` + `No` pair.

**Answer:** Either Conclusion I or II follows.
**Shortcut:** Two unconnected entities with `Some` + `No` conclusions always form an Either-Or pair.
**Difficulty:** ⭐⭐⭐☆☆ | **Target Time:** 35 seconds
**Common Mistake:** Marking "Neither I nor II follows" because both are individually false.

</details>

---

### **Q6.** 
**Statements:**
1. All red are blue.
2. All blue are green.
3. No green is yellow.

**Conclusions:**
I. Some blue are not yellow.
II. All yellow can be red.

> 🎯 **Hint:** Look at the subset relationships and the negative boundary.

<details><summary>✅ Solution</summary>

**Step-by-Step Solution:**
1. Let Red = $R$, Blue = $B$, Green = $G$, and Yellow = $Y$.
2. We have $R \subseteq B \subseteq G$ and $G \cap Y = \emptyset$.
3. Since $B \subseteq G$ and $G \cap Y = \emptyset$, we have $B \cap Y = \emptyset$. Since $B$ is non-empty, "Some blue are not yellow" is valid.
4. Since $R \subseteq G$ and $G \cap Y = \emptyset$, we have $R \cap Y = \emptyset$. Yellow and red can never overlap, so "All yellow can be red" is invalid.

**Answer:** Only Conclusion I follows.
**Shortcut:** $X \subseteq Y$ and $Y \cap Z = \emptyset \implies X \cap Z = \emptyset$ (no overlap possible).
**Difficulty:** ⭐⭐⭐☆☆ | **Target Time:** 30 seconds
**Common Mistake:** Missing the fact that $B \cap Y = \emptyset$ implies that *no* blue is yellow, which also validates *some* blue are not yellow.

</details>

---

### **Q7.** 
**Statements:**
1. Some inputs are devices.
2. No device is a terminal.
3. Some terminals are consoles.

**Conclusions:**
I. Some inputs can be consoles.
II. All consoles can be devices.

> 🎯 **Hint:** Check which consoles are restricted from devices.

<details><summary>✅ Solution</summary>

**Step-by-Step Solution:**
1. Let Inputs = $I$, Devices = $D$, Terminals = $T$, and Consoles = $C$.
2. We have $I \cap D \neq \emptyset$, $D \cap T = \emptyset$, and $T \cap C \neq \emptyset$.
3. Evaluating Conclusion I: There is no constraint between $I$ and $C$. So we can draw them overlapping. The possibility is valid.
4. Evaluating Conclusion II: Since some consoles are terminals ($T \cap C \neq \emptyset$), and no terminal can touch devices ($D \cap T = \emptyset$), the consoles that are terminals can never touch devices. Thus, all consoles can never be devices. Invalid.

**Answer:** Only Conclusion I follows.
**Shortcut:** The portion of consoles that overlap with terminals can never enter devices. Thus, "All consoles can be devices" is blocked.
**Difficulty:** ⭐⭐⭐☆☆ | **Target Time:** 45 seconds
**Common Mistake:** Marking Conclusion II as possible by ignoring the terminal-console intersection.

</details>

---

### **Q8.** 
**Statements:**
1. All circles are rings.
2. Some rings are loops.
3. Some loops are curves.

**Conclusions:**
I. Some circles are loops.
II. Some curves are rings.

> 🎯 **Hint:** Look for direct connections in the minimal Venn diagram.

<details><summary>✅ Solution</summary>

**Step-by-Step Solution:**
1. Let Circles = $C$, Rings = $R$, Loops = $L$, and Curves = $V$.
2. We have $C \subseteq R$, $R \cap L \neq \emptyset$, and $L \cap V \neq \emptyset$.
3. Evaluating Conclusion I: In the minimal Venn, $C$ and $L$ do not touch. Invalid.
4. Evaluating Conclusion II: In the minimal Venn, $V$ and $R$ do not touch. Invalid.

**Answer:** Neither Conclusion I nor II follows.
**Shortcut:** "All" + "Some" + "Some" chain with no negative statements does not guarantee any relations between the non-adjacent sets.
**Difficulty:** ⭐⭐☆☆☆ | **Target Time:** 20 seconds
**Common Mistake:** Drawing loops and curves overlapping with circles in the minimal diagram.

</details>

---

### **Q9.** 
**Statements:**
1. No student is a scholar.
2. No scholar is an athlete.
3. All athletes are players.

**Conclusions:**
I. Some players are not scholars.
II. Some players are not students.

> 🎯 **Hint:** Look at the relation between athletes and players.

<details><summary>✅ Solution</summary>

**Step-by-Step Solution:**
1. Let Students = $S$, Scholars = $C$, Athletes = $A$, and Players = $P$.
2. We have $S \cap C = \emptyset$, $C \cap A = \emptyset$, and $A \subseteq P$.
3. Evaluating Conclusion I: Since $A \subseteq P$, and $C \cap A = \emptyset$, the players that are athletes cannot be scholars. Thus, "Some players are not scholars" is valid.
4. Evaluating Conclusion II: Can we draw all players inside students? Yes, as long as they don't touch scholars. Thus, we cannot definitely say "Some players are not students." Invalid.

**Answer:** Only Conclusion I follows.
**Shortcut:** "All X are Y" + "No X is Z" $\implies$ "Some Y are not Z."
**Difficulty:** ⭐⭐⭐☆☆ | **Target Time:** 45 seconds
**Common Mistake:** Marking Conclusion II as valid by confusing student-scholar disjointedness with student-player relations.

</details>

---

### **Q10.** 
**Statements:**
1. Some keys are locks.
2. No lock is a door.
3. No door is a window.

**Conclusions:**
I. Some keys are not doors.
II. Some windows are locks.

> 🎯 **Hint:** Check the overlap of keys and locks.

<details><summary>✅ Solution</summary>

**Step-by-Step Solution:**
1. Let Keys = $K$, Locks = $L$, Doors = $D$, and Windows = $W$.
2. We have $K \cap L \neq \emptyset$, $L \cap D = \emptyset$, and $D \cap W = \emptyset$.
3. Evaluating Conclusion I: The keys that are locks ($K \cap L$) cannot be doors. Thus, "Some keys are not doors" is valid.
4. Evaluating Conclusion II: In the minimal Venn, windows and locks do not touch. Invalid.

**Answer:** Only Conclusion I follows.
**Shortcut:** "Some + No" combination yields a definite "Some not" conclusion.
**Difficulty:** ⭐⭐☆☆☆ | **Target Time:** 30 seconds
**Common Mistake:** Thinking that because no door is a window, some windows must be locks.

</details>
