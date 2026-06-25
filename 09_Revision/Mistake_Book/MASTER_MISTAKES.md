# TCS NQT 2026: Master Mistake Book

This reference catalog details calculation, conceptual, and carelessness errors, highlighting the 50 most dangerous traps across all exam sections.

---

## 🚫 The 4 Core Mistake Categories

| Mistake Type | Common Example | Why it happens | Prevention Strategy |
| :--- | :--- | :--- | :--- |
| **Calculation** | Adding $12 + 18 = 40$ | Speed anxiety, mental fatigue | Double-check simple additions using units-place digit checks. |
| **Conceptual** | Using Arithmetic Mean for Avg Speed | Misunderstanding underlying rates | Map units: Speed is distance/time, requiring harmonic means. |
| **Trap** | Century year 2100 treated as Leap Year | Forgetting the divisibility-by-400 rule | Century years must be divisible by 400 to be leap years. |
| **Careless** | Not checking if output requires mod $10^9+7$ | Skipping the last sentence of the prompt | Highlight the output requirements before typing code. |

---

## 💀 Top 50 Most Dangerous Exam Traps

### Numerical Ability Traps

1. **Adding Successive Discounts Directly**
   - *Trap*: Stating $20\%$ and $10\%$ discounts equal $30\%$.
   - *Correction*: Net discount $= 20 + 10 - \frac{20 \cdot 10}{100} = 28\%$.

2. **Incorrect Cost Price Base for Profit**
   - *Trap*: Calculating profit percentage using SP in the denominator.
   - *Correction*: Profit is always relative to Cost Price ($\text{CP}$).

3. **Dishonest Dealer Weight Base Mismatch**
   - *Trap*: Using $1000\text{g}$ as cost base when dealer only uses $800\text{g}$.
   - *Correction*: Actual cost base is the false weight delivered ($800\text{g}$).

4. **Compounding Period Doubling Neglect**
   - *Trap*: Using annual rate and years for half-yearly compounding.
   - *Correction*: Halve the rate ($R/2$) and double the time ($2T$).

5. **Direct Mean of Speeds**
   - *Trap*: Calculating average speed of round trip as $\frac{S_1 + S_2}{2}$.
   - *Correction*: Use harmonic mean: $\frac{2 \cdot S_1 \cdot S_2}{S_1 + S_2}$.

6. **Relative Speed Vector Sign Swap**
   - *Trap*: Subtracting speeds when objects move in opposite directions.
   - *Correction*: Add speeds for opposite directions; subtract for same direction.

7. **Speed Unit Conversion Mismatch**
   - *Trap*: Mixing $\text{km/h}$ and $\text{meters}$ without converting units.
   - *Correction*: Convert $\text{km/h} \rightarrow \text{m/s}$ by multiplying by $\frac{5}{18}$.

8. **Weighted Average Sample Size Neglect**
   - *Trap*: Averaging group scores directly without weighting by size.
   - *Correction*: Use $\frac{n_1 A_1 + n_2 A_2}{n_1 + n_2}$.

9. **Double Counting Range Boundaries**
   - *Trap*: Stating there are $B - A$ integers between $A$ and $B$ inclusive.
   - *Correction*: Total integers $= B - A + 1$.

10. **Arrangement vs. Selection Mixing**
    - *Trap*: Using permutations ($nPr$) when order does not matter.
    - *Correction*: Use combinations ($nCr$) for pure selection.

11. **Circular Seating Rotational Shifts**
    - *Trap*: Seating $N$ people in circle in $N!$ ways.
    - *Correction*: Circular arrangements $= (N-1)!$.

12. **Non-Prime Factor Count Bases**
    - *Trap*: Using exponents of non-prime bases in $(a+1)(b+1)$ factor formula.
    - *Correction*: Express number in prime factorization form first.

13. **Pipes and Cisterns Negative Work Sign**
    - *Trap*: Adding outlet pipe rates instead of subtracting them.
    - *Correction*: Treat outlet pipe rate as negative work.

14. **Calendar Century Leap Year Rule**
    - *Trap*: Treating year 1900 as a leap year because it divides by 4.
    - *Correction*: Century years must be divisible by 400 (1900 is not, 2000 is).

