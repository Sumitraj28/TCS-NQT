# Sorting — Coding Application (Full Problem Solutions)

> **Programming Language: C++.**  
> Every solution includes: Problem Statement → Approach → C++ code (line-by-line) → Complexity.

---

## Problem 1 — Sort Colors
**LeetCode:** #75 | **Difficulty:** Medium | **TCS Frequency:** High

### Problem Statement
Given an array `nums` with n objects colored red, white, or blue, sort them in-place so that objects of the same color are adjacent, with the colors in the order red, white, and blue (represented by integers 0, 1, and 2 respectively). Solve in one pass using constant space.

**Example:** `nums = [2,0,2,1,1,0]` → Output: `[0,0,1,1,2,2]`

### Approach (Dutch National Flag)
Three pointers: `low` at the next position for 0, `mid` as the active scanner, and `high` at the next position for 2. 
- If `nums[mid] == 0`: swap with `low`, increment both `low` and `mid`.
- If `nums[mid] == 1`: order correct, just increment `mid`.
- If `nums[mid] == 2`: swap with `high`, decrement `high` (do NOT increment `mid` since the swapped element is unexamined).

### C++ Solution
```cpp
#include <vector>
#include <algorithm>

class Solution {
public:
    void sortColors(std::vector<int>& nums) {
        int low = 0;
        int mid = 0;
        int high = nums.size() - 1;

        while (mid <= high) {
            if (nums[mid] == 0) {
                // Swap current element with the element at low boundary
                std::swap(nums[low++], nums[mid++]);
            } else if (nums[mid] == 1) {
                // Correct middle element placement, just advance
                mid++;
            } else {
                // Swap current element with the element at high boundary
                // Note: mid is NOT incremented because the new element at mid needs to be checked
                std::swap(nums[mid], nums[high--]);
            }
        }
    }
};
```

### Complexity
- **Time Complexity:** O(N) — single pass.
- **Space Complexity:** O(1) — in-place modifications.

---

## Problem 2 — Kth Largest Element in an Array
**LeetCode:** #215 | **Difficulty:** Medium | **TCS Frequency:** High

### Problem Statement
Given an integer array `nums` and an integer `k`, return the `k`th largest element in the array. Note that it is the `k`th largest element in the sorted order, not the `k`th distinct element.

**Example:** `nums = [3,2,1,5,6,4]`, `k = 2` → Output: `5`

### Approach
Instead of sorting the entire array in O(N log N), we can use `std::nth_element` (which implements QuickSelect) to partition the array in O(N) average time. The element at index `n - k` will be the `k`th largest.

### C++ Solution
```cpp
#include <vector>
#include <algorithm>

class Solution {
public:
    int findKthLargest(std::vector<int>& nums, int k) {
        int n = nums.size();
        // std::nth_element rearranges the vector such that the element at index (n - k)
        // is the one that would be there in a fully sorted vector.
        std::nth_element(nums.begin(), nums.begin() + n - k, nums.end());
        return nums[n - k];
    }
};
```

### Complexity
- **Time Complexity:** O(N) average, O(N²) worst-case (extremely rare in STL).
- **Space Complexity:** O(1) auxiliary space.

---

## Problem 3 — Merge Intervals
**LeetCode:** #56 | **Difficulty:** Medium | **TCS Frequency:** High

### Problem Statement
Given an array of `intervals` where `intervals[i] = [start_i, end_i]`, merge all overlapping intervals, and return an array of the non-overlapping intervals that cover all the input intervals.

**Example:** `intervals = [[1,3],[2,6],[8,10],[15,18]]` → Output: `[[1,6],[8,10],[15,18]]`

### Approach
Sort the intervals by their start times. This guarantees that any overlapping intervals are adjacent. Traverse the sorted intervals, merging them if current interval's start ≤ previous interval's end.

### C++ Solution
```cpp
#include <vector>
#include <algorithm>

class Solution {
public:
    std::vector<std::vector<int>> merge(std::vector<std::vector<int>>& intervals) {
        if (intervals.empty()) return {};

        // Sort intervals based on start times (default behavior for std::vector comparison)
        std::sort(intervals.begin(), intervals.end());

        std::vector<std::vector<int>> merged;
        merged.push_back(intervals[0]); // seed with the first interval

        for (size_t i = 1; i < intervals.size(); ++i) {
            // If the current interval overlaps with the previous one
            if (intervals[i][0] <= merged.back()[1]) {
                // Merge them by updating the end time to the max of both
                merged.back()[1] = std::max(merged.back()[1], intervals[i][1]);
            } else {
                // Otherwise, add the current interval as a new non-overlapping one
                merged.push_back(intervals[i]);
            }
        }
        return merged;
    }
};
```

### Complexity
- **Time Complexity:** O(N log N) — dominated by the sorting step.
- **Space Complexity:** O(1) auxiliary space (excluding output space).
