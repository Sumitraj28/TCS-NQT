---
title: "Arrays - Medium Problems"
section: "Coding"
---

# Array Medium Coding Problems

This set contains 10 medium difficulty problems commonly asked in the TCS NQT 55-minute coding section.

---

## 1. Two Sum (Find Pair with Target Sum)
*   **Problem Statement**: Given an unsorted array of integers and a target sum $T$, check if there exists a pair of numbers that sum to $T$. Return indices.
    *   *Constraints*: $2 \le N \le 10^5$, $-10^9 \le arr[i], T \le 10^9$.
    *   *Sample Input*: `[2, 7, 11, 15]`, Target $= 9$ $\implies$ *Sample Output*: `[0, 1]`.
*   **Brute Force Approach**: Check every pair $(i, j)$ using nested loops:
    ```cpp
    // Time: O(N^2), Space: O(1)
    for(int i=0; i<n; i++)
        for(int j=i+1; j<n; j++)
            if(arr[i] + arr[j] == target) return {i, j};
    ```
*   **Why Brute Force Fails (TLE)**: For $N = 10^5$, $O(N^2)$ requires $10^{10}$ operations, exceeding the 1-second execution time limit (~$10^8$ operations).
*   **Key Insight**: Trade space for time. As you scan each number, check if its complement (`target - num`) has already been visited by storing visited numbers in a hash map.
*   **C++14 Optimized Solution**:
    ```cpp
    #include <vector>
    #include <unordered_map>

    std::pair<int, int> twoSum(const std::vector<int>& arr, int target) {
        std::unordered_map<int, int> seen;
        for (int i = 0; i < arr.size(); i++) {
            int complement = target - arr[i];
            if (seen.find(complement) != seen.end()) {
                return {seen[complement], i};
            }
            seen[arr[i]] = i;
        }
        return {-1, -1};
    }
    ```
*   **Complexity**: Time: $O(N)$ average, Space: $O(N)$ (hash map storage).

---

## 2. Maximum Subarray Sum (Kadane's Algorithm)
*   **Problem Statement**: Find the contiguous subarray within an array of numbers which has the largest sum.
    *   *Sample Input*: `[-2, 1, -3, 4, -1, 2, 1, -5, 4]` $\implies$ *Sample Output*: `6` (Subarray is `[4, -1, 2, 1]`).
*   **Brute Force**: Compute sum of all possible subarrays using nested loops ($O(N^2)$). Fails TLE for $N = 10^5$.
*   **Key Insight**: A running subarray sum is only useful if it is positive. If the cumulative sum drops below zero, discard the prefix and restart the subarray from the current element.
*   **C++14 Optimized Solution**:
    ```cpp
    #include <vector>
    #include <algorithm>

    long long maxSubarraySum(const std::vector<int>& arr) {
        long long max_so_far = arr[0];
        long long curr_max = arr[0];
        
        for (size_t i = 1; i < arr.size(); i++) {
            curr_max = std::max((long long)arr[i], curr_max + arr[i]);
            max_so_far = std::max(max_so_far, curr_max);
        }
        return max_so_far;
    }
    ```
*   **Complexity**: Time: $O(N)$, Space: $O(1)$.

---

## 3. Rotate Array by K Steps
*   **Problem Statement**: Rotate an array of $N$ elements to the right by $K$ steps in-place.
    *   *Sample Input*: `[1, 2, 3, 4, 5, 6, 7]`, $K = 3$ $\implies$ *Sample Output*: `[5, 6, 7, 1, 2, 3, 4]`.
*   **Brute Force**: Shift elements one-by-one $K$ times ($O(N \times K)$ time) or copy to auxiliary array ($O(N)$ space).
*   **Key Insight**: Reversing parts of the array achieves rotation in-place without auxiliary space.
*   **C++14 Optimized Solution**:
    ```cpp
    #include <vector>
    #include <algorithm>

    void rotate(std::vector<int>& arr, int k) {
        int n = arr.size();
        k = k % n;
        std::reverse(arr.begin(), arr.end());
        std::reverse(arr.begin(), arr.begin() + k);
        std::reverse(arr.begin() + k, arr.end());
    }
    ```
*   **Complexity**: Time: $O(N)$, Space: $O(1)$.

