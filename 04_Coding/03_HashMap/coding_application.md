# HashMap — Coding Application (Full Problem Solutions)

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

### Complexity
- **Time Complexity:** O(N) — single pass.
- **Space Complexity:** O(N) — hash map storage.

---

## Problem 2 — Intersection of Two Arrays
**LeetCode:** #349 | **Difficulty:** Easy | **TCS Frequency:** High

### Problem Statement
Given two integer arrays `nums1` and `nums2`, return an array of their intersection. Each element in the result must be **unique** and you may return the result in **any order**.

**Example:** `nums1 = [1,2,2,1]`, `nums2 = [2,2]` → Output: `[2]`

### Approach
Insert all elements of `nums1` into a hash set (`std::unordered_set`) to remove duplicates. Iterate through `nums2`, checking if the element exists in the set. If yes, add to result and remove it from the set to avoid duplicate additions to the result.

### C++ Solution
```cpp
#include <vector>
#include <unordered_set>

class Solution {
public:
    std::vector<int> intersection(std::vector<int>& nums1, std::vector<int>& nums2) {
        // Build set of elements from nums1
        std::unordered_set<int> set1(nums1.begin(), nums1.end());
        std::vector<int> result;

        for (int num : nums2) {
            if (set1.count(num)) {
                result.push_back(num);
                set1.erase(num); // remove to prevent duplicates in result
            }
        }
        return result;
    }
};
```

### Complexity
- **Time Complexity:** O(N + M) — where N is size of nums1, M is size of nums2.
- **Space Complexity:** O(N) — set storage.

---

## Problem 3 — Top K Frequent Elements
**LeetCode:** #347 | **Difficulty:** Medium | **TCS Frequency:** High

### Problem Statement
Given an integer array `nums` and an integer `k`, return the `k` most frequent elements. You may return the answer in **any order**.

**Example:** `nums = [1,1,1,2,2,3]`, `k = 2` → Output: `[1, 2]`

### Approach
1. Build a frequency count map using `std::unordered_map`.
2. Use **Bucket Sort** concept: create an array of buckets where the index represents frequency count.
3. Group elements with identical frequencies into their corresponding bucket.
4. Iterate backward from the maximum possible frequency down to 0, collecting elements until `k` elements are gathered.

### C++ Solution
```cpp
#include <vector>
#include <unordered_map>

class Solution {
public:
    std::vector<int> topKFrequent(std::vector<int>& nums, int k) {
        std::unordered_map<int, int> freq;
        for (int num : nums) freq[num]++;

        int n = nums.size();
        // buckets: index represents frequency, contains elements with that frequency
        std::vector<std::vector<int>> buckets(n + 1);
        for (const auto& pair : freq) {
            buckets[pair.second].push_back(pair.first);
        }

        std::vector<int> result;
        // Traverse buckets from right to left (highest frequency first)
        for (int i = n; i >= 0 && result.size() < k; --i) {
            for (int num : buckets[i]) {
                result.push_back(num);
                if (result.size() == k) break;
            }
        }
        return result;
    }
};
```

### Complexity
- **Time Complexity:** O(N) — linear bucket traversal.
- **Space Complexity:** O(N) — bucket and frequency storage.

---

## Problem 4 — Group Anagrams
**LeetCode:** #49 | **Difficulty:** Medium | **TCS Frequency:** High

### Problem Statement
Given an array of strings `strs`, group the anagrams together. You can return the answer in **any order**.

**Example:** `strs = ["eat", "tea", "tan", "ate", "nat", "bat"]` → Output: `[["bat"],["nat","tan"],["ate","eat","tea"]]`

### Approach
Anagrams become identical when sorted. Sort each string to create a "signature key". Group the original strings into lists inside a map keyed by their sorted signatures.

### C++ Solution
```cpp
#include <vector>
#include <string>
#include <unordered_map>
#include <algorithm>

class Solution {
public:
    std::vector<std::vector<std::string>> groupAnagrams(std::vector<std::string>& strs) {
        // Map: sorted signature -> list of anagrams
        std::unordered_map<std::string, std::vector<std::string>> groups;

        for (const std::string& s : strs) {
            std::string key = s;
            std::sort(key.begin(), key.end()); // sort characters
            groups[key].push_back(s);          // group by signature
        }

        std::vector<std::vector<std::string>> result;
        for (const auto& pair : groups) {
            result.push_back(pair.second);
        }
        return result;
    }
};
```

### Complexity
- **Time Complexity:** O(N * L log L) — where N is string count, L is maximum string length.
- **Space Complexity:** O(N * L) — map storage.

---

## Problem 5 — Top K Frequent Words
**LeetCode:** #692 | **Difficulty:** Medium | **TCS Frequency:** High

### Problem Statement
Given an array of strings `words` and an integer `k`, return the `k` most frequent strings. Sort the words by their frequency from highest to lowest. Words with the same frequency should be sorted by their lexicographical order.

**Example:** `words = ["i","love","leetcode","i","love","coding"]`, `k = 2` → Output: `["i","love"]`

### Approach
1. Build a frequency count map of words.
2. Push all unique map entries into a vector.
3. Sort the vector using a custom comparator:
   - If frequencies are different, sort descending.
   - If frequencies are equal, sort lexicographically ascending.
4. Extract the first `k` words.

