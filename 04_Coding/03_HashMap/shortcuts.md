# HashMap — Shortcuts (C++ STL)

Useful syntax tricks for `std::unordered_map` and `std::unordered_set` in C++ STL.

---

## 1. Checking Existence of a Key

```cpp
#include <unordered_map>

std::unordered_map<int, int> map;

// Method 1: Using .count() (cleanest)
// Returns 1 if key exists, 0 otherwise
if (map.count(key)) {
    // key exists
}

// Method 2: Using .find()
// Avoids double-lookup if you need to use the iterator immediately
auto it = map.find(key);
if (it != map.end()) {
    int value = it->second; // key exists
}
```

---

## 2. Insertion and Default Values

- Writing `map[key]++` automatically initializes `map[key]` to 0 (default constructor for `int`) if the key doesn't exist, and then increments it.
- **Set Insertion:** `set.insert(val)` returns `std::pair<iterator, bool>`, where the `bool` is `false` if `val` already existed in the set.

---

## 3. Initializing Map / Set from Ranges

```cpp
#include <vector>
#include <unordered_set>

std::vector<int> nums = {1, 2, 2, 3};

// Initialize set with elements from vector directly
std::unordered_set<int> uniqueNums(nums.begin(), nums.end()); // uniqueNums = {1, 2, 3}
```

---

## 4. Sorting a Map by Values

Maps are sorted by keys (if using `std::map`) or not sorted (if `std::unordered_map`). To sort a map by its values (e.g. finding elements sorted by frequency):
1. Copy map elements to a `std::vector<std::pair<KeyType, ValueType>>`.
2. Sort the vector using a custom comparator.

```cpp
#include <unordered_map>
#include <vector>
#include <algorithm>

std::vector<std::pair<int, int>> sortMapByValue(const std::unordered_map<int, int>& map) {
    std::vector<std::pair<int, int>> vec(map.begin(), map.end());
    
    // Sort descending by value (frequency)
    std::sort(vec.begin(), vec.end(), [](const auto& a, const auto& b) {
        return a.second > b.second;
    });
    return vec;
}
```

---

## 5. Frequency Count in One Line (C++20 range or classic)

```cpp
std::unordered_map<int, int> freq;
for (int x : nums) freq[x]++; // Classic one-liner loop body
```
*Implicit insertion makes frequency counting extremely short.*
```
