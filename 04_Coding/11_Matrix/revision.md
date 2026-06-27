# Matrix — Quick Revision

## Core Templates

### In-place 90 Degrees Clockwise Rotation
```cpp
void rotate(std::vector<std::vector<int>>& matrix) {
    int n = matrix.size();
    for (int i = 0; i < n; ++i) {
        for (int j = i + 1; j < n; ++j) std::swap(matrix[i][j], matrix[j][i]);
    }
    for (int i = 0; i < n; ++i) std::reverse(matrix[i].begin(), matrix[i].end());
}
```

### Search in Row/Col Sorted Matrix
```cpp
bool search(const std::vector<std::vector<int>>& mat, int target) {
    int r = 0, c = mat[0].size() - 1;
    while (r < mat.size() && c >= 0) {
        if (mat[r][c] == target) return true;
        if (mat[r][c] > target) c--;
        else r++;
    }
    return false;
}
```

## Key Facts
- Flat indexing: `mat[i][j]` maps to index `i * cols + j`.
- Total diagonals: `rows + cols - 1`.
- Row-major traversal is faster due to spatial cache locality.
