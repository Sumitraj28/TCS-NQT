# Average — Complete Notes

---

## 1. Weighted Average

The standard average (arithmetic mean) assumes all observations contribute equally. When groups of different sizes or different weights are combined, we use the **Weighted Average**.

If a set contains $k$ groups, where group $i$ has $n_i$ elements and an average value of $A_i$:

$$A_{\text{weighted}} = \frac{n_1 A_1 + n_2 A_2 + \dots + n_k A_k}{n_1 + n_2 + \dots + n_k}$$

### Connection to Ratios
If we only have two groups, the weighted average is:
$$A_{\text{weighted}} = \frac{n_1 A_1 + n_2 A_2}{n_1 + n_2}$$
Rearranging this equation gives:
$$n_1(A_{\text{weighted}} - A_1) = n_2(A_2 - A_{\text{weighted}}) \implies \frac{n_1}{n_2} = \frac{A_2 - A_{\text{weighted}}}{A_{\text{weighted}} - A_1}$$
This is the mathematical proof of the **Alligation Rule** in [Ratio & Proportion Notes — Mixture & Alligation Section](file:///Users/rajsumit/Desktop/TCS-NQT/01_Quantitative_Ability/03_Ratio_Proportion/notes.md#4-mixture--alligation-basics).

---

## 2. Average Speed & The Harmonic Mean Trap

Candidates frequently fall into the trap of calculating average speed as the arithmetic mean of given speeds. 

$$\text{Average Speed} = \frac{\text{Total Distance}}{\text{Total Time}}$$

### Case 1: Equal Distances (Harmonic Mean Trap)
If a journey is divided into two equal halves (or a round trip of the same distance) traveled at speeds $v_1$ and $v_2$, the average speed is the **Harmonic Mean**:

$$v_{\text{avg}} = \frac{2 v_1 v_2}{v_1 + v_2}$$

*   **Derivation:** Let the distance of each half be $D$.
    *   $\text{Total Distance} = 2D$
    *   $\text{Total Time} = t_1 + t_2 = \frac{D}{v_1} + \frac{D}{v_2} = D\left(\frac{v_1 + v_2}{v_1 v_2}\right)$
    *   $v_{\text{avg}} = \frac{2D}{D\left(\frac{v_1+v_2}{v_1 v_2}\right)} = \frac{2 v_1 v_2}{v_1 + v_2}$
*   **Three Equal Distances:** If a journey is split into three equal distances traveled at $v_1$, $v_2$, and $v_3$:
    $$v_{\text{avg}} = \frac{3 v_1 v_2 v_3}{v_1 v_2 + v_2 v_3 + v_3 v_1}$$

### Case 2: Equal Time Intervals (Arithmetic Mean Applies)
If an object travels at speed $v_1$ for time $t$, and at speed $v_2$ for another equal time interval $t$, the average speed is the **Arithmetic Mean**:

$$v_{\text{avg}} = \frac{v_1 \cdot t + v_2 \cdot t}{2t} = \frac{v_1 + v_2}{2}$$

---

## 3. Change-of-Average Problems (Deviation Method)

Instead of using traditional algebraic equations (which require heavy multiplication in the exam), use the **Deviation Method**. The net sum of deviations of all observations from the average is always $0$.

### Concept 1: Addition of a New Element
When a new value is added to a group of $N$ items, the average changes:
$$\text{New Value} = \text{New Average} + N \times (\text{Increase in Average})$$
*   If the average decreases, the "Increase in Average" is negative.

### Concept 2: Exclusion of an Element
When one value is removed from a group of $N$ items:
$$\text{Excluded Value} = \text{Old Average} + (N - 1) \times (\text{Decrease in Average})$$

### Concept 3: Substitution of an Element
When an element in a group of $N$ items is replaced by another:
$$\text{New Value} = \text{Replaced Value} + N \times (\text{Increase in Average})$$

### Worked Example (Substitution)
The average weight of 10 men is increased by 1.5 kg when one of the men, who weights 68 kg, is replaced by a new man. Find the weight of the new man.
*   **Algebraic method:** Slow.
*   **Deviation method:**
    $$\text{New Man Weight} = \text{Replaced Weight} + (\text{Total Men} \times \text{Increase})$$
    $$\text{New Man Weight} = 68 + (10 \times 1.5) = 68 + 15 = 83 \text{ kg}$$

---

## 4. Cross-References & Overlapping Topics

*   **Alligations & Mixtures:** Finding the ratio of mixtures is the inverse of a weighted average problem. For details, refer to [Ratio & Proportion Notes — Mixture & Alligation Section](file:///Users/rajsumit/Desktop/TCS-NQT/01_Quantitative_Ability/03_Ratio_Proportion/notes.md#4-mixture--alligation-basics).
*   **Speed-Time Relations:** Average speed is an application of inverse proportionality. See [Ratio & Proportion Notes — Direct & Inverse section](file:///Users/rajsumit/Desktop/TCS-NQT/01_Quantitative_Ability/03_Ratio_Proportion/notes.md#2-direct-and-inverse-proportion) to review how inverse relationships function.