### C++ Solution
```cpp
#include <vector>
#include <string>
#include <unordered_map>
#include <algorithm>

class Solution {
public:
    std::vector<std::string> topKFrequent(std::vector<std::string>& words, int k) {
        std::unordered_map<std::string, int> freq;
        for (const std::string& w : words) freq[w]++;

        std::vector<std::pair<std::string, int>> entries(freq.begin(), freq.end());

        // Sort using custom comparator
        std::sort(entries.begin(), entries.end(), [](const auto& a, const auto& b) {
            if (a.second != b.second) {
                return a.second > b.second; // higher frequency first
            }
            return a.first < b.first;       // alphabetical tie-breaker
        });

        std::vector<std::string> result;
        for (int i = 0; i < k; ++i) {
            result.push_back(entries[i].first);
        }
        return result;
    }
};
```

### Complexity
- **Time Complexity:** O(U log U) — where U is unique words count.
- **Space Complexity:** O(U) — storage for unique words.

---

## Problem 6 — Set Matrix Zeroes
**LeetCode:** #73 | **Difficulty:** Medium | **TCS Frequency:** High

### Problem Statement
Given an `m x n` integer matrix, if an element is 0, set its entire row and column to 0's. Do it in-place.

**Example:** `matrix = [[1,1,1],[1,0,1],[1,1,1]]` → Output: `[[1,0,1],[0,0,0],[1,0,1]]`

### Approach
Use two sets: `zeroRows` and `zeroCols` to keep track of which rows and columns contain at least one 0. In a second pass, set rows and columns in the sets to 0.

### C++ Solution
```cpp
#include <vector>
#include <unordered_set>

class Solution {
public:
    void setZeroes(std::vector<std::vector<int>>& matrix) {
        std::unordered_set<int> zeroRows;
        std::unordered_set<int> zeroCols;
        int m = matrix.size();
        int n = matrix[0].size();

        // Pass 1: record indices containing zero
        for (int i = 0; i < m; ++i) {
            for (int j = 0; j < n; ++j) {
                if (matrix[i][j] == 0) {
                    zeroRows.insert(i);
                    zeroCols.insert(j);
                }
            }
        }

        // Pass 2: apply zeros to rows
        for (int r : zeroRows) {
            for (int j = 0; j < n; ++j) {
                matrix[r][j] = 0;
            }
        }

        // Pass 2: apply zeros to columns
        for (int c : zeroCols) {
            for (int i = 0; i < m; ++i) {
                matrix[i][c] = 0;
            }
        }
    }
};
```

### Complexity
- **Time Complexity:** O(M * N) — two passes over the matrix cells.
- **Space Complexity:** O(M + N) — set storage.

---

## Problem 7 — Find the Duplicate Number
**LeetCode:** #287 | **Difficulty:** Medium | **TCS Frequency:** High

### Problem Statement
Given an array of integers `nums` containing `n + 1` integers where each integer is in the range `[1, n]` inclusive. There is only one duplicate number in `nums`, return this duplicate number. Do not modify the array, and use O(1) extra space.

**Example:** `nums = [1,3,4,2,2]` → Output: `2`

### Approach (Floyd's Cycle Detection)
Treat the array values as pointers: index `i` points to element at `nums[i]`. Because there is a duplicate value, there must be a cycle. Find the cycle using fast and slow pointers, and then locate the entry node of the cycle (which is the duplicate number).

### C++ Solution
```cpp
#include <vector>

class Solution {
public:
    int findDuplicate(std::vector<int>& nums) {
        // Step 1: Detect intersection point of cycle
        int slow = nums[0];
        int fast = nums[0];

        do {
            slow = nums[slow];
            fast = nums[nums[fast]];
        } while (slow != fast);

        // Step 2: Find entry node of the cycle (duplicate value)
        int ptr1 = nums[0];
        int ptr2 = slow;

        while (ptr1 != ptr2) {
            ptr1 = nums[ptr1];
            ptr2 = nums[ptr2];
        }

        return ptr1;
    }
};
```

### Complexity
- **Time Complexity:** O(N) — linear traversal of the cycle.
- **Space Complexity:** O(1) — constant variables.

---

## Problem 8 — Contiguous Array
**LeetCode:** #525 | **Difficulty:** Medium | **TCS Frequency:** High

### Problem Statement
Given a binary array `nums`, return the maximum length of a contiguous subarray with an equal number of 0 and 1.

**Example:** `nums = [0,1]` → Output: `2`

### Approach
Convert all 0s in the array to -1. The problem then reduces to finding the longest subarray with a sum of 0. Map each prefix sum to its first occurrence index in a hash map. If a prefix sum repeats, the subarray between the two occurrences sums to 0.

### C++ Solution
```cpp
#include <vector>
#include <unordered_map>
#include <algorithm>

class Solution {
public:
    int findMaxLength(std::vector<int>& nums) {
        // Map: prefixSum -> leftmost index
        std::unordered_map<int, int> prefixIndex;
        prefixIndex[0] = -1; // base case for sum starting at index 0

        int sum = 0;
        int maxLen = 0;

        for (int i = 0; i < nums.size(); ++i) {
            // Treat 0 as -1, 1 as 1
            sum += (nums[i] == 0) ? -1 : 1;

            if (prefixIndex.count(sum)) {
                // If sum was seen before, compute subarray length
                maxLen = std::max(maxLen, i - prefixIndex[sum]);
            } else {
                // Record leftmost occurrence index
                prefixIndex[sum] = i;
            }
        }
        return maxLen;
    }
};
```

### Complexity
- **Time Complexity:** O(N) — single pass.
- **Space Complexity:** O(N) — prefix index map.
