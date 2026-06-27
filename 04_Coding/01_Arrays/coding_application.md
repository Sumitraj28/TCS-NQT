# Arrays — Coding Application (Full Problem Solutions)

> **Programming Language: C++.**  
> Every solution includes: Problem Statement → Approach → C++ code (line-by-line) → Complexity.

---

## Problem 1 — Two Sum
**LeetCode:** #1 | **Difficulty:** Easy | **TCS Frequency:** High

### Problem Statement
Given an array of integers `nums` and a target integer `target`, return the indices of the two numbers such that they add up to `target`. Each input has exactly one solution; you may not use the same element twice.

**Example:** `nums = [2, 7, 11, 15]`, `target = 9` → Output: `[0, 1]`

### Approach
Use a hash map (`std::unordered_map`) to store each element and its index as we scan. For each new element, check if its complement (`target − element`) is already in the map. If yes, we found the pair in O(1).

### C++ Solution
```cpp
#include <vector>
#include <unordered_map>

class Solution {
public:
    std::vector<int> twoSum(std::vector<int>& nums, int target) {
        // Map: value → index seen so far
        std::unordered_map<int, int> seen;

        for (int i = 0; i < nums.size(); ++i) {
            int complement = target - nums[i];   // what we need to find

            if (seen.count(complement)) {       // complement already seen
                return {seen[complement], i};
            }

            seen[nums[i]] = i;                   // store current element
        }
        return {};                               // no solution fallback
    }
};
```

**Line-by-line Explanation:**
- `complement = target - nums[i]` — what we need the other number to be.
- `seen.count(complement)` — O(1) hash map lookup to check if we've seen it.
- `return {seen[complement], i}` — returns index of complement and current index.
- `seen[nums[i]] = i` — add current element to map after checking (prevents using same element twice).

### Complexity
- **Time Complexity:** O(n) — single pass.
- **Space Complexity:** O(n) — hash map storage.

---

## Problem 2 — Best Time to Buy and Sell Stock
**LeetCode:** #121 | **Difficulty:** Easy | **TCS Frequency:** High

### Problem Statement
You are given an array `prices` where `prices[i]` is the price of a stock on day `i`. You want to maximize profit by choosing one day to buy and one future day to sell. Return the maximum profit; if none, return 0.

**Example:** `prices = [7,1,5,3,6,4]` → Output: `5` (buy at 1, sell at 6)

### Approach
Track the minimum price seen so far as we scan left to right. At each day, compute potential profit = `price − minPrice`. Track the maximum such profit.

### C++ Solution
```cpp
#include <vector>
#include <algorithm>
#include <climits>

class Solution {
public:
    int maxProfit(std::vector<int>& prices) {
        int minPrice = INT_MAX;  // lowest price seen so far
        int maxProfit = 0;       // best profit found

        for (int price : prices) {
            if (price < minPrice) {
                minPrice = price; // found a cheaper buying day
            } else if (price - minPrice > maxProfit) {
                maxProfit = price - minPrice; // found a better selling opportunity
            }
        }
        return maxProfit;
    }
};
```

**Line-by-line Explanation:**
- `minPrice = INT_MAX` — sentinel so any first price updates it.
- `if (price < minPrice)` — update the best buy day.
- `else if (price - minPrice > maxProfit)` — calculate and compare today's profit.

### Complexity
- **Time Complexity:** O(n) — single pass.
- **Space Complexity:** O(1) — only tracking two variables.

---

## Problem 3 — Move Zeroes
**LeetCode:** #283 | **Difficulty:** Easy | **TCS Frequency:** High

### Problem Statement
Given an array `nums`, move all 0s to the end while maintaining the relative order of non-zero elements. Modify in-place.

**Example:** `nums = [0,1,0,3,12]` → Output: `[1,3,12,0,0]`

### Approach
Two-pointer (same direction): use `insertPos` to track where the next non-zero should go. Write all non-zeros first, then fill the rest with zeros.