15. **Alphabet Reverse Position Shift**
    - *Trap*: Calculating reverse position of letter $X$ as $26 - \text{forward}$.
    - *Correction*: Reverse position $= 27 - \text{forward}$.

16. **Clock Hands Absolute Angle Shift**
    - *Trap*: Forgetting that hour hand moves $0.5^\circ$ every minute.
    - *Correction*: Keep hour hand position formula as $30H + 0.5M$.

17. **Divisibility Rule for 3 and 9**
    - *Trap*: Summing digits without checking if alternating is required.
    - *Correction*: Only 11 uses alternating sum; 3 and 9 use straight sum of digits.

18. **Mixture Replacements Balance**
    - *Trap*: Assuming concentration remains unchanged after adding pure solvent.
    - *Correction*: Recalculate concentration based on final total volume.

19. **Unit Digit Cycle for 4 and 9**
    - *Trap*: Using 4-cycle division for numbers with 2-cycle unit digits (4, 9).
    - *Correction*: Cycle for 4 is odd (4), even (6). Cycle for 9 is odd (9), even (1).

20. **Arithmetic Progression Sum Offsets**
    - *Trap*: Counting terms starting from index $1$ instead of $0$ in sequences.
    - *Correction*: Verify term count $n = \frac{\text{Last} - \text{First}}{\text{Diff}} + 1$.

### Advanced Section Traps

21. **AP Sum Count Mismatch**
    - *Trap*: Using wrong $n$ term count in $S_n$ formula.
    - *Correction*: Write down the explicit formula for $T_n$ to solve for $n$.

22. **Infinite GP Divergence**
    - *Trap*: Applying $\frac{a}{1-r}$ sum formula when ratio $r \ge 1$.
    - *Correction*: Infinite sum only exists if $|r| < 1$.

23. **Distance Formula Coordinate Signs**
    - *Trap*: Subtracting coordinates incorrectly, e.g. $(x_2 - (-x_1)) \rightarrow (x_2 - x_1)$.
    - *Correction*: Keep track of signs: $(x_2 - x_1)^2$.

24. **Section Formula Direction Swap**
    - *Trap*: Confusing signs for internal vs external division points.
    - *Correction*: Internal uses $+$, external uses $-$: $\frac{mx_2 \pm nx_1}{m \pm n}$.

25. **Slope Calculations Axis Swaps**
    - *Trap*: Calculating slope as change in $x$ over change in $y$.
    - *Correction*: Slope $m = \frac{y_2 - y_1}{x_2 - x_1}$.

26. **Cryptarithmetic Letter Value Duplications**
    - *Trap*: Assigning the same digit to two different letters.
    - *Correction*: Every letter must represent a unique digit.

27. **Cryptarithmetic Leading Letter Zero**
    - *Trap*: Allowing a leading letter of a word to equal $0$.
    - *Correction*: Leading letters must be between $1$ and $9$.

28. **Logarithm Quotient base errors**
    - *Trap*: Stating $\frac{\log a}{\log b} = \log(a - b)$.
    - *Correction*: $\log(a/b) = \log a - \log b$, whereas $\frac{\log a}{\log b} = \log_b a$.

29. **Fermat's Theorem Non-Prime Base Divisor**
    - *Trap*: Using $a^{p-1} \equiv 1 \pmod p$ when $p$ is composite.
    - *Correction*: $p$ must be a prime number.

30. **Euler Totient Non-Coprime Base**
    - *Trap*: Using $a^{\phi(n)} \equiv 1 \pmod n$ when $\gcd(a, n) \ne 1$.
    - *Correction*: Verify $\gcd(a, n) = 1$ before using totient reductions.

31. **Modular Division Congruence**
    - *Trap*: Dividing $ax \equiv ay \pmod m$ to get $x \equiv y \pmod m$.
    - *Correction*: New modulo is $m / \gcd(a, m)$.

32. **Laws of Indices Non-Equivalent Bases**
    - *Trap*: Multiplying exponents when bases are different.
    - *Correction*: $a^m \cdot b^n \ne (ab)^{m+n}$.

### Reasoning Ability Traps

33. **Assuming Gender from Name**
    - *Trap*: Assuming "Raviranjan" is male in blood relations puzzles.
    - *Correction*: Do not assume gender based on names. Rely only on explicit clues.

