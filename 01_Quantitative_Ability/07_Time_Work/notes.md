# Time and Work — Complete Notes

---

## 1. The Efficiency-Based Approach

In Time and Work problems, the core relationship between the amount of work done, the rate of work (efficiency), and the time taken is:

$$\text{Work} = \text{Rate (Efficiency)} \times \text{Time}$$

*   **Work ($W$):** The total task to be completed. We often assume total work to be $1$ unit (fraction method) or the LCM of the days taken (LCM method).
*   **Efficiency ($E$):** Work done per unit time (e.g., work done in 1 day).
*   **Time ($T$):** The duration taken to complete the work.

### The LCM Method (Highly Recommended for TCS NQT)
Instead of dealing with fractions like $\frac{1}{A} + \frac{1}{B}$, assume the total work is the LCM of the time taken by each individual.
*   **Step 1:** Find the LCM of the individual times. Assume this is the "Total Units of Work."
*   **Step 2:** Calculate individual efficiencies: $\text{Efficiency} = \frac{\text{Total Units of Work}}{\text{Individual Time}}$.
*   **Step 3:** Add efficiencies of people working together to find combined efficiency.
*   **Step 4:** Find combined time: $\text{Time} = \frac{\text{Total Units of Work}}{\text{Combined Efficiency}}$.

*Example:* $A$ can do a piece of work in 10 days and $B$ in 15 days. In how many days can they complete it together?
1.  $\text{Total Work} = \text{LCM}(10, 15) = 30\text{ units}$.
2.  $\text{Efficiency of } A = \frac{30}{10} = 3\text{ units/day}$.
    $\text{Efficiency of } B = \frac{30}{15} = 2\text{ units/day}$.
3.  $\text{Combined Efficiency} = 3 + 2 = 5\text{ units/day}$.
4.  $\text{Combined Time} = \frac{30}{5} = 6\text{ days}$.

---

## 2. Pipes and Cisterns

Pipes and Cisterns are direct physical applications of Time and Work, where work represents filling or emptying a tank.

*   **Inlet Pipe:** Fills the tank. Its efficiency is positive ($+E$).
*   **Outlet Pipe (or Leak):** Empties the tank. Its efficiency is negative ($-E$).

$$\text{Combined Rate} = E_{\text{inlet 1}} + E_{\text{inlet 2}} - E_{\text{outlet}}$$

*   If the Combined Rate is **positive**, the tank will eventually fill.
*   If the Combined Rate is **negative**, a full tank will eventually empty.

---

## 3. Combined Work with Negative Work (Leaks)

Negative work occurs when an agent destroys work or drains resources while others build/fill.

*   *Scenario:* A tap can fill a tank in 8 hours. Because of a leak in the bottom of the tank, it takes 10 hours to fill the tank. If the tank is full, in how many hours will the leak empty it?
1.  Let total capacity of the tank be $\text{LCM}(8, 10) = 40\text{ units}$.
2.  $\text{Efficiency of Tap} = \frac{40}{8} = +5\text{ units/hour}$.
3.  $\text{Combined Efficiency (Tap + Leak)} = \frac{40}{10} = +4\text{ units/hour}$.
4.  $\text{Efficiency of Leak} = \text{Combined} - \text{Tap} = 4 - 5 = -1\text{ unit/hour}$.
5.  $\text{Time taken by leak to empty full tank} = \frac{40}{|-1|} = 40\text{ hours}$.

---

## 4. Cross-References & Overlapping Topics

*   **Inverse Proportionality:** When the work $W$ is constant, Efficiency ($E$) and Time ($T$) are inversely proportional ($E_1 \cdot T_1 = E_2 \cdot T_2$). If $A$'s efficiency is $1.5$ times $B$'s efficiency, the ratio of their times taken is $2:3$. See [Ratio & Proportion Notes — Direct & Inverse Section](file:///Users/rajsumit/Desktop/TCS-NQT/01_Quantitative_Ability/03_Ratio_Proportion/notes.md#2-direct-and-inverse-proportion) to review inverse proportions.
*   **Weighted Rate (Mixture of Pipes):** Mixing the filling rates of multiple pipes to find the overall net rate of a cistern is similar to finding a weighted average of rates. See [Average Notes — Weighted Average Section](file:///Users/rajsumit/Desktop/TCS-NQT/01_Quantitative_Ability/04_Average/notes.md#1-weighted-average).
