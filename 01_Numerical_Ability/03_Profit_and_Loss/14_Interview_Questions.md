---
title: "Profit & Loss - Interview Questions"
section: "Numerical Ability"
---

# Profit & Loss Interview Questions

This document contains 10 conceptual and derivation questions commonly asked in technical and quantitative interviews.

---

### Q1. Why is Cost Price (CP) always used as the baseline denominator for Profit and Loss calculations?
**Answer**: 
Profit and Loss percentages measure the efficiency or return of an investment. In business transactions, the Cost Price (CP) represents the total capital invested to acquire or manufacture the goods. The Selling Price (SP) is the output variable. To calculate the rate of return (how much the investment grew or shrank), the net change must be measured relative to the initial capital invested (CP), not the final cash collected (SP).

---

### Q2. Can you derive the net loss formula $\left(\frac{x}{10}\right)^2\%$ for two items sold at the same Selling Price?
**Answer**: 
Let the Selling Price of both items be $S$.
*   Item 1 is sold at a profit of $x\% \implies CP_1 = \frac{S}{1 + \frac{x}{100}} = \frac{100S}{100+x}$.
*   Item 2 is sold at a loss of $x\% \implies CP_2 = \frac{S}{1 - \frac{x}{100}} = \frac{100S}{100-x}$.
*   Total CP $= CP_1 + CP_2 = 100S \left(\frac{1}{100+x} + \frac{1}{100-x}\right) = 100S \left(\frac{200}{10000 - x^2}\right) = \frac{20000S}{10000-x^2}$.
*   Total SP $= 2S$.
*   Since $10000 - x^2 < 10000$, the denominator of Total CP is smaller than its baseline numerator, meaning Total CP $> 2S$ (Total SP), which confirms a net loss.
*   $$\text{Net Loss}\% = \left(\frac{\text{Total CP} - \text{Total SP}}{\text{Total CP}}\right) \times 100 = \left(1 - \frac{\text{Total SP}}{\text{Total CP}}\right) \times 100$$
*   $$\text{Net Loss}\% = \left(1 - \frac{2S}{\frac{20000S}{10000-x^2}}\right) \times 100 = \left(1 - \frac{10000-x^2}{10000}\right) \times 100 = \left(\frac{x^2}{10000}\right) \times 100 = \frac{x^2}{100}\% = \left(\frac{x}{10}\right)^2\%$$

---

### Q3. What is the mathematical intuition behind the successive discount formula $d_1 + d_2 - \frac{d_1 d_2}{100}\%$?
**Answer**: 
If you offer a discount $d_1\%$, the price drops to $(1 - \frac{d_1}{100})$ of the original Marked Price. The second discount $d_2\%$ is then applied *only* to this reduced price, not the original price.
*   $$\text{Net multiplier} = \left(1 - \frac{d_1}{100}\right) \times \left(1 - \frac{d_2}{100}\right) = 1 - \frac{d_1}{100} - \frac{d_2}{100} + \frac{d_1 d_2}{10000}$$
*   $$\text{Net Price Ratio} = 1 - \frac{1}{100} \left(d_1 + d_2 - \frac{d_1 d_2}{100}\right)$$
This shows the final price is reduced by the combined term $\left(d_1 + d_2 - \frac{d_1 d_2}{100}\right)\%$. The negative term $-\frac{d_1 d_2}{100}$ represents the discount value that is *lost* because the second discount is calculated on a smaller intermediate base rather than the original price.

---

### Q4. Why is the discount percentage always calculated on Marked Price (MP) instead of Cost Price (CP)?
**Answer**: 
The Marked Price (MP) represents the retail price shown on the label. A discount is a promotional reduction in the advertised retail price. Because the customer only sees the Marked Price and is unaware of the merchant's underlying Cost Price, the discount value must be measured relative to the price being reduced (MP). Calculating a discount on CP would expose the merchant's internal cost margins.

---

