---
title: "Arrays - Brute Force Solutions"
section: "Coding"
---

# Array Brute Force Solutions

This guide covers the naive $O(N^2)$ or $O(N^3)$ approaches for the 5 most common array problem patterns. 

---

## 💡 When is Brute Force Acceptable?
In the TCS NQT coding section, the time limit for test cases is usually **1.0 second** (~$10^8$ basic instructions in C++). If the constraints in the problem statement specify a small array size:
*   If $N \le 10^3$: An $O(N^2)$ brute-force solution requires $10^6$ operations, which takes around 0.01 seconds and will **easily pass all test cases**.
*   Under exam pressure, if you cannot recall the $O(N)$ optimized solution, write the brute force solution immediately to secure partial marks rather than submitting blank code.

---

## 1. Two Sum (Find Pair with Target Sum)
*   **The Naive Solution ($O(N^2)$)**:
    ```cpp
    #include <vector>

    bool hasTwoSumBruteForce(const std::vector<int>& arr, int target) {
        int n = arr.size();
        for (int i = 0; i < n; i++) {
            for (int j = i + 1; j < n; j++) {
                if (arr[i] + arr[j] == target) {
                    return true;
                }
            }
        }
        return false;
    }
    ```
*   **Why it Works**: It performs an exhaustive pair-wise scan checking every possible pair $(i, j)$ in the array.
*   **TCS Acceptability**: Passes completely if $N \le 5000$.

---

## 2. Maximum Subarray Sum
*   **The Naive Solution ($O(N^2)$)**:
    ```cpp
    #include <vector>
    #include <algorithm>
    #include <climits>

    long long maxSubarraySumBruteForce(const std::vector<int>& arr) {
        int n = arr.size();
        long long max_sum = INT_MIN;
        for (int i = 0; i < n; i++) {
            long long current_sum = 0;
            for (int j = i; j < n; j++) {
                current_sum += arr[j];
                max_sum = std::max(max_sum, current_sum);
            }
        }
        return max_sum;
    }
    ```
*   **Why it Works**: It checks the sum of all possible contiguous subarrays `arr[i...j]` starting at index `i` and ending at `j`.
*   **TCS Acceptability**: Works fine for $N \le 2000$.

---

## 3. Subarray Sum Equals K
*   **The Naive Solution ($O(N^2)$)**:
    ```cpp
    #include <vector>

    int countSubarraysSumKBruteForce(const std::vector<int>& arr, int k) {
        int n = arr.size();
        int count = 0;
        for (int i = 0; i < n; i++) {
            int current_sum = 0;
            for (int j = i; j < n; j++) {
                current_sum += arr[j];
                if (current_sum == k) {
                    count++;
                }
            }
        }
        return count;
    }
    ```
*   **Why it Works**: Scans every possible subarray and maintains a running sum, incrementing the count whenever the sum equals $K$.
*   **TCS Acceptability**: Acceptable if $N \le 2000$.

---

## 4. Product of Array Except Self
*   **The Naive Solution ($O(N^2)$)**:
    ```cpp
    #include <vector>

    std::vector<int> productExceptSelfBruteForce(const std::vector<int>& nums) {
        int n = nums.size();
        std::vector<int> result(n, 1);
        for (int i = 0; i < n; i++) {
            int prod = 1;
            for (int j = 0; j < n; j++) {
                if (i != j) {
                    prod *= nums[j];
                }
            }
            result[i] = prod;
        }
        return result;
    }
    ```
*   **Why it Works**: For each position `i`, it loops through all other indices `j` and multiplies the values.
*   **TCS Acceptability**: Passes if $N \le 1000$.

---

## 5. Container With Most Water
*   **The Naive Solution ($O(N^2)$)**:
    ```cpp
    #include <vector>
    #include <algorithm>

    int maxAreaBruteForce(const std::vector<int>& height) {
        int n = height.size();
        int max_water = 0;
        for (int i = 0; i < n; i++) {
            for (int j = i + 1; j < n; j++) {
                int h = std::min(height[i], height[j]);
                int w = j - i;
                max_water = std::max(max_water, h * w);
            }
        }
        return max_water;
    }
    ```
*   **Why it Works**: Compares all possible boundary pairs $(i, j)$ and computes the potential water volume based on the shorter boundary and width.
*   **TCS Acceptability**: Acceptable for $N \le 5000$.
