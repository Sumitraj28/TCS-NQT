# Syllogism Venn Diagram Visualizations

Below are the standard representations of categorical propositions using Mermaid diagrams.

## 1. Universal Positive: "All A are B"

This shows set $A$ is entirely contained within set $B$ ($A \subseteq B$).

```mermaid
graph TD
    subgraph Set B
        A["Set A"]
    end
```

---

## 2. Universal Negative: "No A are B"

This shows set $A$ and set $B$ are completely disjoint ($A \cap B = \emptyset$).

```mermaid
graph LR
    A["Set A"]
    B["Set B"]
    A -.->|No Relation / Disjoint| B
```

---

## 3. Particular Positive: "Some A are B"

This shows that there is an intersection between set $A$ and set $B$ ($A \cap B \neq \emptyset$).

```mermaid
graph LR
    subgraph Set A
        direction LR
        a1[Only A]
        Intersection[Some A and B]
    end
    subgraph Set B
        direction LR
        Intersection --- b1[Only B]
    end
    
    style Intersection fill:#fff3cd,stroke:#ffc107,stroke-width:2px
```