### C++ Solution
```cpp
#include <vector>

class Solution {
public:
    void moveZeroes(std::vector<int>& nums) {
        int insertPos = 0;                         // position to write next non-zero

        // Pass 1: write all non-zero elements to the front
        for (int num : nums) {
            if (num != 0) {
                nums[insertPos++] = num;
            }
        }

        // Pass 2: fill remaining positions with zeros
        while (insertPos < nums.size()) {
            nums[insertPos++] = 0;
        }
    }
};
```

**Line-by-line Explanation:**
- `insertPos` acts as a slow pointer; the loop's iteration is the fast pointer.
- First loop compresses all non-zeros to the front.
- Second loop fills the tail with zeros.

### Complexity
- **Time Complexity:** O(n) — two sequential passes.
- **Space Complexity:** O(1) — modified in-place.

---

## Problem 4 — Contains Duplicate
**LeetCode:** #217 | **Difficulty:** Easy | **TCS Frequency:** High

### Problem Statement
Given an array `nums`, return `true` if any value appears at least twice, `false` if every element is distinct.

**Example:** `nums = [1,2,3,1]` → Output: `true`

### Approach
Use a hash set (`std::unordered_set`). For each element, if it's already in the set, return true. Otherwise, add it.

### C++ Solution
```cpp
#include <vector>
#include <unordered_set>

class Solution {
public:
    bool containsDuplicate(std::vector<int>& nums) {
        std::unordered_set<int> seen;

        for (int num : nums) {
            // insert returns a pair: {iterator, bool} where bool is false if element existed
            if (!seen.insert(num).second) {
                return true; // duplicate found
            }
        }
        return false;
    }
};
```

**Line-by-line Explanation:**
- `seen.insert(num).second` — returns `false` if `num` was already in the set.
- This is a one-liner check — insert and detect duplicate simultaneously.

### Complexity
- **Time Complexity:** O(n) average.
- **Space Complexity:** O(n) for the hash set.

---

## Problem 5 — Maximum Subarray
**LeetCode:** #53 | **Difficulty:** Medium | **TCS Frequency:** High

### Problem Statement
Given an integer array `nums`, find the subarray with the largest sum and return its sum.

**Example:** `nums = [-2,1,-3,4,-1,2,1,-5,4]` → Output: `6` (subarray `[4,-1,2,1]`)

### Approach (Kadane's Algorithm)
At each position: the best subarray ending here is either this element alone (start fresh) or extending the best subarray from the previous position. Take the max of both choices.

### C++ Solution
```cpp
#include <vector>
#include <algorithm>

class Solution {
public:
    int maxSubArray(std::vector<int>& nums) {
        int maxSum = nums[0];      // global maximum
        int currentSum = nums[0]; // max sum ending at current position

        for (size_t i = 1; i < nums.size(); ++i) {
            // Either extend previous subarray OR start fresh from nums[i]
            currentSum = std::max(nums[i], currentSum + nums[i]);

            // Update global maximum if current ending sum is larger
            maxSum = std::max(maxSum, currentSum);
        }
        return maxSum;
    }
};
```

**Line-by-line Explanation:**
- Start from index 1 because we initialized with `nums[0]`.
- `std::max(nums[i], currentSum + nums[i])` — if currentSum is negative, starting fresh is better.
- `std::max(maxSum, currentSum)` — track the best we've ever seen.

### Complexity
- **Time Complexity:** O(n) — single pass.
- **Space Complexity:** O(1) — only tracking two variables.

---

## Problem 6 — Merge Sorted Array
**LeetCode:** #88 | **Difficulty:** Easy | **TCS Frequency:** High

### Problem Statement
You have two sorted arrays `nums1` (with extra space for m+n elements; first m elements are real) and `nums2` (n elements). Merge `nums2` into `nums1` in-place, resulting in one sorted array.

