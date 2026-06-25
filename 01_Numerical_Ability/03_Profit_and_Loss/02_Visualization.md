---
title: "Profit & Loss - Visual Learning Guide"
section: "Numerical Ability"
---

# Profit & Loss Visual Learning Guide

## 1. Formula Strategy Decision Tree
Use this decision tree during the NQT exam to select the correct formula based on the variables provided.

```
                           Analyze the Given Variables
                                       |
           +---------------------------+---------------------------+
           |                                                       |
   Is MP or Discount given?                                Is CP and SP given?
           |                                                       |
           v                                                       v
   Is markup given?                                     Is Profit or Loss expected?
     |                                                     |
     +--[YES]--> MP = CP * (1 + Markup/100)                +--[Profit]--> SP = CP * (1 + P/100)
     |                                                     |
     +--[NO]---> SP = MP * (1 - Discount/100)              +--[Loss]----> SP = CP * (1 - L/100)
```

---

## 2. Multi-Step Pricing Flowchart
Follow this sequential workflow when dealing with consecutive markup, discount, and sale problems.

```
+-------------------------------------------------------------+
| Step 1: Identify Cost Price (CP)                             |
| Ensure all repair/transport costs are added to CP           |
+-------------------------------------------------------------+
                               |
                               v
+-------------------------------------------------------------+
| Step 2: Calculate Marked Price (MP)                         |
| Apply Markup % on CP base: MP = CP * (1 + markup/100)       |
+-------------------------------------------------------------+
                               |
                               v
+-------------------------------------------------------------+
| Step 3: Apply Discount %                                    |
| Apply Discount % on MP base: SP = MP * (1 - discount/100)   |
+-------------------------------------------------------------+
                               |
                               v
+-------------------------------------------------------------+
| Step 4: Determine Net Profit / Loss                         |
| Compare final SP with starting CP: Profit = SP - CP         |
| Net Profit % = (SP - CP)/CP * 100                           |
+-------------------------------------------------------------+
```

---

## 3. Comparison Table: Problem Variations

| Variation Type | Core Characteristic | Key Formula / Strategy | Worked Example |
| :--- | :--- | :--- | :--- |
| **Simple Trade** | Standard CP and SP comparison. | $$P = SP - CP$$ | CP = 100, SP = 120 $\implies$ $20\%$ Profit. |
| **Markup & Discount** | Chain calculation from CP $\rightarrow$ MP $\rightarrow$ SP. | $$SP = CP \times (1 + m\%)(1 - d\%)$$ | Markup $30\%$, Discount $10\% \implies$ Net profit $= 17\%$. |
| **Dishonest Dealer** | Dealer cheats on weight or buying price. | $$\text{Profit}\% = \frac{\text{Error}}{\text{True} - \text{Error}} \times 100$$ | Uses 900g instead of 1kg $\implies \frac{100}{900} \times 100 = 11.11\%$. |
| **Buy X, Get Y Free** | Promotional bundle discounts. | $$\text{Discount}\% = \frac{Y}{X+Y} \times 100$$ | Buy 4 get 1 free $\implies \frac{1}{5} \times 100 = 20\%$ discount. |
| **Identical Selling Price**| Two items sold at same SP (one $x\%$ profit, one $x\%$ loss). | $$\text{Net Loss} = \left(\frac{x}{10}\right)^2\%$$ | Same SP, $+20\%$ and $-20\% \implies$ Net $4\%$ Loss. |

---

## 4. Concept Relationship Memory Map

```
  [Markup %] (Increases CP)
       |
       v
 [Cost Price (CP)] ────────────── Profit/Loss % ─────────────> [Selling Price (SP)]
       │                                                             ▲
       └───────────────> [Marked Price (MP)] ────────────────────────┘
                              (Base for Discount %)
```

---

## 5. Pattern Recognition Chart

| If you see this phrasing in the NQT question: | Interpret it mathematically as: | Action: |
| :--- | :--- | :--- |
| *"A dealer marks his goods X% above CP and sells at Y% discount"* | Successive change markup-discount | Apply $m - d - \frac{md}{100}\%$. |
| *"uses a weight of 800 grams instead of a kilogram"* | Dishonest dealer weight cheat | Error $= 200$, True Value $= 1000$. Use $\frac{200}{800} \times 100\%$. |
| *"Buy 3 get 2 free"* | Bundle discount on total units | Total units $= 5$, Free units $= 2$. Discount $= 2/5 = 40\%$. |
| *"CP of X articles equals SP of Y articles"* | CP-SP ratio equation | Write $X \times CP = Y \times SP \implies \frac{SP}{CP} = \frac{X}{Y}$. |
