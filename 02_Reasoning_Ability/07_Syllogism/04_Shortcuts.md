# Syllogism - Shortcuts & Speed Hacks

These logic translation rules and complementary checklists help you solve complex syllogisms in under 30 seconds without drawing full Venn diagrams.

---

## ⚡ Shortcut 1: The "Only" and "Only a Few" Translation Hack

Use these direct linguistic conversions to rewrite TCS NQT special terms into standard statements:

$$\text{Only } A \text{ is } B \implies \text{All } B \text{ are } A \quad (\text{Note: } B \text{ cannot overlap with any other third set } C)$$
$$\text{Only a few } A \text{ are } B \implies \text{Some } A \text{ are } B \quad \mathbf{AND} \quad \text{Some } A \text{ are not } B$$

### Real-Example Demonstration
*   **Given Statement**: "Only a few students are programmers."
*   **Speed Translation**: 
    1. Draw a standard overlap between `Students` and `Programmers`.
    2. Mark a region of `Students` that is locked outside `Programmers`.
*   **Result**: If a conclusion says "All students can be programmers," immediately mark it **invalid** because "Only a few" demands that some students must *never* be programmers.

---

## ⚡ Shortcut 2: The Direct Conversion Table

You can instantly evaluate direct conclusions using this mapping table:

| If Statement is... | Direct valid conversion (without Venn) | Invalid Trap (do not conclude!) |
| :--- | :--- | :--- |
| **All A are B** | Some B are A | All B are A |
| **No A is B** | No B is A | Some A are B |
| **Some A are B** | Some B are A | All A are B |
| **Some A are not B** | None | Some B are not A |

### Real-Example Demonstration
*   **Given Statement**: "All keys are locks."
*   **Speed Application**: Without drawing, you know:
    *   "Some locks are keys" is **valid**.
    *   "All locks are keys" is **invalid** (Trap).

---

## ⚡ Shortcut 3: Either-Or complementary pair checklist

Instead of drawing multiple Venn diagrams, check if the conclusions satisfy the three-step checklist for **Either-Or** cases:

```
Step 1: Are both conclusions individually false (invalid) in the minimal Venn diagram?
Step 2: Do both conclusions have the exact same Subject and Predicate terms?
Step 3: Do they form one of the standard complementary pairs:
        - (Some + No)
        - (All + Some Not)
        - (Some + Some Not)
```

### Real-Example Demonstration
*   **Given Conclusions**: 
    1. Some pens are pencils (Individual state: False)
    2. No pen is a pencil (Individual state: False)
*   **Verification**:
    *   Terms are identical (`pens` and `pencils`).
    *   Pair is `Some` + `No`.
*   **Decision**: Mark as **Either-Or** immediately. Time saved: 25 seconds.
