# Searching — Practice: Advanced / Prime Level (10 Questions)

> No overlap with basic or medium sets. Full solution in C++ + faster alternate method.

---

### Q1 — Median of Two Sorted Arrays
**Difficulty:** Hard | **Time:** 300s | **TCS Frequency:** Low

`A=[1,3]`, `B=[2,4]`. Find median of merged array.

**Full Solution (Binary Search O(log min(m,n))):**

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
        
        int maxLeftA  = (partA == 0) ? INT_MIN : A[partA - 1];
        int minRightA = (partA == m) ? INT_MAX : A[partA];
        int maxLeftB  = (partB == 0) ? INT_MIN : B[partB - 1];
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

**Answer:** 2.5

**Alternate:** Merge both O(m+n), find middle index. O(m+n) time.

---

### Q2 — Kth Smallest Element in a Sorted Matrix
**Difficulty:** Hard | **Time:** 240s | **TCS Frequency:** Low

`matrix = [[1,5,9],[10,11,13],[12,13,15]]`, k=8. Find 8th smallest.

**Full Solution (Binary Search on Value):**

```cpp
#include <vector>
#include <algorithm>

int countLessEqual(const std::vector<std::vector<int>>& matrix, int mid) {
    int count = 0, n = matrix.size();
    int row = n - 1, col = 0;
    while (row >= 0 && col < n) {
        if (matrix[row][col] <= mid) {
            count += row + 1;
            col++;
        } else {
            row--;
        }
    }
    return count;
}

int kthSmallest(const std::vector<std::vector<int>>& matrix, int k) {
    int n = matrix.size();
    int lo = matrix[0][0], hi = matrix[n-1][n-1], ans = -1;
    while (lo <= hi) {
        int mid = lo + (hi - lo) / 2;
        if (countLessEqual(matrix, mid) >= k) {
            ans = mid;
            hi = mid - 1;
        } else {
            lo = mid + 1;
        }
    }
    return ans;
}
```

**Answer:** 13

---

### Q3 — Find the Rotation Count in Rotated Sorted Array
**Difficulty:** Hard | **Time:** 180s | **TCS Frequency:** Medium

`nums = [15,18,2,3,6,12]`. How many positions was it rotated?

**Full Solution:**
Find index of minimum element = rotation count.

```cpp
#include <vector>

int findRotationCount(const std::vector<int>& nums) {
    int lo = 0, hi = nums.size() - 1;
    while (lo < hi) {
        int mid = lo + (hi - lo) / 2;
        if (nums[mid] > nums[hi]) lo = mid + 1;
        else hi = mid;
    }
    return lo; // index of min element
}
```

**Answer:** 2

---

### Q4 — Split Array Largest Sum
**Difficulty:** Hard | **Time:** 240s | **TCS Frequency:** Low

`nums=[7,2,5,10,8]`, m=2. Split into m=2 parts minimizing the largest part sum.

**Full Solution (Binary Search on Answer):**

```cpp
#include <vector>
#include <numeric>
#include <algorithm>

bool isPossible(const std::vector<int>& nums, int m, int max_sum) {
    int parts = 1, current_sum = 0;
    for (int num : nums) {
        if (num > max_sum) return false;
        if (current_sum + num > max_sum) {
            parts++;
            current_sum = num;
            if (parts > m) return false;
        } else {
            current_sum += num;
        }
    }
    return true;
}

int splitArray(const std::vector<int>& nums, int m) {
    int sum = std::accumulate(nums.begin(), nums.end(), 0);
    int lo = *std::max_element(nums.begin(), nums.end()), hi = sum, ans = -1;
    while (lo <= hi) {
        int mid = lo + (hi - lo) / 2;
        if (isPossible(nums, m, mid)) {
            ans = mid;
            hi = mid - 1;
        } else {
            lo = mid + 1;
        }
    }
    return ans;
}
```

**Answer:** 18

---

### Q5 — Search in 2D Matrix (Not Row-wise Sorted, But Each Row Sorted)
**Difficulty:** Hard | **Time:** 200s | **TCS Frequency:** Medium

`matrix = [[1,4,7,11],[2,5,8,12],[3,6,9,16],[10,13,14,17]]`, target=5. Find it.

