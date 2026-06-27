# Blood Relations — Complete Notes

---

## 1. Core Relationship Definitions

Understanding standard relationship terms is the first step in solving blood relation puzzles.

### Standard Mappings
*   **Father's side relations:** Paternal relations.
*   **Mother's side relations:** Maternal relations.
*   **Siblings:** Brothers and sisters.
*   **Spouse:** Husband or wife.
*   **Siblings-in-law:**
    *   *Brother-in-law:* Husband's/Wife's brother, or sister's husband.
    *   *Sister-in-law:* Husband's/Wife's sister, or brother's wife.
*   **Niece and Nephew:**
    *   *Nephew:* Brother's or sister's son.
    *   *Niece:* Brother's or sister's daughter.
*   **Cousin:** Child of one's uncle or aunt. (Note: "Cousin brother" or "Cousin sister" are grammatically incorrect and should be treated simply as "Cousin").

---

## 2. Diagrammatic Symbols & Rules

Drawing a family tree is the most reliable way to solve blood relation puzzles. Use a consistent set of symbols:

*   **Gender:**
    *   Male: represented by a **square** $[\ ]$ or a plus sign $(+)$.
    *   Female: represented by a **circle** $(\ )$ or a minus sign $(-)$.
*   **Marital Relationship (Couple):** Represented by a double-headed horizontal arrow ($\Leftrightarrow$ or $\rightleftharpoons$).
*   **Sibling Relationship:** Represented by a single horizontal line ($-$).
*   **Generation Gap (Vertical Relationship):** Represented by a vertical line ($|$), with the older generation on top and the younger generation below.

*Refer to [visualization.md](file:///Users/rajsumit/Desktop/TCS-NQT/02_Reasoning/02_Blood_Relation/visualization.md) for actual rendered family trees using these rules.*

---

## 3. Blood Relation Types

### A. Pointing / Statement-Based Relations
In these problems, a person points to someone and describes their relationship using a chain of connections.
*   **Rule:** Solve these backwards starting from "my" or "mine".
*   *Example:* Pointing to a photograph, Amit said, "She is the only daughter of my grandfather's only son." How is the woman related to Amit?
    1.  Start with "my grandfather's only son" -> Amit's father (assuming Amit is speaking paternal side).
    2.  Now substitute: "She is the only daughter of [Amit's father]" -> Amit's sister.
    3.  Therefore, the woman is Amit's sister.

### B. Family Puzzles
These involve a paragraph describing the relationships of multiple family members.
*   **Rule:** Build the family tree step-by-step. Do not make assumptions about gender based on names alone (unless explicitly stated).

### C. Coded Relations
Symbols represent relations. E.g., $A + B$ means $A$ is the brother of $B$.
*   **Rule:** Use gender elimination and generation-gap count checks to eliminate options quickly instead of drawing full trees for every option.
