# HashMap — 5 Worked Examples

---

## Example 1 — Two Sum (HashMap O(N))

**Problem:** `nums = [3, 2, 4]`, `target = 6`. Find indices.

**Trace:**
- Initialize `seen` map.
- i=0 (num=3): `complement = 6 - 3 = 3`. `seen` doesn't have 3. Insert `seen[3] = 0`.
- i=1 (num=2): `complement = 6 - 2 = 4`. `seen` doesn't have 4. Insert `seen[2] = 1`.
- i=2 (num=4): `complement = 6 - 4 = 2`. `seen` HAS 2 (value is index 1) → Return `[1, 2]`.

**Result:** `[1, 2]`

**C++ Code Snippet:**
```cpp
#include <vector>
#include <unordered_map>

std::vector<int> twoSum(const std::vector<int>& nums, int target) {
    std::unordered_map<int, int> seen;
    for (int i = 0; i < nums.size(); ++i) {
        int complement = target - nums[i];
        if (seen.count(complement)) {
            return {seen[complement], i};
        }
        seen[nums[i]] = i;
    }
    return {};
}
```

---

## Example 2 — Intersection of Two Arrays (Unique)

**Problem:** `nums1 = [4,9,5]`, `nums2 = [9,4,9,8,4]`. Find intersection.

**Trace:**
1. Put all elements of `nums1` in a set: `s1 = {4, 5, 9}`.
2. Initialize `result` set.
3. Check `nums2` elements in `s1`:
   - 9: in `s1` → insert 9 into `result`.
   - 4: in `s1` → insert 4 into `result`.
   - 9: in `s1` → insert 9 into `result` (already exists).
   - 8: not in `s1`.
   - 4: in `s1` → insert 4 into `result` (already exists).
4. `result` set contains `{4, 9}`.

**Result:** `[4, 9]`

**C++ Code Snippet:**
```cpp
#include <vector>
#include <unordered_set>

std::vector<int> intersection(const std::vector<int>& nums1, const std::vector<int>& nums2) {
    std::unordered_set<int> s1(nums1.begin(), nums1.end());
    std::vector<int> result;
    for (int num : nums2) {
        if (s1.count(num)) {
            result.push_back(num);
            s1.erase(num);
        }
    }
    return result;
}
```

---

## Example 3 — Top K Frequent Elements

**Problem:** `nums = [1,1,1,2,2,3]`, `k = 2`. Find top 2 frequent.

**Trace:**
1. Count frequencies: `1 -> 3`, `2 -> 2`, `3 -> 1`.
2. Push pairs into bucket lists or use a min-heap.
   - Bucket array: index represents frequency count.
   - `bucket[3] = {1}`
   - `bucket[2] = {2}`
   - `bucket[1] = {3}`
3. Iterate from back of bucket array down to collect `k` elements:
   - index 3: collect `1` (k becomes 1).
   - index 2: collect `2` (k becomes 0).
4. Return `[1, 2]`.

**Result:** `[1, 2]`

**C++ Code Snippet:**
```cpp
#include <vector>
#include <unordered_map>
#include <algorithm>

std::vector<int> topKFrequent(const std::vector<int>& nums, int k) {
    std::unordered_map<int, int> count;
    for (int num : nums) count[num]++;
    
    int n = nums.size();
    std::vector<std::vector<int>> buckets(n + 1);
    for (const auto& pair : count) {
        buckets[pair.second].push_back(pair.first);
    }
    
    std::vector<int> result;
    for (int i = n; i >= 0 && result.size() < k; --i) {
        for (int num : buckets[i]) {
            result.push_back(num);
            if (result.size() == k) break;
        }
    }
    return result;
}
```

---

## Example 4 — Group Anagrams

**Problem:** `strs = ["eat", "tea", "tan", "ate", "nat", "bat"]`.

**Trace:**
- Initialize `groups` map: `unordered_map<string, vector<string>>`.
- "eat": sort key is "aet". Map: `{"aet": ["eat"]}`
- "tea": sort key is "aet". Map: `{"aet": ["eat", "tea"]}`
- "tan": sort key is "ant". Map: `{"aet": ["eat", "tea"], "ant": ["tan"]}`
- "ate": sort key is "aet". Map: `{"aet": ["eat", "tea", "ate"], ...}`
- "nat": sort key is "ant". Map: `{"ant": ["tan", "nat"], ...}`
- "bat": sort key is "abt". Map: `{"abt": ["bat"], ...}`
- Gather vectors: `[["eat", "tea", "ate"], ["tan", "nat"], ["bat"]]`.

**C++ Code Snippet:**
```cpp
#include <vector>
#include <string>
#include <unordered_map>
#include <algorithm>

std::vector<std::vector<std::string>> groupAnagrams(const std::vector<std::string>& strs) {
    std::unordered_map<std::string, std::vector<std::string>> groups;
    for (const std::string& s : strs) {
        std::string key = s;
        std::sort(key.begin(), key.end());
        groups[key].push_back(s);
    }
    
    std::vector<std::vector<std::string>> result;
    for (const auto& pair : groups) {
        result.push_back(pair.second);
    }
    return result;
}
```

---

## Example 5 — Subarray Sum Equals K

**Problem:** `nums = [1, 2, 3]`, `k = 3`.

**Trace:**
- Map: `{0: 1}`, `sum = 0`, `count = 0`.
- num=1: `sum = 1`. `need = 1 - 3 = -2`. Not in map. Map: `{0:1, 1:1}`.
- num=2: `sum = 3`. `need = 3 - 3 = 0`. Map HAS 0 (count=1) → `count = 1`. Map: `{0:1, 1:1, 3:1}`.
- num=3: `sum = 6`. `need = 6 - 3 = 3`. Map HAS 3 (count=1) → `count = 2`. Map: `{0:1, 1:1, 3:1, 6:1}`.

**Result:** 2

**C++ Code Snippet:**
```cpp
#include <vector>
#include <unordered_map>

int subarraySum(const std::vector<int>& nums, int k) {
    std::unordered_map<int, int> prefix;
    prefix[0] = 1;
    int sum = 0, count = 0;
    for (int num : nums) {
        sum += num;
        if (prefix.count(sum - k)) {
            count += prefix[sum - k];
        }
        prefix[sum]++;
    }
    return count;
}
```
