---
title: "Arrays - Coding Patterns"
section: "Coding"
---

# Array Coding Patterns

## 1. The 5 Core Array Patterns

### A. Two Pointers
*   **When to Use**: Sorted arrays, pair sum search, reversing arrays, partitioning (e.g. even numbers first).
*   **Key Insight**: Meet in the middle. Place pointers at the beginning (`left`) and end (`right`). Move them toward each other based on comparison checks to scan the search space in $O(N)$ instead of $O(N^2)$.
*   **Template Approach**:
    ```cpp
    int left = 0, right = n - 1;
    while (left < right) {
        int sum = arr[left] + arr[right];
        if (sum == target) return {left, right};
        else if (sum < target) left++;
        else right--;
    }
    ```

---

### B. Sliding Window (Fixed Size)
*   **When to Use**: Finding maximum/minimum sum of a subarray of fixed length $K$.
*   **Key Insight**: Instead of recalculating the sum of all elements inside the window, add the new element entering the window on the right and subtract the old element leaving the window on the left.
*   **Template Approach**:
    ```cpp
    int window_sum = 0;
    for (int i = 0; i < k; i++) window_sum += arr[i];
    int max_sum = window_sum;
    for (int i = k; i < n; i++) {
        window_sum += arr[i] - arr[i - k]; // Slide right
        max_sum = max(max_sum, window_sum);
    }
    ```

---

### C. Prefix Sum
*   **When to Use**: Range sum queries, finding equilibrium index where left sum equals right sum.
*   **Key Insight**: Precalculate a running cumulative sum array. The sum of any subarray from index $L$ to $R$ can be found in $O(1)$ time:
    $$\text{Sum}(L, R) = \text{Prefix}[R] - \text{Prefix}[L-1]$$
*   **Template Approach**:
    ```cpp
    vector<int> prefix(n, 0);
    prefix[0] = arr[0];
    for (int i = 1; i < n; i++) prefix[i] = prefix[i - 1] + arr[i];
    ```

---

### D. Frequency Hashing (Unordered Map / Frequency Array)
*   **When to Use**: Finding duplicate elements, element counts, checking if target sums exist in unsorted arrays.
*   **Key Insight**: Use an auxiliary hash table to store visited numbers, enabling $O(1)$ lookup checks.
*   **Template Approach**:
    ```cpp
    unordered_map<int, int> freq;
    for (int num : arr) {
        freq[num]++;
    }
    ```

---

### E. Triple Reversal Rotation
*   **When to Use**: Rotating an array to the right or left by $K$ positions without auxiliary space.
*   **Key Insight**: Reversing the entire array, and then reversing the sub-segments individually, rotates the array in place in $O(N)$ time and $O(1)$ space.
*   **Template Approach (Rotate Right by K)**:
    ```cpp
    k = k % n; // Handle k >= n
    reverse(arr.begin(), arr.end());          // Reverse all
    reverse(arr.begin(), arr.begin() + k);    // Reverse first k
    reverse(arr.begin() + k, arr.end());      // Reverse remaining
    ```

---

## 🌳 2. Pattern Strategy Decision Tree
Use this tree to match the problem description to the correct coding pattern:

```
                            Read the Coding Problem
                                       |
                   What is the main question asking for?
                                       |
         +-----------------------------+-----------------------------+
         |                             |                             |
   Range Sum Queries?          Subarray of size K?            Sorted pair sum?
         v                             v                             v
     PREFIX SUM                  SLIDING WINDOW                 TWO POINTERS
   prefix[R] - prefix[L-1]       add right, subtract left       left=0, right=N-1
```

---

## 📊 3. Problem Classification Table

| Problem Type | Target Goal | Pattern Selection | Time Complexity | Space Complexity |
| :--- | :--- | :--- | :---: | :---: |
| **Two Sum (Sorted)** | Find index of pair summing to target | Two Pointers | $O(N)$ | $O(1)$ |
| **Max Subarray Sum** | Maximize contiguous sum (Kadane) | Prefix Sum / Greedy | $O(N)$ | $O(1)$ |
| **Rotate Array** | Shift elements right by $K$ places | Triple Reversal | $O(N)$ | $O(1)$ |
| **Find Duplicate** | Detect any repeating element | Hashing / Visited Set | $O(N)$ | $O(N)$ |
| **Equilibrium Index**| Find index where left sum = right sum| Running Sums | $O(N)$ | $O(1)$ |
