# Matrix — Practice: Advanced / Prime Level (10 Questions)

---

### Q1 — Spiral Matrix II
Generate an $n \times n$ matrix filled with elements from 1 to $n^2$ in spiral order.
**Full Solution:**
```cpp
#include <vector>

class Solution {
public:
    std::vector<std::vector<int>> generateMatrix(int n) {
        std::vector<std::vector<int>> matrix(n, std::vector<int>(n, 0));
        int top = 0, bottom = n - 1;
        int left = 0, right = n - 1;
        int val = 1;
        
        while (top <= bottom && left <= right) {
            for (int i = left; i <= right; ++i) matrix[top][i] = val++;
            top++;
            for (int i = top; i <= bottom; ++i) matrix[i][right] = val++;
            right--;
            if (top <= bottom) {
                for (int i = right; i >= left; --i) matrix[bottom][i] = val++;
                bottom--;
            }
            if (left <= right) {
                for (int i = bottom; i >= top; --i) matrix[i][left] = val++;
                left++;
            }
        }
        return matrix;
    }
};
```
**Complexity:** Time $O(N^2)$ | Space $O(1)$ auxiliary

---

### Q2 — Submatrix Sum Queries (2D Range Sum Query)
Respond to multiple submatrix sum queries in $O(1)$ time.
**Full Solution (2D Prefix Sum):**
Define prefix sum matrix `dp` where `dp[i][j]` is sum of elements in rectangle from `(0,0)` to `(i-1, j-1)`.
$$\text{Sum} = \text{dp}[r2+1][c2+1] - \text{dp}[r1][c2+1] - \text{dp}[r2+1][c1] + \text{dp}[r1][c1]$$
```cpp
#include <vector>

class NumMatrix {
private:
    std::vector<std::vector<int>> dp;
public:
    NumMatrix(std::vector<std::vector<int>>& matrix) {
        if (matrix.empty() || matrix[0].empty()) return;
        int m = matrix.size(), n = matrix[0].size();
        dp.assign(m + 1, std::vector<int>(n + 1, 0));
        for (int i = 1; i <= m; ++i) {
            for (int j = 1; j <= n; ++j) {
                dp[i][j] = matrix[i - 1][j - 1] + dp[i - 1][j] + dp[i][j - 1] - dp[i - 1][j - 1];
            }
        }
    }
    
    int sumRegion(int row1, int col1, int row2, int col2) {
        return dp[row2 + 1][col2 + 1] - dp[row1][col2 + 1] - dp[row2 + 1][col1] + dp[row1][col1];
    }
};
```
**Complexity:** Construction $O(M \times N)$ | Query $O(1)$ | Space $O(M \times N)$

---

### Q3 — Rotate Matrix Elements (Shell Rotation)
Rotate elements of a specific shell layer of matrix by $K$ positions.
**Full Solution:** Extract elements of layer to 1D array, rotate array by $K$, write back to layer coordinates.

---

### Q4 — Count Submatrices with Sum equals Target
**Full Solution:** Use 2D prefix sums. For each row pair, project columns to 1D array and use hash map range sum target search in $O(N)$ (overall $O(R^2 \times C)$).

---

### Q5 — Sudoku Validation
Verify if a 9x9 Sudoku board is valid (no duplicates in rows, columns, or 3x3 boxes).
**Full Solution:** Use 2D boolean flags checking rows, cols, and grid box numbers.

---

### Q6 — K-th Smallest Element in a Sorted Matrix
Find $k$-th smallest element in row/column-wise sorted matrix.
**Full Solution:** Binary search on values from `matrix[0][0]` to `matrix[N-1][N-1]`, counting elements smaller than mid pointer in $O(N)$ time.

---

### Q7 — Maximal Rectangle
Find area of largest rectangle containing only 1s in a 2D binary matrix.
**Full Solution:** Project rows as histogram heights, solve using Largest Rectangle in Histogram O(N) stack method on each row.

---

### Q8 — Longest Increasing Path in a Matrix
Find length of longest increasing path in a matrix (can move up, down, left, right).
**Full Solution:** DFS traversal combined with 2D memoization table.
```cpp
#include <vector>
#include <algorithm>

class Solution {
private:
    int dfs(const std::vector<std::vector<int>>& matrix, std::vector<std::vector<int>>& memo, int i, int j) {
        if (memo[i][j] != 0) return memo[i][j];
        int m = matrix.size(), n = matrix[0].size();
        int maxLen = 1;
        int dirs[4][2] = {{0, 1}, {0, -1}, {1, 0}, {-1, 0}};
        for (auto& d : dirs) {
            int r = i + d[0], c = j + d[1];
            if (r >= 0 && r < m && c >= 0 && c < n && matrix[r][c] > matrix[i][j]) {
                maxLen = std::max(maxLen, 1 + dfs(matrix, memo, r, c));
            }
        }
        return memo[i][j] = maxLen;
    }
public:
    int longestIncreasingPath(std::vector<std::vector<int>>& matrix) {
        if (matrix.empty() || matrix[0].empty()) return 0;
        int m = matrix.size(), n = matrix[0].size();
        std::vector<std::vector<int>> memo(m, std::vector<int>(n, 0));
        int longest = 0;
        for (int i = 0; i < m; ++i) {
            for (int j = 0; j < n; ++j) {
                longest = std::max(longest, dfs(matrix, memo, i, j));
            }
        }
        return longest;
    }
};
```
**Complexity:** Time $O(M \times N)$ | Space $O(M \times N)$

---

### Q9 — Shortest Path in Binary Matrix (BFS grid)
Find shortest path from top-left to bottom-right in binary grid.
**Full Solution:** Breadth-First Search (BFS) tracking distance coordinates.

---

### Q10 — Toeplitz Matrix Check
**Full Solution:** Check diagonal cells: `matrix[i][j] == matrix[i - 1][j - 1]`.
