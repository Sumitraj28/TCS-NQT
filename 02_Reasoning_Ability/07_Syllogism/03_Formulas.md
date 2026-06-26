# Syllogism - Formal Logical Formulas & Set-Theory Derivations

This guide establishes the mathematical foundation of Syllogisms using Set Theory. In mathematical logic, categorical propositions are represented as operations on sets.

---

## 1. 📐 Universal Affirmative ("All $A$ are $B$")

### Formula
$$\boxed{A \subseteq B \iff A \cap B' = \emptyset}$$
*   **$A$**: Subject set.
*   **$B$**: Predicate set.
*   **$B'$**: Complement of set $B$ (all elements not in $B$).

### Derivation
By definition, "All $A$ are $B$" means that every element $x \in A$ must also satisfy $x \in B$. If there were an element in $A$ that was not in $B$ ($x \in A \cap B'$), the premise would be violated. Therefore, the set of elements in $A$ but not in $B$ must be empty:
$$A \setminus B = A \cap B' = \emptyset$$

### Immediate Worked Example
*   **Scenario**: "All Laptops ($A$) are Computers ($B$)."
*   **Mathematical Model**: Let $A = \{L_1, L_2\}$ and $B = \{L_1, L_2, C_1\}$.
*   **Verification**:
    $$A \cap B' = \{L_1, L_2\} \cap \{C_1\}' = \{L_1, L_2\} \cap \{\text{Everything except } L_1, L_2, C_1\} = \emptyset$$
    Since the intersection is empty, the subset relation $A \subseteq B$ holds.

---

## 2. 📐 Universal Negative ("No $A$ is $B$")

### Formula
$$\boxed{A \cap B = \emptyset}$$

### Derivation
"No $A$ is $B$" means that there is no element that is a member of both set $A$ and set $B$ simultaneously. In set theory, the collection of elements shared by both sets is their intersection ($A \cap B$). For this relation to hold, this intersection must contain zero elements:
$$A \cap B = \emptyset$$

### Immediate Worked Example
*   **Scenario**: "No Circle ($A$) is a Square ($B$)."
*   **Mathematical Model**: Let $A = \{C_1, C_2\}$ and $B = \{S_1, S_2\}$.
*   **Verification**:
    $$A \cap B = \{C_1, C_2\} \cap \{S_1, S_2\} = \emptyset$$
    Because the intersection is empty, the sets are disjoint, validating the negative universal relationship.

---

## 3. 📐 Particular Affirmative ("Some $A$ are $B$")

### Formula
$$\boxed{A \cap B \neq \emptyset}$$

### Derivation
In mathematical logic, the word "some" is defined as *"there exists at least one"* ($\exists x$). Therefore, "Some $A$ are $B$" implies that there exists at least one element $x$ such that:
$$x \in A \quad \text{and} \quad x \in B \implies x \in (A \cap B)$$
Since there is at least one element in the intersection, the intersection cannot be the empty set:
$$A \cap B \neq \emptyset$$

### Immediate Worked Example
*   **Scenario**: "Some Engineers ($A$) are Artists ($B$)."
*   **Mathematical Model**: Let $A = \{E_1, E_2, E_3\}$ and $B = \{E_3, A_1\}$.
*   **Verification**:
    $$A \cap B = \{E_1, E_2, E_3\} \cap \{E_3, A_1\} = \{E_3\}$$
    Since $\{E_3\} \neq \emptyset$, the particular relationship is mathematically valid.

---

## 4. 📐 Particular Negative ("Some $A$ are not $B$")

### Formula
$$\boxed{A \cap B' \neq \emptyset}$$

### Derivation
"Some $A$ are not $B$" asserts the existence of at least one element $x$ that belongs to set $A$ but does not belong to set $B$ ($x \notin B$, which is equivalent to $x \in B'$). Therefore, the set difference $A \setminus B$, represented as $A \cap B'$, must contain at least one element:
$$A \cap B' \neq \emptyset$$

### Immediate Worked Example
*   **Scenario**: "Some Cars ($A$) are not Electric ($B$)."
*   **Mathematical Model**: Let $A = \{\text{Petrol\_Car}, \text{EV\_Car}\}$ and $B = \{\text{EV\_Car}, \text{EV\_Bike}\}$.
*   **Verification**:
    $$A \cap B' = \{\text{Petrol\_Car}, \text{EV\_Car}\} \cap \{\text{Petrol\_Car}, \text{EV\_Bike}\} = \{\text{Petrol\_Car}\}$$
    Since $\{\text{Petrol\_Car}\} \neq \emptyset$, the particular negative relationship holds.
