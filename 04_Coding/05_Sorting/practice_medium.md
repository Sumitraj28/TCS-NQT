# Sorting — Practice: Medium (15 Questions)

> No overlap with practice_basic.md

---

### Q1 — Sort Colors (Dutch National Flag)
**Difficulty:** Medium | **Time:** 90s | **TCS Frequency:** High

`nums = [2,0,2,1,1,0]`. Sort in-place.

**Full Solution:**
```cpp
#include <vector>
#include <algorithm>

void sortColors(std::vector<int>& nums) {
    int low = 0, mid = 0, high = nums.size() - 1;
    while (mid <= high) {
        if (nums[mid] == 0) {
            std::swap(nums[low++], nums[mid++]);
        } else if (nums[mid] == 1) {
            mid++;
        } else {
            std::swap(nums[mid], nums[high--]);
        }
    }
}
```

**Answer:** `[0,0,1,1,2,2]`

---

### Q2 — Kth Largest Element in an Array
**Difficulty:** Medium | **Time:** 90s | **TCS Frequency:** High

`nums = [3,2,1,5,6,4]`, k=2. Find the 2nd largest.

**Full Solution:**
Use `std::nth_element` to find the (n-k)th smallest element.
```cpp
#include <vector>
#include <algorithm>

int findKthLargest(std::vector<int>& nums, int k) {
    int n = nums.size();
    std::nth_element(nums.begin(), nums.begin() + n - k, nums.end());
    return nums[n - k];
}
```

**Answer:** 5

---

### Q3 — Merge Intervals
**Difficulty:** Medium | **Time:** 120s | **TCS Frequency:** High

`intervals = [[1,3],[2,6],[8,10],[15,18]]`.

**Full Solution:**
Sort by start time, then merge overlapping.
```cpp
#include <vector>
#include <algorithm>

std::vector<std::vector<int>> merge(std::vector<std::vector<int>>& intervals) {
    if (intervals.empty()) return {};
    std::sort(intervals.begin(), intervals.end());
    std::vector<std::vector<int>> merged;
    merged.push_back(intervals[0]);
    for (size_t i = 1; i < intervals.size(); ++i) {
        if (intervals[i][0] <= merged.back()[1]) {
            merged.back()[1] = std::max(merged.back()[1], intervals[i][1]);
        } else {
            merged.push_back(intervals[i]);
        }
    }
    return merged;
}
```

**Answer:** `[[1,6],[8,10],[15,18]]`

---

### Q4 — Intersection of Two Sorted Arrays
**Difficulty:** Medium | **Time:** 90s | **TCS Frequency:** High

`A = [1, 2, 2, 3, 4]`, `B = [2, 2, 4, 5]`. Find intersection.

**Full Solution (Two Pointers):**
```cpp
#include <vector>

std::vector<int> intersection(const std::vector<int>& A, const std::vector<int>& B) {
    std::vector<int> res;
    int i = 0, j = 0;
    while (i < A.size() && j < B.size()) {
        if (A[i] == B[j]) {
            if (res.empty() || res.back() != A[i]) res.push_back(A[i]);
            i++; j++;
        } else if (A[i] < B[j]) {
            i++;
        } else {
            j++;
        }
    }
    return res;
}
```

**Answer:** `[2, 4]`

---

### Q5 — Sort Array by Frequency
**Difficulty:** Medium | **Time:** 120s | **TCS Frequency:** Medium

`nums = [1, 1, 2, 2, 2, 3]`. Sort descending by frequency, ascending by value on tie.

**Full Solution (Custom Comparator):**
```cpp
#include <vector>
#include <unordered_map>
#include <algorithm>

std::vector<int> frequencySort(std::vector<int>& nums) {
    std::unordered_map<int, int> freq;
    for (int num : nums) freq[num]++;
    
    std::sort(nums.begin(), nums.end(), [&](int a, int b) {
        if (freq[a] != freq[b]) return freq[a] > freq[b]; // higher frequency first
        return a < b; // smaller value first
    });
    return nums;
}
```

**Answer:** `[2, 2, 2, 1, 1, 3]`

---

### Q6 — High-Frequency Custom Sorting
**Difficulty:** Medium | **Time:** 90s | **TCS Frequency:** Medium

Sort `arr = [5, 4, 3, 2, 1]` such that all odd numbers appear first sorted ascending, then all even numbers sorted descending.

**Full Solution:**
```cpp
#include <vector>
#include <algorithm>

void customSort(std::vector<int>& arr) {
    std::sort(arr.begin(), arr.end(), [](int a, int b) {
        if (a % 2 != 0 && b % 2 == 0) return true;  // odd before even
        if (a % 2 == 0 && b % 2 != 0) return false; // even after odd
        if (a % 2 != 0) return a < b;               // both odd: ascending
        return a > b;                               // both even: descending
    });
}
```

**Answer:** `[1, 3, 5, 4, 2]`

---

### Q7 — Minimum Swaps to Sort Unsorted Array
**Difficulty:** Medium | **Time:** 120s | **TCS Frequency:** High

`arr = [4, 3, 2, 1]`. Find min swaps.

