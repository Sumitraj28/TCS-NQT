# Searching — Practice: Medium (15 Questions)

> No overlap with practice_basic.md

---

### Q1 — Search in Rotated Sorted Array
**Difficulty:** Medium | **Time:** 150s | **TCS Frequency:** High

`nums = [4,5,6,7,0,1,2]`, target=0. Find index or return -1.

**Full Solution:**
Binary search — at each mid, one half is always sorted. Check which half and whether target falls in it.

```cpp
#include <vector>

int search(const std::vector<int>& nums, int target) {
    int lo = 0, hi = nums.size() - 1;
    while (lo <= hi) {
        int mid = lo + (hi - lo) / 2;
        if (nums[mid] == target) return mid;
        
        if (nums[lo] <= nums[mid]) { // left half sorted
            if (nums[lo] <= target && target < nums[mid]) hi = mid - 1;
            else lo = mid + 1;
        } else { // right half sorted
            if (nums[mid] < target && target <= nums[hi]) lo = mid + 1;
            else hi = mid - 1;
        }
    }
    return -1;
}
```

**Answer:** Index 4

---

### Q2 — Find Peak Element (Any Peak)
**Difficulty:** Medium | **Time:** 90s | **TCS Frequency:** High

`nums = [1,2,1,3,5,6,4]`. Find any peak (element > both neighbors).

**Full Solution:**
```cpp
#include <vector>

int findPeakElement(const std::vector<int>& nums) {
    int lo = 0, hi = nums.size() - 1;
    while (lo < hi) {
        int mid = lo + (hi - lo) / 2;
        if (nums[mid] < nums[mid + 1]) lo = mid + 1;
        else hi = mid;
    }
    return lo;
}
```

**Answer:** Index 5 (value 6 > neighbors 5 and 4) ✓

---

### Q3 — First Bad Version
**Difficulty:** Medium | **Time:** 90s | **TCS Frequency:** High

Versions 1..10. isBad(v) returns true for v ≥ 4. Find the first bad version.

**Full Solution:**
```cpp
int firstBadVersion(int n) {
    int lo = 1, hi = n;
    while (lo < hi) {
        int mid = lo + (hi - lo) / 2;
        if (isBadVersion(mid)) hi = mid;  // bad version, search left
        else lo = mid + 1;                // good version, search right
    }
    return lo;
}
```

**Answer:** 4

---

### Q4 — Find Minimum in Rotated Sorted Array
**Difficulty:** Medium | **Time:** 120s | **TCS Frequency:** High

`nums = [3,4,5,1,2]`. Find the minimum element.

**Full Solution:**
```cpp
#include <vector>

int findMin(const std::vector<int>& nums) {
    int lo = 0, hi = nums.size() - 1;
    while (lo < hi) {
        int mid = lo + (hi - lo) / 2;
        if (nums[mid] > nums[hi]) lo = mid + 1; // min is in right half
        else hi = mid;                          // min is at mid or left
    }
    return nums[lo];
}
```

**Answer:** 1

---

### Q5 — Search Insert Position
**Difficulty:** Medium | **Time:** 75s | **TCS Frequency:** High

`arr = [1,3,5,6]`, target=5. Return the index if found, else where it would be inserted.

**Full Solution:** Lower bound.
Using C++ `std::lower_bound`:
```cpp
#include <vector>
#include <algorithm>

int searchInsert(std::vector<int>& nums, int target) {
    return std::lower_bound(nums.begin(), nums.end(), target) - nums.begin();
}
```

**Answer:** 2

---

### Q6 — Count Negative Numbers in Sorted 2D Matrix
**Difficulty:** Medium | **Time:** 150s | **TCS Frequency:** Medium

`grid = [[4,3,2,-1],[3,2,1,-1],[1,1,-1,-2],[-1,-1,-2,-3]]`. Count negatives.

**Full Solution:**
Start at top-right. Move left if negative, down if non-negative.
```cpp
#include <vector>

int countNegatives(const std::vector<std::vector<int>>& grid) {
    int m = grid.size(), n = grid[0].size();
    int row = 0, col = n - 1, count = 0;
    while (row < m && col >= 0) {
        if (grid[row][col] < 0) {
            count += m - row;
            col--;
        } else {
            row++;
        }
    }
    return count;
}
```

**Answer:** 8

---

### Q7 — Sqrt(x) Using Binary Search
**Difficulty:** Medium | **Time:** 120s | **TCS Frequency:** High

Find floor(sqrt(16)).

**Full Solution:**
Binary search for largest k where k² ≤ x.
```cpp
int mySqrt(int x) {
    if (x == 0) return 0;
    int lo = 1, hi = x, ans = 0;
    while (lo <= hi) {
        int mid = lo + (hi - lo) / 2;
        if (mid <= x / mid) { // avoids overflow instead of mid*mid <= x
            ans = mid;
            lo = mid + 1;
        } else {
            hi = mid - 1;
        }
    }
    return ans;
}
```

**Answer:** 4

---

### Q8 — Find Position of Element in Infinite Array
**Difficulty:** Medium | **Time:** 150s | **TCS Frequency:** Low

In an infinite sorted array, find element 77.

**Full Solution:**
Exponential search: start with range [0, 1]. Double the range size until `arr[hi] >= target`. Then perform binary search in that range.
```cpp
// 1. Find boundaries
int lo = 0, hi = 1;
while (arr[hi] < target) {
    lo = hi;
    hi = hi * 2;
}
// 2. Binary search in [lo, hi]
```

---

### Q9 — Number of 1s in Sorted Binary Array
**Difficulty:** Medium | **Time:** 90s | **TCS Frequency:** High

