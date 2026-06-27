# HashMap — Practice: Medium (15 Questions)

> No overlap with practice_basic.md

---

### Q1 — Subarray Sum Equals K
**Difficulty:** Medium | **Time:** 120s | **TCS Frequency:** High

`nums = [1, 1, 1]`, `k = 2`. Find total number of continuous subarrays with sum = k.

**Full Solution:**
```cpp
#include <vector>
#include <unordered_map>

int subarraySum(std::vector<int>& nums, int k) {
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
**Answer:** 2

---

### Q2 — Intersection of Two Arrays II
**Difficulty:** Medium | **Time:** 90s | **TCS Frequency:** High

`nums1 = [1,2,2,1]`, `nums2 = [2,2]`. Find elements common to both including duplicates.

**Full Solution:**
```cpp
#include <vector>
#include <unordered_map>

std::vector<int> intersect(std::vector<int>& nums1, std::vector<int>& nums2) {
    std::unordered_map<int, int> counts;
    for (int num : nums1) counts[num]++;
    std::vector<int> res;
    for (int num : nums2) {
        if (counts[num] > 0) {
            res.push_back(num);
            counts[num]--;
        }
    }
    return res;
}
```
**Answer:** `[2, 2]`

---

### Q3 — Top K Frequent Elements
**Difficulty:** Medium | **Time:** 120s | **TCS Frequency:** High

`nums = [1,1,1,2,2,3]`, `k = 2`. Find the 2 most frequent elements.

**Full Solution (Bucket Sort variant):**
```cpp
#include <vector>
#include <unordered_map>

std::vector<int> topKFrequent(std::vector<int>& nums, int k) {
    std::unordered_map<int, int> freq;
    for (int num : nums) freq[num]++;
    
    int n = nums.size();
    std::vector<std::vector<int>> buckets(n + 1);
    for (const auto& p : freq) {
        buckets[p.second].push_back(p.first);
    }
    
    std::vector<int> res;
    for (int i = n; i >= 0 && res.size() < k; --i) {
        for (int num : buckets[i]) {
            res.push_back(num);
            if (res.size() == k) break;
        }
    }
    return res;
}
```
**Answer:** `[1, 2]`

---

### Q4 — Group Anagrams
**Difficulty:** Medium | **Time:** 120s | **TCS Frequency:** High

`strs = ["eat", "tea", "tan", "ate", "nat", "bat"]`. Group together.

**Full Solution:** Group elements in a hash map using the sorted string as signature key.

**Answer:** `[["eat", "tea", "ate"], ["tan", "nat"], ["bat"]]`

---

### Q5 — Two Sum (O(N) Time)
**Difficulty:** Medium | **Time:** 75s | **TCS Frequency:** High

`nums = [2, 7, 11, 15]`, `target = 9`. Find indices of two numbers that add to target.

**Full Solution:**
```cpp
#include <vector>
#include <unordered_map>

std::vector<int> twoSum(std::vector<int>& nums, int target) {
    std::unordered_map<int, int> seen;
    for (int i = 0; i < nums.size(); i++) {
        int complement = target - nums[i];
        if (seen.count(complement)) return {seen[complement], i};
        seen[nums[i]] = i;
    }
    return {};
}
```
**Answer:** `[0, 1]`

---

### Q6 — First Unique Character in a String
**Difficulty:** Medium | **Time:** 75s | **TCS Frequency:** High

`s = "leetcode"`. Find index of first unique character.

**Full Solution:** frequency map + scan.
**Answer:** 0 (character 'l')

---

### Q7 — Majority Element (>n/2)
**Difficulty:** Medium | **Time:** 75s | **TCS Frequency:** High

`nums = [2,2,1,1,1,2,2]`. Find majority element.

**Full Solution:** Track frequency count. If any `count[x] > n/2`, return `x`.
**Answer:** 2

---

### Q8 — Set Matrix Zeroes
**Difficulty:** Medium | **Time:** 120s | **TCS Frequency:** High

`matrix = [[1,1,1],[1,0,1],[1,1,1]]`. If element is 0, set its entire row and column to 0.

**Full Solution (Tracking Rows/Cols using sets):**
```cpp
#include <vector>
#include <unordered_set>

