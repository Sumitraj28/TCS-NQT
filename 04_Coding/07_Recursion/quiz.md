# Recursion — Quiz

## Rapid-Fire Q&A
1. **What happens if a recursive function lacks a base case?**
   - **Answer:** It results in infinite recursion and causes a stack overflow error.
2. **What is the space complexity of a recursive call stack of depth $H$?**
   - **Answer:** $O(H)$ due to activation records stored on stack.
3. **What is the count of moves to solve Tower of Hanoi with 4 disks?**
   - **Answer:** $2^4 - 1 = 15$ moves.
4. **Can recursion always be converted to iteration?**
   - **Answer:** Yes, using an explicit stack data structure to mimic call stack frames.
5. **What is tail recursion?**
   - **Answer:** A recursive call that is the very last instruction executed in the function.
6. **What is the time complexity of the recursive Fibonacci function?**
   - **Answer:** $O(2^N)$.
7. **What is Binet's Formula used for?**
   - **Answer:** To compute the $N$-th Fibonacci term in closed form.
8. **Why does plain recursion fail for large inputs in problems with overlapping subproblems?**
   - **Answer:** Because it recalculates duplicate states repeatedly, causing exponential time complexity.
9. **How many parameters are needed to implement a recursive range print?**
   - **Answer:** Two (typically `start` and `end`).
10. **What is backtracking?**
    - **Answer:** A recursive search technique that reverts choice changes if they do not lead to a valid solution.

## True or False
1. **A recursive function can only make one self-call within its body.**
   - **Answer:** False (e.g. `fib(n-1) + fib(n-2)` makes two calls).
2. **The recursive sum of digits has logarithmic time complexity.**
   - **Answer:** True ($O(\log_{10} N)$).
3. **In the Tower of Hanoi, a larger disk can be placed on top of a smaller one.**
   - **Answer:** False.
4. **Tail recursion is generally more space-efficient if the compiler optimizes it.**
   - **Answer:** True.
5. **Recursion consumes stack memory, whereas iteration uses heap memory.**
   - **Answer:** False (Iteration does not use extra call stack memory).
 Richmond.
