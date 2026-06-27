# Matrix — Quiz

## Rapid-Fire Q&A
1. **What is the flat index of `mat[2][3]` in a $5 \times 6$ matrix?**
   - **Answer:** $2 \times 6 + 3 = 15$.
2. **What does transposing a matrix do?**
   - **Answer:** Swaps row indices with column indices ($A[i][j] \rightarrow A[j][i]$).
3. **What is the complexity of rotating an $N \times N$ matrix in-place?**
   - **Answer:** Time $O(N^2)$ and Space $O(1)$.
4. **How do you rotate a matrix by 90 degrees counter-clockwise?**
   - **Answer:** Transpose the matrix, then reverse each column.
5. **What is the number of diagonals in an $M \times N$ matrix?**
   - **Answer:** $M + N - 1$.
6. **Where does staircase search start in a row/column-wise sorted matrix?**
   - **Answer:** Top-right or bottom-left corner.
7. **Which traversal direction is faster: row-wise or column-wise?**
   - **Answer:** Row-wise, due to C++ storing matrices in row-major order (cache locality).
8. **What represents the trace of a square matrix?**
   - **Answer:** The sum of elements on the main diagonal.
9. **How do you declare a $4 \times 5$ vector of integers initialized to 0?**
   - **Answer:** `std::vector<std::vector<int>> mat(4, std::vector<int>(5, 0));`
10. **Is in-place matrix transposition possible for non-square matrices?**
    - **Answer:** No, it requires changing the dimensions.

## True or False
1. **A Toeplitz matrix has identical elements along each descending diagonal.**
   - **Answer:** True.
2. **Binary search on a 2D matrix requires copying the elements to a 1D array first.**
   - **Answer:** False (index arithmetic does this virtually).
3. **Row-wise sum requires $O(M \times N)$ time.**
   - **Answer:** True.
4. **Rotating a matrix by 180 degrees is equivalent to reversing its rows and then reversing its columns.**
   - **Answer:** True.
5. **A symmetric matrix satisfies $A = A^T$.**
   - **Answer:** True.
 Richmond.
