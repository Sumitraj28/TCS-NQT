# Matrix — Tricks, Traps, and TCS-Specific Patterns

## Trap 1 — Index Out of Bounds in Spiral Traversal
**The trap:** In spiral traversal, when you increment `top++` or decrement `right--`, boundaries can cross. If you perform subsequent loops without re-evaluating `top <= bottom` and `left <= right`, duplicate elements are printed, or index out of bounds exceptions occur.

**Fix:** Add boundary check guards inside the loop before executing right-to-left or bottom-to-top directions.
```cpp
if (top <= bottom) {
    for (int i = right; i >= left; --i) res.push_back(matrix[bottom][i]);
    bottom--;
}
```

---

## Trap 2 — Non-Square Matrix Rotations
**The trap:** Attempting to transpose and reverse in-place on a non-square ($M \neq N$) matrix. This results in index out of bounds because `matrix[i][j]` cannot be swapped with `matrix[j][i]` in-place if dimensions do not match.

**Fix:** In-place rotations only work on $N \times N$ matrices. For non-square matrices, allocate a new output matrix with swapped dimensions ($N \times M$).

---

## Trap 3 — Memory Cache Locality
**The trap:** Traversing column-by-column (`matrix[row][col]` in outer col loop) is significantly slower than row-by-row traversal because C++ stores matrices in row-major order. Col-by-col traversal results in cache misses.

**Fix:** Traverse row-by-row whenever order does not matter.
