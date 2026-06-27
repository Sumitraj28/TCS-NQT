# HashMap — Previous Year Style Questions (TCS NQT)

---

### PYQ1 — Find Pairs with Given Sum
**Difficulty:** Medium | **Time:** 90s | **TCS Frequency:** High

**Problem:** Find all pairs in an array that sum to a given number.

Input: `arr = [1, 5, 7, -1, 5]`, `sum = 6`  
Output: 3 pairs (1,5), (7,-1), (1,5)

**C++ Solution:**
```cpp
#include <vector>
#include <unordered_map>

int countPairsWithSum(const std::vector<int>& arr, int target) {
    std::unordered_map<int, int> seen;
    int count = 0;
    for (int num : arr) {
        int complement = target - num;
        if (seen.count(complement)) {
            count += seen[complement];
        }
        seen[num]++;
    }
    return count;
}
```

---

### PYQ2 — Find Elements with Frequency K
**Difficulty:** Easy | **Time:** 60s | **TCS Frequency:** High

**Problem:** Find all elements in an array that appear exactly k times.

Input: `arr = [1, 2, 1, 3, 4, 2]`, `k = 2`  
Output: `[1, 2]`

**C++ Solution:** Build frequency map, filter keys with value = k.

---

### PYQ3 — Non-Overlapping Elements Sum
**Difficulty:** Easy | **Time:** 60s | **TCS Frequency:** Medium

**Problem:** Find the sum of all elements that are unique in two arrays combined (excluding elements present in both).

Input: `A = [5, 4, 9, 2]`, `B = [5, 1, 9, 3]`  
Output: 10 (4 + 2 + 1 + 3)

**C++ Solution:** Build sets, sum elements present in one set but not the other.

---

### PYQ4 — Count Subarrays with Sum = 0
**Difficulty:** Medium | **Time:** 90s | **TCS Frequency:** High

**Problem:** Count total contiguous subarrays whose sum equals 0.

Input: `arr = [1, -1, 2, -2]`  
Output: 4 (subarrays `[1,-1]`, `[2,-2]`, `[1,-1,2,-2]`, `[-1,2,-2]` ? Wait: 1-1=0, 2-2=0, 1-1+2-2=0, wait: index 1 to 3 is -1+2-2=-1 not 0.
Correct: `[1,-1]`, `[2,-2]`, `[1,-1,2,-2]`. Total = 3 subarrays.

---

### PYQ5 — Distinct Element in Windows
**Difficulty:** Hard | **Time:** 180s | **TCS Frequency:** Medium

**Problem:** Find count of distinct elements in every sliding window of size k.

Input: `arr = [1, 2, 1, 3, 4, 2, 3]`, `k = 4`  
Output: `[3, 4, 4, 3]`

**C++ Solution:**
```cpp
#include <vector>
#include <unordered_map>

std::vector<int> countDistinct(const std::vector<int>& arr, int k) {
    std::unordered_map<int, int> map;
    std::vector<int> result;
    for (int i = 0; i < k; ++i) map[arr[i]]++;
    result.push_back(map.size());
    
    for (size_t i = k; i < arr.size(); ++i) {
        map[arr[i]]++;
        if (--map[arr[i - k]] == 0) map.erase(arr[i - k]);
        result.push_back(map.size());
    }
    return result;
}
```
```
