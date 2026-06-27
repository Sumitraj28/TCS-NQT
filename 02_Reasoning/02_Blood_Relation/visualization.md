# Family Tree Visualization

Below are visual representations of family trees using Mermaid diagrams.

## 1. Key Legend

Before drawing a family tree, understand the visual notation:

```mermaid
graph TD
    Male["[Male] (Represented by Square)"]
    Female("(Female) (Represented by Circle)")
    
    Husband["[Husband]"] <-->|Marital Bond| Wife("(Wife)")
    Brother["[Brother]"] ---|Sibling Bond| Sister("(Sister)")
    
    Parent["[Parent]"] --- |Generation Gap| Child["[Child]"]
```

---

## 2. Standard 3-Generation Family Tree

Here is a visual map of a typical family structure covering Grandparents, Parents, Uncles/Aunts, Children, and Cousins.

```mermaid
graph TD
    %% Generation 1 (Grandparents)
    GF["[Grandfather]"] <--> GM("(Grandmother)")
    
    %% Generation 2 (Parents & Aunts/Uncles)
    Father["[Father]"] <--> Mother("(Mother)")
    Uncle["[Uncle]"] <--> Aunt("(Aunt)")
    
    GF --- Father
    GF --- Uncle
    
    %% Generation 3 (Self, Siblings & Cousins)
    Self["[Self]"] --- Sister("(Sister)")
    Cousin["[Cousin (Male/Female)]"]
    
    Father --- Self
    Uncle --- Cousin
    
    %% Styling
    style GF fill:#d4edda,stroke:#28a745,stroke-width:2px
    style GM fill:#f8d7da,stroke:#dc3545,stroke-width:2px
    style Father fill:#d4edda,stroke:#28a745,stroke-width:2px
    style Mother fill:#f8d7da,stroke:#dc3545,stroke-width:2px
    style Uncle fill:#d4edda,stroke:#28a745,stroke-width:2px
    style Aunt fill:#f8d7da,stroke:#dc3545,stroke-width:2px
    style Self fill:#d4edda,stroke:#28a745,stroke-width:2px
    style Sister fill:#f8d7da,stroke:#dc3545,stroke-width:2px
    style Cousin fill:#fff3cd,stroke:#ffc107,stroke-width:2px
```
