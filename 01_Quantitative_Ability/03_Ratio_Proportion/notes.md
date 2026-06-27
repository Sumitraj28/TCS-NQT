# Ratio & Proportion — Complete Notes

---

## 1. Ratio & Proportion Fundamentals

### Ratio
A **ratio** is a comparison of two quantities of the same kind by division. The ratio of $a$ to $b$ is written as $a:b$ or $\frac{a}{b}$.
*   **Properties:**
    *   Multiplying or dividing both terms of a ratio by the same non-zero number does not change its value ($a:b = am:bm$).
    *   To compare ratios, convert them to fractions or express them with a common denominator.

### Proportion
An equality of two ratios is called a **proportion**. If $a:b = c:d$, then $a, b, c, d$ are in proportion, written as:

$$a:b :: c:d \implies \frac{a}{b} = \frac{c}{d} \implies a \times d = b \times c$$

*   $a$ and $d$ are called **extremes**, while $b$ and $c$ are called **means**.
*   **Mean Proportional:** If $a, b, c$ are in continuous proportion ($a:b :: b:c$), then $b$ is the mean proportional between $a$ and $c$:
    $$b^2 = ac \implies b = \sqrt{ac}$$
*   **Third Proportional:** In $a:b :: b:c$, $c$ is the third proportional to $a$ and $b$:
    $$c = \frac{b^2}{a}$$
*   **Fourth Proportional:** If $a:b :: c:d$, then $d$ is the fourth proportional to $a, b, c$:
    $$d = \frac{b \times c}{a}$$

---

## 2. Direct and Inverse Proportion

### Direct Proportion ($Y \propto X$)
When one quantity increases, the other increases in the same ratio.

$$Y = kX \implies \frac{Y_1}{X_1} = \frac{Y_2}{X_2}$$

where $k$ is the constant of proportionality.
*   *Application:* Work done is directly proportional to the number of men working (when hours and days are constant).

### Inverse Proportion ($Y \propto \frac{1}{X}$)
When one quantity increases, the other decreases in the same ratio.

$$Y = \frac{k}{X} \implies X \times Y = k \implies X_1 Y_1 = X_2 Y_2$$

*   *Application:* Speed and time are inversely proportional when the distance is constant ($S_1 T_1 = S_2 T_2$). See [Average Notes — Average Speed section](file:///Users/rajsumit/Desktop/TCS-NQT/01_Quantitative_Ability/04_Average/notes.md#2-average-speed--harmonic-mean-trap) for applications in traveling.

---

## 3. Partnership Problems

Partnership is an association of two or more persons who invest money to run a business.

$$\text{Profit Ratio} = \text{Investment Ratio} \times \text{Time Ratio}$$

### Simple Partnership
If investments are for the same time period, profits are shared in the ratio of the investments:

$$\text{Profit}_A : \text{Profit}_B = I_A : I_B$$

### Compound Partnership
If investments are for different time periods, profits are shared in the ratio of the product of investments and their respective time periods:

$$\text{Profit}_A : \text{Profit}_B : \text{Profit}_C = (I_A \times T_A) : (I_B \times T_B) : (I_C \times T_C)$$

### Working vs. Sleeping Partners
*   **Working (Active) Partner:** Manages the business and is paid a salary or fee (often a percentage of total profit) before the remaining profit is distributed.
*   **Sleeping (Passive) Partner:** Only invests capital; does not manage. The profit is distributed after deducting the active partner's salary.

---

## 4. Mixture & Alligation Basics

**Alligation** is a mathematical tool used to find the ratio in which two ingredients of different prices/concentrations must be mixed to produce a mixture of a desired mean value.

### The Alligation Rule
Let:
*   $C$ = Cost of cheaper ingredient (per unit)
*   $D$ = Cost of dearer ingredient (per unit)
*   $M$ = Mean price / mixture value (per unit)
*   Note that $C < M < D$.

$$\frac{\text{Quantity of Cheaper } (q_c)}{\text{Quantity of Dearer } (q_d)} = \frac{D - M}{M - C}$$

### Visual Diagram
```text
Cheaper Cost (C)              Dearer Cost (D)
               \              /
                \            /
                Mean Cost (M)
                /            \
               /              \
         (D - M)              (M - C)
```
$$\text{Ratio of Cheaper to Dearer} = (D - M) : (M - C)$$

*   *Important Constraint:* All three quantities ($C$, $D$, and $M$) must be in the same unit and represent the same variable (e.g., all cost prices, all milk concentrations, or all profit percentages).

---

## 5. Cross-References & Overlapping Topics

Ratios and mixtures are used to simplify complex equations in other topics:

*   **Weighted Average Connection:** The alligation equation is simply a algebraic rearrangement of the weighted average equation. See [Average Notes — Weighted Average section](file:///Users/rajsumit/Desktop/TCS-NQT/01_Quantitative_Ability/04_Average/notes.md#1-weighted-average) to see how this relation is derived.
*   **Dishonest Dealers (Profit & Loss):** False-weight problems can be solved in seconds by writing down the ratio of True Weight to False Weight. See [Profit & Loss Notes — False Weight section](file:///Users/rajsumit/Desktop/TCS-NQT/01_Quantitative_Ability/05_Profit_Loss/notes.md#3-false-weight-problems-dishonest-dealers) to see how ratios convert complex percentage gains into simple multiplication factors.
*   **Interest Mixtures (SI & CI):** When a sum of money is divided and lent at two different rates of interest, the overall rate of interest earned is solved using Alligation. See [SI & CI Notes](file:///Users/rajsumit/Desktop/TCS-NQT/01_Quantitative_Ability/06_SI_CI/notes.md).
