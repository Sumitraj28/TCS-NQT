# Coding & Decoding — Complete Notes

---

## 1. Letter Shifting

Letter-shifting is the most common coding pattern in TCS NQT. Letters of a word are shifted forward or backward by a specific numerical value.

### Position of Letters (A-Z)
To solve these quickly, memorize the alphabetical positions using the **EJOTY** keyword:
*   **E** = $5$
*   **J** = $10$
*   **O** = $15$
*   **T** = $20$
*   **Y** = $25$

To find the position of other letters, relate them to EJOTY. E.g., to find $G$: $E$ is 5, so $F$ is 6, and $G$ is 7.

### Opposite Letters (Pairs)
Opposite letters are pairs that are equidistant from both ends of the alphabet (e.g., $A$ and $Z$, $B$ and $Y$).
*   **Rule:** The sum of the alphabetical positions of any letter and its opposite letter is always **$27$**.
    *   *Example:* Opposite of $G$ (position 7) is the letter at position $27 - 7 = 20$, which is $T$.

### Shift Patterns
1.  **Constant Shift:** Every letter shifted by the same value (e.g., $+2, +2, +2$).
2.  **Variable / Incremental Shift:** The shifting value increases or decreases progressively (e.g., $+1, +2, +3$).
3.  **Cross Shift:** The word is split into halves, and shifting is performed crosswise.
    *   *Example:* "COLD" is coded as "DPDM"?
        *   C (+1) -> D (last letter of first half)
        *   O (+1) -> P
        *   L (+1) -> M
        *   D (+1) -> E

---

## 2. Number Coding

Words are converted into numbers based on alphabetical values.

### Pattern Types
1.  **Direct Position Coding:** Letters are replaced by their standard positions.
    *   *Example:* "CAB" = $3-1-2$.
2.  **Sum of Positions:** Adding alphabetical positions of all characters.
    *   *Example:* "CAB" = $3 + 1 + 2 = 6$.
3.  **Reverse Sum Coding:** Adding the positions of the opposite letters.
    *   *Example:* "CAB" reverse sum:
        *   Opposite of C = X (24)
        *   Opposite of A = Z (26)
        *   Opposite of B = Y (25)
        *   Reverse Sum $= 24 + 26 + 25 = 75$.
4.  **Count-Based Multiplying:** Multiplying the sum of positions by the number of letters in the word.

---

## 3. Substitution Coding (Sentence Coding)

In substitution coding, words in a sentence are replaced by code words. By comparing multiple sentences, we can isolate codes for individual words.

### Worked Example
Suppose:
*   "study very hard" is coded as "7 8 6"
*   "hard work pays" is coded as "6 9 5"
*   "study pays well" is coded as "7 5 3"

Find the code for "study".
1.  Compare Statement 1 and Statement 3: "study very hard" and "study pays well". The common word is **"study"**. The common digit is **"7"**.
2.  Therefore, the code for "study" is **7**.
