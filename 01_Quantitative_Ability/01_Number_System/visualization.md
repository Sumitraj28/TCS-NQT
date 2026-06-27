# Number System — Visualization

---

## 1. Factor Tree Diagram (Composite Number 60)

```mermaid
graph TD
    Node60["60"] --> Node2["2 (Prime)"]
    Node60 --> Node30["30"]
    Node30 --> Node2_2["2 (Prime)"]
    Node30 --> Node15["15"]
    Node15 --> Node3["3 (Prime)"]
    Node15 --> Node5["5 (Prime)"]

    style Node2 fill:#2ecc71,color:#fff
    style Node2_2 fill:#2ecc71,color:#fff
    style Node3 fill:#2ecc71,color:#fff
    style Node5 fill:#2ecc71,color:#fff
    style Node60 fill:#3498db,color:#fff
```

---

## 2. Divisibility Rule Flowchart

```mermaid
flowchart TD
    Start["Check Divisibility of N"]
    Start --> Even{"Is last digit even?"}
    Even -- Yes --> Div2["Divisible by 2"]
    Even -- No --> NotDiv2["Not divisible by 2"]
    
    Start --> DigSum{"Sum of digits divisible by 3?"}
    DigSum -- Yes --> Div3["Divisible by 3"]
    DigSum -- No --> NotDiv3["Not divisible by 3"]
    
    Div2 & Div3 --> Div6{"Divisible by both?"}
    Div6 -- Yes --> Div6Yes["Divisible by 6"]
    Div6 -- No --> Div6No["Not divisible by 6"]
    
    Start --> LastTwo{"Last 2 digits divisible by 4?"}
    LastTwo -- Yes --> Div4["Divisible by 4"]
    LastTwo -- No --> NotDiv4["Not divisible by 4"]
```

---

## 3. "Prime Ladder" Diagram for Prime Factorization (For 60)

```mermaid
graph TD
    Step1["60 / 2"] --> Step2["30 / 2"]
    Step2 --> Step3["15 / 3"]
    Step3 --> Step4["5 / 5"]
    Step4 --> Step5["1"]

    classDef prime fill:#e74c3c,color:#fff;
    class Step1,Step2,Step3,Step4 prime;
```
*(Divide by prime numbers step-by-step down to 1: $60 = 2^2 \times 3^1 \times 5^1$).*