### Q5. Derive the Dishonest Dealer profit formula $\frac{\text{Error}}{\text{Delivered}} \times 100\%$ from first principles.
**Answer**: 
Let the cost price of 1 gram of goods be ₹1.
*   If a customer orders $G$ grams (nominal weight), they expect to pay ₹$G$ (since the dealer sells at cost price).
*   However, the dealer delivers a lighter weight $D$ grams.
*   The Cost Price of the goods actually delivered by the dealer is $CP = D \times 1 = \text{₹}D$.
*   The Selling Price collected from the customer is $SP = G \times 1 = \text{₹}G$.
*   $$\text{Profit}\% = \left(\frac{SP - CP}{CP}\right) \times 100 = \left(\frac{G - D}{D}\right) \times 100$$
*   Since $G - D$ is the difference between nominal and delivered weight (the cheat error $E$), we get:
    $$\text{Profit}\% = \frac{E}{D} \times 100 = \frac{\text{Error}}{\text{Delivered}} \times 100\%$$

---

### Q6. Explain why cheating by $10\%$ when buying is not mathematically identical to cheating by $10\%$ when selling.
**Answer**: 
*   **Cheating when buying** means getting $10\%$ more volume for the same price: you pay for 1000g but take 1100g.
    $$\text{Profit Factor} = \frac{1100}{1000} = 1.10\text{ (10\% profit)}$$
*   **Cheating when selling** means delivering $10\%$ less volume for the same price: the customer pays for 1000g but receives 900g.
    $$\text{Profit Factor} = \frac{1000}{900} = 1.1111\text{ (11.11\% profit)}$$
Cheating when selling yields a higher profit margin because the base (delivered weight) is reduced to 900g, whereas cheating when buying increases the goods volume on a fixed nominal cash base.

---

### Q7. Why does a markup followed by a discount of the same percentage always result in a net loss?
**Answer**: 
Applying a markup of $x\%$ increases the Cost Price to $MP = CP \times (1 + \frac{x}{100})$. 
When the discount of $x\%$ is applied, it is calculated on this new, larger Marked Price base.
*   $$SP = MP \times \left(1 - \frac{x}{100}\right) = CP \times \left(1 + \frac{x}{100}\right) \times \left(1 - \frac{x}{100}\right) = CP \times \left(1 - \frac{x^2}{10000}\right)$$
Because $\frac{x^2}{10000}$ is always positive for any non-zero $x$, the Selling Price multiplier $\left(1 - \frac{x^2}{10000}\right)$ is always less than 1, resulting in a net loss of $\frac{x^2}{100}\%$.

---

### Q8. How does the presence of overhead charges (transportation, repairs) affect the calculation of Profit or Loss percentage?
**Answer**: 
Overhead charges represent additional expenses incurred to bring the product to a saleable condition. By accounting principles, these costs must be capitalized. They are added directly to the purchase price to form the Total Cost Price base ($CP_{\text{total}} = CP_{\text{purchase}} + CP_{\text{overhead}}$). Because this increases the denominator base, failing to include overhead charges will artificially inflate the calculated profit percentage, leading to inaccurate financial tracking.

---

### Q9. What happens to the profit percentage if a merchant decides to charge a commission on the Selling Price?
**Answer**: 
If a broker or salesman charges a commission of $c\%$ on the Selling Price, the net revenue received by the merchant drops to $SP_{\text{net}} = SP \times (1 - \frac{c}{100})$.
The merchant's profit is then calculated as $\frac{SP_{\text{net}} - CP}{CP} \times 100$. This commission effectively reduces the Selling Price multiplier, directly subtracting from the profit margin.

---

### Q10. What is the advantage of using the Multiplying Factor method over traditional ratio equations for successive transactions?
**Answer**: 
Traditional ratio methods require solving for intermediate selling prices at each stage, which introduces rounding errors and increases calculation steps. The Multiplying Factor (MF) method expresses each profit or loss rate as a single decimal or fraction coefficient (e.g. $1.25$ or $\frac{5}{4}$). By chaining these coefficients together ($CP \times MF_1 \times MF_2 = SP$), you can simplify common factors in the numerator and denominator, reducing the multi-stage transaction to a single division step.
