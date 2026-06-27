# Matrix — Practice: Basic (15 Questions)

---

### Q1 — Declare static 2D array (Matrix)
**Answer:** `int mat[3][4];` (3 rows, 4 columns).

---

### Q2 — Declare dynamic 2D vector
**Answer:** `std::vector<std::vector<int>> mat(rows, std::vector<int>(cols, 0));`

---

### Q3 — Find row count of a 2D vector
**Answer:** `matrix.size()`.

---

### Q4 — Find column count of a 2D vector
**Answer:** `matrix[0].size()` (assuming row count is at least 1).

---

### Q5 — Traversing Matrix row-by-row
**Answer:**
```cpp
for (int i = 0; i < rows; ++i) {
    for (int j = 0; j < cols; ++j) {
        std::cout << mat[i][j] << " ";
    }
}
```

---

### Q6 — Print main diagonal of a square matrix
**Answer:**
```cpp
for (int i = 0; i < n; ++i) {
    std::cout << mat[i][i] << " ";
}
```

---

### Q7 — Print anti-diagonal of a square matrix
**Answer:**
```cpp
for (int i = 0; i < n; ++i) {
    std::cout << mat[i][n - 1 - i] << " ";
}
```

---

### Q8 — Transpose of square matrix in-place
**Answer:**
```cpp
for (int i = 0; i < n; ++i) {
    for (int j = i + 1; j < n; ++j) {
        std::swap(mat[i][j], mat[j][i]);
    }
}
```

---

### Q9 — Sum of all elements in matrix
**Answer:** Nested loops accumulating `sum += mat[i][j]`.

---

### Q10 — Find target in unsorted matrix
**Answer:** Traverse all elements, returning true on match.

---

### Q11 — Row-wise sum
**Answer:** For each row index $i$, loop column index $j$ accumulating sum of elements in that row.

---

### Q12 — Column-wise sum
**Answer:** For each column index $j$, loop row index $i$ accumulating sum of elements in that column.

---

### Q13 — Check if matrix is symmetric
**Answer:** Check if $A[i][j] == A[j][i]$ for all indices $i, j$.

---

### Q14 — Initialize Identity Matrix of size N
**Answer:**
```cpp
std::vector<std::vector<int>> mat(n, std::vector<int>(n, 0));
for (int i = 0; i < n; ++i) mat[i][i] = 1;
```

---

### Q15 — Scalar multiplication on matrix
**Answer:** Loop through all cells, updating `mat[i][j] *= k`.
