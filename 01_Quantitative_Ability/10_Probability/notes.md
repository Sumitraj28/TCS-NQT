# Probability — Complete Notes

---

## 1. Basic Probability Definition

Probability measures the likelihood of an event occurring. It is expressed as a value between $0$ (impossible event) and $1$ (certain event).

Let:
*   $S$ = The **Sample Space** (the set of all possible outcomes).
*   $E$ = The **Event** (the set of favorable outcomes, where $E \subseteq S$).

The probability of event $E$ occurring, denoted by $P(E)$, is:

$$P(E) = \frac{N(E)}{N(S)}$$

where:
*   $N(E)$ = Number of outcomes favorable to event $E$.
*   $N(S)$ = Total number of possible outcomes in the sample space.

---

## 2. Complementary Events (The "At Least" Rule)

For any event $E$, there is a complementary event $E'$ (or $\bar{E}$), representing the event that $E$ does **not** occur.

$$P(E) + P(E') = 1 \implies P(E') = 1 - P(E)$$

### The "At Least" Shortcut
In exam questions containing the phrase **"at least one"**, it is usually far faster to calculate the probability of the complementary event ("none") and subtract it from 1.

$$P(\text{At least one success}) = 1 - P(\text{No successes})$$

*   *Example:* If a coin is tossed 3 times, what is the probability of getting at least one head?
    1.  The complementary event is getting **no heads** (i.e., all tails: T-T-T).
    2.  Total outcomes: $2^3 = 8$.
    3.  Outcomes for "no heads": 1 (T-T-T).
    4.  $P(\text{No heads}) = \frac{1}{8}$.
    5.  $P(\text{At least one head}) = 1 - \frac{1}{8} = \frac{7}{8}$.

---

## 3. Core Problem Scenarios

TCS NQT probability questions center on a few classical setups:

### A. Coins
*   Tossing $n$ coins yields $2^n$ total outcomes in the sample space.
    *   *1 coin:* $\{H, T\} \rightarrow N(S) = 2$
    *   *2 coins:* $\{HH, HT, TH, TT\} \rightarrow N(S) = 4$
    *   *3 coins:* $\{HHH, HHT, HTH, THH, HTT, THT, TTH, TTT\} \rightarrow N(S) = 8$

### B. Dice
*   Rolling $n$ six-sided dice yields $6^n$ total outcomes in the sample space.
    *   *1 die:* $N(S) = 6$
    *   *2 dice:* $N(S) = 36$
    *   *TCS Trick (Sum of two dice):* Learn the frequency of sums:
        *   Sum is 2 or 12: 1 way
        *   Sum is 3 or 11: 2 ways
        *   Sum is 4 or 10: 3 ways
        *   Sum is 5 or 9: 4 ways
        *   Sum is 6 or 8: 5 ways
        *   Sum is 7: 6 ways

### C. Cards (52-Deck Structure)
A standard deck contains 52 cards divided into 4 suits (Spades ♠, Hearts ♥, Diamonds ♦, Clubs ♣) of 13 cards each.
*   **Colors:** 26 Red (Hearts, Diamonds) and 26 Black (Spades, Clubs).
*   **Face Cards:** 12 cards total (4 Kings, 4 Queens, 4 Jacks).
*   **Number Cards:** 36 cards total (numbers 2 through 10 in each suit).
*   **Aces:** 4 cards total (not considered face cards).

---

## 4. Cross-References & Overlapping Topics

*   **Sample Space Selections:** For complex selections (e.g., drawing 3 cards from a deck, or selecting 4 balls from a bag), combinations must be used to calculate $N(S)$ and $N(E)$. Refer to [Permutations and Combinations Notes — Combinations Section](file:///Users/rajsumit/Desktop/TCS-NQT/01_Quantitative_Ability/09_Permutation_Combination/notes.md#permutations-vs-combinations-npr) to review selection calculations.
