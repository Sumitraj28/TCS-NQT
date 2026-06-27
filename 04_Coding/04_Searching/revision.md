# Searching — Quick Revision

## Template Selector (30 seconds)

| Use Case | lo | hi | Loop | On Match | Return |
|----------|----|----|------|----------|--------|
| Exact match | 0 | n-1 | `<=` | `return mid` | mid or -1 |
| First occurrence | 0 | n-1 | `<=` | `result=mid; hi=mid-1` | result |
| Last occurrence | 0 | n-1 | `<=` | `result=mid; lo=mid+1` | result |
| Lower bound | 0 | n | `<` | `hi=mid` | lo |
| Upper bound | 0 | n | `<` | `lo=mid+1` | lo |
| Peak element | 0 | n-1 | `<` | (slope check) | lo |
| Answer space | lo=min | hi=max | `<` | `hi=mid` or `lo=mid+1` | lo |

## 3 Critical Rules
1. **Mid:** Always `lo + (hi - lo) / 2`
2. **Bounds need hi = n** (not n-1)
3. **hi = mid**, not hi = mid-1, for bounds and peak (don't exclude potential answer)

## Complexities
| Search | Time | Space |
|--------|------|-------|
| Linear | O(n) | O(1) |
| Binary | O(log n) | O(1) |
| Lower/Upper Bound | O(log n) | O(1) |

## C++ STL One-Liners
```cpp
#include <algorithm>

bool found = std::binary_search(arr.begin(), arr.end(), x);
int lb = std::lower_bound(arr.begin(), arr.end(), x) - arr.begin();
int ub = std::upper_bound(arr.begin(), arr.end(), x) - arr.begin();
int count = ub - lb;
```
