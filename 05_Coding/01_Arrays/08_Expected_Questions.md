---
title: "Arrays - Expected Questions"
section: "Coding"
---

# Array Expected Coding Questions (2026 Predictions)

> [!NOTE]
> These are **high-probability practice patterns** based on observed NQT exam coding questions. They are not guaranteed actual exam content.

---

## 1. Expected Pattern: Sort Array of 0s, 1s, and 2s (Dutch National Flag)
*   **Problem Statement**: Sort an array containing only `0`s, `1`s, and `2`s in-place in $O(N)$ time and $O(1)$ space.
    *   *Sample Input*: `[2, 0, 2, 1, 1, 0]` $\implies$ *Sample Output*: `[0, 0, 1, 1, 2, 2]`.
*   **C++14 Solution**:
    ```cpp
    #include <vector>
    #include <algorithm>

    void sortColors(std::vector<int>& nums) {
        int low = 0, mid = 0, high = nums.size() - 1;
        while (mid <= high) {
            if (nums[mid] == 0) {
                std::swap(nums[low], nums[mid]);
                low++;
                mid++;
            } else if (nums[mid] == 1) {
                mid++;
            } else { // nums[mid] == 2
                std::swap(nums[mid], nums[high]);
                high--;
            }
        }
    }
    ```
*   **Complexity**: Time: $O(N)$, Space: $O(1)$.

---

## 2. Expected Pattern: Product of Array Except Self
*   **Problem Statement**: Given an array of $N$ integers, return an array `output` such that `output[i]` is equal to the product of all elements of the array except `arr[i]`. Solve in $O(N)$ time without using the division operator.
    *   *Sample Input*: `[1, 2, 3, 4]` $\implies$ *Sample Output*: `[24, 12, 8, 6]`.
*   **C++14 Solution**:
    ```cpp
    #include <vector>

    std::vector<int> productExceptSelf(const std::vector<int>& nums) {
        int n = nums.size();
        std::vector<int> res(n, 1);
        
        // Calculate prefix products
        int prefix = 1;
        for (int i = 0; i < n; i++) {
            res[i] = prefix;
            prefix *= nums[i];
        }
        
        // Calculate suffix products on the fly
        int suffix = 1;
        for (int i = n - 1; i >= 0; i--) {
            res[i] *= suffix;
            suffix *= nums[i];
        }
        return res;
    }
    ```
*   **Complexity**: Time: $O(N)$, Space: $O(1)$ auxiliary (excluding output array).

---

## 3. Expected Pattern: Find Peak Element
*   **Problem Statement**: A peak element is an element that is strictly greater than its neighbors. Find the index of any peak element in an array in $O(\log N)$ time.
    *   *Sample Input*: `[1, 2, 3, 1]` $\implies$ *Sample Output*: `2` (Index of value 3).
*   **C++14 Solution**:
    ```cpp
    #include <vector>

    int findPeakElement(const std::vector<int>& nums) {
        int low = 0, high = nums.size() - 1;
        while (low < high) {
            int mid = low + (high - low) / 2;
            if (nums[mid] < nums[mid + 1]) {
                low = mid + 1; // Peak must lie on right side
            } else {
                high = mid;    // Peak must lie on left side (or at mid)
            }
        }
        return low;
    }
    ```
*   **Complexity**: Time: $O(\log N)$, Space: $O(1)$.

---

## 4. Expected Pattern: Merge Sorted Arrays in-place
*   **Problem Statement**: Merge two sorted arrays `arr1` of size $M$ and `arr2` of size $N$ into a single sorted array of size $M+N$, where `arr1` has enough buffer space at the end to hold `arr2` elements.
    *   *Sample Input*: `arr1 = [1, 2, 3, 0, 0, 0]`, `arr2 = [2, 5, 6]` $\implies$ *Sample Output*: `[1, 2, 2, 3, 5, 6]`.
*   **C++14 Solution**:
    ```cpp
    #include <vector>

    void merge(std::vector<int>& nums1, int m, const std::vector<int>& nums2, int n) {
        int i = m - 1;     // End of valid nums1 elements
        int j = n - 1;     // End of nums2 elements
        int k = m + n - 1; // End of nums1 buffer
        
        while (i >= 0 && j >= 0) {
            if (nums1[i] > nums2[j]) {
                nums1[k--] = nums1[i--];
            } else {
                nums1[k--] = nums2[j--];
            }
        }
        while (j >= 0) {
            nums1[k--] = nums2[j--];
        }
    }
    ```
*   **Complexity**: Time: $O(M + N)$, Space: $O(1)$.

---

## 5. Expected Pattern: Subarray Sum with Given Sum (Non-Negatives)
*   **Problem Statement**: Find a continuous subarray that sums to a given number $S$ in an array of non-negative integers. Return 1-based start and end indices.
    *   *Sample Input*: `[1, 2, 3, 7, 5]`, Sum $= 12$ $\implies$ *Sample Output*: `2 4` (Subarray is `[2, 3, 7]`).
