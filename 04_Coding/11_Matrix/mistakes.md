# Matrix — Common Mistakes

## 1. Missing Boundary Checks during Spiral Loops
**Mistake:** Not checking if `top <= bottom` or `left <= right` before the third and fourth traversal directions. This prints duplicate values.
**Fix:** Add conditional checks inside the loop block.

---

## 2. In-place Swapping on Non-Square Matrices
**Mistake:** Attempting `swap(mat[i][j], mat[j][i])` on a matrix with dimensions $2 \times 3$. This raises an index out of bounds exception.
**Fix:** Create a new output matrix of size $3 \times 2$ for non-square transposes.

---

## 3. High Cache Miss rates from Bad Iteration
**Mistake:** Writing outer loop column indices and inner loop row indices. This causes slow performance due to memory cache misses.
**Fix:** Loop row indices in the outer loop to achieve row-major sequential access.