---

## 4. Equilibrium Index of an Array
*   **Problem Statement**: Find the index $i$ such that the sum of elements at lower indices is equal to the sum of elements at higher indices. If multiple exist, return the first one.
    *   *Sample Input*: `[-7, 1, 5, 2, -4, 3, 0]` $\implies$ *Sample Output*: `3` (indices lower sum: $-7+1+5 = -1$; higher sum: $-4+3+0 = -1$).
*   **Brute Force**: For each index, calculate left and right sums using nested loops ($O(N^2)$).
*   **Key Insight**: Maintain a running `leftSum` and `rightSum`. Initialize `rightSum` as the sum of all elements. As you traverse, subtract the current element from `rightSum` and check if it equals `leftSum`.
*   **C++14 Optimized Solution**:
    ```cpp
    #include <vector>
    #include <numeric>

    int equilibriumIndex(const std::vector<int>& arr) {
        long long totalSum = 0;
        for (int num : arr) totalSum += num;
        
        long long leftSum = 0;
        for (size_t i = 0; i < arr.size(); i++) {
            totalSum -= arr[i]; // totalSum now acts as rightSum
            if (leftSum == totalSum) {
                return i;
            }
            leftSum += arr[i];
        }
        return -1;
    }
    ```
*   **Complexity**: Time: $O(N)$, Space: $O(1)$.

---

## 5. Move Zeroes to End
*   **Problem Statement**: Move all `0`s to the end of an array while maintaining the relative order of non-zero elements.
    *   *Sample Input*: `[0, 1, 0, 3, 12]` $\implies$ *Sample Output*: `[1, 3, 12, 0, 0]`.
*   **Brute Force**: Copy non-zero elements to a temp vector, fill remaining slots with zero ($O(N)$ space).
*   **Key Insight**: Use a pointer `insertPos` that keeps track of where the next non-zero element should be written. Swap elements when a non-zero element is encountered.
*   **C++14 Optimized Solution**:
    ```cpp
    #include <vector>
    #include <algorithm>

    void moveZeroes(std::vector<int>& arr) {
        int insertPos = 0;
        for (size_t i = 0; i < arr.size(); i++) {
            if (arr[i] != 0) {
                std::swap(arr[i], arr[insertPos]);
                insertPos++;
            }
        }
    }
    ```
*   **Complexity**: Time: $O(N)$, Space: $O(1)$.

---

## 6. Container With Most Water
*   **Problem Statement**: Given $N$ non-negative integers representing heights of vertical lines, find two lines which together with the x-axis forms a container that holds the most water.
    *   *Sample Input*: `[1, 8, 6, 2, 5, 4, 8, 3, 7]` $\implies$ *Sample Output*: `49`.
*   **Brute Force**: Compare all pairs using nested loops ($O(N^2)$).
*   **Key Insight**: Start with maximum width using pointers at both ends. To maximize area, move the pointer that points to the shorter line inward.
*   **C++14 Optimized Solution**:
    ```cpp
    #include <vector>
    #include <algorithm>

    int maxArea(const std::vector<int>& height) {
        int left = 0, right = height.size() - 1;
        int max_water = 0;
        while (left < right) {
            int h = std::min(height[left], height[right]);
            max_water = std::max(max_water, h * (right - left));
            if (height[left] < height[right]) left++;
            else right--;
        }
        return max_water;
    }
    ```
*   **Complexity**: Time: $O(N)$, Space: $O(1)$.

---

## 7. Subarray Sum Equals K
*   **Problem Statement**: Find the total number of continuous subarrays whose sum equals $K$.
    *   *Sample Input*: `[1, 1, 1]`, $K = 2$ $\implies$ *Sample Output*: `2` (subarrays are `arr[0..1]` and `arr[1..2]`).
*   **Brute Force**: Check all subarrays using nested loops ($O(N^2)$).
*   **Key Insight**: Maintain a running prefix sum. If `prefixSum - K` has been seen previously in our prefix sum history, it means there exists a subarray ending at the current index that sums to $K$.
*   **C++14 Optimized Solution**:
    ```cpp
    #include <vector>
    #include <unordered_map>

    int subarraySum(const std::vector<int>& arr, int k) {
        std::unordered_map<int, int> prevSum;
        int count = 0;
        int currSum = 0;
        prevSum[0] = 1; // Base case
        
        for (int num : arr) {
            currSum += num;
            if (prevSum.find(currSum - k) != prevSum.end()) {
                count += prevSum[currSum - k];
            }
            prevSum[currSum]++;
        }
        return count;
    }
    ```
