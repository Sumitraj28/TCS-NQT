# Arrays — Practice: Advanced / Prime Level (10 Questions)

> **Tags:** Difficulty / Expected Time / TCS Frequency  
> No overlap with basic or medium sets. Each includes a faster alternate method.

---

### Q1 — Trapping Rain Water
**Difficulty:** Hard | **Time:** 240s | **TCS Frequency:** Medium

`height = [0,1,0,2,1,0,1,3,2,1,2,1]`. How much rainwater is trapped?

**Full Solution (Two Pointer — O(n) time, O(1) space):**
- Water at any index = min(maxLeft, maxRight) − height[i]
- Use two pointers: if maxLeft < maxRight, process left side (since left is the bottleneck).

```cpp
#include <vector>
#include <algorithm>

int trap(const std::vector<int>& height) {
    int n = height.size();
    int left = 0, right = n - 1;
    int maxLeft = 0, maxRight = 0, water = 0;
    while (left < right) {
        if (height[left] < height[right]) {
            if (height[left] >= maxLeft) maxLeft = height[left];
            else water += maxLeft - height[left];
            left++;
        } else {
            if (height[right] >= maxRight) maxRight = height[right];
            else water += maxRight - height[right];
            right--;
        }
    }
    return water;
}
```

**Answer:** 6

**Alternate (O(n) space):** Precompute `leftMax` and `rightMax` arrays, then sum `max(0, min(leftMax[i], rightMax[i]) - height[i])`.

---

### Q2 — Maximum Product Subarray
**Difficulty:** Hard | **Time:** 180s | **TCS Frequency:** Medium

`nums = [2, 3, -2, 4]`. Find maximum product of any contiguous subarray.

**Full Solution:**
- Track both max and min (negative × negative = positive).

```cpp
#include <vector>
#include <algorithm>

int maxProduct(const std::vector<int>& nums) {
    int maxProd = nums[0], minProd = nums[0], result = nums[0];
    for (size_t i = 1; i < nums.size(); ++i) {
        if (nums[i] < 0) std::swap(maxProd, minProd);
        maxProd = std::max(nums[i], maxProd * nums[i]);
        minProd = std::min(nums[i], minProd * nums[i]);
        result  = std::max(result, maxProd);
    }
    return result;
}
```

**Answer:** 6 (subarray [2,3])

---

### Q3 — First Missing Positive
**Difficulty:** Hard | **Time:** 240s | **TCS Frequency:** Medium

`nums = [3, 4, -1, 1]`. Find the smallest missing positive integer.

**Full Solution (O(n) time, O(1) space — cyclic sort):**
- Place each number x in position x-1 (if 1 ≤ x ≤ n).

```cpp
#include <vector>
#include <algorithm>

int firstMissingPositive(std::vector<int>& nums) {
    int n = nums.size();
    for (int i = 0; i < n; ++i) {
        while (nums[i] > 0 && nums[i] <= n && nums[nums[i] - 1] != nums[i]) {
            std::swap(nums[i], nums[nums[i] - 1]);
        }
    }
    for (int i = 0; i < n; ++i) {
        if (nums[i] != i + 1) return i + 1;
    }
    return n + 1;
}
```

**Answer:** 2

---

### Q4 — Jump Game II (Minimum Jumps to Reach End)
**Difficulty:** Hard | **Time:** 200s | **TCS Frequency:** Low

`nums = [2,3,1,1,4]`. What is the minimum number of jumps to reach the last index?

**Full Solution (Greedy — O(n)):**
- Track `farthest` reach and `currentEnd` of current jump level.

```cpp
#include <vector>
#include <algorithm>

int jump(const std::vector<int>& nums) {
    int jumps = 0, farthest = 0, currentEnd = 0;
    for (size_t i = 0; i < nums.size() - 1; ++i) {
        farthest = std::max(farthest, (int)i + nums[i]);
        if (i == currentEnd) {
            jumps++;
            currentEnd = farthest;
        }
    }
    return jumps;
}
```

**Answer:** 2

---

### Q5 — Sliding Window Maximum
**Difficulty:** Hard | **Time:** 240s | **TCS Frequency:** Low

`nums = [1,3,-1,-3,5,3,6,7]`, k=3. Return max of each sliding window of size 3.

**Full Solution (std::deque — O(n)):**
- Maintain a deque of indices; front always has the current max.

```cpp
#include <vector>
#include <deque>

std::vector<int> maxSlidingWindow(const std::vector<int>& nums, int k) {
    std::deque<int> dq;
    std::vector<int> result;
    for (int i = 0; i < nums.size(); ++i) {
        if (!dq.empty() && dq.front() < i - k + 1) dq.pop_front();
        while (!dq.empty() && nums[dq.back()] < nums[i]) dq.pop_back();
        dq.push_back(i);
        if (i >= k - 1) result.push_back(nums[dq.front()]);
    }
    return result;
}
```

**Answer:** `[3, 3, 5, 5, 6, 7]`

---

### Q6 — Maximum Circular Subarray Sum
**Difficulty:** Hard | **Time:** 200s | **TCS Frequency:** Low

`nums = [5, -3, 5]`. Find the maximum subarray sum considering wrap-around.

**Full Solution:**
- Two cases: (1) Max subarray doesn't wrap → Kadane's normally. (2) Max subarray wraps → total_sum − min_subarray_sum.

