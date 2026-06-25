---
title: "Profit & Loss - Cheatsheet"
section: "Numerical Ability"
---

# Profit & Loss 3-Min Cheatsheet

**Exam Weight**: 2 Questions | **Target Time**: < 75s | **OS Tip**: Enter numbers only in FIBs.

---

## 📐 Formulas & Memory Tricks

| Concept | Mathematical Formula | Memory Trick |
| :--- | :--- | :--- |
| **Profit %** | $$\text{Profit}\% = \left(\frac{SP - CP}{CP}\right) \times 100$$ | CP is the base (capital invested) |
| **Loss %** | $$\text{Loss}\% = \left(\frac{CP - SP}{CP}\right) \times 100$$ | CP is the base (capital invested) |
| **Discount %** | $$\text{Discount}\% = \left(\frac{MP - SP}{MP}\right) \times 100$$ | Discount is off MP (label price) |
| **Markup %** | $$\text{Markup}\% = \left(\frac{MP - CP}{CP}\right) \times 100$$ | Markup is added to CP |
| **MP-CP Ratio** | $$\frac{MP}{CP} = \frac{100 + P}{100 - D}$$ | Profit increases MP; discount reduces CP base |
| **Dishonest Dealer**| $$\text{Profit}\% = \left(\frac{\text{Error}}{\text{Delivered}}\right) \times 100$$ | Dealer invests delivered weight |

---

## ⚡ Speed Shortcuts
*   **Successive Discount**: $d_{\text{net}} = d_1 + d_2 - \frac{d_1 d_2}{100}$. (e.g. $10\% + 20\% \implies 28\%$).
*   **Symmetric Equal SP**: same SP, $+x\%$ and $-x\% \implies$ Net Loss $= (\frac{x}{10})^2\%$.
*   **Buy X, get Y free**: discount $= \frac{Y}{X+Y} \times 100\%$. (e.g. Buy 4 get 1 free $= 20\%$).
*   **CP-SP Article Count**: CP of X = SP of Y $\implies \frac{SP}{CP} = \frac{X}{Y}$.
*   **Weight cheating buy & sell**: Net Profit% $= \frac{\text{Cheat Buy}\% + \text{Cheat Sell}\%}{100 - \text{Cheat Sell}\%} \times 100\%$.

---

## ⚠️ Warning Box: Top 3 Traps
> [!WARNING]
> 1. **Dishonest Dealer Denominator**: Do **NOT** divide by 1000g. Always divide by the actual weight delivered to the customer (e.g., 900g).
> 2. **Discount Baseline**: Never calculate a discount on Cost Price. Apply discounts to the Marked Price (MP) only.
> 3. **Hypothetical Base Shift**: When solving "if bought for $x\%$ less," make sure to calculate the new profit margin on the reduced CP base.

---

## 🌳 Decision Support Map
```
                         Identify the Given Variables
                                      |
                +---------------------+---------------------+
                |                                           |
         CP and SP given?                            MP and Discount given?
                |                                           |
         +------+------+                             +------+------+
         |             |                             |             |
      SP > CP       CP > SP                       Markup?       No Markup?
         v             v                             v             v
      Profit %      Loss %                        MP = CP*(1+m) SP = MP*(1-d)
```
