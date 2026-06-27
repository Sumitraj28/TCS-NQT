# Easy DP — Quiz

## Rapid-Fire Q&A
1. **What are the two key properties required to apply Dynamic Programming?**
   - **Answer:** Overlapping subproblems and optimal substructure.
2. **What is the space complexity of bottom-up Fibonacci when optimized with variables?**
   - **Answer:** $O(1)$.
3. **In the House Robber problem, what is the state transition formula?**
   - **Answer:** `dp[i] = max(dp[i-1], dp[i-2] + nums[i])`.
4. **What does -1 typically represent in a memoization table?**
   - **Answer:** An uncomputed/unvisited state.
5. **How does bottom-up tabulation build solutions?**
   - **Answer:** Iteratively, starting from base cases and building up to the target.
6. **What is the time complexity of the space-optimized Climbing Stairs solution?**
   - **Answer:** $O(N)$.
7. **Which DP approach is also known as Top-Down?**
   - **Answer:** Memoization.
8. **What is the transition formula for Tribonacci?**
   - **Answer:** `dp[i] = dp[i-1] + dp[i-2] + dp[i-3]`.
9. **Why is recursion slower than DP for overlapping subproblems?**
   - **Answer:** Recursion recalculates overlapping states repeatedly, resulting in exponential runtime.
10. **In a 2D Unique Paths grid, what is the value of `dp[i][j]`?**
    - **Answer:** `dp[i-1][j] + dp[i][j-1]`.

## True or False
1. **Memoization is a bottom-up approach.**
   - **Answer:** False (It is top-down).
2. **Tabulation uses loops rather than recursion.**
   - **Answer:** True.
3. **If a problem lacks optimal substructure, we can still solve it with DP.**
   - **Answer:** False.
4. **Every recursive solution can be optimized to $O(1)$ space using variables.**
   - **Answer:** False (only if the transition has a fixed history window).
5. **Dynamic Programming is slower than plain recursion.**
   - **Answer:** False (it is much faster for overlapping subproblems).