```cpp
#include <vector>
#include <numeric>
#include <algorithm>

int maxSubarraySumCircular(const std::vector<int>& nums) {
    int totalSum = 0, maxSum = nums[0], curMax = 0, minSum = nums[0], curMin = 0;
    for (int num : nums) {
        curMax = std::max(num, curMax + num);
        maxSum = std::max(maxSum, curMax);
        curMin = std::min(num, curMin + num);
        minSum = std::min(minSum, curMin);
        totalSum += num;
    }
    return (maxSum < 0) ? maxSum : std::max(maxSum, totalSum - minSum);
}
```

**Answer:** 10 (wrap-around: [5, 5])

---

### Q7 — Merge k Sorted Arrays (k=3)
**Difficulty:** Hard | **Time:** 240s | **TCS Frequency:** Low

Merge 3 sorted arrays: `[1,4,7]`, `[2,5,8]`, `[3,6,9]`.

**Full Solution (std::priority_queue — O(N log k)):**

```cpp
#include <vector>
#include <queue>

struct Element {
    int val, valIdx, arrIdx;
    bool operator>(const Element& other) const { return val > other.val; }
};

std::vector<int> mergeKArrays(const std::vector<std::vector<int>>& arrays) {
    std::priority_queue<Element, std::vector<Element>, std::greater<Element>> pq;
    for (int i = 0; i < arrays.size(); ++i) {
        if (!arrays[i].empty()) pq.push({arrays[i][0], 0, i});
    }
    std::vector<int> result;
    while (!pq.empty()) {
        auto curr = pq.top(); pq.pop();
        result.push_back(curr.val);
        if (curr.valIdx + 1 < arrays[curr.arrIdx].size()) {
            pq.push({arrays[curr.arrIdx][curr.valIdx + 1], curr.valIdx + 1, curr.arrIdx});
        }
    }
    return result;
}
```

**Answer:** `[1, 2, 3, 4, 5, 6, 7, 8, 9]`

---

### Q8 — Median of Two Sorted Arrays
**Difficulty:** Hard | **Time:** 300s | **TCS Frequency:** Low

`A = [1,3]`, `B = [2]`. Find the median.

**Full Solution (Binary Search — O(log(min(m,n)))):**

```cpp
#include <vector>
#include <algorithm>
#include <climits>

double findMedianSortedArrays(const std::vector<int>& A, const std::vector<int>& B) {
    if (A.size() > B.size()) return findMedianSortedArrays(B, A);
    int m = A.size(), n = B.size();
    int lo = 0, hi = m;
    while (lo <= hi) {
        int partA = (lo + hi) / 2;
        int partB = (m + n + 1) / 2 - partA;
        int maxLeftA  = (partA == 0) ? INT_MIN : A[partA-1];
        int minRightA = (partA == m) ? INT_MAX : A[partA];
        int maxLeftB  = (partB == 0) ? INT_MIN : B[partB-1];
        int minRightB = (partB == n) ? INT_MAX : B[partB];
        
        if (maxLeftA <= minRightB && maxLeftB <= minRightA) {
            if ((m + n) % 2 == 1) return std::max(maxLeftA, maxLeftB);
            return (std::max(maxLeftA, maxLeftB) + std::min(minRightA, minRightB)) / 2.0;
        } else if (maxLeftA > minRightB) {
            hi = partA - 1;
        } else {
            lo = partA + 1;
        }
    }
    return 0.0;
}
```

**Answer:** 2.0

---

### Q9 — Minimum in Rotated Sorted Array (With Duplicates)
**Difficulty:** Hard | **Time:** 180s | **TCS Frequency:** Medium

`nums = [2,2,2,0,1]` (rotated sorted with duplicates). Find the minimum.

**Full Solution (Modified Binary Search):**

```cpp
#include <vector>

int findMin(const std::vector<int>& nums) {
    int lo = 0, hi = nums.size() - 1;
    while (lo < hi) {
        int mid = lo + (hi - lo) / 2;
        if (nums[mid] > nums[hi]) lo = mid + 1;
        else if (nums[mid] < nums[hi]) hi = mid;
        else hi--; // duplicate
    }
    return nums[lo];
}
```

**Answer:** 0

---

### Q10 — Minimum Absolute Difference (All Pairs)
**Difficulty:** Hard | **Time:** 180s | **TCS Frequency:** Medium

`arr = [4, 2, 1, 3]`. Find all pairs with minimum absolute difference.

**Full Solution:**
1. Sort: `[1, 2, 3, 4]`
2. Min diff = min of consecutive differences = 1
3. Collect all adjacent pairs with diff = 1: (1,2), (2,3), (3,4)

```cpp
#include <vector>
#include <algorithm>

std::vector<std::vector<int>> minimumAbsDifference(std::vector<int>& arr) {
    std::sort(arr.begin(), arr.end());
    int minDiff = 1e9;
    for (size_t i = 1; i < arr.size(); ++i) {
        minDiff = std::min(minDiff, arr[i] - arr[i - 1]);
    }
    std::vector<std::vector<int>> result;
    for (size_t i = 1; i < arr.size(); ++i) {
        if (arr[i] - arr[i - 1] == minDiff) {
            result.push_back({arr[i - 1], arr[i]});
        }
    }
    return result;
}
```

**Answer:** `[[1,2],[2,3],[3,4]]`
