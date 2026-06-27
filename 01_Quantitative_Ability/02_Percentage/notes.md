# Percentage — Complete Notes

---

## 1. Introduction & The Base Value Concept

A **percentage** is a fraction expressed with a denominator of 100. The term *percent* comes from the Latin *per centum*, meaning "by the hundred."

$$\text{Value} = \text{Base} \times \frac{\text{Percentage}}{100}$$

### The Critical "Base Value" Rule
Whenever a percentage is calculated, it **must** have a base. Identifying the correct base is the most common source of errors in TCS NQT questions.
*   **Rule:** The quantity that comes after the word "than" or "of" is typically the base value.
*   *Example:* If $A$'s salary is 25% more than $B$'s salary, the base is $B$'s salary.
    $$A = B + 0.25B = 1.25B$$
    Conversely, if we want to know how much percent $B$'s salary is less than $A$'s, the base is now $A$'s salary:
    $$\text{Percentage Less} = \frac{A - B}{A} \times 100 = \frac{1.25B - B}{1.25B} \times 100 = \frac{0.25}{1.25} \times 100 = 20\%$$

---

## 2. Percentage-to-Fraction Shortcuts Table

To save time in the exam, memorize the fractional equivalents of common percentages. This converts complex multiplication/division into simple fraction arithmetic.

| Fraction | Percentage | Fraction | Percentage |
| :--- | :--- | :--- | :--- |
| $\frac{1}{1}$ | $100\%$ | $\frac{1}{11}$ | $9.09\% \text{ or } 9\frac{1}{11}\%$ |
| $\frac{1}{2}$ | $50\%$ | $\frac{1}{12}$ | $8.33\% \text{ or } 8\frac{1}{3}\%$ |
| $\frac{1}{3}$ | $33.33\% \text{ or } 33\frac{1}{3}\%$ | $\frac{1}{13}$ | $7.69\% \text{ or } 7\frac{9}{13}\%$ |
| $\frac{1}{4}$ | $25\%$ | $\frac{1}{14}$ | $7.14\% \text{ or } 7\frac{1}{7}\%$ |
| $\frac{1}{5}$ | $20\%$ | $\frac{1}{15}$ | $6.66\% \text{ or } 6\frac{2}{3}\%$ |
| $\frac{1}{6}$ | $16.67\% \text{ or } 16\frac{2}{3}\%$ | $\frac{1}{16}$ | $6.25\% \text{ or } 6\frac{1}{4}\%$ |
| $\frac{1}{7}$ | $14.28\% \text{ or } 14\frac{2}{7}\%$ | $\frac{1}{17}$ | $5.88\% \text{ or } 5\frac{15}{17}\%$ |
| $\frac{1}{8}$ | $12.5\%$ | $\frac{1}{18}$ | $5.56\% \text{ or } 5\frac{5}{9}\%$ |
| $\frac{1}{9}$ | $11.11\% \text{ or } 11\frac{1}{9}\%$ | $\frac{1}{19}$ | $5.26\% \text{ or } 5\frac{5}{19}\%$ |
| $\frac{1}{10}$ | $10\%$ | $\frac{1}{20}$ | $5\%$ |

---

## 3. Successive Percentage Change

When a quantity is changed by $A\%$ and then the resulting quantity is changed by $B\%$, the net percentage change is given by the formula:

$$\text{Net \% Change} = A + B + \frac{AB}{100}$$

*   **Sign Convention:** Use $+A$ or $+B$ for increases, and $-A$ or $-B$ for decreases.
*   **Three Changes:** If there are three successive changes $A\%$, $B\%$, and $C\%$, first find the net change of $A$ and $B$ (say $X$), then find the net change of $X$ and $C$.

### Application: Area & Volume Changes
*   **Area of a Rectangle:** $\text{Area} = \text{Length} \times \text{Width}$. If length increases by $L\%$ and width increases by $W\%$, the net change in area is:
    $$\text{Net Change in Area} = L + W + \frac{LW}{100}$$
*   **Volume of a Cuboid:** $\text{Volume} = l \times w \times h$. If dimensions change successively by $x\%$, $y\%$, and $z\%$, the net change is computed using the three-change method or the multiplier method.
    $$\text{New Volume} = \text{Original Volume} \times \left(1 + \frac{x}{100}\right)\left(1 + \frac{y}{100}\right)\left(1 + \frac{z}{100}\right)$$

### The Product-Constancy Rule
If $\text{Product} = X \times Y$ is kept constant, and $X$ changes by a certain percentage, how does $Y$ change?
*   **Concept:** $\text{Expenditure} = \text{Price} \times \text{Consumption}$. If price increases, consumption must decrease to keep expenditure constant.
*   **Rule:** If $X$ increases by $x\% = \frac{a}{b}$, then $Y$ must decrease by:
    $$\text{\% Decrease in } Y = \frac{a}{b + a} \times 100\%$$
*   *Example:* If the price of sugar increases by $25\%$ ($\frac{1}{4}$), then to keep expenditure constant, consumption must decrease by:
    $$\frac{1}{4 + 1} \times 100\% = \frac{1}{5} \times 100\% = 20\%$$

---

## 4. Percentage Point vs. Percentage Change

Understanding this distinction is critical for data interpretation questions.

*   **Percentage Point ($\text{pp}$):** The simple arithmetic difference between two percentages.
    $$\text{Percentage Points} = P_{\text{final}} - P_{\text{initial}}$$
*   **Percentage Change ($\%$):** The relative change of a percentage value with respect to its initial value.
    $$\text{Percentage Change} = \frac{P_{\text{final}} - P_{\text{initial}}}{P_{\text{initial}}} \times 100\%$$

### Worked Example
Suppose a bank's interest rate increases from $10\%$ to $12\%$.
1.  **Percentage Point Difference:** $12\% - 10\% = 2\text{ percentage points (pp)}$.
2.  **Percentage Change:** $\frac{12 - 10}{10} \times 100\% = \frac{2}{10} \times 100\% = 20\%$.

---

## 5. Cross-References & Overlapping Topics

Percentages form the mathematical bedrock of several other Quantitative Ability modules. Refer to the corresponding notes for advanced applications:

*   **Successive Discounting:** Successive percentage decreases are equivalent to successive trade discounts. See [Profit & Loss Notes — Successive Discounts Section](file:///Users/rajsumit/Desktop/TCS-NQT/01_Quantitative_Ability/05_Profit_Loss/notes.md#2-discounts--successive-discounts) for details on calculating single equivalent discounts.
*   **Compound Interest:** Compound Interest is simply the application of successive percentage increases over multiple time periods. See [SI & CI Notes — Compound Interest Section](file:///Users/rajsumit/Desktop/TCS-NQT/01_Quantitative_Ability/06_SI_CI/notes.md#1-simple-vs-compound-interest-formulas) to understand compounding as a geometric progression of percentage growth.
*   **Alligation & Mixtures:** Mixing solutions of different percentage concentrations (e.g., 20% acid and 50% acid) is solved using weighted averages or alligations. See [Ratio & Proportion Notes — Mixture & Alligation Section](file:///Users/rajsumit/Desktop/TCS-NQT/01_Quantitative_Ability/03_Ratio_Proportion/notes.md#4-mixture--alligation-basics) for the visual cross-method.
