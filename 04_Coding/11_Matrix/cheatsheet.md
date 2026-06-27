# Matrix — Cheat Sheet

## Index Conversions
For $M \times N$ matrix:
- `mat[i][j]` flat index: `i * N + j`
- Flat index `idx` 2D position: `row = idx / N`, `col = idx % N`

## Core Algorithms Reference

```cpp
// Transpose
for (int i = 0; i < n; ++i) {
    for (int j = i + 1; j < n; ++j) swap(mat[i][j], mat[j][i]);
}

// Staircase Search (O(M+N))
int r = 0, c = cols - 1;
while (r < rows && c >= 0) {
    if (mat[r][c] == target) return true;
    mat[r][c] > target ? c-- : r++;
}
```

## Rotate Operations

| Rotation | Steps |
|----------|-------|
| 90 degrees Clockwise | Transpose, then Reverse Rows |
| 90 degrees Counter-Clockwise | Transpose, then Reverse Columns |
| 180 degrees | Reverse Rows, then Reverse Columns |
