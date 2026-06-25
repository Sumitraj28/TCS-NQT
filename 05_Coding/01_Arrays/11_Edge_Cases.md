---
title: "Arrays - Edge Cases"
section: "Coding"
---

# Array Edge Cases Catalog

This document details every common edge case that can break array algorithms on the TCS NQT coding console.

---

## 1. Empty Input
*   **What Breaks**: Trying to access `arr[0]` or doing operations on `arr.size() - 1` when the size is `0` leads to a segmentation fault or division-by-zero error.
*   **How to Handle**: Check if the array is empty at the very beginning of the function.
*   **Code Fix**:
    ```cpp
    if (arr.empty()) {
        return -1; // Or return appropriate default value
    }
    ```

---

## 2. Single Element Array
*   **What Breaks**: Pointer adjustments (like `left < right` when `left = 0, right = 0`) or loop conditions comparing `arr[i]` with `arr[i-1]`.
*   **How to Handle**: Ensure loop boundaries are safe for $N = 1$ and return the element directly if no calculations can be performed.
*   **Code Fix (Second Largest)**:
    ```cpp
    if (arr.size() < 2) {
        return -1; // Second largest doesn't exist
    }
    ```

---

## 3. All Same Elements
*   **What Breaks**: Search algorithms or unique checks. For instance, finding the second largest element in `[5, 5, 5, 5]`.
*   **How to Handle**: Use strict inequality checks (`num < largest` and `num > secondLargest`) rather than weak inequality (`<=`).
*   **Code Fix**:
    ```cpp
    if (num > largest) {
        secondLargest = largest;
        largest = num;
    } else if (num > secondLargest && num < largest) {
        secondLargest = num;
    }
    ```

---

## 4. Integer Overflow (INT_MAX & INT_MIN)
*   **What Breaks**: Summing elements in a large array (e.g. $10^5$ elements of value $10^9$) exceeds the limit of 32-bit signed integers ($2 \times 10^9$), causing wrapping to negative values.
*   **How to Handle**: Use 64-bit integers (`long long` in C++) for cumulative calculations.
*   **Code Fix**:
    ```cpp
    long long sum = 0;
    for (int num : arr) {
        sum += num; // Prevents overflow
    }
    ```

---

## 5. Negative Numbers
*   **What Breaks**: Algorithms initialized to `0` (e.g. Kadane's maximum subarray sum on an array of all negative numbers `[-3, -2, -5]`). If initialized to `0`, the algorithm will incorrectly return `0` instead of `-2`.
*   **How to Handle**: Initialize tracking variables (like `maxVal`) to the first element of the array or `INT_MIN` rather than `0`.
*   **Code Fix**:
    ```cpp
    long long max_so_far = arr[0]; // NOT 0
    long long curr_max = arr[0];
    ```

---

## 6. Zero Element Arrays
*   **What Breaks**: Sliding window divisions or multiplication chains (multiplying anything by 0 yields 0).
*   **How to Handle**: Check specifically for zero elements if dividing or doing product checks.
*   **Code Fix (Product Except Self)**:
    Ensure you handle multiple zeros. If there is 1 zero, all elements except the zero index will have product 0. If there are $\ge 2$ zeros, all products will be 0.

---

## 7. Already Sorted / Reverse Sorted
*   **What Breaks**: Quickselect partitioning (worse case $O(N^2)$ time if pivot is poorly chosen) or Binary Search.
*   **How to Handle**: Choose randomized pivots in partition algorithms.
