# Searching — Complete Notes

## 1. Linear Search

**Concept:** Scan from left to right until target is found or array ends.

```cpp
#include <vector>

int linearSearch(const std::vector<int>& arr, int target) {
    for (int i = 0; i < arr.size(); ++i) {
        if (arr[i] == target) return i;
    }
    return -1; // not found
}
```

**Properties:**
- Works on any array (sorted or unsorted)
- Time: O(n) | Space: O(1)
- Best case: O(1) (target is at index 0)
- Worst case: O(n) (target is last or absent)

**When to use:**
- Array is unsorted
- Array is very small (n < 10)
- Searching for a condition (not just equality): first element > x, etc.

---

## 2. Binary Search

**Concept:** On a SORTED array, compare target with the middle element. Eliminate half the search space each step.

### Standard Template (Closed Interval [lo, hi])
```cpp
#include <vector>

int binarySearch(const std::vector<int>& arr, int target) {
    int lo = 0, hi = arr.size() - 1;

    while (lo <= hi) {
        int mid = lo + (hi - lo) / 2;   // avoids integer overflow vs (lo+hi)/2

        if (arr[mid] == target) return mid;
        else if (arr[mid] < target) lo = mid + 1;
        else hi = mid - 1;
    }
    return -1; // not found
}
```

**Why `lo + (hi - lo) / 2` not `(lo + hi) / 2`?**  
If lo and hi are both near `INT_MAX`, their sum overflows. The subtraction form is always safe.

**Properties:**
- Array MUST be sorted
- Time: O(log n) | Space: O(1)
- After each step, the search space halves

**Invariant:** Target, if present, is always in [lo, hi].

---

## 3. Lower Bound

**Definition:** The smallest index `i` such that `arr[i] >= target` (first position where target could be inserted while keeping array sorted).

```cpp
#include <vector>

int lowerBound(const std::vector<int>& arr, int target) {
    int lo = 0, hi = arr.size(); // hi = size (not size-1), can return n

    while (lo < hi) {            // strict < (not <=)
        int mid = lo + (hi - lo) / 2;
        if (arr[mid] < target) lo = mid + 1;
        else hi = mid;           // mid could be the answer
    }
    return lo;                   // first index with arr[i] >= target
}
```

**Why `hi = arr.size()` (not `size-1`)?** Because the lower bound can be beyond the last element (if target > all elements, return n).

**Example:** `arr = [1,3,3,5,7]`, target=3 → Lower bound = 1 (first 3 is at index 1).

---

## 4. Upper Bound

**Definition:** The smallest index `i` such that `arr[i] > target` (first position strictly after all occurrences of target).

```cpp
#include <vector>

int upperBound(const std::vector<int>& arr, int target) {
    int lo = 0, hi = arr.size();  // hi can be n

    while (lo < hi) {
        int mid = lo + (hi - lo) / 2;
        if (arr[mid] <= target) lo = mid + 1;  // note: <= (includes equal)
        else hi = mid;
    }
    return lo;                     // first index with arr[i] > target
}
```

**Example:** `arr = [1,3,3,5,7]`, target=3 → Upper bound = 3 (first element > 3 is at index 3, value=5).

**Count of occurrences of target in sorted array:**
```cpp
int count = upperBound(arr, target) - lowerBound(arr, target);
```

---

## 5. First and Last Occurrence

### First Occurrence
```cpp
#include <vector>

int firstOccurrence(const std::vector<int>& arr, int target) {
    int lo = 0, hi = arr.size() - 1, result = -1;

    while (lo <= hi) {
        int mid = lo + (hi - lo) / 2;
        if (arr[mid] == target) {
            result = mid;      // found, but keep searching LEFT
            hi = mid - 1;      // narrow to left half
        } else if (arr[mid] < target) lo = mid + 1;
        else hi = mid - 1;
    }
    return result;
}
```

### Last Occurrence
```cpp
#include <vector>

int lastOccurrence(const std::vector<int>& arr, int target) {
    int lo = 0, hi = arr.size() - 1, result = -1;

    while (lo <= hi) {
        int mid = lo + (hi - lo) / 2;
        if (arr[mid] == target) {
            result = mid;      // found, but keep searching RIGHT
            lo = mid + 1;      // narrow to right half
        } else if (arr[mid] < target) lo = mid + 1;
        else hi = mid - 1;
    }
    return result;
}
```

---

## 6. Binary Search on Answer Space

**Concept:** Instead of searching for a value IN an array, search for the optimal ANSWER within a range. If you can write a `bool feasible(mid)` function, you can binary search on the answer.

**Template:**
```cpp
int lo = minPossibleAnswer, hi = maxPossibleAnswer;
while (lo < hi) {
    int mid = lo + (hi - lo) / 2;
    if (feasible(mid)) hi = mid;      // if feasible, try smaller
    else lo = mid + 1;                // if not, increase
}
return lo;
```

**Examples:**
- "Find minimum capacity to ship all packages in D days"
- "Koko Eating Bananas — minimum eating speed"
- "First Bad Version" (simplified version of this)

---

## 7. Find Peak Element

A peak element is one that is greater than its neighbors. Binary search applies because if `arr[mid] < arr[mid+1]`, the right half must contain a peak (either mid+1 itself or further right).

```cpp
#include <vector>

int findPeakElement(const std::vector<int>& nums) {
    int lo = 0, hi = nums.size() - 1;

    while (lo < hi) {
        int mid = lo + (hi - lo) / 2;
        if (nums[mid] < nums[mid + 1]) lo = mid + 1;  // peak is on the right
        else hi = mid;                                 // peak is at mid or left
    }
    return lo;
}
```

---

## TCS-Specific Patterns

1. **"Search in sorted array"** → Standard binary search
2. **"Count of element x"** → upper_bound − lower_bound
3. **"First bad version"** → Binary search on answer (first True in a boolean sequence)
4. **"Find peak"** → Binary search on slope direction
5. **"Minimum maximum"** or "Maximum minimum"** → Binary search on answer space
6. **"Insert position"** → Lower bound
