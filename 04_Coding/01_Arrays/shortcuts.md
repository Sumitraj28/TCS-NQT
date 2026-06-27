# Arrays — Coding Shortcuts (C++ STL)

These are genuine time-savers in a 45-minute coding exam — C++ Standard Template Library (STL) features that replace 5–10 lines of code with 1.

---

## C++ STL Shortcuts

### Sort an array / vector
```cpp
#include <algorithm>

std::sort(arr.begin(), arr.end());                      // ascending, O(n log n)
std::sort(arr.rbegin(), arr.rend());                    // descending, O(n log n)
std::sort(arr.begin(), arr.end(), std::greater<int>()); // descending using greater comparator
```

### Copy a vector
```cpp
std::vector<int> copy = arr;                             // deep copy constructor
std::vector<int> partial(arr.begin() + l, arr.begin() + r); // [l, r) range copy
```

### Fill a vector / array
```cpp
std::fill(arr.begin(), arr.end(), 0);                   // fill all with 0
std::fill(arr.begin() + l, arr.begin() + r, -1);        // fill [l, r) with -1
```

### Max / Min of a vector (STL algorithms)
```cpp
#include <numeric>

int max_val = *std::max_element(arr.begin(), arr.end()); // returns iterator, dereference with *
int min_val = *std::min_element(arr.begin(), arr.end());
int sum = std::accumulate(arr.begin(), arr.end(), 0);    // sum of all elements, 3rd arg is init value
```

### Reverse a vector
```cpp
std::reverse(arr.begin(), arr.end());
```

### Frequency counting with `std::unordered_map`
```cpp
#include <unordered_map>

std::unordered_map<int, int> freq;
for (int num : arr) freq[num]++;
```

### Check if element exists in vector (Unsorted vs Sorted)
```cpp
// Unsorted: O(n)
bool exists = std::find(arr.begin(), arr.end(), target) != arr.end();

// Sorted: O(log n)
bool exists_sorted = std::binary_search(arr.begin(), arr.end(), target);
```

### Swap two elements
```cpp
std::swap(arr[i], arr[j]);
```

### Remove duplicates from sorted vector
```cpp
std::sort(arr.begin(), arr.end());
arr.erase(std::unique(arr.begin(), arr.end()), arr.end());
```

---

## Pattern Recognition Shortcuts (30-Second Decision Tree)

```
Question involves contiguous subarray?
├── Fixed size k          → Sliding Window (fixed)
├── Variable size         → Sliding Window (variable) or Prefix Sum
├── Maximum/minimum sum   → Kadane's
└── Count subarrays = k   → Prefix Sum + std::unordered_map

Question asks for a pair/triplet?
├── Array is sorted       → Two Pointer (opposite ends)
└── Array unsorted        → std::unordered_map O(n) or Sort first then Two Pointer

Question involves all elements in range [1..n]?
├── Find missing          → Expected sum − actual sum, OR frequency array
├── Find duplicate        → Frequency array, OR in-place sign marking
└── Both missing & dup    → In-place sign marking

Question needs partition?
├── 2 groups (even/odd)   → Two Pointer (same direction)
└── 3 groups (0,1,2)      → Dutch National Flag
```
