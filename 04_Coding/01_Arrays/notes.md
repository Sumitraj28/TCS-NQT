# Arrays — Complete Notes

## What Is an Array?

An array is a contiguous block of memory storing elements of the same type, accessed by zero-based index.
In C++: 
- Fixed size: `int arr[n];` or `std::array<int, n> arr;` — allocated on stack.
- Dynamic size: `std::vector<int> arr(n);` — allocated on heap, supports O(1) random access, and amortized O(1) append.

**Key properties:**
- Random access: O(1)
- Insert/Delete at end: O(1) amortized (for `std::vector`)
- Insert/Delete at arbitrary position: O(n) — elements must shift
- Search (unsorted): O(n)
- Search (sorted): O(log n) with binary search

---

## Pattern 1 — Kadane's Algorithm (Maximum Subarray)

**Problem:** Find the contiguous subarray with the largest sum.

**Core idea:** At each position, decide: is it better to extend the current subarray, or start fresh from this element?

```cpp
#include <vector>
#include <algorithm>

int maxSubArray(const std::vector<int>& nums) {
    int maxSum = nums[0], currentSum = nums[0];
    for (size_t i = 1; i < nums.size(); ++i) {
        currentSum = std::max(nums[i], currentSum + nums[i]);
        maxSum = std::max(maxSum, currentSum);
    }
    return maxSum;
}
```

**Why it works:** `currentSum + nums[i]` extends the subarray. `nums[i]` alone starts fresh. We keep whichever is larger — this is optimal by induction.

**Variants:**
- Maximum product subarray: track both max and min (negatives flip sign)
- Circular maximum subarray: max(Kadane's result, total_sum − Kadane's on negated array)

---

## Pattern 2 — Prefix Sum

**Problem:** Answer multiple range-sum queries efficiently.

**Core idea:** Build an auxiliary array where `prefix[i] = nums[0] + nums[1] + ... + nums[i-1]`.
Then sum of range [l, r] = `prefix[r+1] - prefix[l]` in O(1).

```cpp
std::vector<int> prefix(n + 1, 0);
for (int i = 0; i < n; ++i) {
    prefix[i + 1] = prefix[i] + nums[i];
}
// Sum from index l to r (0-indexed, inclusive):
int rangeSum = prefix[r + 1] - prefix[l];
```

**TCS use case:** Subarray sum equals K — use `std::unordered_map` of prefix sums to count in O(n).

```cpp
#include <unordered_map>

int subarraySum(const std::vector<int>& nums, int k) {
    std::unordered_map<int, int> prefix_map;
    prefix_map[0] = 1;
    int sum = 0, count = 0;
    for (int num : nums) {
        sum += num;
        if (prefix_map.count(sum - k)) {
            count += prefix_map[sum - k];
        }
        prefix_map[sum]++;
    }
    return count;
}
```

---

## Pattern 3 — Sliding Window

**Problem:** Find the maximum/minimum/sum of a subarray of fixed size k, or find the smallest window satisfying a condition.

**Fixed window (size k):**
```cpp
// Step 1: Build first window
int windowSum = 0;
for (int i = 0; i < k; ++i) windowSum += nums[i];
int maxSum = windowSum;
// Step 2: Slide — add right, remove left
for (size_t i = k; i < nums.size(); ++i) {
    windowSum += nums[i] - nums[i - k];
    maxSum = std::max(maxSum, windowSum);
}
```

**Variable window (shrink when condition violated):**
```cpp
int left = 0, windowSum = 0, minLen = 1e9;
for (int right = 0; right < nums.size(); ++right) {
    windowSum += nums[right];
    while (windowSum >= target) {
        minLen = std::min(minLen, right - left + 1);
        windowSum -= nums[left++];
    }
}
```

**When to use sliding window:**
- Contiguous subarray / substring question
- Fixed or bounded window size
- All elements are non-negative (for variable window with sum condition)

---

## Pattern 4 — Two Pointer

**Problem:** Find a pair/triplet with given sum, or partition an array in-place.