*   **Complexity**: Time: $O(N)$ average, Space: $O(N)$.

---

## 8. Find the Duplicate Number (Floyd's Cycle Find)
*   **Problem Statement**: Given an array containing $N+1$ integers where each integer is between $1$ and $N$ inclusive, prove that at least one duplicate exists. Find the duplicate in $O(N)$ time and $O(1)$ space.
    *   *Sample Input*: `[1, 3, 4, 2, 2]` $\implies$ *Sample Output*: `2`.
*   **Brute Force**: Sorting ($O(N \log N)$) or Hash Set ($O(N)$ space).
*   **Key Insight**: Treat the array values as pointers to indices. A duplicate value creates a cycle. Use Floyd's Tortoise and Hare algorithm to detect the cycle entry point.
*   **C++14 Optimized Solution**:
    ```cpp
    #include <vector>

    int findDuplicate(const std::vector<int>& arr) {
        int tortoise = arr[0];
        int hare = arr[0];
        
        // Find intersection point of cycle
        do {
            tortoise = arr[tortoise];
            hare = arr[arr[hare]];
        } while (tortoise != hare);
        
        // Find entry point (duplicate value)
        tortoise = arr[0];
        while (tortoise != hare) {
            tortoise = arr[tortoise];
            hare = arr[hare];
        }
        return tortoise;
    }
    ```
*   **Complexity**: Time: $O(N)$, Space: $O(1)$.

---

## 9. Next Permutation
*   **Problem Statement**: Rearrange numbers into the lexicographically next greater permutation of numbers.
    *   *Sample Input*: `[1, 2, 3]` $\implies$ *Sample Output*: `[1, 3, 2]`.
*   **Key Insight**: 
    1. Find the first decreasing element `i` from the right.
    2. Find the element `j` larger than `arr[i]` from the right.
    3. Swap them, then reverse the elements after `i`.
*   **C++14 Optimized Solution**:
    ```cpp
    #include <vector>
    #include <algorithm>

    void nextPermutation(std::vector<int>& nums) {
        int n = nums.size(), k, l;
        for (k = n - 2; k >= 0; k--) {
            if (nums[k] < nums[k + 1]) break;
        }
        if (k < 0) {
            std::reverse(nums.begin(), nums.end());
        } else {
            for (l = n - 1; l > k; l--) {
                if (nums[l] > nums[k]) break;
            }
            std::swap(nums[k], nums[l]);
            std::reverse(nums.begin() + k + 1, nums.end());
        }
    }
    ```
*   **Complexity**: Time: $O(N)$, Space: $O(1)$.

---

## 10. Rearrange Positive and Negative Elements Alternately
*   **Problem Statement**: Rearrange array elements such that positive and negative numbers alternate. Order of same sign elements must be preserved.
    *   *Sample Input*: `[1, 2, -3, -4, -5, 6]` $\implies$ *Sample Output*: `[1, -3, 2, -4, 6, -5]`.
*   **Brute Force**: Split positive and negative into two arrays, then merge alternately ($O(N)$ space).
*   **C++14 Solution (preserves relative order with space)**:
    ```cpp
    #include <vector>

    std::vector<int> rearrange(const std::vector<int>& arr) {
        std::vector<int> pos, neg;
        for (int x : arr) {
            if (x >= 0) pos.push_back(x);
            else neg.push_back(x);
        }
        
        std::vector<int> result(arr.size());
        size_t i = 0, p = 0, n = 0;
        while (p < pos.size() && n < neg.size()) {
            result[i++] = pos[p++];
            result[i++] = neg[n++];
        }
        while (p < pos.size()) result[i++] = pos[p++];
        while (n < neg.size()) result[i++] = neg[n++];
        return result;
    }
    ```
*   **Complexity**: Time: $O(N)$, Space: $O(N)$.