`arr = [0,0,0,1,1,1,1]`. Count number of 1s using binary search.

**Full Solution:**
Use `std::lower_bound` to find first index of 1.
```cpp
#include <vector>
#include <algorithm>

int countOnes(const std::vector<int>& arr) {
    auto it = std::lower_bound(arr.begin(), arr.end(), 1);
    return arr.end() - it;
}
```

**Answer:** 4

---

### Q10 — Allocate Minimum Number of Pages
**Difficulty:** Medium | **Time:** 180s | **TCS Frequency:** Medium

Books = [12,34,67,90], students=2. Minimize the maximum pages any student reads.

**Full Solution (Binary Search on Answer):**
```cpp
#include <vector>
#include <numeric>
#include <algorithm>

bool isPossible(const std::vector<int>& arr, int n, int m, int min_pages) {
    int studentsRequired = 1, sum = 0;
    for (int i = 0; i < n; ++i) {
        if (arr[i] > min_pages) return false;
        if (sum + arr[i] > min_pages) {
            studentsRequired++;
            sum = arr[i];
            if (studentsRequired > m) return false;
        } else {
            sum += arr[i];
        }
    }
    return true;
}

int findPages(const std::vector<int>& arr, int n, int m) {
    if (n < m) return -1;
    int sum = std::accumulate(arr.begin(), arr.end(), 0);
    int lo = *std::max_element(arr.begin(), arr.end()), hi = sum, ans = -1;
    while (lo <= hi) {
        int mid = lo + (hi - lo) / 2;
        if (isPossible(arr, n, m, mid)) {
            ans = mid;
            hi = mid - 1;
        } else {
            lo = mid + 1;
        }
    }
    return ans;
}
```

**Answer:** 113

---

### Q11 — Find K Closest Elements
**Difficulty:** Medium | **Time:** 150s | **TCS Frequency:** Medium

`arr = [1,2,3,4,5]`, k=4, x=3. Find 4 elements closest to 3.

**Full Solution:**
Binary search to find window start.
```cpp
#include <vector>
#include <algorithm>

std::vector<int> findClosestElements(const std::vector<int>& arr, int k, int x) {
    int lo = 0, hi = arr.size() - k;
    while (lo < hi) {
        int mid = lo + (hi - lo) / 2;
        if (x - arr[mid] > arr[mid + k] - x) lo = mid + 1;
        else hi = mid;
    }
    return std::vector<int>(arr.begin() + lo, arr.begin() + lo + k);
}
```

**Answer:** [1,2,3,4]

---

### Q12 — Find Target in 2D Sorted Matrix
**Difficulty:** Medium | **Time:** 120s | **TCS Frequency:** High

`matrix = [[1,3,5],[7,9,11],[13,15,17]]`, target=9.

**Full Solution:**
Staircase search: start at top-right.
```cpp
#include <vector>

bool searchMatrix(const std::vector<std::vector<int>>& matrix, int target) {
    int m = matrix.size(), n = matrix[0].size();
    int row = 0, col = n - 1;
    while (row < m && col >= 0) {
        if (matrix[row][col] == target) return true;
        else if (matrix[row][col] > target) col--;
        else row++;
    }
    return false;
}
```

**Answer:** true

---

### Q13 — Minimum Difference in Sorted Array
**Difficulty:** Medium | **Time:** 120s | **TCS Frequency:** Medium

`arr = [1,5,10,20]`, target=6. Find element closest to 6.

**Full Solution:**
Use `std::lower_bound` and compare difference of `arr[idx]` and `arr[idx-1]`.

**Answer:** 5 (diff is 1)

---

### Q14 — Find Duplicate in Sorted Array (Binary Search)
**Difficulty:** Medium | **Time:** 120s | **TCS Frequency:** High

`arr = [1,2,3,3,4,5]`. Find duplicate.

**Full Solution:**
```cpp
#include <vector>

int findDuplicate(const std::vector<int>& arr) {
    int lo = 0, hi = arr.size() - 1;
    while (lo <= hi) {
        int mid = lo + (hi - lo) / 2;
        if (mid > 0 && arr[mid] == arr[mid - 1]) return arr[mid];
        if (mid < arr.size() - 1 && arr[mid] == arr[mid + 1]) return arr[mid];
        
        if (arr[mid] >= mid + 1) lo = mid + 1;
        else hi = mid - 1;
    }
    return -1;
}
```

**Answer:** 3

---

### Q15 — Aggressive Cows (Binary Search on Answer)
**Difficulty:** Medium | **Time:** 200s | **TCS Frequency:** Low

Stalls at [1,2,4,8,9], 3 cows. Maximize minimum distance.

**Full Solution:**
```cpp
#include <vector>
#include <algorithm>

bool canPlace(const std::vector<int>& stalls, int k, int dist) {
    int count = 1, last = stalls[0];
    for (size_t i = 1; i < stalls.size(); ++i) {
        if (stalls[i] - last >= dist) {
            count++;
            last = stalls[i];
            if (count >= k) return true;
        }
    }
    return false;
}

int aggressiveCows(std::vector<int>& stalls, int k) {
    std::sort(stalls.begin(), stalls.end());
    int lo = 1, hi = stalls.back() - stalls[0], ans = 0;
    while (lo <= hi) {
        int mid = lo + (hi - lo) / 2;
        if (canPlace(stalls, k, mid)) {
            ans = mid;
            lo = mid + 1;
        } else {
            hi = mid - 1;
        }
    }
    return ans;
}
```

**Answer:** 3