**Opposite ends (sorted array):**
```cpp
int left = 0, right = nums.size() - 1;
while (left < right) {
    int sum = nums[left] + nums[right];
    if (sum == target) { /* found */ break; }
    else if (sum < target) left++;
    else right--;
}
```

**Same direction (fast/slow pointers):**
```cpp
// Move zeroes to end
int insertPos = 0;
for (int i = 0; i < nums.size(); ++i) {
    if (nums[i] != 0) nums[insertPos++] = nums[i];
}
while (insertPos < nums.size()) nums[insertPos++] = 0;
```

**When to use two pointer:**
- Array is sorted (or can be sorted)
- Looking for pair/triplet with given sum/difference
- Partitioning (even/odd, sort colors, move zeroes)

---

## Pattern 5 — Frequency Array (Counting Sort Concept)

**Problem:** Count occurrences of elements when values are bounded.

```cpp
// If values are in range [0, max_val]
std::vector<int> freq(max_val + 1, 0);
for (int num : nums) freq[num]++;
// freq[x] = number of times x appears
```

**Use cases:**
- Find missing numbers (freq[i] == 0 means i is missing)
- Find duplicates (freq[i] > 1)
- Sort by frequency
- Sort Colors (Dutch National Flag is a variant)

**In-place marking trick (O(1) space):**
```cpp
// For array with values in [1, n], use sign as a visited marker
for (int i = 0; i < nums.size(); ++i) {
    int idx = std::abs(nums[i]) - 1;
    if (nums[idx] > 0) nums[idx] = -nums[idx]; // mark as visited
}
// After loop: nums[i] > 0 means (i+1) was not visited → missing
```

---

## Pattern 6 — Rotate Array

**Rotate right by k positions:** The last k elements become the first k.

**Reverse-based approach (O(1) space):**
```cpp
// Rotate right by k
k = k % nums.size(); // handle k > n
std::reverse(nums.begin(), nums.end());
std::reverse(nums.begin(), nums.begin() + k);
std::reverse(nums.begin() + k, nums.end());
```

**Why it works:**
Original: `[1,2,3,4,5,6,7]`, rotate right by 3 → `[5,6,7,1,2,3,4]`
- Reverse all → `[7,6,5,4,3,2,1]`
- Reverse first 3 → `[5,6,7,4,3,2,1]`
- Reverse rest → `[5,6,7,1,2,3,4]` ✓

---

## Pattern 7 — Merge Arrays

**Merge two sorted arrays into one sorted array (extra space):**
```cpp
int i = 0, j = 0, k = 0;
while (i < m && j < n) {
    result[k++] = (A[i] <= B[j]) ? A[i++] : B[j++];
}
while (i < m) result[k++] = A[i++];
while (j < n) result[k++] = B[j++];
```

**Merge sorted array in-place (from right — LeetCode 88):**
```cpp
// Place elements from the back to avoid overwriting
int i = m-1, j = n-1, k = m+n-1;
while (i >= 0 && j >= 0)
    nums1[k--] = (nums1[i] >= nums2[j]) ? nums1[i--] : nums2[j--];
while (j >= 0) nums1[k--] = nums2[j--];
```

---

## Dutch National Flag (Sort Colors — 3-way partition)

```cpp
int low = 0, mid = 0, high = n - 1;
while (mid <= high) {
    if (nums[mid] == 0)      { std::swap(nums[low++], nums[mid++]); }
    else if (nums[mid] == 1) { mid++; }
    else                     { std::swap(nums[mid], nums[high--]); }
}
```

---

## TCS-Specific Patterns to Watch For

1. **"Find pairs with sum X"** → Two pointer (sorted) or std::unordered_map
2. **"Maximum/minimum subarray"** → Kadane's
3. **"Sum of elements between indices L and R"** → Prefix sum
4. **"Window of size k"** → Sliding window
5. **"Remove/move specific elements"** → Two pointer (same direction)
6. **"Count frequency / find missing"** → Frequency array
7. **"Sort 0s, 1s, 2s"** → Dutch National Flag
