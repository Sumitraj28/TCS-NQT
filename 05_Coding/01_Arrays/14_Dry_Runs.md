---
title: "Arrays - Dry Runs"
section: "Coding"
---

# Array Algorithm Dry Runs

This guide provides step-by-step tracing tables for the 5 core array algorithms.

---

## 1. Two Pointers Tracing Table
*   **Input**: `arr = [1, 2, 4, 6]`, Target $= 8$.
*   **Initial State**: `left = 0`, `right = 3`.

| Loop Iteration | `left` (Index) | `right` (Index) | `arr[left]` | `arr[right]` | `Sum` | Action / Decision |
| :--- | :---: | :---: | :---: | :---: | :---: | :--- |
| **Start** | 0 | 3 | 1 | 6 | 7 | $7 < 8 \implies$ Move `left` pointer right (`left++`) |
| **Iter 1** | 1 | 3 | 2 | 6 | 8 | $8 == 8 \implies$ Pair found at indexes `(1, 3)`. Stop. |

*   **Output**: Pair index `(1, 3)` (values 2 and 6).

---

## 2. Kadane's Algorithm Tracing Table
*   **Input**: `arr = [-2, 1, -3, 4, -1]`.
*   **Initial State**: `max_so_far = arr[0] = -2`, `curr_max = arr[0] = -2`.

| Step | Index `i` | `arr[i]` | `curr_max + arr[i]` | `curr_max = max(arr[i], sum)` | `max_so_far = max(max, curr_max)` | Key Decision / Action |
| :--- | :---: | :---: | :---: | :---: | :---: | :--- |
| **0** | 0 | -2 | - | -2 | -2 | Initialize parameters. |
| **1** | 1 | 1 | -2 + 1 = -1 | $\max(1, -1) = 1$ | $\max(-2, 1) = 1$ | Subarray restarts at index 1 because prefix sum was negative. |
| **2** | 2 | -3 | 1 - 3 = -2 | $\max(-3, -2) = -2$ | $\max(1, -2) = 1$ | Running sum drops but remains within negative limits. |
| **3** | 3 | 4 | -2 + 4 = 2 | $\max(4, 2) = 4$ | $\max(1, 4) = 4$ | Subarray restarts at index 3. Global max updated to 4. |
| **4** | 4 | -1 | 4 - 1 = 3 | $\max(-1, 3) = 3$ | $\max(4, 3) = 4$ | Subarray continues; global max remains 4. |

*   **Output**: Max Subarray Sum $= 4$.

---

## 3. Sliding Window Tracing Table
*   **Input**: `arr = [1, 8, 3, 0, 5, 2]`, Window Size $K = 3$.
*   **Initial Window Sum**: `arr[0]+arr[1]+arr[2] = 1+8+3 = 12`. `max_sum = 12`.

| Step | Index `i` | `arr[i]` (incoming) | `arr[i-K]` (outgoing) | `window_sum = prev + incoming - outgoing` | `max_sum` | Action / Decision |
| :--- | :---: | :---: | :---: | :---: | :---: | :--- |
| **0** | 3 | 0 | 1 | $12 + 0 - 1 = 11$ | $\max(12, 11) = 12$ | Slide window to indices `[1, 2, 3]`. |
| **1** | 4 | 5 | 8 | $11 + 5 - 8 = 8$ | $\max(12, 8) = 12$ | Slide window to indices `[2, 3, 4]`. |
| **2** | 5 | 2 | 3 | $8 + 2 - 3 = 7$ | $\max(12, 7) = 12$ | Slide window to indices `[3, 4, 5]`. |

*   **Output**: Max Window Sum $= 12$.

---

## 4. Triple Reversal Rotation Tracing Table
*   **Input**: `arr = [1, 2, 3, 4, 5]`, rotate right by $K = 2$ steps.

| Step | Operation | Target Sub-segment | Array State | Key Decision / Action |
| :--- | :--- | :--- | :--- | :--- |
| **0** | Original Array | - | `[1, 2, 3, 4, 5]` | Starting state. |
| **1** | Reverse entire array | `arr[0...4]` | `[5, 4, 3, 2, 1]` | Rotated segments are now aligned but reversed. |
| **2** | Reverse first $K$ elements | `arr[0...1]` | `[4, 5, 3, 2, 1]` | Corrects order of rotated items. |
| **3** | Reverse remaining elements | `arr[2...4]` | `[4, 5, 1, 2, 3]` | Corrects order of unrotated prefix. |

*   **Output**: Rotated array `[4, 5, 1, 2, 3]`.

---

## 5. Equilibrium Index Tracing Table
*   **Input**: `arr = [1, 7, 3, 6, 5, 6]`.
*   **Initial Sum**: `totalSum = 28`, `leftSum = 0`.

| Step | Index `i` | `arr[i]` | `totalSum = totalSum - arr[i] (rightSum)` | `leftSum == totalSum ?` | `leftSum = leftSum + arr[i]` | Key Decision / Action |
| :--- | :---: | :---: | :---: | :---: | :---: | :--- |
| **0** | 0 | 1 | $28 - 1 = 27$ | $0 == 27$ (NO) | $0 + 1 = 1$ | - |
| **1** | 1 | 7 | $27 - 7 = 20$ | $1 == 20$ (NO) | $1 + 7 = 8$ | - |
| **2** | 2 | 3 | $20 - 3 = 17$ | $8 == 17$ (NO) | $8 + 3 = 11$ | - |
| **3** | 3 | 6 | $17 - 6 = 11$ | $11 == 11$ (**YES**) | - | Match found! Equilibrium index is 3. |

*   **Output**: Equilibrium Index $= 3$.
