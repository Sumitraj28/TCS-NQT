---
title: "Arrays - Hard Problems"
section: "Coding"
---

# Array Hard Coding Problems

This set contains 5 hard-level array problems to maximize performance in the Prime hiring bracket.

---

## 1. Trapping Rain Water
*   **Problem Statement**: Given $N$ non-negative integers representing an elevation map where the width of each bar is 1, compute how much water it can trap after raining.
    *   *Constraints*: $1 \le N \le 10^5$, $0 \le arr[i] \le 10^5$.
    *   *Sample Input*: `[0, 1, 0, 2, 1, 0, 1, 3, 2, 1, 2, 1]` $\implies$ *Sample Output*: `6`.

### Approaches Comparison

| Method | Time Complexity | Space Complexity | Description |
| :--- | :---: | :---: | :--- |
| **Brute Force** | $O(N^2)$ | $O(1)$ | Scan left and right boundaries for every element. Fails TLE. |
| **Dynamic Programming** | $O(N)$ | $O(N)$ | Precompute and store prefix and suffix maximum arrays. |
| **Two Pointers** | $O(N)$ | $O(1)$ | Meet in the middle using left and right height buffers. **(Optimal)** |

*   **Key Insight**: Water trapped above any bar $i$ depends on: $\min(\text{max\_left}, \text{max\_right}) - \text{height}[i]$.
*   **C++14 Optimal Solution**:
    ```cpp
    #include <vector>
    #include <algorithm>

    int trap(const std::vector<int>& height) {
        int left = 0, right = height.size() - 1;
        int left_max = 0, right_max = 0;
        int trapped_water = 0;
        
        while (left < right) {
            if (height[left] < height[right]) {
                if (height[left] >= left_max) {
                    left_max = height[left];
                } else {
                    trapped_water += left_max - height[left];
                }
                left++;
            } else {
                if (height[right] >= right_max) {
                    right_max = height[right];
                } else {
                    trapped_water += right_max - height[right];
                }
                right--;
            }
        }
        return trapped_water;
    }
    ```
*   **Interview Follow-ups**: "How would you modify this algorithm to handle variable width bars?" (Water volume becomes height difference times width of segment).
*   **Similar TCS Patterns**: Container With Most Water, Building Heights visibility.

---

## 2. Largest Rectangle in Histogram
*   **Problem Statement**: Find the area of the largest rectangle in a histogram represented by an array of heights.
    *   *Sample Input*: `[2, 1, 5, 6, 2, 3]` $\implies$ *Sample Output*: `10`.

### Approaches Comparison
*   *Brute Force*: Calculate area for all possible pairs of columns ($O(N^2)$). Fails TLE.
*   *Monotonic Stack*: Maintain indices of columns in increasing order of height. Find left and right smaller boundaries in $O(1)$ stack operations.

*   **Key Insight**: A bar can only extend its rectangle to the left and right as long as the adjacent bars are taller or equal in height.
*   **C++14 Optimal Solution**:
    ```cpp
    #include <vector>
    #include <stack>
    #include <algorithm>

    int largestRectangleArea(const std::vector<int>& heights) {
        std::stack<int> s;
        int max_area = 0;
        int n = heights.size();
        
        for (int i = 0; i <= n; i++) {
            int curr_height = (i == n) ? 0 : heights[i];
            while (!s.empty() && curr_height < heights[s.top()]) {
                int h = heights[s.top()];
                s.pop();
                int w = s.empty() ? i : i - s.top() - 1;
                max_area = std::max(max_area, h * w);
            }
            s.push(i);
        }
        return max_area;
    }
    ```
*   **Complexity**: Time: $O(N)$, Space: $O(N)$ (stack).
*   **Interview Follow-ups**: "How would you extend this to find the largest 1-filled subgrid in a binary 2D matrix?" (Convert each row into a running histogram and apply this solver row-by-row).

---

## 3. Maximum Product Subarray
*   **Problem Statement**: Find the contiguous subarray within a 1D numerical array which has the largest product.
    *   *Sample Input*: `[2, 3, -2, 4]` $\implies$ *Sample Output*: `6` (subarray is `[2, 3]`).

