# Profit and Loss — Complete Notes

---

## 1. CP, SP, and MP Relations

To solve Profit & Loss questions quickly, you must master the relationships between the three primary price markers.

### Definitions
1.  **Cost Price (CP):** The price at which a product is bought or produced.
2.  **Selling Price (SP):** The price at which a product is sold to a customer.
3.  **Marked Price (MP):** The price printed or labeled on the product (also called list price or MRP).

### Key Equations
*   **Profit (P):** Occurs when $SP > CP$.
    $$P = SP - CP \implies \text{Profit \%} = \frac{SP - CP}{CP} \times 100$$
*   **Loss (L):** Occurs when $CP > SP$.
    $$L = CP - SP \implies \text{Loss \%} = \frac{CP - SP}{CP} \times 100$$
    *Note:* Profit % and Loss % are always calculated with **CP** as the base value (unless stated otherwise in the problem).
*   **Markup:** The amount by which MP exceeds CP.
    $$\text{Markup} = MP - CP \implies \text{Markup \%} = \frac{MP - CP}{CP} \times 100$$
    *Note:* Markup % is calculated with **CP** as the base value.

### The Master CP-SP-MP Equation
Selling Price can be calculated by applying Profit/Loss % to Cost Price OR by applying Discount % to Marked Price:

$$\text{SP} = \text{CP} \times \left(1 + \frac{\text{Profit\%}}{100}\right) = \text{MP} \times \left(1 - \frac{\text{Discount\%}}{100}\right)$$

Rearranging this equality gives a critical exam formula:

$$\frac{\text{MP}}{\text{CP}} = \frac{100 + \text{Profit\%}}{100 - \text{Discount\%}}$$

*   *If there is a loss, replace $+\text{Profit\%}$ with $-\text{Loss\%}$.*

---

## 2. Discounts & Successive Discounts

A **discount** is a reduction offered on the Marked Price of a product.

$$\text{Discount (D)} = MP - SP \implies \text{Discount \%} = \frac{MP - SP}{MP} \times 100$$

*   *Note:* Discount % is always calculated with **MP** as the base value.

### Successive Discounts
When multiple discounts are applied one after another, they are calculated successively.
*   **Formula (Two Discounts):** If successive discounts of $d_1\%$ and $d_2\%$ are given, the single equivalent discount is:
    $$\text{Net Discount \%} = d_1 + d_2 - \frac{d_1 d_2}{100}$$
*   **Multiplier Method (Three or More):**
    $$\text{Final SP} = \text{MP} \times \left(1 - \frac{d_1}{100}\right)\left(1 - \frac{d_2}{100}\right)\left(1 - \frac{d_3}{100}\right)$$
    $$\text{Single Equivalent Discount} = \frac{MP - Final SP}{MP} \times 100$$

---

## 3. False-Weight Problems (Dishonest Dealers)

A dishonest dealer cheats by either using a false weight (giving less quantity) or marking up prices while claiming to sell at CP.

### Basic Gain Formula
If a merchant claims to sell goods at Cost Price but uses a false weight of $W_f$ instead of the true weight $W_t$, the profit percentage is:

$$\text{Profit \%} = \frac{\text{True Weight} - \text{False Weight}}{\text{False Weight}} \times 100 = \frac{\text{Error}}{\text{True Weight} - \text{Error}} \times 100$$

### The Ratio Method (Multi-Condition Problems)
For advanced TCS NQT questions where the dealer marks up the price, gives a discount, AND uses a false weight, the **Ratio Method** is the fastest approach. Write the ratio of $\frac{\text{SP}}{\text{CP}}$ for each transaction element:

$$\frac{\text{SP}}{\text{CP}} = \text{Price Factor} \times \text{Weight Factor} \times \text{Discount Factor}$$

*   **Price Factor (Markup):** If marked up by $m\%$, factor is $\frac{100+m}{100}$.
*   **Discount Factor:** If discount of $d\%$ is given, factor is $\frac{100-d}{100}$.
*   **Weight Factor:** If $W_f$ is given instead of $W_t$, the dealer gains because he saves inventory. The factor is $\frac{W_t}{W_f}$.
*   **Overall Result:**
    *   If $\frac{SP}{CP} > 1$, there is a profit. Profit \% $= \left(\frac{SP}{CP} - 1\right) \times 100$.
    *   If $\frac{SP}{CP} < 1$, there is a loss.

---

## 4. Cross-References & Overlapping Topics

*   **Percentage Base:** Profit, loss, and discounts are direct applications of percentages. If you struggle to identify what value to divide by, refer to [Percentage Notes — The Base Value Concept](file:///Users/rajsumit/Desktop/TCS-NQT/01_Quantitative_Ability/02_Percentage/notes.md#1-introduction--the-base-value-concept).
*   **Successive Changes:** Calculating successive discounts is identical to successive percentage changes. See [Percentage Notes — Successive Percentage Change](file:///Users/rajsumit/Desktop/TCS-NQT/01_Quantitative_Ability/02_Percentage/notes.md#3-successive-percentage-change) to see the underlying algebraic derivation.
*   **Ratio Multipliers:** The ratio method used in false-weight problems is based on compounded ratios. See [Ratio & Proportion Notes](file:///Users/rajsumit/Desktop/TCS-NQT/01_Quantitative_Ability/03_Ratio_Proportion/notes.md) to understand how compound ratios scale values.
*   **Mixing Goods:** Profit and loss problems involving mixing two varieties of items and selling them at a specific price are solved using the alligation method. See [Ratio & Proportion Notes — Mixture & Alligation Section](file:///Users/rajsumit/Desktop/TCS-NQT/01_Quantitative_Ability/03_Ratio_Proportion/notes.md#4-mixture--alligation-basics).