**Example:** `nums1 = [1,2,3,0,0,0]` (m=3), `nums2 = [2,5,6]` (n=3) → Output: `[1,2,2,3,5,6]`

### Approach
Merge from the **right** to avoid overwriting values in `nums1`. Three pointers: `i` at last real element of nums1, `j` at last of nums2, `k` at the very end of nums1.

### C++ Solution
```cpp
#include <vector>

class Solution {
public:
    void merge(std::vector<int>& nums1, int m, std::vector<int>& nums2, int n) {
        int i = m - 1;          // last real element of nums1
        int j = n - 1;          // last element of nums2
        int k = m + n - 1;      // last position in nums1 (write position)

        // Compare from the right and fill from the right
        while (i >= 0 && j >= 0) {
            if (nums1[i] >= nums2[j]) {
                nums1[k--] = nums1[i--];   // nums1's element is larger
            } else {
                nums1[k--] = nums2[j--];   // nums2's element is larger
            }
        }

        // If nums2 still has elements (nums1 exhausted first)
        while (j >= 0) {
            nums1[k--] = nums2[j--];
        }
    }
};
```

**Line-by-line Explanation:**
- Start from the right: largest elements placed at the end first — no overwriting risk.
- `if (nums1[i] >= nums2[j])` — pick the bigger of the two right-end elements.
- The `while (j >= 0)` handles leftover nums2 elements.

### Complexity
- **Time Complexity:** O(m+n) — single pass over the elements.
- **Space Complexity:** O(1) — merged in-place.

---

## Problem 7 — Product of Array Except Self
**LeetCode:** #238 | **Difficulty:** Medium | **TCS Frequency:** High

### Problem Statement
Given an integer array `nums`, return an array `answer` where `answer[i]` is the product of all elements of `nums` except `nums[i]`. Solve without using division and in O(n) time.

**Example:** `nums = [1,2,3,4]` → Output: `[24,12,8,6]`

### Approach
Two passes: (1) Left pass — `result[i]` = product of all elements to the left of i. (2) Right pass — multiply `result[i]` by the product of all elements to the right of i (tracked in a running variable).

### C++ Solution
```cpp
#include <vector>

class Solution {
public:
    std::vector<int> productExceptSelf(std::vector<int>& nums) {
        int n = nums.size();
        std::vector<int> result(n, 1);

        // LEFT PASS: result[i] = product of nums[0..i-1]
        for (int i = 1; i < n; ++i) {
            result[i] = result[i - 1] * nums[i - 1];
        }

        // RIGHT PASS: multiply by product of nums[i+1..n-1]
        int rightProduct = 1;                    // running right-side product
        for (int i = n - 1; i >= 0; --i) {
            result[i] *= rightProduct;           // incorporate right side
            rightProduct *= nums[i];             // update for next iteration
        }

        return result;
    }
};
```

### Complexity
- **Time Complexity:** O(n) — two linear passes.
- **Space Complexity:** O(1) extra space (ignoring output vector).

---

## Problem 8 — Third Maximum Number
**LeetCode:** #414 | **Difficulty:** Easy | **TCS Frequency:** Medium

### Problem Statement
Given an integer array `nums`, return the **third distinct maximum**. If it does not exist, return the maximum.

**Example:** `nums = [3,2,1]` → Output: `1`; `nums = [1,2]` → Output: `2` (no third distinct)

### Approach
Track three distinct maximums (first, second, third) using `long long` to handle `INT_MIN` as a valid input.

### C++ Solution
```cpp
#include <vector>
#include <climits>

class Solution {
public:
    int thirdMax(std::vector<int>& nums) {
        long long first  = LLONG_MIN;
        long long second = LLONG_MIN;
        long long third  = LLONG_MIN;

        for (int num : nums) {
            long long n = num;

            // Skip if already accounted for
            if (n == first || n == second || n == third) continue;

            if (n > first) {
                third = second; second = first; first = n;    // shift down
            } else if (n > second) {
                third = second; second = n;                    // shift down
            } else if (n > third) {
                third = n;
            }
        }

        return (third == LLONG_MIN) ? first : third;
    }
};
```

