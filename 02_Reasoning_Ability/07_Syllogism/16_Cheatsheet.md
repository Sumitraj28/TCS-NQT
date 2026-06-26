# Syllogism - Cheatsheet

A compact reference sheet of boxed formulas and rules for instant lookup.

---

## 📐 1. Set-Theory Formulas

### Universal Affirmative ("All A are B")
$$\boxed{A \subseteq B \iff A \cap B' = \emptyset}$$

### Universal Negative ("No A is B")
$$\boxed{A \cap B = \emptyset}$$

### Particular Affirmative ("Some A are B")
$$\boxed{A \cap B \neq \emptyset}$$

### Particular Negative ("Some A are not B")
$$\boxed{A \cap B' \neq \emptyset}$$

---

## 📐 2. Exclusive & Special Quantifier Formulas

### The Exclusivity Rule ("Only A is B")
$$\boxed{B \subseteq A \quad \mathbf{and} \quad B \cap C = \emptyset \quad (\forall C \neq A)}$$

### The Dual Constraint Rule ("Only a few A are B")
$$\boxed{(A \cap B \neq \emptyset) \quad \mathbf{and} \quad (A \cap B' \neq \emptyset)}$$

---

## 📐 3. Deductive Chains

### Nested Containers (Barbara Syllogism)
$$\boxed{A \subseteq B \quad \mathbf{and} \quad B \subseteq C \implies A \subseteq C \quad \mathbf{and} \quad C \cap A \neq \emptyset}$$

### Disjoint Containers (Celarent Syllogism)
$$\boxed{A \subseteq B \quad \mathbf{and} \quad B \cap C = \emptyset \implies A \cap C = \emptyset}$$

### Intersecting Containers (Darii Syllogism)
$$\boxed{A \cap B \neq \emptyset \quad \mathbf{and} \quad B \subseteq C \implies A \cap C \neq \emptyset}$$

### Negative Intersections (Ferio Syllogism)
$$\boxed{A \cap B \neq \emptyset \quad \mathbf{and} \quad B \cap C = \emptyset \implies A \cap C' \neq \emptyset}$$
