# Matrix — Complete Notes

## 1. What is a Matrix?
A Matrix is a 2D grid structure. In C++, it can be represented as:
- Static: `int mat[M][N];`
- Dynamic: `std::vector<std::vector<int>> mat(M, std::vector<int>(N));`

---

## 2. Basic Traversal Patterns
- **Row-wise Traversal:** Loop row index in outer loop, column index in inner loop.
- **Column-wise Traversal:** Loop column index in outer loop, row index in inner loop.

---

## 3. Spiral Traversal
Traverse grid in outward-in spiral rings.
Maintain boundary pointers: `top`, `bottom`, `left`, `right`.
```cpp
#include <vector>

std::vector<int> spiralOrder(const std::vector<std::vector<int>>& matrix) {
    std::vector<int> res;
    if (matrix.empty()) return res;
    int top = 0, bottom = matrix.size() - 1;
    int left = 0, right = matrix[0].size() - 1;
    
    while (top <= bottom && left <= right) {
        // Traverse Left to Right
        for (int i = left; i <= right; ++i) res.push_back(matrix[top][i]);
        top++;
        
        // Traverse Top to Bottom
        for (int i = top; i <= bottom; ++i) res.push_back(matrix[i][right]);
        right--;
        
        // Traverse Right to Left
        if (top <= bottom) {
            for (int i = right; i >= left; --i) res.push_back(matrix[bottom][i]);
            bottom--;
        }
        
        // Traverse Bottom to Top
        if (left <= right) {
            for (int i = bottom; i >= top; --i) res.push_back(matrix[i][left]);
            left++;
        }
    }
    return res;
}
```
*Time Complexity: $O(M \times N)$ | Space Complexity: $O(1)$ auxiliary*

---

## 4. Matrix Rotation (90 degrees Clockwise)
To rotate an $N \times N$ square matrix by 90 degrees clockwise *in-place*:
1. **Transpose the matrix:** Swap `matrix[i][j]` with `matrix[j][i]` for $i < j$.
2. **Reverse each row:** Swap elements of each row from left to right.

```cpp
#include <vector>
#include <algorithm>

void rotate(std::vector<std::vector<int>>& matrix) {
    int n = matrix.size();
    // Transpose
    for (int i = 0; i < n; ++i) {
        for (int j = i + 1; j < n; ++j) {
            std::swap(matrix[i][j], matrix[j][i]);
        }
    }
    // Reverse each row
    for (int i = 0; i < n; ++i) {
        std::reverse(matrix[i].begin(), matrix[i].end());
    }
}
```
*Time Complexity: $O(N^2)$ | Space Complexity: $O(1)$ auxiliary*

---

## 5. Diagonal Traverse
Traverse elements in diagonal strips. In a diagonal strip, the sum of indices `row + col` is constant.
- Strip index $S$ ranges from $0$ to $M + N - 2$.
- If $S$ is even, we traverse upward (row decreases, col increases).
- If $S$ is odd, we traverse downward (row increases, col decreases).