### Complexity
- **Time Complexity:** O(n) — single pass.
- **Space Complexity:** O(1) — constant storage.

---

## Problem 9 — Majority Element
**LeetCode:** #169 | **Difficulty:** Easy | **TCS Frequency:** High

### Problem Statement
Given an array `nums` of size n, return the majority element — the element appearing more than ⌊n/2⌋ times. It is guaranteed to always exist.

**Example:** `nums = [2,2,1,1,1,2,2]` → Output: `2`

### Approach (Boyer-Moore Voting Algorithm)
Maintain a candidate and a count. When count reaches 0, change the candidate. The majority element always survives because it appears more than all others combined.

### C++ Solution
```cpp
#include <vector>

class Solution {
public:
    int majorityElement(std::vector<int>& nums) {
        int candidate = 0;   // current candidate
        int count = 0;       // vote count for candidate

        for (int num : nums) {
            if (count == 0) {
                candidate = num;   // reset candidate when votes run out
            }
            count += (num == candidate) ? 1 : -1;
        }

        return candidate;
    }
};
```

### Complexity
- **Time Complexity:** O(n) — single pass.
- **Space Complexity:** O(1).

---

## Problem 10 — Find All Numbers Disappeared in an Array
**LeetCode:** #448 | **Difficulty:** Easy | **TCS Frequency:** High

### Problem Statement
Given an array `nums` of n integers where each integer is in `[1, n]`, return all integers in `[1, n]` that do not appear in `nums`.

**Example:** `nums = [4,3,2,7,8,2,3,1]` → Output: `[5,6]`

### Approach (In-place sign marking — O(1) extra space)
For each value `v`, negate `nums[v-1]` to mark that `v` has been seen. After the pass, positions with positive values correspond to missing numbers.

### C++ Solution
```cpp
#include <vector>
#include <cmath>

class Solution {
public:
    std::vector<int> findDisappearedNumbers(std::vector<int>& nums) {
        // MARK PASS: negate nums[|num|-1] for each num seen
        for (int i = 0; i < nums.size(); ++i) {
            int idx = std::abs(nums[i]) - 1;   // convert value to 0-based index
            if (nums[idx] > 0) {
                nums[idx] = -nums[idx];        // mark as "seen" (negate)
            }
        }

        // COLLECT PASS: unmarked (positive) positions = missing numbers
        std::vector<int> result;
        for (int i = 0; i < nums.size(); ++i) {
            if (nums[i] > 0) {
                result.push_back(i + 1);       // i+1 is the missing number
            }
        }
        return result;
    }
};
```

### Complexity
- **Time Complexity:** O(n) — two linear passes.
- **Space Complexity:** O(1) extra space.

---

## Problem 11 — Sort Colors (Dutch National Flag)
**LeetCode:** #75 | **Difficulty:** Medium | **TCS Frequency:** High

### Problem Statement
Given an array `nums` with values 0, 1, or 2 (representing red, white, blue), sort them in-place so all 0s come first, then 1s, then 2s. Must use O(1) extra space and one pass.

**Example:** `nums = [2,0,2,1,1,0]` → Output: `[0,0,1,1,2,2]`

### Approach (Dutch National Flag — 3-way partition)
Three pointers: `low` (left boundary for 0s), `mid` (current element), `high` (right boundary for 2s).

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
                std::swap(nums[low++], nums[mid++]);
            } else if (nums[mid] == 1) {
                mid++;
            } else {
                // Do not increment mid here because swapped element is unexamined
                std::swap(nums[mid], nums[high--]);
            }
        }
    }
};
```

### Complexity
- **Time Complexity:** O(n) — single pass.
- **Space Complexity:** O(1) — in-place swaps.

---

## Problem 12 — Sort Array by Parity
**LeetCode:** #905 | **Difficulty:** Easy | **TCS Frequency:** Medium

### Problem Statement
Given an integer array `nums`, move all even integers to the beginning followed by all odd integers. Return any valid answer.

**Example:** `nums = [3,1,2,4]` → Output: `[2,4,3,1]` or `[4,2,3,1]` etc.

### Approach (Two Pointer — opposite ends)
Left pointer seeks odd numbers, right pointer seeks even numbers. Swap them.

### C++ Solution
```cpp
#include <vector>
#include <algorithm>

