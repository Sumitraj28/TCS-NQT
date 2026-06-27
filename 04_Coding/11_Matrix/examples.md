# Matrix — Worked Examples

---

## Example 1 — Spiral Order print

**Problem:** Traverse `matrix = [[1, 2, 3], [4, 5, 6], [7, 8, 9]]`.

**Trace:**
- Initialize `top = 0`, `bottom = 2`, `left = 0`, `right = 2`.
1. **Left to Right (row 0):** `matrix[0][0..2] = [1, 2, 3]`. `top = 1`.
2. **Top to Bottom (col 2):** `matrix[1..2][2] = [6, 9]`. `right = 1`.
3. **Right to Left (row 2):** `matrix[2][1..0] = [8, 7]`. `bottom = 1`.
4. **Bottom to Top (col 0):** `matrix[1..1][0] = [4]`. `left = 1`.
5. **Left to Right (row 1):** `matrix[1][1..1] = [5]`. `top = 2`.
- Loop terminates since `top > bottom`.
- Result: `[1, 2, 3, 6, 9, 8, 7, 4, 5]`.

---

## Example 2 — Rotate 90 Degrees Clockwise (In-Place)

**Problem:** Rotate `matrix = [[1, 2], [3, 4]]`.

**Trace:**
1. **Transpose Matrix:**
   - Swap `matrix[0][1] (2)` and `matrix[1][0] (3)`.
   - Transposed state: `[[1, 3], [2, 4]]`.
2. **Reverse each row:**
   - Row 0 `[1, 3]` $\rightarrow$ reversed `[3, 1]`.
   - Row 1 `[2, 4]` $\rightarrow$ reversed `[4, 2]`.
   - Final state: `[[3, 1], [4, 2]]`. (Correct clockwise rotation).

**C++ Code:**
```cpp
void rotate(std::vector<std::vector<int>>& matrix) {
    int n = matrix.size();
    for (int i = 0; i < n; ++i) {
        for (int j = i + 1; j < n; ++j) std::swap(matrix[i][j], matrix[j][i]);
    }
    for (int i = 0; i < n; ++i) std::reverse(matrix[i].begin(), matrix[i].end());
}
```
*Time Complexity: $O(N^2)$ | Space Complexity: $O(1)$*
