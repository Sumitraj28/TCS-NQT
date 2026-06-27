# Searching — Coding Application (Full Problem Solutions)

> **Programming Language: C++.**  
> Every solution includes: Problem Statement → Approach → C++ code (line-by-line) → Complexity.

---

## Problem 1 — Binary Search
**LeetCode:** #704 | **Difficulty:** Easy | **TCS Frequency:** High

### Problem Statement
Given an array of integers `nums` sorted in ascending order and an integer `target`, write a function to search `target` in `nums`. Return its index if found, or -1.

**Example:** `nums = [-1,0,3,5,9,12]`, `target = 9` → Output: `4`

### Approach
Classic binary search. Maintain a search range `[lo, hi]`. Compare the middle element with target. Eliminate the half that cannot contain the target.

### C++ Solution
```cpp
#include <vector>

class Solution {
public:
    int search(std::vector<int>& nums, int target) {
        int lo = 0;
        int hi = nums.size() - 1;  // inclusive right boundary

        while (lo <= hi) {         // loop while search space is non-empty
            int mid = lo + (hi - lo) / 2;  // safe midpoint (no overflow)

            if (nums[mid] == target) {
                return mid;        // target found
            } else if (nums[mid] < target) {
                lo = mid + 1;      // target is in the right half
            } else {
                hi = mid - 1;      // target is in the left half
            }
        }
        return -1;                 // target not found
    }
};
```

**Line-by-line Explanation:**
- `hi = nums.size() - 1` — closed interval [lo, hi].
- `lo <= hi` — continue as long as search space contains at least one element.
- `mid = lo + (hi - lo) / 2` — safe calculation to prevent integer overflow.
- `nums[mid] < target` → target must lie in the right half → `lo = mid + 1`.
- `nums[mid] > target` → target must lie in the left half → `hi = mid - 1`.

### Complexity
- **Time Complexity:** O(log n).
- **Space Complexity:** O(1).

---

## Problem 2 — First Bad Version
**LeetCode:** #278 | **Difficulty:** Easy | **TCS Frequency:** High

### Problem Statement
You are a product manager with n product versions. Version k and all after it are "bad". You have an API `isBadVersion(version)` returning true/false. Find the first bad version with the minimum number of API calls.

**Example:** n=5, first bad=4. `isBad(3)=false, isBad(4)=true` → Output: 4

### Approach
This is a binary search on a boolean sequence: `[false, false, ..., false, true, true, ..., true]`. Find the first `true`. If mid is bad, the answer is ≤ mid. If mid is good, the answer is > mid.

### C++ Solution
```cpp
class Solution {
public:
    int firstBadVersion(int n) {
        int lo = 1;   // versions are 1-indexed
        int hi = n;

        while (lo < hi) {                    // stops when lo == hi
            int mid = lo + (hi - lo) / 2;

            if (isBadVersion(mid)) {
                hi = mid;                    // mid is bad → answer is at mid or before
            } else {
                lo = mid + 1;                // mid is good → answer is after mid
            }
        }
        return lo;                           // first bad version
    }
};
```

**Line-by-line Explanation:**
- `lo < hi` — loops until convergence.
- `hi = mid` — mid could be the first bad version, so we do not exclude it.
- `lo = mid + 1` — mid is good, so first bad version must be strictly after mid.

### Complexity
- **Time Complexity:** O(log n).
- **Space Complexity:** O(1).

---

## Problem 3 — Find Peak Element
**LeetCode:** #162 | **Difficulty:** Medium | **TCS Frequency:** High

### Problem Statement
A peak element is an element strictly greater than its neighbors. Given `nums`, return the index of any peak element. Assume `nums[-1] = nums[n] = -∞`. You must write an O(log n) algorithm.

**Example:** `nums = [1,2,3,1]` → Output: 2 (nums[2]=3 is a peak)

### Approach
Compare `nums[mid]` and `nums[mid+1]`. If `nums[mid] < nums[mid+1]`, then the slope goes up to the right, meaning a peak must exist on the right. Otherwise, the slope goes down, so a peak exists on the left (or at mid itself).

### C++ Solution
```cpp
#include <vector>

class Solution {
public:
    int findPeakElement(std::vector<int>& nums) {
        int lo = 0;
        int hi = nums.size() - 1;

        while (lo < hi) {
            int mid = lo + (hi - lo) / 2;

            if (nums[mid] < nums[mid + 1]) {
                // Right side is higher → peak is in right half
                lo = mid + 1;
            } else {
                // Current is higher than or equal to next → peak is at mid or left half
                hi = mid;
            }
        }
        return lo;  // lo == hi == index of a peak
    }
};
```

**Line-by-line Explanation:**
- `lo < hi` — stops when they converge.
- `nums[mid] < nums[mid+1]` — uphill to the right → peak is in the right half.
- `lo = mid + 1` — excludes mid since it is strictly less than mid+1.
- `hi = mid` — mid could be the peak, so we don't exclude it.

### Complexity
- **Time Complexity:** O(log n).
- **Space Complexity:** O(1).
