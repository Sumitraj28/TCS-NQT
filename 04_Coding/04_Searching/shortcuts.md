# Searching — Shortcuts (C++ STL)

## C++ Built-In Binary Search Functions

C++ STL provides powerful built-in binary search functions in the `<algorithm>` library that work on sorted vectors or arrays.

### 1. `std::binary_search`
Checks if the target exists in the sorted range. Returns `bool`.
```cpp
#include <algorithm>

bool found = std::binary_search(arr.begin(), arr.end(), target); // O(log n)
```

### 2. `std::lower_bound`
Returns an iterator pointing to the first element which is **greater than or equal to** target.
To get the index: subtract `arr.begin()`.
```cpp
#include <algorithm>

auto it = std::lower_bound(arr.begin(), arr.end(), target);
int idx = it - arr.begin(); // O(log n)
// If target is larger than all elements, returns arr.size()
```

### 3. `std::upper_bound`
Returns an iterator pointing to the first element which is **strictly greater than** target.
```cpp
#include <algorithm>

auto it = std::upper_bound(arr.begin(), arr.end(), target);
int idx = it - arr.begin(); // O(log n)
```

### 4. Count Occurrences of x in Sorted Vector
```cpp
int count = std::upper_bound(arr.begin(), arr.end(), x) - std::lower_bound(arr.begin(), arr.end(), x);
```

### 5. `std::equal_range`
Returns both lower_bound and upper_bound in a single call as a `std::pair`.
```cpp
auto range = std::equal_range(arr.begin(), arr.end(), target);
int count = range.second - range.first;
```

---

## Decide Binary Search vs Linear Search (30 seconds)

```
Is the array sorted?
├── YES → Can I express what I'm looking for as a monotone condition?
│         ├── YES → Binary Search (or its variant)
│         └── NO  → Linear Search (or Hash Table)
└── NO  → Linear Search (or sort first if n is small)

Is n > 1000 and I need to search often?
└── YES → Must use O(log n) binary search (or O(1) hash table)
```

---

## Template Cheat — Which Binary Search?

```
Searching for exact value      →  lo<=hi, hi=n-1, return mid or -1
First occurrence               →  lo<=hi, hi=n-1, result=mid; hi=mid-1 on match
Last occurrence                →  lo<=hi, hi=n-1, result=mid; lo=mid+1 on match
Lower bound (first >= x)       →  lo<hi,  hi=n,   if arr[mid]<x: lo=mid+1 else hi=mid
Upper bound (first > x)        →  lo<hi,  hi=n,   if arr[mid]<=x: lo=mid+1 else hi=mid
Peak element                   →  lo<hi,  hi=n-1, if arr[mid]<arr[mid+1]: lo=mid+1 else hi=mid
Answer space (min satisfying)  →  lo<hi,  hi=max, if feasible: hi=mid else lo=mid+1
```

---

## Fast Pattern Recognition in Exam

| Keyword / Phrase in Problem | Binary Search Variant |
|----------------------------|----------------------|
| "sorted array, find x" | Standard |
| "find first/last position of x in sorted array" | First/Last occurrence |
| "how many times does x appear" | upper_bound − lower_bound |
| "find the insert position" | Lower bound (`std::lower_bound`) |
| "find a peak" | Peak element binary search |
| "minimum possible maximum" | Answer-space binary search |
| "first bad version" / "first True" | Answer-space binary search |
| "search in rotated sorted array" | Modified binary search (check which half is sorted) |
