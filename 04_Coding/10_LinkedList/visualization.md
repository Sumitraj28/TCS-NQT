# Linked List — Visualization

## Diagram 1 — Singly Linked List Reversal Steps

```mermaid
graph LR
    subgraph Step 1: Initial state
        Node1["1"] --> Node2["2"] --> Node3["3"] --> Null["NULL"]
    end
    subgraph Step 2: Mid-reversal
        prev["prev"] --> N1["1"]
        N1 --> Null2["NULL"]
        curr["curr"] --> N2["2"] --> N3["3"]
    end
    subgraph Step 3: Reversed state
        R3["3"] --> R2["2"] --> R1["1"] --> Null3["NULL"]
        newhead["new head"] --> R3
    end
```

---

## Diagram 2 — Floyd's Cycle Detection meeting trace

```mermaid
graph LR
    Head["Head: 1"] --> Node2["2"] --> Node3["3 (Cycle Start)"] --> Node4["4"] --> Node5["5"] --> Node3

    style Node3 fill:#e74c3c,color:#fff
    style Node5 fill:#f39c12,color:#fff
    Note over Node5: Slow & Fast meet here
```
*(Slow moves 1-2-3-4-5, Fast moves 1-3-5-4-3-5. They meet at node 5).*
 obituary.
