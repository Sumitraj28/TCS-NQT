# Matrix — Practice: Medium (15 Questions)

---

### Q1 — Spiral Matrix Traversal
**Difficulty:** Medium | **Time:** 90s | **TCS Frequency:** High
Traverse matrix in spiral order.
**Full Solution:**
```cpp
#include <vector>

std::vector<int> spiralOrder(std::vector<std::vector<int>>& matrix) {
    std::vector<int> res;
    if (matrix.empty()) return res;
    int top = 0, bottom = matrix.size() - 1;
    int left = 0, right = matrix[0].size() - 1;
    while (top <= bottom && left <= right) {
        for (int i = left; i <= right; ++i) res.push_back(matrix[top][i]);
        top++;
        for (int i = top; i <= bottom; ++i) res.push_back(matrix[i][right]);
        right--;
        if (top <= bottom) {
            for (int i = right; i >= left; --i) res.push_back(matrix[bottom][i]);
            bottom--;
        }
        if (left <= right) {
            for (int i = bottom; i >= top; --i) res.push_back(matrix[i][left]);
            left++;
        }
    }
    return res;
}
```
**Complexity:** Time $O(M \times N)$ | Space $O(1)$ auxiliary

---

### Q2 — Rotate Image 90 Degrees Clockwise
**Difficulty:** Medium | **Time:** 60s | **TCS Frequency:** High
**Full Solution:** Transpose, then reverse each row.

---

### Q3 — Diagonal Traverse
**Difficulty:** Medium | **Time:** 90s | **TCS Frequency:** High
**Full Solution:** Track `sum = row + col` and change directions.

---

### Q4 — Set Matrix Zeroes
Given $M \times N$ matrix, if an element is 0, set its entire row and column to 0.
**Full Solution:**
Use first row and column as marker storage to do it in $O(1)$ auxiliary space.
```cpp
#include <vector>

void setZeroes(std::vector<std::vector<int>>& matrix) {
    int m = matrix.size(), n = matrix[0].size();
    bool firstRowZero = false, firstColZero = false;
    
    for (int i = 0; i < m; ++i) if (matrix[i][0] == 0) firstColZero = true;
    for (int j = 0; j < n; ++j) if (matrix[0][j] == 0) firstRowZero = true;
    
    for (int i = 1; i < m; ++i) {
        for (int j = 1; j < n; ++j) {
            if (matrix[i][j] == 0) {
                matrix[i][0] = 0;
                matrix[0][j] = 0;
            }
        }
    }
    for (int i = 1; i < m; ++i) {
        for (int j = 1; j < n; ++j) {
            if (matrix[i][0] == 0 || matrix[0][j] == 0) matrix[i][j] = 0;
        }
    }
    if (firstColZero) for (int i = 0; i < m; ++i) matrix[i][0] = 0;
    if (firstRowZero) for (int j = 0; j < n; ++j) matrix[0][j] = 0;
}
```
**Complexity:** Time $O(M \times N)$ | Space $O(1)$ auxiliary

---

### Q5 — Search a 2D Matrix
Search target in sorted matrix where each row is sorted and starts after previous row's end.
**Full Solution:** Binary search treating 2D matrix as flat 1D array: `index / cols` and `index % cols`.

---

### Q6 — Search a 2D Matrix II
Search target in matrix where rows and columns are sorted independently.
**Full Solution:**
Start search from top-right corner. If value > target, move left. If value < target, move down.
```cpp
#include <vector>

bool searchMatrix(std::vector<std::vector<int>>& matrix, int target) {
    if (matrix.empty() || matrix[0].empty()) return false;
    int r = 0, c = matrix[0].size() - 1;
    while (r < (int)matrix.size() && c >= 0) {
        if (matrix[r][c] == target) return true;
        if (matrix[r][c] > target) c--;
        else r++;
    }
    return false;
}
```
**Complexity:** Time $O(M + N)$ | Space $O(1)$

---

### Q7 — Matrix Multiplication
Multiply two matrices $A$ ($M \times K$) and $B$ ($K \times N$).
**Full Solution:**
Loop $i \rightarrow M, j \rightarrow N, k \rightarrow K$ accumulating `C[i][j] += A[i][k] * B[k][j]`.

---

### Q8 — Rotate Image 90 Degrees Counter-Clockwise
**Full Solution:** Transpose, then reverse each column.

---

### Q9 — Transpose of Non-Square Matrix
**Full Solution:** Allocate $N \times M$ output matrix, set `out[i][j] = in[j][i]`.

---

### Q10 — Boundary Traversal of Matrix
Traverse outer boundary cells of matrix in clockwise direction.
**Full Solution:** Traverse top row, right column, bottom row, left column.

---

### Q11 — Find Row with Maximum Number of 1s
In binary matrix where rows are sorted, find row index with maximum 1s.
**Full Solution:** Start from top-right corner. Move left if element is 1, otherwise move down. Track best row index.

---

### Q12 — Matrix Block Sum
**Full Solution:** Use 2D Prefix Sum array (Integral Image) to query region sums in $O(1)$.

---

### Q13 — Shift Matrix elements by K places
**Full Solution:** Flatten matrix, shift elements, reconstruct 2D indexes.

---

### Q14 — Print Matrix in Snake Pattern
**Full Solution:** Traverse even rows from left to right, odd rows from right to left.

---

### Q15 — Check if Matrix is Toeplitz Matrix
A Toeplitz matrix is a matrix where every diagonal from top-left to bottom-right has the same elements.
**Full Solution:**
```cpp
bool isToeplitzMatrix(const std::vector<std::vector<int>>& matrix) {
    for (size_t i = 1; i < matrix.size(); ++i) {
        for (size_t j = 1; j < matrix[0].size(); ++j) {
            if (matrix[i][j] != matrix[i - 1][j - 1]) return false;
        }
    }
    return true;
}
```
**Complexity:** Time $O(M \times N)$ | Space $O(1)$
