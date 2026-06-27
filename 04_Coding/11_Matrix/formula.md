# Matrix — Formulas and Relations

## 1. Index Math
For a 2D matrix of size $M \times N$:
- **Flat 1D index mapping:** `mat[i][j]` maps to flat array index:
  $$\text{Index} = i \times N + j$$
- **Flat index reconstruction:** From 1D index $K$:
  $$i = K / N, \quad j = K \bmod N$$

---

## 2. Diagonal Indexing
- **Main Diagonal Direction (Top-Left to Bottom-Right):** In any such diagonal, the difference `row - col` is constant.
- **Anti-Diagonal Direction (Top-Right to Bottom-Left):** In any such diagonal, the sum `row + col` is constant.
- Total number of diagonals = $M + N - 1$.

---

## 3. Transpose relations
- Transpose $A^T$ is defined by:
  $$A^T[i][j] = A[j][i]$$
- Clockwise 90 rotation:
  $$\text{Rotate}(A) = \text{ReverseRows}(A^T)$$
- Counter-clockwise 90 rotation:
  $$\text{RotateCCW}(A) = \text{ReverseCols}(A^T)$$
