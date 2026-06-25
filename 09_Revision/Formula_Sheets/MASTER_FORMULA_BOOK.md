# TCS NQT 2026: Master Formula Book

This master guide aggregates every critical formula from Numerical Ability, Reasoning, Advanced Section, and Coding. Use this for quick printable review (A4-optimized layout).

---

## 📌 Master Table of Contents

- [Numerical Ability](#1-numerical-ability)
  - [Number System](#number-system)
  - [Percentages](#percentages)
  - [Profit and Loss](#profit-and-loss)
  - [SI & CI](#si--ci)
  - [Ratio & Proportion](#ratio--proportion)
  - [Time & Work](#time--work)
  - [Time Speed Distance](#time-speed-distance)
  - [Averages](#averages)
  - [Permutations & Combinations](#permutations--combinations)
  - [Probability](#probability)
- [Advanced Section](#2-advanced-section)
  - [AP & GP Series](#ap--gp-series)
  - [Coordinate Geometry](#coordinate-geometry)
  - [Logarithms](#logarithms)
  - [Modular Arithmetic](#modular-arithmetic)
  - [Surds & Indices](#surds--indices)
- [Reasoning Ability](#3-reasoning-ability)
  - [Clocks & Calendars](#clocks--calendars)
- [Coding Section](#4-coding-section)
  - [Memory Addressing](#memory-addressing)
  - [Time & Space Constraints](#time--space-constraints)

---

> [!TIP]
> **Night-Before-Exam Reading Order**:
> 1. [Modular Arithmetic](#modular-arithmetic) (High-weight, high-forgetting rate)
> 2. [Clocks & Calendars](#clocks--calendars) (Specific angle & odd-day rules)
> 3. [SI & CI](#si--ci) (Successive interest and difference formulas)
> 4. [Time Speed Distance](#time-speed-distance) (Relative speed and average speed)
> 5. [Memory Addressing](#memory-addressing) (Dynamic offset formulas)

---

## 1. Numerical Ability

### Number System
#### 1. Number of Factors
- **Formula**: For a number $N = p^a \cdot q^b \cdot r^c \dots$ (where $p, q, r$ are prime factors):
  $$\text{Total Factors} = (a + 1)(b + 1)(c + 1)\dots$$
- **Derivation**: Each prime factor $p$ can be chosen in $(a+1)$ ways (from $p^0$ to $p^a$). By multiplication rule, total selections form the divisor set.
- **When to Use**: Finding the count of numbers that divide a target integer.
- **Quick Example**: For $12 = 2^2 \cdot 3^1$, factors $= (2+1)(1+1) = 6$.
- **Memory Trick**: "Add 1 to exponents and multiply."

#### 2. Divisibility Rule for 11
- **Formula**:
  $$\text{Sum of odd-position digits} - \text{Sum of even-position digits} = 0 \text{ or multiple of } 11$$
- **Derivation**: Since $10 \equiv -1 \pmod{11}$, $10^k \equiv (-1)^k \pmod{11}$. Thus:
  $$\sum d_k 10^k \equiv \sum d_k (-1)^k \pmod{11}$$
- **When to Use**: Finding missing digits in numbers divisible by 11.
- **Quick Example**: For $121$, $(1+1) - (2) = 0$. Divisible.
- **Memory Trick**: "Alternate sum difference."

---

### Percentages
#### 1. Successive Percentage Change
- **Formula**: Two successive changes of $x\%$ and $y\%$ yield a net change of:
  $$\text{Net Change} = \left(x + y + \frac{xy}{100}\right)\%$$
- **Derivation**:
  $$\text{Final} = \text{Initial} \times \left(1 + \frac{x}{100}\right)\left(1 + \frac{y}{100}\right) = \text{Initial} \times \left(1 + \frac{x + y + xy/100}{100}\right)$$
- **When to Use**: Consecutive markup/discount, population changes, salary increments.
- **Quick Example**: $10\%$ increase then $20\%$ increase yields $10 + 20 + 2 = 32\%$ net change.
- **Memory Trick**: "Sum plus product over hundred."

#### 2. Product Constancy (Expenditure Rule)
- **Formula**: If quantity $A \times B = \text{Constant}$, and $A$ increases by $x\% = \frac{a}{b}$, then $B$ must decrease by:
  $$\text{Decrease} = \frac{a}{a+b}$$
- **Derivation**:
  $$(A \cdot (1 + a/b)) \times (B \cdot (1 - \text{dec})) = A \cdot B \implies \frac{a+b}{b} (1-\text{dec}) = 1 \implies \text{dec} = \frac{a}{a+b}$$
- **When to Use**: Price rises and we want to keep overall expenditure constant.
- **Quick Example**: Price of petrol rises by $25\% = 1/4$. Consumption must drop by $\frac{1}{1+4} = 1/5 = 20\%$.
- **Memory Trick**: "Increase numerator to denominator for decrease."

---

### Profit and Loss
#### 1. Profit / Loss Percentage
- **Formula**:
  $$\text{Profit \%} = \frac{\text{SP} - \text{CP}}{\text{CP}} \times 100$$
  $$\text{Loss \%} = \frac{\text{CP} - \text{SP}}{\text{CP}} \times 100$$
- **Derivation**: Relative change calculated with Cost Price (CP) as the base.
- **When to Use**: Measuring basic trade margins.
- **Quick Example**: $\text{CP} = 100$, $\text{SP} = 120$. Profit $\% = \frac{20}{100} \times 100 = 20\%$.
- **Memory Trick**: "CP is always the anchor base."

#### 2. Dishonest Dealer Formula
- **Formula**:
  $$\frac{\text{SP}}{\text{CP}} = \left(\frac{\text{True Weight}}{\text{False Weight}}\right) \times \left(1 + \text{stated profit \%}\right)$$
- **Derivation**: Selling less weight means cost is reduced to the false weight while revenue is charged for the true weight.
- **When to Use**: Calculating actual profit when seller uses faulty weights.
- **Quick Example**: Dealer claims to sell at CP but uses $900\text{g}$ instead of $1\text{kg}$. Profit ratio $= \frac{1000}{900} = 1.11 \implies 11.11\%$ profit.
- **Memory Trick**: "True weight goes on top."

---

### SI & CI
#### 1. Simple Interest (SI)
- **Formula**:
  $$\text{SI} = \frac{P \times R \times T}{100}$$
- **Derivation**: Constant rate accumulation: $P \times R\%$ added every year for $T$ periods.
- **When to Use**: Straight-line interest calculation.
- **Quick Example**: $P = 1000$, $R = 10\%$, $T = 2 \implies \text{SI} = \frac{1000 \times 10 \times 2}{100} = 200$.
- **Memory Trick**: "PRT over 100."

#### 2. Compound Interest (CI) Amount
- **Formula**:
  $$\text{Amount} = P \left(1 + \frac{R}{100}\right)^T$$
- **Derivation**: Geometric progression: Year-end balance becomes principal for the next period.
- **When to Use**: Compounding calculations.
- **Quick Example**: $P = 1000$, $R = 10\%$, $T = 2 \implies \text{Amount} = 1000(1.1)^2 = 1210$.
- **Memory Trick**: "Principal times multiplier to power T."

#### 3. Difference between CI and SI
- **Formula (2 Years)**:
  $$D_2 = P\left(\frac{R}{100}\right)^2$$
- **Formula (3 Years)**:
  $$D_3 = P\left(\frac{R}{100}\right)^2 \times \left(3 + \frac{R}{100}\right)$$
- **Derivation**: Expanding the binomial compound formulas and subtracting simple interest.
- **When to Use**: Comparing compound and simple interest payouts.
- **Quick Example**: $P=1000, R=10\% \implies D_2 = 1000 \times (0.1)^2 = 10$.
- **Memory Trick**: "$P R$-square for 2 years."

---

### Ratio & Proportion
#### 1. Third Proportional
- **Formula**: For $a : b = b : c$, $c$ is the third proportional:
  $$c = \frac{b^2}{a}$$
- **Derivation**: $a/b = b/c \implies ac = b^2 \implies c = b^2/a$.
- **When to Use**: Finding missing continuous proportions.
- **Quick Example**: Third proportional to 4 and 6 is $\frac{36}{4} = 9$.
- **Memory Trick**: "Square the middle, divide by start."

#### 2. Mixture Allegation Formula
- **Formula**:
  $$\frac{\text{Qty of Cheap}}{\text{Qty of Dear}} = \frac{\text{Dear Rate} - \text{Mean Rate}}{\text{Mean Rate} - \text{Cheap Rate}}$$
- **Derivation**: Weighted average balance:
  $$C \cdot x + D \cdot y = M(x + y) \implies x(M - C) = y(D - M) \implies \frac{x}{y} = \frac{D-M}{M-C}$$
- **When to Use**: Mixing commodities of two different costs.
- **Quick Example**: Mixing milk at $10\text{/L}$ and $20\text{/L}$ to get $12\text{/L}$ mixture. Ratio $= \frac{20-12}{12-10} = \frac{8}{2} = 4:1$.
- **Memory Trick**: "Cross-subtract differences."

---

### Time & Work
#### 1. Combined Efficiency Rule
- **Formula**: If $A$ does work in $D_1$ days, and $B$ does work in $D_2$ days, together they take:
  $$\text{Days} = \frac{D_1 \times D_2}{D_1 + D_2}$$
- **Derivation**: Combined rate $= \frac{1}{D_1} + \frac{1}{D_2} = \frac{D_1 + D_2}{D_1 D_2}$. Reverse rate to get time.
- **When to Use**: Finding combined durations.
- **Quick Example**: $A=10$ days, $B=15$ days $\implies \text{Time} = \frac{150}{25} = 6$ days.
- **Memory Trick**: "Product over sum."

#### 2. Chain Rule (Man-Days Equivalence)
- **Formula**:
  $$\frac{M_1 \cdot D_1 \cdot H_1}{W_1} = \frac{M_2 \cdot D_2 \cdot H_2}{W_2}$$
- **Derivation**: Total work is proportional to men, days, and hours, and inversely proportional to output.
- **When to Use**: Group productivity comparisons.
- **Quick Example**: 5 men do 10 toys in 6 days. How many days for 3 men to do 8 toys? $\frac{5 \cdot 6}{10} = \frac{3 \cdot D}{8} \implies 3 = \frac{3D}{8} \implies D = 8$ days.
- **Memory Trick**: "$MDH$ over $W$ is constant."

---

### Time Speed Distance
#### 1. Average Speed (Equal Distance halves)
- **Formula**:
  $$\text{Avg Speed} = \frac{2 \cdot S_1 \cdot S_2}{S_1 + S_2}$$
- **Derivation**:
  $$\text{Total Distance} = 2d, \text{ Total Time} = \frac{d}{S_1} + \frac{d}{S_2} \implies \text{Avg Speed} = \frac{2d}{d(S_1 + S_2)/(S_1 S_2)}$$
- **When to Use**: Round trips, equal distance segments.
- **Quick Example**: $S_1 = 40$, $S_2 = 60 \implies \text{Avg} = \frac{2 \cdot 2400}{100} = 48\text{ km/h}$.
- **Memory Trick**: "Harmonic mean of speeds."

#### 2. Relative Speed
- **Formula**:
  $$\text{Same Direction} = |S_1 - S_2|$$
  $$\text{Opposite Direction} = S_1 + S_2$$
- **Derivation**: Vectors summation in one-dimensional space.
- **When to Use**: Overtaking, meeting times, train cross pass.
- **Quick Example**: Police ($12\text{ m/s}$) chasing thief ($10\text{ m/s}$). Catch-up rate $= 12 - 10 = 2\text{ m/s}$.
- **Memory Trick**: "Opposites attract (add), sames repel (subtract)."

---

### Averages
#### 1. Weighted Average
- **Formula**:
  $$\text{Mean} = \frac{n_1 \cdot A_1 + n_2 \cdot A_2}{n_1 + n_2}$$
- **Derivation**: Total sum divided by total observations count.
- **When to Use**: Averaging groups of different sizes.
- **Quick Example**: Class A (20 students) averages 80. Class B (30 students) averages 90. $\text{Avg} = \frac{20(80) + 30(90)}{50} = \frac{1600+2700}{50} = 86$.
- **Memory Trick**: "Sum of weights times values over sum of weights."

---

### Permutations & Combinations
#### 1. Selection ($nCr$) and Arrangement ($nPr$)
- **Formulas**:
  $$nCr = \frac{n!}{r!(n-r)!}$$
  $$nPr = \frac{n!}{(n-r)!}$$
- **Derivation**: $nPr$ counts arrangements. Dividing by $r!$ removes ordering of selected items.
- **When to Use**: Team selection ($nCr$), word formation ($nPr$).
- **Quick Example**: Select 2 from 5: $5C2 = \frac{120}{2 \cdot 6} = 10$.
- **Memory Trick**: "Arrangement has more options than selection."

#### 2. Circular Permutation
- **Formula**:
  $$\text{Arrangements} = (n - 1)!$$
- **Derivation**: Fixing one person's position removes rotational symmetry.
- **When to Use**: Table seating, round necklace loop (divide by 2 if clockwise/counterclockwise are identical).
- **Quick Example**: 5 people at round table $= (5-1)! = 24$ ways.
- **Memory Trick**: "Lock one down."

---

### Probability
#### 1. General Probability Rule
- **Formula**:
  $$P(A) = \frac{\text{Number of Favorable Outcomes}}{\text{Total Sample Space Size}}$$
- **Derivation**: Laplace's classical definition of equally likely events.
- **When to Use**: Base probability of rolls, picks, coins.
- **Quick Example**: Roll even number on 6-sided die: $3/6 = 0.5$.
- **Memory Trick**: "Want over all."

#### 2. Conditional Probability
- **Formula**:
  $$P(A|B) = \frac{P(A \cap B)}{P(B)}$$
- **Derivation**: Restricting the sample space to event $B$.
- **When to Use**: Event $A$ occurring given event $B$ has already happened.
- **Quick Example**: $P(\text{Ace}) = 4/52$. Given card is red, $P(\text{Ace|Red}) = 2/26 = 1/13$.
- **Memory Trick**: "Intersect over given."

---

## 2. Advanced Section

### AP & GP Series
#### 1. Arithmetic Progression (AP) Sum
- **Formula**:
  $$S_n = \frac{n}{2}[2a + (n-1)d]$$
- **Derivation**: Summing terms forwards and backwards yields $n$ instances of $(a + L)$.
- **When to Use**: Evenly spaced series summation.
- **Quick Example**: Sum of first 10 terms of $2, 4, 6\dots \implies S_{10} = 5(4 + 18) = 110$.
- **Memory Trick**: "Half of terms times sum of first and last."

#### 2. Geometric Progression (GP) Sum
- **Formula**:
  $$S_n = \frac{a(r^n - 1)}{r - 1}$$
- **Formula (Infinite GP, $|r| < 1$)**:
  $$S_{\infty} = \frac{a}{1 - r}$$
- **Derivation (Infinite)**:
  $$S = a + ar + ar^2 \dots \implies rS = ar + ar^2 + \dots \implies S - rS = a \implies S(1-r) = a$$
- **When to Use**: Exponential series summation.
- **Quick Example**: $1 + 1/2 + 1/4 + \dots \implies S_{\infty} = \frac{1}{1 - 0.5} = 2$.
- **Memory Trick**: "Start over one minus ratio."

---

### Coordinate Geometry
#### 1. Distance between Points
- **Formula**:
  $$d = \sqrt{(x_2 - x_1)^2 + (y_2 - y_1)^2}$$
- **Derivation**: Pythagorean theorem applied to right-triangle coordinate shifts.
- **When to Use**: Segment lengths.
- **Quick Example**: Distance between $(1, 2)$ and $(4, 6)$ is $\sqrt{3^2 + 4^2} = 5$.
- **Memory Trick**: "Square root of sum of differences squared."

#### 2. Distance from Point $(x_0, y_0)$ to Line $Ax + By + C = 0$
- **Formula**:
  $$d = \frac{|Ax_0 + By_0 + C|}{\sqrt{A^2 + B^2}}$$
- **Derivation**: Projection of distance vector onto unit normal vector.
- **When to Use**: Altitude of triangles, shortest path checks.
- **Quick Example**: Distance from $(1, 1)$ to $3x + 4y - 2 = 0$ is $\frac{|3(1)+4(1)-2|}{\sqrt{9+16}} = \frac{5}{5} = 1$.
- **Memory Trick**: "Plug point into line, divide by vector magnitude."

---

### Logarithms
#### 1. Base Change Theorem
- **Formula**:
  $$\log_b a = \frac{\log_c a}{\log_c b}$$
- **Derivation**: Let $\log_b a = x \implies b^x = a$. Take $\log_c$ on both sides:
  $$x \log_c b = \log_c a \implies x = \frac{\log_c a}{\log_c b}$$
- **When to Use**: Evaluating logarithms with mismatched bases.
- **Quick Example**: $\log_8 4 = \frac{\log_2 4}{\log_2 8} = \frac{2}{3}$.
- **Memory Trick**: "Upper term goes up, base term goes down."

---

### Modular Arithmetic
#### 1. Fermat's Little Theorem
- **Formula**: If $p$ is prime, for any integer $a$ not divisible by $p$:
  $$a^{p-1} \equiv 1 \pmod p$$
- **Derivation**: Congruence properties of the set of multiples $\{a, 2a, \dots, (p-1)a\}$ modulo $p$.
- **When to Use**: Finding remainders of large powers divided by primes.
- **Quick Example**: $2^{10} \equiv 1 \pmod{11}$.
- **Memory Trick**: "Power is prime minus one."

#### 2. Euler's Totient Rule
- **Formula**: If $\gcd(a, n) = 1$, then:
  $$a^{\phi(n)} \equiv 1 \pmod n$$
  where $\phi(n) = n \left(1 - \frac{1}{p_1}\right)\left(1 - \frac{1}{p_2}\right)\dots$
- **Derivation**: Generalization of FLT using reduced residue classes.
- **When to Use**: Remainders when divisor is composite.
- **Quick Example**: Find $3^{100} \pmod{10}$. $\phi(10) = 10(1/2)(4/5) = 4$.
  Since $3^4 \equiv 1 \pmod{10}$, $3^{100} = (3^4)^{25} \equiv 1 \pmod{10}$.
- **Memory Trick**: "Euler totient general power reducer."

---

### Surds & Indices
#### 1. Laws of Indices
- **Formula**:
  $$a^m \cdot a^n = a^{m+n}$$
  $$(a^m)^n = a^{m \cdot n}$$
- **Derivation**: Expanded multiplicative sequences.
- **When to Use**: Simplifying exponential expressions.
- **Quick Example**: $(2^2)^3 = 2^6 = 64$.
- **Memory Trick**: "Power of power multiplies, multiplying bases adds."

---

## 3. Reasoning Ability

### Clocks & Calendars
#### 1. Clock Hands Angle Formula
- **Formula**: The angle $\theta$ between hour hand and minute hand at $H$ hours and $M$ minutes is:
  $$\theta = |30H - 5.5M|^\circ$$
- **Derivation**: Hour hand speed $= 0.5^\circ/\text{min}$, minute hand speed $= 6^\circ/\text{min}$.
  Hour hand position $= 30H + 0.5M$. Minute hand position $= 6M$. Difference $= |30H - 5.5M|$.
- **When to Use**: Finding angle or coincident positions of hands.
- **Quick Example**: At 3:40, $\theta = |30(3) - 5.5(40)| = |90 - 220| = 130^\circ$.
- **Memory Trick**: "Thirty times Hours minus five-point-five times Minutes."

#### 2. Odd Days Leap Cycle
- **Formula**:
  $$\text{Ordinary Year} = 1 \text{ odd day (365 days } = 52 \text{ weeks } + 1 \text{ day)}$$
  $$\text{Leap Year} = 2 \text{ odd days (366 days } = 52 \text{ weeks } + 2 \text{ days)}$$
- **When to Use**: Calculating weekday dates across years.
- **Quick Example**: If Jan 1, 2023 was Sunday, Jan 1, 2024 is Monday ($+1$).
- **Memory Trick**: "Normal adds 1, leap adds 2."

---

## 4. Coding Section

### Memory Addressing
#### 1. Address Offset (1D Array)
- **Formula**:
  $$\text{Address}(A[i]) = \text{Base} + i \times \text{sizeof(DataType)}$$
- **Derivation**: Index $i$ indicates the number of preceding elements. The size of the data type scales the pointer shift.
- **When to Use**: Pointer offset calculations and low-level memory analysis.
- **Quick Example**: For `int arr[5]` starting at `1000`, `arr[3]` address is $1000 + 3 \times 4 = 1012$.
- **Memory Trick**: "Base plus index times size."

#### 2. Address Offset (2D Array Row-Major)
- **Formula**:
  $$\text{Address}(A[i][j]) = \text{Base} + (i \times \text{Cols} + j) \times \text{sizeof(DataType)}$$
- **Derivation**: To reach row $i$, we skip $i$ full rows of size $\text{Cols}$. Then, we skip $j$ elements in row $i$.
- **When to Use**: Mapped dynamic 1D allocations representing 2D grids.
- **Quick Example**: For $3 \times 5$ array, element at $(2, 1)$ with Base `1000`:
  $$\text{Address} = 1000 + (2 \times 5 + 1) \times 4 = 1044$$
- **Memory Trick**: "Rows skipped times cols plus current column."

---

### Time & Space Constraints

The table below maps problem size $N$ to the required time complexity to avoid Time Limit Exceeded (TLE) under a 1.0-second limit ($10^8$ operations):

| Constraint Size ($N$) | Required Time Complexity | Typical Algorithms |
| :--- | :--- | :--- |
| $N \le 10$ | $O(N!)$ or $O(2^N)$ | Backtracking, subset generation |
| $N \le 10^3$ | $O(N^2)$ | Bubble sort, naive subarray search |
| $N \le 10^5$ | $O(N \log N)$ | Merge sort, Heap sort, binary search sorting |
| $N \le 10^7$ | $O(N)$ | Sliding window, prefix sums, single scans |
| $N \ge 10^8$ | $O(\log N)$ or $O(1)$ | Binary search, mathematical calculations |
