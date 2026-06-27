# HashMap — Complete Notes

## 1. Map and Set Types in C++ STL

C++ provides two main kinds of map and set structures:

### `std::unordered_map` and `std::unordered_set`
- **Underlying structure:** Hash Table.
- **Lookup/Insert/Delete:** O(1) average, O(N) worst-case (due to hash collisions).
- **Ordering:** Unordered.
- **When to use:** Default choice for speed. Preferred for frequency count, duplicate detection, and general lookups.

### `std::map` and `std::set`
- **Underlying structure:** Self-balancing Binary Search Tree (Red-Black Tree).
- **Lookup/Insert/Delete:** O(log N) guaranteed.
- **Ordering:** Kept sorted by key.
- **When to use:** When you need elements in sorted order, or range queries (like lower_bound on map keys).

---

## 2. Pattern 1 — Frequency Count

**Problem:** Count the occurrences of each element in an array.

```cpp
#include <unordered_map>
#include <vector>

std::unordered_map<int, int> countFrequencies(const std::vector<int>& arr) {
    std::unordered_map<int, int> freq;
    for (int num : arr) {
        freq[num]++; // inserts if absent (init to 0), then increments
    }
    return freq;
}
```

**Iterating through frequencies:**
```cpp
for (const auto& pair : freq) {
    int element = pair.first;
    int count = pair.second;
    // Process element and count
}
```

---

## 3. Pattern 2 — First Unique Character

**Problem:** Find the first non-repeating element in an array.

**Core idea:** Two passes. First pass builds the frequency map. Second pass traverses the array to find the first element whose frequency in the map is 1.

```cpp
#include <vector>
#include <unordered_map>

int firstUniqueElement(const std::vector<int>& arr) {
    std::unordered_map<int, int> freq;
    for (int num : arr) freq[num]++;
    
    for (int i = 0; i < arr.size(); ++i) {
        if (freq[arr[i]] == 1) return i;
    }
    return -1; // no unique element
}
```

---

## 4. Pattern 3 — Majority Element (>n/2)

**Problem:** Find the element that appears more than ⌊n/2⌋ times.

**HashMap Approach (O(N) space):**
```cpp
#include <vector>
#include <unordered_map>

int majorityElementMap(const std::vector<int>& nums) {
    std::unordered_map<int, int> count;
    int n = nums.size();
    for (int num : nums) {
        count[num]++;
        if (count[num] > n / 2) return num;
    }
    return -1;
}
```
*(Boyer-Moore Voting is O(1) space, but this is the classic HashMap approach).*

---

## 5. Pattern 4 — Array Intersection

**Problem:** Find elements common to two arrays.

### Intersection with Duplicates Allowed (LeetCode 350)
```cpp
#include <vector>
#include <unordered_map>

std::vector<int> intersect(std::vector<int>& nums1, std::vector<int>& nums2) {
    std::unordered_map<int, int> counts;
    for (int num : nums1) counts[num]++;
    
    std::vector<int> result;
    for (int num : nums2) {
        if (counts[num] > 0) {
            result.push_back(num);
            counts[num]--;
        }
    }
    return result;
}
```

### Unique Intersection Elements (LeetCode 349)
Use `std::unordered_set` for O(1) duplicate filter.
```cpp
#include <vector>
#include <unordered_set>

std::vector<int> intersection(std::vector<int>& nums1, std::vector<int>& nums2) {
    std::unordered_set<int> set1(nums1.begin(), nums1.end());
    std::unordered_set<int> resultSet;
    for (int num : nums2) {
        if (set1.count(num)) {
            resultSet.insert(num);
        }
    }
    return std::vector<int>(resultSet.begin(), resultSet.end());
}
```

---

## 6. Pattern 5 — Grouping by Key (Equivalence Classes)

**Problem:** Group anagrams together.

**Core idea:** For each string, sort its characters to create a "signature key". Put strings sharing the same signature key into a list stored in the map.

```cpp
#include <vector>
#include <string>
#include <unordered_map>
#include <algorithm>

std::vector<std::vector<std::string>> groupAnagrams(std::vector<std::string>& strs) {
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
*Signature keys group elements into buckets.*
