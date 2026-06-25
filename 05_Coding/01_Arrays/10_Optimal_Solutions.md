---
title: "Arrays - Optimal Solutions"
section: "Coding"
---

# Array Optimal Solutions

This guide covers the optimal $O(N)$ solutions for the 5 core array patterns.

---

## 1. Two Sum (Unsorted Target Sum check)
*   **The Optimal Solution**: Hashing check.
*   **Key Insight**: Instead of looking at all pairs, we store each visited element `x` in a hash map. For any subsequent element `y`, we can check if its complement `target - y` has been seen in $O(1)$ time.
*   **Proof of Correctness**: For any valid pair $x + y = T$, since the array is scanned left to right, the element appearing second (say $y$) will trigger a match because $x = T - y$ is already in the hash map.
*   **C++14 Implementation**:
    ```cpp
    #include <vector>
    #include <unordered_map>

    std::pair<int, int> twoSumOptimal(const std::vector<int>& nums, int target) {
        std::unordered_map<int, int> seen;
        for (int i = 0; i < nums.size(); i++) {
            int comp = target - nums[i];
            if (seen.find(comp) != seen.end()) {
                return {seen[comp], i};
            }
            seen[nums[i]] = i;
        }
        return {-1, -1};
    }
    ```
*   **Complexity**: Time: $O(N)$ average, Space: $O(N)$.

---

## 2. Maximum Subarray Sum (Kadane's Algorithm)
*   **The Optimal Solution**: Linear Greedy sum tracking.
*   **Key Insight**: A running contiguous subarray sum is only useful if it is positive. If the cumulative sum drops below zero, we drop the prefix and restart from the current element.
*   **Proof of Correctness**: Adding a negative prefix sum to any element `arr[i]` will always result in a sum smaller than `arr[i]` itself. Thus, resetting the running sum to `0` when it becomes negative is mathematically optimal.
*   **C++14 Implementation**:
    ```cpp
    #include <vector>
    #include <algorithm>

    long long maxSubarraySumOptimal(const std::vector<int>& arr) {
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

## 3. Subarray Sum Equals K
*   **The Optimal Solution**: Prefix sum hashing.
*   **Key Insight**: Let the prefix sum up to index `i` be `prefix[i]`. The sum of any subarray from `j` to `i` is `prefix[i] - prefix[j-1]`. If `prefix[i] - prefix[j-1] = K`, then `prefix[j-1] = prefix[i] - K`. We use a hash map to keep track of how many times each prefix sum has occurred.
*   **Proof of Correctness**: For every index `i`, the hash map tells us exactly how many previous indices `j-1` have a prefix sum equal to `prefix[i] - K`, which is the count of subarrays ending at `i` that sum to $K$.
*   **C++14 Implementation**:
    ```cpp
    #include <vector>
    #include <unordered_map>

    int subarraySumOptimal(const std::vector<int>& nums, int k) {
        std::unordered_map<int, int> prefixFreq;
        prefixFreq[0] = 1; // Base case
        int curr_sum = 0;
        int count = 0;
        
        for (int num : nums) {
            curr_sum += num;
            if (prefixFreq.find(curr_sum - k) != prefixFreq.end()) {
                count += prefixFreq[curr_sum - k];
            }
            prefixFreq[curr_sum]++;
        }
        return count;
    }
    ```
*   **Complexity**: Time: $O(N)$ average, Space: $O(N)$.

---

## 4. Product of Array Except Self
*   **The Optimal Solution**: Prefix and Suffix products.
*   **Key Insight**: Any element `output[i]` is the product of all elements to its left (prefix) multiplied by all elements to its right (suffix). We can calculate prefix products in a forward pass, and then apply suffix products in a backward pass in-place.
*   **Proof of Correctness**: At index `i`, the output variable first stores $\prod_{j=0}^{i-1} arr[j]$ (prefix). During the reverse loop, we multiply it by $\prod_{j=i+1}^{n-1} arr[j]$ (suffix), resulting in the product of all elements except `arr[i]`.
*   **C++14 Implementation**:
    ```cpp
    #include <vector>

    std::vector<int> productExceptSelfOptimal(const std::vector<int>& nums) {
        int n = nums.size();
        std::vector<int> res(n, 1);
        
        int prefix = 1;
        for (int i = 0; i < n; i++) {
            res[i] = prefix;
            prefix *= nums[i];
        }
        
        int suffix = 1;
        for (int i = n - 1; i >= 0; i--) {
            res[i] *= suffix;
            suffix *= nums[i];
        }
        return res;
    }
    ```
*   **Complexity**: Time: $O(N)$, Space: $O(1)$ auxiliary.

---

## 5. Container With Most Water
*   **The Optimal Solution**: Two Pointers.
*   **Key Insight**: Start with maximum width using pointers at both ends (`left` and `right`). The area is limited by the shorter boundary. To find a larger area, we must move the pointer pointing to the shorter boundary inward.
*   **Proof of Correctness**: Moving the pointer pointing to the taller boundary inward cannot increase the area because the width decreases and the height remains limited by the shorter boundary. Thus, we only move the shorter pointer.
*   **C++14 Implementation**:
    ```cpp
    #include <vector>
    #include <algorithm>

    int maxAreaOptimal(const std::vector<int>& height) {
        int left = 0, right = height.size() - 1;
        int max_water = 0;
        while (left < right) {
            int h = std::min(height[left], height[right]);
            max_water = std::max(max_water, h * (right - left));
            if (height[left] < height[right]) {
                left++;
            } else {
                right--;
            }
        }
        return max_water;
    }
    ```
*   **Complexity**: Time: $O(N)$, Space: $O(1)$.
