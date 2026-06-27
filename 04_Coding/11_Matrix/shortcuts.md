# Matrix — Shortcuts & Traversal Optimization

## 1. Fast Row Swapping (for rotation reverse steps)
Instead of swapping elements cell-by-cell, swap entire row structures:
```cpp
std::reverse(matrix.begin(), matrix.end()); // swaps entire row vectors in-place
```

---

## 2. Dynamic 2D Array allocation
Initialize a 2D vector with predefined sizes in a single line:
```cpp
std::vector<std::vector<int>> grid(m, std::vector<int>(n, 0));
```

---

## 3. Flat 1D Binary Search
For a sorted 2D matrix (where each row is sorted, and the first element of each row is greater than the last of previous):
```cpp
int left = 0, right = m * n - 1;
while (left <= right) {
    int mid = left + (right - left) / 2;
    int val = matrix[mid / n][mid % n]; // reconstruct 2D coordinate
    if (val == target) return true;
    if (val < target) left = mid + 1;
    else right = mid - 1;
}
```
*(Avoids copying to a 1D array).*