34. **Syllogism "Some" Assumption**
    - *Trap*: Assuming "Some A are B" implies "Some A are not B".
    - *Correction*: "Some" only guarantees existence of overlap; the remaining elements are undefined.

35. **Blood Relations "Point to Photo" Direction**
    - *Trap*: Reversing relationship direction (e.g. saying father instead of son).
    - *Correction*: Trace relationships step-by-step from the speaker's anchor.

36. **Directions Turning Angle Mismatch**
    - *Trap*: Treating a $45^\circ$ turn as a $90^\circ$ turn in coordinate paths.
    - *Correction*: Use standard angles on a 2D compass map.

37. **Seating Clockwise/Counter-clockwise Reference**
    - *Trap*: Swapping left/right directions for inward vs outward facing arrangements.
    - *Correction*: For inward facing, left is clockwise. For outward facing, left is counter-clockwise.

38. **Letter Series Position Wraparounds**
    - *Trap*: Stopping series calculations at Z.
    - *Correction*: Wrap positions around (e.g., $Z + 1 = A$, or index $27 = 1$).

39. **Floor Puzzle Constant Reference Swaps**
    - *Trap*: Mixing row counts with floor counts (floors start from 1 at the bottom).
    - *Correction*: Set up a vertical grid template from highest floor down to 1.

40. **Clock Hands Overlapping Count**
    - *Trap*: Stating that hands overlap 24 times in 24 hours.
    - *Correction*: They only overlap 22 times due to shifts at 11-12 and 12-1.

41. **Odd One Out Partial Matching**
    - *Trap*: Finding a commonality for only 3 out of 5 options.
    - *Correction*: The common rule must apply to exactly 4 options, leaving 1 outlier.

### Coding & Verbal Traps

42. **Array Index Out of Bounds**
    - *Trap*: Accessing `arr[n]` in a loop.
    - *Correction*: Loop limit must be `< n`.

43. **Integer Accumulation Overflow**
    - *Trap*: Accumulating sums in an `int` variable when elements are up to $10^9$.
    - *Correction*: Use `long long` for sum variables.

44. **Function Parameter Array Decay**
    - *Trap*: Using `sizeof(arr)` inside helper functions to calculate size.
    - *Correction*: Pass array size $N$ explicitly to functions.

45. **Division by Zero in Modulo Operations**
    - *Trap*: Computing `val % count` where `count` can dynamically drop to $0$.
    - *Correction*: Add a check `if (count == 0)` to prevent runtime crashes.

46. **Modulo Order of Operations**
    - *Trap*: Performing `(a * b) % MOD` without modulo on intermediate steps.
    - *Correction*: Use `((a % MOD) * (b % MOD)) % MOD`.

47. **Verb Agreement with Parenthetical Expressions**
    - *Trap*: Letting phrases like "as well as" or "along with" change verb numbers.
    - *Correction*: The subject remains singular: "The manager, along with his team, **is** attending."

48. **Pronoun Ambiguity**
    - *Trap*: Using "he" or "it" when multiple nouns are present.
    - *Correction*: Specify the noun explicitly to avoid confusion.

49. **Active/Passive Tense Changes**
    - *Trap*: Changing the main verb tense when rewriting in passive voice.
    - *Correction*: Keep the original tense (e.g., "writes" becomes "is written").

50. **Incorrect Modulo Division**
    - *Trap*: Division under modulo without using modular multiplicative inverse.
    - *Correction*: To divide $A/B \pmod M$, multiply $A$ by $B^{-1} \pmod M$.

---

## ⏱️ "Last 5 Minutes" Mistake Prevention Checklist

Execute this checklist in the final 5 minutes of each section.

- [ ] **Check the Question Prompt**: Did the question ask for "not possible," "except," or "incorrect" options?
- [ ] **Units Verification**: Are all distances in meters and times in seconds? Verify speed calculations.
- [ ] **FIB Field Formats**: Did you enter units (e.g., "kg") in the fill-in-the-blank field? Enter numbers only.
- [ ] **Negative Bounds in Coding**: Does your code check for negative array inputs or empty arrays?
- [ ] **Modular Reductions**: Ensure every multiplication step has modulo applied if required by the question.
- [ ] **Venn Intersection Checks**: In syllogisms, confirm that "either-or" cases have been evaluated.
- [ ] **Memory Allocations**: Verify that C++ arrays are declared using `long long` for sum operations.