void setZeroes(std::vector<std::vector<int>>& matrix) {
    std::unordered_set<int> zeroRows;
    std::unordered_set<int> zeroCols;
    int m = matrix.size(), n = matrix[0].size();
    
    for (int i = 0; i < m; ++i) {
        for (int j = 0; j < n; ++j) {
            if (matrix[i][j] == 0) {
                zeroRows.insert(i);
                zeroCols.insert(j);
            }
        }
    }
    for (int r : zeroRows) {
        for (int j = 0; j < n; ++j) matrix[r][j] = 0;
    }
    for (int c : zeroCols) {
        for (int i = 0; i < m; ++i) matrix[i][c] = 0;
    }
}
```
**Answer:** `[[1,0,1],[0,0,0],[1,0,1]]`

---

### Q9 — Find the Duplicate Number
**Difficulty:** Medium | **Time:** 90s | **TCS Frequency:** High

`nums = [1,3,4,2,2]`. Find duplicate (only one duplicate, size n+1, values in 1..n).

**Full Solution (Set insertion check):**
```cpp
#include <vector>
#include <unordered_set>

int findDuplicate(const std::vector<int>& nums) {
    std::unordered_set<int> seen;
    for (int num : nums) {
        if (!seen.insert(num).second) return num;
    }
    return -1;
}
```
**Answer:** 2

---

### Q10 — Contiguous Array (Equal 0s and 1s)
**Difficulty:** Medium | **Time:** 120s | **TCS Frequency:** High

`nums = [0, 1]`. Find maximum length of contiguous subarray with equal number of 0s and 1s.

**Full Solution (Prefix sum index map):**
Convert 0 to -1. Find longest subarray summing to 0.
```cpp
#include <vector>
#include <unordered_map>
#include <algorithm>

int findMaxLength(std::vector<int>& nums) {
    std::unordered_map<int, int> map;
    map[0] = -1;
    int sum = 0, maxLen = 0;
    for (int i = 0; i < nums.size(); ++i) {
        sum += (nums[i] == 0) ? -1 : 1;
        if (map.count(sum)) {
            maxLen = std::max(maxLen, i - map[sum]);
        } else {
            map[sum] = i;
        }
    }
    return maxLen;
}
```
**Answer:** 2

---

### Q11 — Top K Frequent Words
**Difficulty:** Medium | **Time:** 150s | **TCS Frequency:** Medium

`words = ["i","love","leetcode","i","love","coding"]`, k=2. Get top 2 frequent words (sort alphabetically on a tie).

**Full Solution:** Map count -> custom comparator sort.

**Answer:** `["i", "love"]`

---

### Q12 — Unique Number of Occurrences
**Difficulty:** Medium | **Time:** 90s | **TCS Frequency:** Medium

`arr = [1,2,2,1,1,3]`. Return true if number of occurrences of each value in array is unique.

**Full Solution:**
Build freq map: `{1:3, 2:2, 3:1}`. Check if values of map contain duplicate elements using set: values = `{3, 2, 1}` (no duplicates).

**Answer:** true

---

### Q13 — Find All Duplicates in an Array
**Difficulty:** Medium | **Time:** 90s | **TCS Frequency:** High

`arr = [4,3,2,7,8,2,3,1]`. Find all duplicates.

**Full Solution:** HashSet duplicate check.
**Answer:** `[2, 3]`

---

### Q14 — Subarray Sums Divisible by K
**Difficulty:** Medium | **Time:** 120s | **TCS Frequency:** High

`nums = [4, 5, 0, -2, -3, 1]`, `k = 5`. Count subarrays whose sum is divisible by 5.

**Full Solution (Prefix Sum Modulo Map):**
**Answer:** 7

---

### Q15 — Custom Key Sort (Rank Map)
**Difficulty:** Medium | **Time:** 90s | **TCS Frequency:** Medium

Given list of items, sort them by custom ranking mapping key to rank.
**Full Solution:** Use hash map lookup inside sort comparator.
```
