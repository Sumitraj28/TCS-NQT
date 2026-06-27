# Matrix — Visualization

## Diagram 1 — Spiral Traversal Ring Boundaries

```mermaid
flowchart TD
    subgraph Grid Boundaries
        direction TB
        L["left = 0"] --- R["right = 2"]
        T["top = 0"] --- B["bottom = 2"]
    end
    subgraph Path Directions
        direction LR
        p1["(0,0) -> (0,2)"] --> p2["(1,2) -> (2,2)"]
        p2 --> p3["(2,1) -> (2,0)"]
        p3 --> p4["(1,0) -> (1,1)"]
    end
```

---

## Diagram 2 — Matrix Transposition Swap Cells

```mermaid
matrix
  | 1  2  3 |         | 1  4  7 |
  | 4  5  6 |   ==>   | 2  5  8 |
  | 7  8  9 |         | 3  6  9 |
```
*(Swap elements across main diagonal: 2<->4, 3<->7, 6<->8).*
