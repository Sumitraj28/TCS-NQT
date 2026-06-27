# Matrix — Coding Application (Full Problem Solutions)

---

## Problem 1 — Spiral Matrix
**LeetCode:** #54 | **Difficulty:** Medium | **TCS Frequency:** High

### Problem Statement
Given an $m \times n$ matrix, return all elements of the matrix in spiral order.

### Approach
Maintain boundary pointers: `top`, `bottom`, `left`, `right`. Traverse the four edges clockwise, and shift the boundaries inward until they cross.

### C++ Solution
```cpp
#include <vector>

class Solution {
public:
    std::vector<int> spiralOrder(std::vector<std::vector<int>>& matrix) {
        std::vector<int> result;
        if (matrix.empty() || matrix[0].empty()) return result;
        
        int top = 0, bottom = matrix.size() - 1;
        int left = 0, right = matrix[0].size() - 1;
        
        while (top <= bottom && left <= right) {
            // Left to Right
            for (int i = left; i <= right; ++i) {
                result.push_back(matrix[top][i]);
            }
            top++;
            
            // Top to Bottom
            for (int i = top; i <= bottom; ++i) {
                result.push_back(matrix[i][right]);
            }
            right--;
            
            // Right to Left
            if (top <= bottom) {
                for (int i = right; i >= left; --i) {
                    result.push_back(matrix[bottom][i]);
                }
                bottom--;
            }
            
            // Bottom to Top
            if (left <= right) {
                for (int i = bottom; i >= top; --i) {
                    result.push_back(matrix[i][left]);
                }
                left++;
            }
        }
        return result;
    }
};
```
**Complexity:** Time $O(M \times N)$ | Space $O(1)$ auxiliary

---

## Problem 2 — Rotate Image (90 degrees clockwise)
**LeetCode:** #48 | **Difficulty:** Medium | **TCS Frequency:** High

### Problem Statement
You are given an $n \times n$ 2D matrix representing an image, rotate the image by 90 degrees (clockwise) in-place.

### Approach
1. Transpose the matrix (swap `matrix[i][j]` with `matrix[j][i]` for $i < j$).
2. Reverse each row.

### C++ Solution
```cpp
#include <vector>
#include <algorithm>

class Solution {
public:
    void rotate(std::vector<std::vector<int>>& matrix) {
        int n = matrix.size();
        // Step 1: Transpose
        for (int i = 0; i < n; ++i) {
            for (int j = i + 1; j < n; ++j) {
                std::swap(matrix[i][j], matrix[j][i]);
            }
        }
        // Step 2: Reverse each row
        for (int i = 0; i < n; ++i) {
            std::reverse(matrix[i].begin(), matrix[i].end());
        }
    }
};
```
**Complexity:** Time $O(N^2)$ | Space $O(1)$ auxiliary

---

## Problem 3 — Diagonal Traverse
**LeetCode:** #498 | **Difficulty:** Medium | **TCS Frequency:** High

### Problem Statement
Given an $m \times n$ matrix, return all elements of the matrix in a diagonal order.

### Approach
The sum of index coordinate values `i + j` is constant along any diagonal line. We can iterate through sum index keys $S$ from $0$ to $M + N - 2$, changing direction at each diagonal strip.

### C++ Solution
```cpp
#include <vector>
#include <algorithm>

class Solution {
public:
    std::vector<int> findDiagonalOrder(std::vector<std::vector<int>>& mat) {
        std::vector<int> result;
        if (mat.empty() || mat[0].empty()) return result;
        
        int m = mat.size();
        int n = mat[0].size();
        
        for (int s = 0; s < m + n - 1; ++s) {
            // Find boundaries of current diagonal
            int r = s < n ? 0 : s - n + 1;
            int c = s < n ? s : n - 1;
            
            std::vector<int> temp;
            while (r < m && c >= 0) {
                temp.push_back(mat[r][c]);
                r++;
                c--;
            }
            
            // Even sums: traverse upwards (reverse list)
            if (s % 2 == 0) {
                std::reverse(temp.begin(), temp.end());
            }
            
            for (int x : temp) {
                result.push_back(x);
            }
        }
        return result;
    }
};
```
**Complexity:** Time $O(M \times N)$ | Space $O(M \times N)$ temp storage or $O(1)$ with direct index math.
