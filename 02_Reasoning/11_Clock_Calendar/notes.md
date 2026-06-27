# Clocks and Calendars — Complete Notes

---

## 1. Clock Formulas

Clock problems involve analyzing the positions and angles of the hour hand and minute hand.

### Angle Between Hands
To find the angle $\theta$ between the hour hand and the minute hand at a given time $H:M$ (where $H$ is the hour value and $M$ is the minute value):

$$\theta = \left| 30H - \frac{11}{2}M \right|$$

*   *Note:* If the calculated angle is greater than $180^\circ$, find the reflex angle by subtracting it from $360^\circ$.
*   *Example:* What is the angle between the hands at 3:40?
    $$\theta = \left| 30(3) - \frac{11}{2}(40) \right| = | 90 - 220 | = | -130 | = 130^\circ$$

### Hand Speeds
*   **Minute Hand:** Moves $360^\circ$ in 60 minutes $\rightarrow 6^\circ/\text{minute}$.
*   **Hour Hand:** Moves $360^\circ$ in 12 hours ($720$ minutes) $\rightarrow 0.5^\circ/\text{minute}$.
*   **Relative Speed:** The minute hand gains $6^\circ - 0.5^\circ = 5.5^\circ$ (or $\frac{11}{2}^\circ$) per minute over the hour hand.

### Standard Coincidence Rules
In a 12-hour period:
*   The hands **coincide (overlap, $0^\circ$)** exactly **$11$ times** (they do not overlap between 11 and 1).
*   The hands are **opposite (straight line, $180^\circ$)** exactly **$11$ times**.
*   The hands are at **right angles ($90^\circ$)** exactly **$22$ times**.
*   *In a 24-hour period, double these values (22, 22, and 44 times respectively).*

---

## 2. Calendar Calculations (The Odd Days Method)

The calendar system is built on tracking "odd days" (remainders after dividing total days by 7).

$$\text{Odd Days} = \text{Total Days} \bmod 7$$

### Leap Year Rules
*   An ordinary year has 365 days. A leap year has 366 days (February has 29 days).
*   **Check:** A year is a leap year if it is divisible by 4.
*   **Century Year Exception:** A century year (ending in 00, like 1900 or 2000) is a leap year **only** if it is divisible by **$400$**. E.g., 2000 is a leap year, but 1900 is not.

### Odd Days count
*   **Ordinary Year:** $365 \text{ days} = 52\text{ weeks} + 1\text{ day} \rightarrow \mathbf{1\text{ odd day}}$.
*   **Leap Year:** $366 \text{ days} = 52\text{ weeks} + 2\text{ days} \rightarrow \mathbf{2\text{ odd days}}$.

### Century Odd Days Table
*   **100 Years:** $5$ odd days
*   **200 Years:** $3$ odd days
*   **300 Years:** $1$ odd day
*   **400 Years:** $0$ odd days
*   *(This cycle repeats: 800, 1200, 1600, 2000 years all have 0 odd days).*

### Day Mapping Code
If you calculate the net odd days from a base reference (like Jan 1, 1 AD, which was a Monday):
*   0 = Sunday
*   1 = Monday
*   2 = Tuesday
*   3 = Wednesday
*   4 = Thursday
*   5 = Friday
*   6 = Saturday
