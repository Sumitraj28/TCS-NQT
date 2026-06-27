# Seating Arrangement — Complete Notes

---

## 1. Linear Arrangements

Linear arrangement involves placing objects or people in a row (or multiple rows) based on given constraints.

### Single Row
*   **Facing North:** Left of a person is towards the left of the page. Right is towards the right of the page.
    $$\text{[Left]} \leftarrow A - B - C - D - E \rightarrow \text{[Right]}$$
*   **Facing South:** Left of a person is towards the right of the page. Right is towards the left of the page.
    $$\text{[Right]} \leftarrow A - B - C - D - E \rightarrow \text{[Left]}$$

### Double Row (Facing Each Other)
Often involves two rows where people in Row 1 face South and people in Row 2 face North.
*   *TCS Trick:* If $X$ is opposite $Y$ and $X$ is facing North, then $Y$ is facing South. Pay close attention to who is to the "immediate left" of whom, as the left of a South-facing person is opposite to the left of a North-facing person.

---

## 2. Circular Arrangements

Circular arrangement involves placing people around a circular table.

### Case A: Facing Inwards (Towards the Center)
*   **Right Turn:** Counter-clockwise direction.
*   **Left Turn:** Clockwise direction.
*   *Tip:* Think of sitting at the bottom of the circle facing up. Left is your left, right is your right.

### Case B: Facing Outwards (Away from the Center)
*   **Right Turn:** Clockwise direction.
*   **Left Turn:** Counter-clockwise direction.
*   *Tip:* The directions are exactly opposite to the facing inwards scenario.

### Case C: Mixed Facing
Some people face the center, while others face away from the center.
*   *Rule:* Do not start drawing positions from a person whose facing direction is unknown. Find a clue that specifies both the position and the facing direction of a person to anchor your circle.

---

## 3. General Seating Rules & Clues

To solve seating arrangements efficiently:
1.  **Identify Definite Clues:** Look for clues that give a fixed position (e.g., "A sits at the extreme left end of the row" or "B sits third to the right of C"). Do not start with negative clues (e.g., "A does not sit next to B").
2.  **Define Left vs. Immediate Left:**
    *   "$A$ sits to the left of $B$" means $A$ is somewhere to the left of $B$, not necessarily adjacent.
    *   "$A$ sits to the **immediate left** of $B$" means $A$ is directly next to $B$ on his left side.
3.  **Read Conjunctions Carefully:**
    *   "A sits second to the left of B **and** is third to the right of C": The word **"and"** refers to the first person (**A**).
    *   "A sits second to the left of B **who** is third to the right of C": The word **"who"** refers to the second person (**B**).
