# Sorting — Previous Year Style Questions

---

### PYQ1 — Minimum Platforms
**Difficulty:** Hard | **Time:** 180s | **TCS Frequency:** High

**Problem:** Given arrival and departure times of trains, find the minimum number of platforms needed at the station so that no train has to wait.

Input: `arr = [900, 940, 950, 1100, 1500, 1800]`, `dep = [910, 1200, 1120, 1130, 1900, 2000]`  
Output: 3

**C++ Solution:**
```cpp
#include <vector>
#include <algorithm>

int findPlatform(std::vector<int>& arr, std::vector<int>& dep) {
    std::sort(arr.begin(), arr.end());
    std::sort(dep.begin(), dep.end());
    
    int plat_needed = 1, result = 1;
    int i = 1, j = 0;
    
    while (i < arr.size() && j < dep.size()) {
        if (arr[i] <= dep[j]) {
            plat_needed++;
            i++;
        } else {
            plat_needed--;
            j++;
        }
        result = std::max(result, plat_needed);
    }
    return result;
}
```

---

### PYQ2 — Sort Array of 0s, 1s, and 2s
**Difficulty:** Easy | **Time:** 60s | **TCS Frequency:** High

**Problem:** Given an array containing only 0s, 1s, and 2s, sort it in O(N) time and O(1) space.

**C++ Solution:**
```cpp
#include <vector>
#include <algorithm>

void sort012(std::vector<int>& arr) {
    int low = 0, mid = 0, high = arr.size() - 1;
    while (mid <= high) {
        if (arr[mid] == 0) {
            std::swap(arr[low++], arr[mid++]);
        } else if (arr[mid] == 1) {
            mid++;
        } else {
            std::swap(arr[mid], arr[high--]);
        }
    }
}
```

---

### PYQ3 — Largest Number Formed from Array
**Difficulty:** Medium | **Time:** 120s | **TCS Frequency:** High

**Problem:** Arrange the given numbers to form the largest possible number.

Input: `[3, 30, 34, 5, 9]`  
Output: "9534330"

**C++ Solution:**
```cpp
#include <vector>
#include <string>
#include <algorithm>

std::string largestNumber(std::vector<int>& nums) {
    std::vector<std::string> strs;
    for (int num : nums) strs.push_back(std::to_string(num));
    
    std::sort(strs.begin(), strs.end(), [](const std::string& a, const std::string& b) {
        return a + b > b + a;
    });
    if (strs[0] == "0") return "0";
    std::string res = "";
    for (const auto& s : strs) res += s;
    return res;
}
```

---

### PYQ4 — Count Inversions
**Difficulty:** Hard | **Time:** 240s | **TCS Frequency:** Medium

**Problem:** Find the inversion count of an array.

Input: `arr = [2, 4, 1, 3, 5]`  
Output: 3

**C++ Solution:** Use the modified merge sort technique.

---

### PYQ5 — Minimum Swaps to Sort
**Difficulty:** Medium | **Time:** 120s | **TCS Frequency:** High

**Problem:** Find the minimum swaps needed to sort an unsorted array of distinct elements.

Input: `[4, 3, 2, 1]`  
Output: 2

**C++ Solution:** Use cycle decomposition on graph index positions.
```
