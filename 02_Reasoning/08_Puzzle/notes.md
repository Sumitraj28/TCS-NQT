# Puzzles — Complete Notes

---

## 1. Floor-Based Puzzles

In floor-based puzzles, individuals live on different floors of a building. By convention, the ground floor is numbered $1$, the floor above it is $2$, and the top floor is $N$.

### Floor Template
Create a vertical table to represent the building. Always sketch multiple case columns next to it to handle possibilities:

| Floor | Case 1 (Person) | Case 2 (Person) |
| :---: | :---: | :---: |
| 8 | | |
| 7 | | |
| 6 | | |
| 5 | | |
| 4 | | |
| 3 | | |
| 2 | | |
| 1 | | |

### Core Clues & Solving Tricks
*   **Odd/Even Floor:** "A lives on an even-numbered floor" -> Place A in possibilities on floors 2, 4, 6, or 8.
*   **Gap Clues:** "There are three floors between A and B."
    *   If A is on floor 8, B must be on floor $8 - 3 - 1 = 4$.
*   **Above/Below:** "A lives immediately above B" means A and B are adjacent ($A = B + 1$). "A lives above B" means A is on any floor higher than B, not necessarily adjacent.

---

## 2. Box-Based Puzzles

Similar to floor puzzles, box puzzles involve boxes stacked on top of each other. However, the total number of positions is often not fixed at the start.

### Box Stack Template
Track positions from top to bottom.

| Position | Box Name |
| :---: | :---: |
| 1 (Top) | |
| 2 | |
| 3 | |
| 4 | |
| 5 (Bottom)| |

### Solving Tricks
*   **Anchor Items:** Find clues that link a box to the top or bottom position (e.g., "Box A is kept at the bottom-most position").
*   **Consecutive Chains:** If "Box A is immediately above B" and "Box B is immediately above C", treat $(A-B-C)$ as a single block of size 3 and see where it can fit in the stack.

---

## 3. Table-Based / Scheduling Puzzles

These involve distributing parameters (e.g., people, days of the week, cities, professions) into a grid.

### Scheduling Template (e.g., Monday to Sunday)
Use the fixed chronological sequence (days or months) as the anchor column:

| Day | Person | City |
| :--- | :--- | :--- |
| Monday | | |
| Tuesday | | |
| Wednesday | | |
| Thursday | | |
| Friday | | |
| Saturday | | |
| Sunday | | |

### Solving Tricks
1.  **Fixed Column:** Always anchor the table with the parameter that has a natural order (Days of the week, Months, or Floor numbers).
2.  **Cross Out Table:** Maintain a list of remaining variables. Every time a person is placed, cross them off.
3.  **Represent Negative Clues:** If "A does not go to Delhi on Wednesday," write " Delhi" in the Wednesday row to ensure you don't make this mistake later.
