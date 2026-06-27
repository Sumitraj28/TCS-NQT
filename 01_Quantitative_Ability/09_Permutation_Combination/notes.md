# Permutations and Combinations — Complete Notes

---

## 1. The Fundamental Counting Principles

Combinatorics is the study of counting possibilities. Two core rules form the base of all counting problems:

### The Addition Rule (The "OR" Rule)
If a task can be performed in $m$ ways, and another independent task can be performed in $n$ ways, then either of the tasks can be performed in:

$$\text{Total Ways} = m + n$$

*   *Usage:* When selecting between mutually exclusive options. E.g., choosing 1 book to read from 5 novels OR 3 history books: $5 + 3 = 8$ choices.

### The Product Rule (The "AND" Rule)
If a task consists of multiple consecutive steps, where the first step can be done in $m$ ways and the second step can be done in $n$ ways, the entire task can be performed in:

$$\text{Total Ways} = m \times n$$

*   *Usage:* When operations must occur in sequence. E.g., choosing an outfit consisting of 1 shirt out of 5 AND 1 pair of trousers out of 3: $5 \times 3 = 15$ outfits.

---

## 2. Permutations vs. Combinations

Understanding the difference between arrangement (order matters) and selection (order does not matter) is the most critical hurdle in this topic.

| Attribute | Permutation | Combination |
| :--- | :--- | :--- |
| **Core Concept** | **Arrangement** (Order matters) | **Selection** (Order does not matter) |
| **Key Question** | In how many ways can we *arrange*? | In how many ways can we *choose*? |
| **Keywords** | Arrange, line, row, schedule, signal | Select, choose, committee, team, group |
| **Formula** | $^nP_r = \frac{n!}{(n-r)!}$ | $^nC_r = \frac{n!}{r!(n-r)!}$ |

### Permutations ($^nP_r$)
Used to find the number of ways to arrange $r$ objects out of a total pool of $n$ distinct objects.
*   **Identical Objects Rule:** If there are $n$ objects where $p$ are of one type, $q$ are of a second type, and $r$ are of a third type, the number of unique arrangements is:
    $$\text{Arrangements} = \frac{n!}{p! \cdot q! \cdot r!}$$
    *Example:* Arranging the letters of the word "APPLE" ($N=5$, 'P' repeats twice):
    $$\text{Arrangements} = \frac{5!}{2!} = \frac{120}{2} = 60$$

### Combinations ($^nC_r$)
Used to find the number of ways to select $r$ objects out of $n$ distinct objects, where the sequence of selection is irrelevant.
*   **Properties of $^nC_r$:**
    *   $^nC_r = ^nC_{n-r}$ (Choosing $r$ objects is identical to choosing the $n-r$ objects to leave behind).
    *   $^nC_0 = ^nC_n = 1$
    *   $^nC_1 = n$

---

## 3. Circular Permutations

When arranging objects in a circle rather than a straight line, there is no absolute starting point. Shifting every object by one position does not create a new arrangement.

### Case 1: Distinct Left and Right (e.g., People Sitting at a Round Table)
If $n$ distinct objects are arranged in a circle, and clockwise and counter-clockwise arrangements are considered different:

$$\text{Circular Permutations} = (n-1)!$$

### Case 2: Left and Right are Indistinguishable (e.g., Beads on a Necklace, Flowers on a Garland)
If turning the circle over does not change the pattern (i.e., clockwise and counter-clockwise arrangements are identical):

$$\text{Circular Permutations} = \frac{(n-1)!}{2}$$

---

## 4. Cross-References & Overlapping Topics

*   **Probability calculations:** Permutations and combinations are the primary tools used to determine the sizes of the event space $N(E)$ and sample space $N(S)$. See [Probability Notes](file:///Users/rajsumit/Desktop/TCS-NQT/01_Quantitative_Ability/10_Probability/notes.md) to see how combinations are used to solve marble, card, and committee probability questions.