*   **C++14 Solution**:
    ```cpp
    #include <iostream>
    #include <vector>

    std::pair<int, int> subarraySum(const std::vector<int>& arr, long long targetSum) {
        int start = 0;
        long long currentSum = 0;
        for (int end = 0; end < arr.size(); end++) {
            currentSum += arr[end];
            while (currentSum > targetSum && start < end) {
                currentSum -= arr[start];
                start++;
            }
            if (currentSum == targetSum) {
                return {start + 1, end + 1}; // 1-based indexing
            }
        }
        return {-1, -1};
    }
    ```
*   **Complexity**: Time: $O(N)$, Space: $O(1)$.

---

## 6. Expected Pattern: Kth Smallest Element
*   **Problem Statement**: Find the Kth smallest element in an unsorted array of size $N$.
    *   *Sample Input*: `[7, 10, 4, 3, 20, 15]`, $K = 3$ $\implies$ *Sample Output*: `7`.
*   **C++14 Solution**:
    ```cpp
    #include <vector>
    #include <queue>

    int findKthSmallest(const std::vector<int>& arr, int k) {
        // Max heap to track K smallest elements
        std::priority_queue<int> maxHeap;
        for (int num : arr) {
            maxHeap.push(num);
            if (maxHeap.size() > k) {
                maxHeap.pop();
            }
        }
        return maxHeap.top();
    }
    ```
*   **Complexity**: Time: $O(N \log K)$, Space: $O(K)$.

---

## 7. Expected Pattern: Minimum Size Subarray Sum
*   **Problem Statement**: Find the minimal length of a contiguous subarray of which the sum is $\ge S$. If none exists, return 0.
    *   *Sample Input*: `[2, 3, 1, 2, 4, 3]`, $S = 7$ $\implies$ *Sample Output*: `2` (Subarray is `[4, 3]`).
*   **C++14 Solution**:
    ```cpp
    #include <vector>
    #include <algorithm>
    #include <climits>

    int minSubArrayLen(int s, const std::vector<int>& nums) {
        int left = 0;
        int sum = 0;
        int min_len = INT_MAX;
        
        for (int right = 0; right < nums.size(); right++) {
            sum += nums[right];
            while (sum >= s) {
                min_len = std::min(min_len, right - left + 1);
                sum -= nums[left];
                left++;
            }
        }
        return (min_len == INT_MAX) ? 0 : min_len;
    }
    ```
*   **Complexity**: Time: $O(N)$, Space: $O(1)$.

---

## 8. Expected Pattern: Maximum Sum of Non-Adjacent Elements
*   **Problem Statement**: Find the maximum sum of a subsequence in an array such that no two elements in the subsequence are adjacent.
    *   *Sample Input*: `[5, 5, 10, 100, 10, 5]` $\implies$ *Sample Output*: `110` (Sequence is `[5, 100, 5]`).
*   **C++14 Solution**:
    ```cpp
    #include <vector>
    #include <algorithm>

    int findMaxSum(const std::vector<int>& arr) {
        if (arr.empty()) return 0;
        int incl = arr[0]; // Max sum including current element
        int excl = 0;      // Max sum excluding current element
        
        for (size_t i = 1; i < arr.size(); i++) {
            int new_excl = std::max(incl, excl);
            incl = excl + arr[i];
            excl = new_excl;
        }
        return std::max(incl, excl);
    }
    ```
*   **Complexity**: Time: $O(N)$, Space: $O(1)$.

---

## 9. Expected Pattern: Count Subarrays with Given XOR
*   **Problem Statement**: Count the number of subarrays having XOR sum equal to $M$.
    *   *Sample Input*: `[4, 2, 2, 6, 4]`, $M = 6$ $\implies$ *Sample Output*: `4`.
*   **C++14 Solution**:
    ```cpp
    #include <vector>
    #include <unordered_map>

    int countSubarraysXOR(const std::vector<int>& arr, int m) {
        std::unordered_map<int, int> visitedXOR;
        int count = 0;
        int xr = 0;
        visitedXOR[0] = 1; // Base case
        
        for (int num : arr) {
            xr = xr ^ num;
            int target = xr ^ m;
            if (visitedXOR.find(target) != visitedXOR.end()) {
                count += visitedXOR[target];
            }
            visitedXOR[xr]++;
        }
        return count;
    }
    ```
*   **Complexity**: Time: $O(N)$ average, Space: $O(N)$.

---

## 10. Expected Pattern: Duplicate Find in range [1, N-1]
*   **Problem Statement**: In an array of size $N$ containing elements from $1$ to $N-1$ where exactly one element repeats, find the repeating number.
    *   *Sample Input*: `[1, 3, 2, 1]` $\implies$ *Sample Output*: `1`.
*   **C++14 Solution**:
    ```cpp
    #include <vector>

    int findDuplicateXOR(const std::vector<int>& arr) {
        int res = 0;
        // XOR all array values
        for (int val : arr) res ^= val;
        // XOR all index values from 1 to N-1
        for (int i = 1; i < arr.size(); i++) res ^= i;
        return res;
    }
    ```
*   **Complexity**: Time: $O(N)$, Space: $O(1)$.
