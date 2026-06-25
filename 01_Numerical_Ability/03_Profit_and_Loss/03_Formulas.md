---
title: "Profit & Loss - Formulas Sheet"
section: "Numerical Ability"
---

# Profit & Loss Formulas

## 1. Core Formulas & Derivations

### A. Profit and Loss Percentages
$$\text{Profit}\% = \left(\frac{SP - CP}{CP}\right) \times 100, \quad \text{Loss}\% = \left(\frac{CP - SP}{CP}\right) \times 100$$

#### 💡 Where it comes from:
We calculate the absolute gain or deficit, and express it as a fraction of the starting investment (Cost Price), scaling to a percentage out of 100.

#### Worked Example:
An item bought for ₹200 is sold for ₹250. Find the profit percentage.
*   $CP = 200, SP = 250$.
*   Calculation:
    $$\text{Profit}\% = \frac{250 - 200}{200} \times 100 = \frac{50}{200} \times 100 = 25\%$$

---

### B. Selling Price (SP) relative to Cost Price (CP)
$$SP = CP \times \left(1 + \frac{P}{100}\right) \quad \text{[For Profit]}$$
$$SP = CP \times \left(1 - \frac{L}{100}\right) \quad \text{[For Loss]}$$

#### 💡 Where it comes from:
The Selling Price is the Cost Price ($100\%$) plus the profit percentage (or minus the loss percentage), represented as a multiplier.

#### Worked Example:
An item bought for ₹150 is sold at a $20\%$ loss. Find the Selling Price.
*   $CP = 150, L = 20$.
*   Calculation:
    $$SP = 150 \times \left(1 - \frac{20}{100}\right) = 150 \times 0.8 = ₹120$$

---

### C. Discount Percentage
$$\text{Discount}\% = \left(\frac{MP - SP}{MP}\right) \times 100$$

#### 💡 Where it comes from:
The discount is the absolute reduction in marked price, measured using the Marked Price (MP) as the $100\%$ baseline.

#### Worked Example:
A shirt marked at ₹800 is sold for ₹680. Find the discount percentage.
*   $MP = 800, SP = 680$.
*   Calculation:
    $$\text{Discount}\% = \frac{800 - 680}{800} \times 100 = \frac{120}{800} \times 100 = 15\%$$

---

### D. Markup Percentage
$$\text{Markup}\% = \left(\frac{MP - CP}{CP}\right) \times 100$$

#### 💡 Where it comes from:
Markup is the raw price increase added to the Cost Price to set the Marked Price, measured with the Cost Price (CP) as the $100\%$ baseline.

#### Worked Example:
An item costing ₹400 is marked up to ₹520. Find the markup percentage.
*   $CP = 400, MP = 520$.
*   Calculation:
    $$\text{Markup}\% = \frac{520 - 400}{400} \times 100 = \frac{120}{400} \times 100 = 30\%$$

---

## 2. Special Case Formulas

### A. Net Profit/Loss from Successive Markup & Discount
$$\text{Net Profit/Loss}\% = m - d - \frac{md}{100}\%$$
*(Where $m$ is markup percentage and $d$ is discount percentage. A positive result indicates net profit; negative indicates net loss).*

#### 💡 Derivation:
Applying a markup $m\%$ followed by a discount $d\%$ is equivalent to successive percentage changes of $+m\%$ and $-d\%$ on the starting CP base:
$$\text{Net multiplier} = \left(1 + \frac{m}{100}\right)\left(1 - \frac{d}{100}\right) = 1 + \frac{m - d - \frac{md}{100}}{100}$$
Subtracting the base 1 yields the net change formula.

#### Worked Example:
A dealer marks his goods up by $20\%$ and then offers a $10\%$ discount. Find the net profit percentage.
*   $m = 20, d = 10$.
*   Calculation:
    $$\text{Net Change} = 20 - 10 - \frac{20 \times 10}{100} = 10 - 2 = +8\%\text{ (Net Profit)}$$

---

### B. Two Items Sold at the Same SP (Equal SP Case)
If two items are sold at the same Selling Price, one at a profit of $x\%$ and the other at a loss of $x\%$:
$$\text{Net Loss}\% = \left(\frac{x}{10}\right)^2\%$$
*(This transaction ALWAYS results in a net loss).*

#### 💡 Derivation:
Let $SP$ be the selling price. The cost prices are $CP_1 = \frac{SP}{1 + x/100}$ and $CP_2 = \frac{SP}{1 - x/100}$.
$$\text{Total CP} = CP_1 + CP_2 = SP \times \left(\frac{1}{1 + x/100} + \frac{1}{1 - x/100}\right) = SP \times \left(\frac{2}{1 - x^2/10000}\right)$$
$$\text{Total SP} = 2 \times SP$$
Comparing Total SP and Total CP yields a net loss fraction of $\frac{x^2}{10000}$, which is a percentage of $\frac{x^2}{100}\% = (\frac{x}{10})^2\%$.

#### Worked Example:
Two items are sold for ₹9,900 each. One makes a profit of $10\%$ and the other a loss of $10\%$. Find the net gain or loss percentage.
*   $x = 10$.
*   Calculation:
    $$\text{Net Loss}\% = \left(\frac{10}{10}\right)^2 = 1\%$$

---

## 3. Boundary Conditions (Where Formulas Break)
*   **Zero Cost Price ($CP = 0$)**: The Profit/Loss percentage equations break because division by zero is undefined. In real markets, items received for free have an infinite markup/profit rate if sold for any price.
*   **Discount $> 100\%$**: If the discount percentage exceeds $100\%$, the Selling Price becomes negative ($SP < 0$). In commercial markets, this is equivalent to paying a customer to take the goods away (negative revenue).
*   **Equal SP profit/loss rate symmetry**: The net loss shortcut $(\frac{x}{10})^2\%$ **only** works if the profit rate on the first item exactly equals the loss rate on the second item. If they differ (e.g., $10\%$ profit and $15\%$ loss), you must calculate $CP_1$ and $CP_2$ individually.

---

## 4. Formula Relationship Map
```
              [Cost Price (CP)] 
                │            ▲
         * (1 + m/100)    / (1 + P/100)
                │            │
                v            │
            [Marked Price (MP)] ── * (1 - d/100) ──> [Selling Price (SP)]
```