**Full Solution (Graph cycle decomposition):**
```cpp
#include <vector>
#include <algorithm>

int minSwaps(std::vector<int>& arr) {
    int n = arr.size();
    std::vector<std::pair<int, int>> arrPos(n);
    for (int i = 0; i < n; i++) arrPos[i] = {arr[i], i};
    std::sort(arrPos.begin(), arrPos.end());
    
    std::vector<bool> visited(n, false);
    int swaps = 0;
    for (int i = 0; i < n; i++) {
        if (visited[i] || arrPos[i].second == i) continue;
        
        int cycle_size = 0;
        int j = i;
        while (!visited[j]) {
            visited[j] = true;
            j = arrPos[j].second;
            cycle_size++;
        }
        if (cycle_size > 0) swaps += (cycle_size - 1);
    }
    return swaps;
}
```

**Answer:** 2 swaps (swap 4 and 1, then swap 3 and 2)

---

### Q8 — Largest Number Formed from Array
**Difficulty:** Medium | **Time:** 120s | **TCS Frequency:** High

`arr = [3, 30, 34, 5, 9]`. Find largest number string.

**Full Solution:**
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

**Answer:** "9534330"

---

### Q9 — Relative Sort Array
**Difficulty:** Medium | **Time:** 120s | **TCS Frequency:** High

`A1 = [2,3,1,3,2,4,6,7,9,2,19]`, `A2 = [2,1,4,3,9,6]`. Sort A1 such that order matches A2. Rest at end sorted.

**Full Solution:**
```cpp
#include <vector>
#include <unordered_map>
#include <algorithm>

std::vector<int> relativeSortArray(std::vector<int>& A1, std::vector<int>& A2) {
    std::unordered_map<int, int> rank;
    for (int i = 0; i < A2.size(); i++) rank[A2[i]] = i;
    
    std::sort(A1.begin(), A1.end(), [&](int a, int b) {
        bool hasA = rank.count(a);
        bool hasB = rank.count(b);
        if (hasA && hasB) return rank[a] < rank[b];
        if (hasA) return true;
        if (hasB) return false;
        return a < b;
    });
    return A1;
}
```

**Answer:** `[2, 2, 2, 1, 4, 3, 3, 9, 6, 7, 19]`

---

### Q10 — Meeting Rooms (Can Person Attend All Meetings?)
**Difficulty:** Medium | **Time:** 90s | **TCS Frequency:** High

`intervals = [[0,30],[5,10],[15,20]]`.

**Full Solution:**
```cpp
#include <vector>
#include <algorithm>

bool canAttendMeetings(std::vector<std::vector<int>>& intervals) {
    std::sort(intervals.begin(), intervals.end());
    for (size_t i = 1; i < intervals.size(); i++) {
        if (intervals[i][0] < intervals[i-1][1]) return false;
    }
    return true;
}
```

**Answer:** false (overlap between [0,30] and [5,10])

---

### Q11 — Pancake Sorting
**Difficulty:** Medium | **Time:** 150s | **TCS Frequency:** Low

Given an array, sort it by reversing prefixes.

**Full Solution:**
For each step from n down to 1: find index of max element, reverse prefix to bring it to index 0, then reverse entire prefix of current size to bring it to its correct sorted position.

---

### Q12 — H-Index
**Difficulty:** Medium | **Time:** 120s | **TCS Frequency:** Medium

`citations = [3, 0, 6, 1, 5]`. Find H-index.

**Full Solution:**
Sort descending: `[6, 5, 3, 1, 0]`. Find last position i where `citations[i] >= i + 1`.
i=0: 6≥1; i=1: 5≥2; i=2: 3≥3; i=3: 1<4. H-Index = 3.

**Answer:** 3

---

### Q13 — Matrix Cells Distance Order
**Difficulty:** Medium | **Time:** 150s | **TCS Frequency:** Low

Sort cells by Manhattan distance to center cell. Use custom comparator.

---

### Q14 — Sorting Strings Alphabetically (Anagram Buckets)
**Difficulty:** Medium | **Time:** 120s | **TCS Frequency:** High

Group anagrams together from a list of strings.

**Full Solution:**
```cpp
#include <vector>
#include <string>
#include <unordered_map>
#include <algorithm>

std::vector<std::vector<std::string>> groupAnagrams(const std::vector<std::string>& strs) {
    std::unordered_map<std::string, std::vector<std::string>> map;
    for (std::string s : strs) {
        std::string t = s;
        std::sort(t.begin(), t.end());
        map[t].push_back(s);
    }
    std::vector<std::vector<std::string>> res;
    for (auto const& pair : map) res.push_back(pair.second);
    return res;
}
```

---

### Q15 — Sort List of Coordinates (Distance from Origin)
**Difficulty:** Medium | **Time:** 90s | **TCS Frequency:** Medium

Sort points `[[3,3],[5,-1],[1,1]]` by Euclidean distance to origin `[0,0]`.

**Full Solution:**
```cpp
#include <vector>
#include <algorithm>

void sortPoints(std::vector<std::vector<int>>& points) {
    std::sort(points.begin(), points.end(), [](const std::vector<int>& a, const std::vector<int>& b) {
        return (a[0]*a[0] + a[1]*a[1]) < (b[0]*b[0] + b[1]*b[1]);
    });
}
```

**Answer:** `[[1,1],[3,3],[5,-1]]` (distances squared: 2, 18, 26)
