# HashMap — Practice: Advanced / Prime Level (10 Questions)

> No overlap with basic or medium sets. Each includes a faster alternate method.

---

### Q1 — Continuous Subarray Sum (Multiple of K)
**Difficulty:** Hard | **Time:** 180s | **TCS Frequency:** Medium

`nums = [23, 2, 4, 6, 7]`, `k = 6`. Find if there is a contiguous subarray of size at least 2 that sums to a multiple of k.

**Full Solution (Prefix sum remainder index map):**
```cpp
#include <vector>
#include <unordered_map>

bool checkSubarraySum(std::vector<int>& nums, int k) {
    std::unordered_map<int, int> remMap;
    remMap[0] = -1;
    int sum = 0;
    
    for (int i = 0; i < nums.size(); ++i) {
        sum += nums[i];
        int rem = sum % k;
        if (remMap.count(rem)) {
            if (i - remMap[rem] >= 2) return true;
        } else {
            remMap[rem] = i;
        }
    }
    return false;
}
```
**Answer:** true (subarray `[2, 4]` sums to 6)

---

### Q2 — Subarray Sum Equals K (Negative Numbers)
**Difficulty:** Hard | **Time:** 120s | **TCS Frequency:** High

`nums = [1, -1, 0]`, `k = 0`. Find total subarrays with sum = 0.

**Full Solution:**
```cpp
#include <vector>
#include <unordered_map>

int subarraySumZero(std::vector<int>& nums, int k) {
    std::unordered_map<int, int> prefix;
    prefix[0] = 1;
    int sum = 0, count = 0;
    for (int num : nums) {
        sum += num;
        if (prefix.count(sum - k)) count += prefix[sum - k];
        prefix[sum]++;
    }
    return count;
}
```
**Answer:** 3 (subarrays: `[-1,0]`, `[0]`, `[1,-1,0]`)

---

### Q3 — First Unique Character (Optimized Stream logic)
**Difficulty:** Hard | **Time:** 180s | **TCS Frequency:** Medium

Implement a stream data structure that accepts characters and reports the first unique character.

**Full Solution (DLL + HashMap):**
Maintain a doubly-linked list of unique characters and a map pointing to the list node. If a character is seen again, remove it from list.

---

### Q4 — Set Matrix Zeroes (Space-Optimized O(1) space)
**Difficulty:** Hard | **Time:** 200s | **TCS Frequency:** High

Solve Set Matrix Zeroes using O(1) extra space.

**Full Solution:** Use the first row and first column of the matrix itself as markers instead of separate sets.

---

### Q5 — Find the Duplicate Number (O(1) space, O(N) time)
**Difficulty:** Hard | **Time:** 180s | **TCS Frequency:** High

Solve Find the Duplicate Number without modifying the array and in O(1) space.

**Full Solution (Floyd's Cycle Detection):**
Treat array indices as linked list pointers.
```cpp
int findDuplicateCycle(const std::vector<int>& nums) {
    int slow = nums[0], fast = nums[0];
    do {
        slow = nums[slow];
        fast = nums[nums[fast]];
    } while (slow != fast);
    
    int p1 = nums[0], p2 = slow;
    while (p1 != p2) {
        p1 = nums[p1];
        p2 = nums[p2];
    }
    return p1;
}
```

---

### Q6 — Subarrays with K Different Integers
**Difficulty:** Hard | **Time:** 240s | **TCS Frequency:** Low

`nums = [1,2,1,2,3]`, `k = 2`. Find number of subarrays with exactly k different integers.

**Full Solution:**
`exact(K) = atMost(K) - atMost(K-1)`. Compute `atMost` using sliding window.

**Answer:** 7

---

### Q7 — Longest Consecutive Sequence
**Difficulty:** Hard | **Time:** 180s | **TCS Frequency:** High

`nums = [100, 4, 200, 1, 3, 2]`. Find length of longest consecutive sequence in O(N) time.

**Full Solution:**
```cpp
#include <vector>
#include <unordered_set>
#include <algorithm>

int longestConsecutive(const std::vector<int>& nums) {
    std::unordered_set<int> s(nums.begin(), nums.end());
    int maxLen = 0;
    
    for (int num : nums) {
        if (!s.count(num - 1)) { // sequence start
            int curr = num;
            int len = 1;
            while (s.count(curr + 1)) {
                curr++;
                len++;
            }
            maxLen = std::max(maxLen, len);
        }
    }
    return maxLen;
}
```
**Answer:** 4 (sequence `[1, 2, 3, 4]`)

---

### Q8 — Max Points on a Line
**Difficulty:** Hard | **Time:** 240s | **TCS Frequency:** Low

Find max points on a line using slopes map.

---

### Q9 — Subarray Product Less Than K
**Difficulty:** Hard | **Time:** 150s | **TCS Frequency:** Low

Find count of contiguous subarrays whose product is strictly less than k. Use sliding window.

---

### Q10 — Fraction to Recurring Decimal
**Difficulty:** Hard | **Time:** 240s | **TCS Frequency:** Low

Convert fraction to decimal representation. If recurring, wrap inside parenthesis.
Use map to track fractional remainder positions.