class Solution {
public:
    std::vector<int> sortArrayByParity(std::vector<int>& nums) {
        int left = 0;
        int right = nums.size() - 1;

        while (left < right) {
            while (left < right && nums[left] % 2 == 0) left++;
            while (left < right && nums[right] % 2 == 1) right--;

            if (left < right) {
                std::swap(nums[left++], nums[right--]);
            }
        }
        return nums;
    }
};
```

### Complexity
- **Time Complexity:** O(n) — single pass.
- **Space Complexity:** O(1) — modified in-place.

---

## Problem 13 — Minimum Absolute Difference
**LeetCode:** #1200 | **Difficulty:** Easy | **TCS Frequency:** Medium

### Problem Statement
Given an array of distinct integers `arr`, find all pairs with the minimum absolute difference. Return a list of all pairs `[a, b]` (a < b) in ascending order.

**Example:** `arr = [4,2,1,3]` → Output: `[[1,2],[2,3],[3,4]]`

### Approach
Sort the array. The minimum absolute difference must occur between adjacent elements in sorted order. Scan once to find the minimum, then scan again to collect all adjacent pairs with that difference.

### C++ Solution
```cpp
#include <vector>
#include <algorithm>

class Solution {
public:
    std::vector<std::vector<int>> minimumAbsDifference(std::vector<int>& arr) {
        std::sort(arr.begin(), arr.end());

        // PASS 1: find the minimum absolute difference
        int minDiff = 2e9;
        for (size_t i = 1; i < arr.size(); ++i) {
            minDiff = std::min(minDiff, arr[i] - arr[i - 1]);
        }

        // PASS 2: collect all adjacent pairs with that difference
        std::vector<std::vector<int>> result;
        for (size_t i = 1; i < arr.size(); ++i) {
            if (arr[i] - arr[i - 1] == minDiff) {
                result.push_back({arr[i - 1], arr[i]});
            }
        }
        return result;
    }
};
```

### Complexity
- **Time Complexity:** O(n log n) — due to sorting.
- **Space Complexity:** O(1) extra space (ignoring output vector).

---

## Problem 14 — Subarray Sum Equals K
**LeetCode:** #560 | **Difficulty:** Medium | **TCS Frequency:** High

### Problem Statement
Given an array of integers `nums` and an integer `k`, return the total number of contiguous subarrays whose sum equals `k`.

**Example:** `nums = [1,1,1]`, `k = 2` → Output: `2`

### Approach (Prefix Sum + Hash Map)
For each prefix sum `s`, if `(s - k)` was seen before, there exist subarrays ending at the current index with sum `k`. The count of such subarrays equals how many times `(s - k)` appeared as a prefix sum.

### C++ Solution
```cpp
#include <vector>
#include <unordered_map>

class Solution {
public:
    int subarraySum(std::vector<int>& nums, int k) {
        // Map: prefixSum → occurrence count
        std::unordered_map<int, int> prefixCount;
        prefixCount[0] = 1;    // empty prefix (sum=0) occurs once

        int sum = 0;     // running prefix sum
        int count = 0;   // total subarrays found

        for (int num : nums) {
            sum += num;

            if (prefixCount.count(sum - k)) {
                count += prefixCount[sum - k];
            }

            prefixCount[sum]++;
        }
        return count;
    }
};
```

### Complexity
- **Time Complexity:** O(n) — single pass.
- **Space Complexity:** O(n) — for hash map storage.
