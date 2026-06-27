# Series — Complete Notes

---

## 1. Number Series

Number series questions test your ability to recognize mathematical patterns in a sequence of numbers.

### Common Number Series Patterns
1.  **Arithmetic Series (Difference-based):** The difference between consecutive terms is constant or forms a sequence.
    *   *Double Difference:* If the first difference is not constant, find the difference of the differences.
2.  **Geometric Series (Ratio-based):** Consecutive terms are multiplied or divided by a constant ratio.
    *   *Clue:* Numbers increase or decrease extremely rapidly.
3.  **Power Series (Squares/Cubes):** Terms are close to squares ($n^2$) or cubes ($n^3$) of consecutive numbers, often with a constant added or subtracted ($n^2 \pm k$, $n^3 \pm n$).
4.  **Prime Number Series:** Terms are consecutive prime numbers (e.g., $2, 3, 5, 7, 11, 13 \dots$).
5.  **Mixed Operations:** Combining multiplication/division with addition/subtraction.
    *   *Patterns:* $x_n = x_{n-1} \times k + c$ or $x_n = x_{n-1} \times n + n$.

### Pattern-Spotting Tricks
*   **Check differences first:** If the series increases slowly, the pattern is almost always addition/subtraction. Calculate differences between terms immediately.
*   **Check ratios if growth is steep:** If the numbers escalate quickly (e.g., $3, 12, 60, 360 \dots$), think multiplication.
*   **Alternate Series:** If a series goes up and down (e.g., $10, 5, 12, 7, 14 \dots$), it is likely two interleaved series. Split them: $(10, 12, 14 \dots)$ and $(5, 7 \dots)$.

---

## 2. Alphabet Series

Alphabet series require finding patterns in letter sequences.

### Shift Interval Pattern
Look for constant or progressive shifting of letters.
*   *Example:* $A, D, G, J, \dots$
    *   Positions: $A(1) \rightarrow D(4) \rightarrow G(7) \rightarrow J(10)$.
    *   Pattern is $+3$ shifts. Next is $13$ ($M$).

### Position Gaps
Track the gaps between letters. To speed up calculations, write the EJOTY numerical positions above the letters on your scratch pad.

---

## 3. Mixed Alpha-Numeric Series

These combine letters, numbers, and sometimes symbols.

### Solving Strategy
1.  **Deconstruct the series:** Separate the elements into a Letter Series, a Number Series, and a Symbol Series.
2.  **Solve independently:** Find the pattern for the letters and the numbers separately.
3.  *Example:* $A1Z, C3X, E5V, \dots$
    *   *First Letter:* $A \rightarrow C \rightarrow E$ ($+2$ shifts) $\rightarrow G$.
    *   *Middle Number:* $1 \rightarrow 3 \rightarrow 5$ ($+2$ increase) $\rightarrow 7$.
    *   *Last Letter:* $Z \rightarrow X \rightarrow V$ ($-2$ shifts backwards) $\rightarrow T$.
    *   *Result:* $G7T$.