**Full Solution (Staircase Search):**
```cpp
#include <vector>

bool searchMatrixII(const std::vector<std::vector<int>>& matrix, int target) {
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

### Q6 — Koko Eating Bananas
**Difficulty:** Hard | **Time:** 180s | **TCS Frequency:** Low

Piles=[3,6,7,11], hours=8. Minimum eating speed to finish all piles in 8 hours.

**Full Solution:**
```cpp
#include <vector>
#include <algorithm>
#include <cmath>

bool canEatAll(const std::vector<int>& piles, int h, int k) {
    int hoursSpent = 0;
    for (int pile : piles) {
        hoursSpent += (pile + k - 1) / k; // ceiling division
    }
    return hoursSpent <= h;
}

int minEatingSpeed(const std::vector<int>& piles, int h) {
    int lo = 1, hi = *std::max_element(piles.begin(), piles.end()), ans = hi;
    while (lo <= hi) {
        int mid = lo + (hi - lo) / 2;
        if (canEatAll(piles, h, mid)) {
            ans = mid;
            hi = mid - 1;
        } else {
            lo = mid + 1;
        }
    }
    return ans;
}
```

**Answer:** 4

---

### Q7 — Find K-th Positive Missing Number
**Difficulty:** Hard | **Time:** 180s | **TCS Frequency:** Medium

`arr = [2,3,4,7,11]`, k=5. Find 5th positive missing integer.

**Full Solution (Binary Search):**
```cpp
#include <vector>

int findKthPositive(const std::vector<int>& arr, int k) {
    int lo = 0, hi = arr.size() - 1;
    while (lo <= hi) {
        int mid = lo + (hi - lo) / 2;
        int missing = arr[mid] - (mid + 1);
        if (missing < k) {
            lo = mid + 1;
        } else {
            hi = mid - 1;
        }
    }
    return lo + k;
}
```

**Answer:** 9

---

### Q8 — Find Duplicate Using Binary Search (Without Extra Space)
**Difficulty:** Hard | **Time:** 240s | **TCS Frequency:** Medium

`nums = [1,3,4,2,2]`. Find duplicate. Use binary search O(n log n), O(1) space.

**Full Solution:**
```cpp
#include <vector>

int findDuplicate(const std::vector<int>& nums) {
    int lo = 1, hi = nums.size() - 1, ans = -1;
    while (lo <= hi) {
        int mid = lo + (hi - lo) / 2;
        int count = 0;
        for (int num : nums) {
            if (num <= mid) count++;
        }
        if (count > mid) {
            ans = mid;
            hi = mid - 1;
        } else {
            lo = mid + 1;
        }
    }
    return ans;
}
```

**Answer:** 2

---

### Q9 — Gas Station (Feasibility Check + Binary Search Concept)
**Difficulty:** Hard | **Time:** 240s | **TCS Frequency:** Low

`gas=[1,2,3,4,5]`, `cost=[3,4,5,1,2]`. Find starting station for a complete circuit.

**Full Solution (Greedy — O(n)):**
```cpp
#include <vector>
#include <numeric>

int canCompleteCircuit(const std::vector<int>& gas, const std::vector<int>& cost) {
    int total_surplus = 0, current_surplus = 0, start = 0;
    for (int i = 0; i < gas.size(); ++i) {
        total_surplus += gas[i] - cost[i];
        current_surplus += gas[i] - cost[i];
        if (current_surplus < 0) {
            start = i + 1;
            current_surplus = 0;
        }
    }
    return (total_surplus < 0) ? -1 : start;
}
```

**Answer:** 3

---

### Q10 — Minimum Speed to Arrive on Time
**Difficulty:** Hard | **Time:** 240s | **TCS Frequency:** Low

`dist=[1,3,2]`, `hour=6`. Minimum speed (ceil(d/v)).

**Full Solution (Binary Search on speed):**
```cpp
#include <vector>
#include <algorithm>
#include <cmath>

bool checkSpeed(const std::vector<int>& dist, double hour, int speed) {
    double time = 0;
    for (int i = 0; i < (int)dist.size() - 1; ++i) {
        time += std::ceil((double)dist[i] / speed);
    }
    time += (double)dist.back() / speed;
    return time <= hour;
}

int minSpeedOnTime(const std::vector<int>& dist, double hour) {
    if (hour <= dist.size() - 1) return -1;
    int lo = 1, hi = 1e7, ans = -1;
    while (lo <= hi) {
        int mid = lo + (hi - lo) / 2;
        if (checkSpeed(dist, hour, mid)) {
            ans = mid;
            hi = mid - 1;
        } else {
            lo = mid + 1;
        }
    }
    return ans;
}
```

**Answer:** 1
