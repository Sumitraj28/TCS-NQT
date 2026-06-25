---
title: "Profit & Loss - Pattern Recognition Guide"
section: "Numerical Ability"
---

# Profit & Loss Pattern Recognition

## 1. Trigger Word Table
Identify the question type within 5 seconds of reading by spotting these key trigger phrases:

| Spotted Phrase in Question | Mapped Pattern | Instant Solver Tool |
| :--- | :--- | :--- |
| *"marks his goods X% above cost"* | Markup-Discount Cycle | Successive Change Formula: $m - d - \frac{md}{100}\%$ |
| *"sells at cost price but uses a weight..."* | Faulty Weight Cheat | Dishonest Dealer Shortcut: $\frac{\text{Error}}{\text{Delivered}} \times 100\%$ |
| *"Buy X get Y free"* | Bundle Discount | Free-to-Total ratio: $\frac{Y}{X+Y} \times 100\%$ |
| *"Cost price of X equals Selling price of Y"* | CP-SP Ratio | Ratio equation: $\frac{SP}{CP} = \frac{X}{Y}$ |
| *"Sold two articles at ₹X each, one at profit..."* | Same SP, Symmetric Change | Net Loss Shortcut: $\left(\frac{x}{10}\right)^2\%$ |
| *"A sells to B, B sells to C..."* | Transaction Chain | Multiplying Factor Chain equation |

---

## 2. Decision Tree: Identification to Method
Use this mental tree to route the question to the correct shortcut:

```
                            Read the Question
                                    |
                    What is the core merchant trick?
                                    |
         +--------------------------+--------------------------+
         |                          |                          |
   Cheating on Weight?       Giving Free Items?         Multiple Sales?
         |                          |                          |
         v                          v                          v
   Dishonest Dealer           Buy X Get Y Free          Transaction Chain
   Error / Delivered          Y / (X+Y) * 100           A * MF_1 * MF_2 = C
```

---

## 3. Disguised Profit & Loss Patterns
Sometimes, Profit & Loss questions are hidden inside other quantitative domains:

### A. Hidden in Ratio & Proportion:
*   *Disguised wording*: "The ratio of investments of A and B is $3:5$. The profit share of A is..."
*   *Real P&L link*: A's share is $\frac{3}{8}$ of the total profit pool. Use ratio scaling.

### B. Hidden in Mixtures & Alligation:
*   *Disguised wording*: "A merchant mixes two types of wheat costing ₹40/kg and ₹50/kg and sells the mixture at ₹48/kg to make a $10\%$ profit."
*   *Real P&L link*: The average cost price (CP) of the mixture is $\frac{SP}{1.10} = \frac{48}{1.10} = ₹43.63/\text{kg}$. Use this CP in the alligation scale.

---

## 4. Difficulty Escalation Patterns
Understand how TCS makes an easy concept difficult:

```
[Level 1: Basic Trade] 
"Buy for 100, sell for 120. Find profit%."
           │
           v
[Level 2: Consecutive Markup-Discount] 
"Mark up by 30%, discount by 10%. Find net profit%."
           │
           v
[Level 3: Dishonest Dealer with Markup] 
"Mark up by 20%, give 10% discount, AND use 900g instead of 1kg. Find net profit%."
```
*(To solve Level 3, multiply the profit factor of markup/discount by the profit factor of the faulty weight: $1.08 \times \frac{1000}{900} = 1.20 \implies 20\%$ profit).*
