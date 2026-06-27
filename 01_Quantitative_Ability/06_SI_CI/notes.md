# Simple and Compound Interest — Complete Notes

---

## 1. Simple vs. Compound Interest Formulas

Interest is the cost of borrowing capital. How this cost is calculated over time differentiates Simple Interest (SI) from Compound Interest (CI).

### Simple Interest (SI)
SI is calculated only on the principal (initial amount) borrowed. The interest accrued is constant each year.

$$\text{SI} = \frac{P \times R \times T}{100}$$

$$\text{Amount (A)} = P + \text{SI} = P \times \left(1 + \frac{R \times T}{100}\right)$$

*   $P$ = Principal, $R$ = Annual interest rate (in %), $T$ = Time (in years).
*   **Linear Growth:** SI grows linearly over time (Arithmetic Progression). Each year adds a fixed percentage increase of the *initial* principal.

### Compound Interest (CI)
CI is calculated on the principal plus any accumulated interest from previous periods. It is "interest on interest."

$$\text{Amount (A)} = P \times \left(1 + \frac{R}{100}\right)^n$$

$$\text{CI} = A - P = P \times \left[\left(1 + \frac{R}{100}\right)^n - 1\right]$$

*   $n$ = Number of compounding cycles.
*   **Exponential Growth:** CI grows exponentially over time (Geometric Progression).
*   **Compounding Intervals:** If interest is not compounded annually, the rate and cycles adjust as follows:
    *   *Half-Yearly (Semi-Annually):* Rate becomes $\frac{R}{2}\%$, cycles become $2n$.
        $$A = P \times \left(1 + \frac{R/2}{100}\right)^{2n}$$
    *   *Quarterly:* Rate becomes $\frac{R}{4}\%$, cycles become $4n$.
        $$A = P \times \left(1 + \frac{R/4}{100}\right)^{4n}$$

---

## 2. Difference Between SI and CI

TCS NQT regularly tests the difference ($D$) between Compound Interest and Simple Interest earned over a fixed period on the same principal $P$ and rate $R\%$.

*   **For 1 Year:** If compounded annually, the interest for the first year is the same for both SI and CI:
    $$D_1 = \text{CI}_1 - \text{SI}_1 = 0$$
*   **For 2 Years ($D_2$):**
    $$D_2 = \text{CI}_2 - \text{SI}_2 = P \times \left(\frac{R}{100}\right)^2$$
*   **For 3 Years ($D_3$):**
    $$D_3 = \text{CI}_3 - \text{SI}_3 = P \times \left(\frac{R}{100}\right)^2 \times \left(3 + \frac{R}{100}\right) = D_2 \times \left(3 + \frac{R}{100}\right)$$

---

## 3. Installment Problems

Installment equations help calculate the regular payments required to clear a accumulated loan or debt.

### Case 1: Simple Interest Installments
Let a debt of $D$ be discharged in $t$ equal annual installments of $\$x$ each, at $r\%$ Simple Interest.
The total value of all installments must equal the debt $D$ at the end of $t$ years:

$$D = x \cdot t + \frac{x \cdot r \cdot t(t-1)}{200}$$

*   **Logic:**
    *   The last installment is paid at the end of year $t$, so it accrues $0$ interest.
    *   The second-last installment is paid at year $t-1$, accruing interest for $1$ year: $x + \frac{xr}{100}$.
    *   The first installment is paid at year $1$, accruing interest for $t-1$ years: $x + \frac{x \cdot r(t-1)}{100}$.
    *   Adding these terms forms an arithmetic series resulting in the equation above.

### Case 2: Compound Interest Installments
Let a loan of principal $P$ be repaid in $n$ equal annual installments of $\$x$ each, at $r\%$ Compound Interest.
The present value of all installments must equal the initial principal $P$:

$$P = \frac{x}{\left(1 + \frac{r}{100}\right)^1} + \frac{x}{\left(1 + \frac{r}{100}\right)^2} + \dots + \frac{x}{\left(1 + \frac{r}{100}\right)^n}$$

*   **Logic:**
    *   Each term represents the discounted present value of the installment paid at the end of that specific year.
    *   To solve quickly, let $v = \frac{1}{1 + R/100}$. Then:
        $$P = x(v + v^2 + \dots + v^n)$$
    *   The sum inside the parentheses can be calculated using the sum of a Geometric Progression (GP).

---

## 4. Cross-References & Overlapping Topics

*   **Successive Percentage Increases:** Compound Interest is mathematically identical to successive percentage increases. See [Percentage Notes — Successive Percentage Change Section](file:///Users/rajsumit/Desktop/TCS-NQT/01_Quantitative_Ability/02_Percentage/notes.md#3-successive-percentage-change) to see how the compounding factor is built from successive rates.
*   **Geometric Progression:** CI amount equations represent terms of a Geometric Progression where the common ratio is $\left(1 + \frac{R}{100}\right)$.
*   **Weighted Averages in Investments:** If a principal is split and invested in different accounts at rates $r_1\%$ and $r_2\%$, the net interest rate is solved using Alligations. Refer to [Ratio & Proportion Notes — Mixture & Alligation Section](file:///Users/rajsumit/Desktop/TCS-NQT/01_Quantitative_Ability/03_Ratio_Proportion/notes.md#4-mixture--alligation-basics).
