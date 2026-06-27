# Matrix — Top 20 Important TCS NQT-Style Questions

---

### IQ1 — Print elements of matrix in spiral order.
**Answer:** Maintain boundary pointers `top`, `bottom`, `left`, `right`, and shift inward clockwise.

---

### IQ2 — Rotate square matrix clockwise by 90 degrees in-place.
**Answer:** Transpose matrix, then reverse each row.

---

### IQ3 — Print matrix elements diagonally.
**Answer:** Loop index coordinate sum `s = row + col`, swapping traversal directions.

---

### IQ4 — Set row/col to zeros if cell is zero.
**Answer:** Use first row and column cell values as state markers.

---

### IQ5 — Binary search in sorted 2D matrix.
**Answer:** Map 1D index mid pointer using division/modulo: `mid / cols`, `mid % cols`.

---

### IQ6 — Search row/col sorted matrix.
**Answer:** Start from top-right corner. Move left if larger, down if smaller.

---

### IQ7 — Multiply two matrices.
**Answer:** Loop row, col, and inner common size index, summing products.

---

### IQ8 — Rotate matrix 90 degrees counter-clockwise.
**Answer:** Transpose matrix, then reverse each column.

---

### IQ9 — Boundary traversal of matrix.
**Answer:** Print outer boundary cells clockwise.

---

### IQ10 — Find row with max 1s.
**Answer:** Start top-right corner, move left if cell is 1 (increment count), else move down.

---

### IQ11 — Matrix addition.
**Answer:** Check matching dimensions, sum corresponding cells `A[i][j] + B[i][j]`.

---

### IQ12 — Print matrix in snake pattern.
**Answer:** Alternate left-to-right and right-to-left traversals of row vectors.

---

### IQ13 — Transpose a non-square matrix.
**Answer:** Allocate target matrix of swapped size, copying `out[i][j] = in[j][i]`.

---

### IQ14 — Check if matrix is symmetric.
**Answer:** Verify `A[i][j] == A[j][i]` for all cells.

---

### IQ15 — Find trace of a matrix.
**Answer:** Sum of main diagonal elements $\sum A[i][i]$.

---

### IQ16 — Check if matrix is Toeplitz.
**Answer:** Verify `matrix[i][j] == matrix[i - 1][j - 1]` for all indices $i, j \geq 1$.

---

### IQ17 — Shell rotation of matrix elements.
**Answer:** Extract shell to array, rotate array, write back.

---

### IQ18 — 2D Range Sum Query (Submatrix Sum).
**Answer:** Use 2D Prefix Sum array.

---

### IQ19 — Longest Increasing Path in Matrix.
**Answer:** DFS traversal with 2D memoization table.

---

### IQ20 — Shortest path in grid BFS.
**Answer:** Breadth-First Search checking cell boundaries.
 Richmond.