### Approaches Comparison
*   *Brute Force*: $O(N^2)$ nested loops checking all subarrays product.
*   *Dynamic Programming (Two Buffers)*: Maintain running `max_prod` and `min_prod` because a negative number multiplied by a negative number can yield a new maximum product.

*   **C++14 Optimal Solution**:
    ```cpp
    #include <vector>
    #include <algorithm>

    int maxProduct(const std::vector<int>& nums) {
        if (nums.empty()) return 0;
        int max_prod = nums[0];
        int min_prod = nums[0];
        int result = nums[0];
        
        for (size_t i = 1; i < nums.size(); i++) {
            if (nums[i] < 0) std::swap(max_prod, min_prod);
            max_prod = std::max(nums[i], max_prod * nums[i]);
            min_prod = std::min(nums[i], min_prod * nums[i]);
            result = std::max(result, max_prod);
        }
        return result;
    }
    ```
*   **Complexity**: Time: $O(N)$, Space: $O(1)$.

---

## 4. Merge Intervals
*   **Problem Statement**: Given a collection of intervals, merge all overlapping intervals.
    *   *Sample Input*: `[[1, 3], [2, 6], [8, 10], [15, 18]]` $\implies$ *Sample Output*: `[[1, 6], [8, 10], [15, 18]]`.

### Approaches Comparison
*   *Unsorted Search*: $O(N^2)$ scan and merge.
*   *Sorting-based Merge*: Sort intervals by starting boundary. If current interval starts after the last merged interval ends, append it. Otherwise, extend the last merged interval.

*   **C++14 Optimal Solution**:
    ```cpp
    #include <vector>
    #include <algorithm>

    std::vector<std::vector<int>> mergeIntervals(std::vector<std::vector<int>>& intervals) {
        if (intervals.empty()) return {};
        // Sort by start values
        std::sort(intervals.begin(), intervals.end(), [](const std::vector<int>& a, const std::vector<int>& b) {
            return a[0] < b[0];
        });
        
        std::vector<std::vector<int>> merged;
        merged.push_back(intervals[0]);
        
        for (size_t i = 1; i < intervals.size(); i++) {
            if (intervals[i][0] <= merged.back()[1]) {
                // Overlap: update end value
                merged.back()[1] = std::max(merged.back()[1], intervals[i][1]);
            } else {
                // No overlap: add new interval
                merged.push_back(intervals[i]);
            }
        }
        return merged;
    }
    ```
*   **Complexity**: Time: $O(N \log N)$ (due to sort), Space: $O(1)$ auxiliary.

---

## 5. First Missing Positive
*   **Problem Statement**: Find the smallest missing positive integer from an unsorted integer array in $O(N)$ time and $O(1)$ space.
    *   *Sample Input*: `[3, 4, -1, 1]` $\implies$ *Sample Output*: `2`.

### Approaches Comparison
*   *Sorting*: $O(N \log N)$ time, $O(1)$ space.
*   *Hash Set*: $O(N)$ time, $O(N)$ space.
*   *Cycle Sort Index Marking*: Place each number `X` at index `X - 1` using swaps.

*   **C++14 Optimal Solution**:
    ```cpp
    #include <vector>
    #include <algorithm>

    int firstMissingPositive(std::vector<int>& nums) {
        int n = nums.size();
        for (int i = 0; i < n; i++) {
            // Place num at index num-1 if valid
            while (nums[i] > 0 && nums[i] <= n && nums[nums[i] - 1] != nums[i]) {
                std::swap(nums[i], nums[nums[i] - 1]);
            }
        }
        for (int i = 0; i < n; i++) {
            if (nums[i] != i + 1) return i + 1;
        }
        return n + 1;
    }
    ```
*   **Complexity**: Time: $O(N)$, Space: $O(1)$.
*   **Interview Follow-ups**: "Why is the time complexity $O(N)$ even with a nested while loop?" (Each swap places at least one element in its correct final position. Since there are at most $N$ elements, at most $N$ swaps can occur across the entire loop).
