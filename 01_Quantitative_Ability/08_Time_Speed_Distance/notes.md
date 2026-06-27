# Time, Speed, and Distance — Complete Notes

---

## 1. Relative Speed

Relative speed is the speed of an object with respect to another moving object. 

### Case 1: Moving in the Same Direction
When two objects are moving in the same direction at speeds $v_1$ and $v_2$ (where $v_1 > v_2$), the relative speed is the **difference** between their speeds:

$$v_{\text{rel}} = v_1 - v_2$$

*   *Usage:* Chasing problems (police and thief), overtaking.

### Case 2: Moving in Opposite Directions
When two objects are moving in opposite directions at speeds $v_1$ and $v_2$, the relative speed is the **sum** of their speeds:

$$v_{\text{rel}} = v_1 + v_2$$

*   *Usage:* Meeting problems, trains moving toward each other.

---

## 2. Train Problems

Train problems require setting up the basic formula $\text{Distance} = \text{Speed} \times \text{Time}$, but the distance variable depends on what the train is crossing.

### Scenario A: Crossing a Stationary Point Object (Pole, Standing Man, Tree)
Since the length of the pole/man is negligible compared to the length of the train:
*   $\text{Distance} = L_{\text{train}}$
*   $\text{Speed} = v_{\text{train}}$
*   $\text{Time taken to cross} = \frac{L_{\text{train}}}{v_{\text{train}}}$

### Scenario B: Crossing a Stationary Object of Length (Platform, Bridge, Tunnel)
*   $\text{Distance} = L_{\text{train}} + L_{\text{platform}}$
*   $\text{Speed} = v_{\text{train}}$
*   $\text{Time taken to cross} = \frac{L_{\text{train}} + L_{\text{platform}}}{v_{\text{train}}}$

### Scenario C: Crossing Another Moving Train
*   $\text{Distance} = L_{\text{train 1}} + L_{\text{train 2}}$
*   $\text{Speed} = v_{\text{rel}}$ (dependent on direction of motion)
*   $\text{Time taken to cross} = \frac{L_{\text{train 1}} + L_{\text{train 2}}}{v_{\text{rel}}}$

---

## 3. Boats and Streams

When an object travels in water, the velocity of the water stream affects its net speed.

Let:
*   $u$ = Speed of the boat in still water (km/h)
*   $v$ = Speed of the stream (km/h)

### Downstream Speed ($d$)
When the boat moves in the direction of the stream:

$$d = u + v$$

### Upstream Speed ($u_s$)
When the boat moves against the direction of the stream:

$$u_s = u - v$$

*   *Note:* The boat can only move upstream if $u > v$; otherwise, the stream will wash it backward.

### Formulas to Find Still Water & Stream Speeds
If you are given the downstream speed $d$ and upstream speed $u_s$:

$$\text{Speed of boat in still water } (u) = \frac{d + u_s}{2}$$

$$\text{Speed of stream } (v) = \frac{d - u_s}{2}$$

---

## 4. Cross-References & Overlapping Topics

*   **Average Speed & The Harmonic Mean:** If a round trip covers the same distance at different speeds, do not average the speeds arithmetically. See [Average Notes — Average Speed Section](file:///Users/rajsumit/Desktop/TCS-NQT/01_Quantitative_Ability/04_Average/notes.md#2-average-speed--harmonic-mean-trap) for the Harmonic Mean speed trap.
*   **Speed-Time Inverse Relationship:** Since $\text{Distance} = \text{Speed} \times \text{Time}$, if the distance is kept constant, Speed and Time are inversely proportional ($S_1 T_1 = S_2 T_2$). Refer to [Ratio & Proportion Notes — Direct & Inverse Section](file:///Users/rajsumit/Desktop/TCS-NQT/01_Quantitative_Ability/03_Ratio_Proportion/notes.md#2-direct-and-inverse-proportion) to see speed-time ratio tricks.
