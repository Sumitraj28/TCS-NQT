# Sorting — Practice: Advanced / Prime Level (10 Questions)

> No overlap with basic or medium sets. Each includes a faster alternate method.

---

### Q1 — Count Inversions in an Array
**Difficulty:** Hard | **Time:** 240s | **TCS Frequency:** Medium

`arr = [2, 4, 1, 3, 5]`. Find number of pairs (i,j) where i < j and arr[i] > arr[j].

**Full Solution (Modified Merge Sort — O(n log n)):**
During the merge step, if `arr[i] > arr[j]`, then all remaining elements in the left sorted subarray (from index `i` to `mid`) are also greater than `arr[j]`. Add `(mid - i + 1)` to inversion count.

```cpp
#include <vector>

long long mergeAndCount(std::vector<int>& arr, std::vector<int>& temp, int left, int mid, int right) {
    int i = left, j = mid + 1, k = left;
    long long inv_count = 0;
    
    while (i <= mid && j <= right) {
        if (arr[i] <= arr[j]) {
            temp[k++] = arr[i++];
        } else {
            temp[k++] = arr[j++];
            inv_count += (mid - i + 1); // key logic
        }
    }
    while (i <= mid) temp[k++] = arr[i++];
    while (j <= right) temp[k++] = arr[j++];
    for (i = left; i <= right; i++) arr[i] = temp[i];
    return inv_count;
}

long long mergeSortAndCount(std::vector<int>& arr, std::vector<int>& temp, int left, int right) {
    long long inv_count = 0;
    if (left < right) {
        int mid = left + (right - left) / 2;
        inv_count += mergeSortAndCount(arr, temp, left, mid);
        inv_count += mergeSortAndCount(arr, temp, mid + 1, right);
        inv_count += mergeAndCount(arr, temp, left, mid, right);
    }
    return inv_count;
}
```

**Answer:** 3

**Alternate:** Fenwick Tree / Binary Indexed Tree O(n log n).

---

### Q2 — Kth Largest Element (Optimized QuickSelect)
**Difficulty:** Hard | **Time:** 180s | **TCS Frequency:** High

Implement QuickSelect to find Kth largest in O(N) average time.

**Full Solution:**
```cpp
#include <vector>
#include <algorithm>

int partition(std::vector<int>& nums, int left, int right) {
    int pivot = nums[right];
    int i = left;
    for (int j = left; j < right; j++) {
        if (nums[j] <= pivot) {
            std::swap(nums[i++], nums[j]);
        }
    }
    std::swap(nums[i], nums[right]);
    return i;
}

int quickSelect(std::vector<int>& nums, int left, int right, int k) {
    if (left == right) return nums[left];
    int pIdx = partition(nums, left, right);
    if (pIdx == k) return nums[pIdx];
    else if (pIdx < k) return quickSelect(nums, pIdx + 1, right, k);
    else return quickSelect(nums, left, pIdx - 1, k);
}
```

**Alternate:** Use `std::nth_element` which performs this exact logic built-in.

---

### Q3 — Maximum Gap (Bucket Sort concept)
**Difficulty:** Hard | **Time:** 240s | **TCS Frequency:** Low

`arr = [3,6,9,1]`. Find maximum difference between successive elements in sorted form in O(N) time.

**Full Solution (Pigeonhole / Bucket Principle):**
Create bucket min/max arrays of size N. Bucket size = `max(1, (maxVal - minVal) / (N - 1))`. Put elements in buckets. Max gap occurs between maximum of one non-empty bucket and minimum of next non-empty bucket.

**Answer:** 3 (gap between 3 and 6, or 6 and 9)

**Alternate:** Sort the array O(n log n) and scan consecutive diffs. O(N log N) time, simpler to code.

---

### Q4 — Count of Smaller Numbers After Self
**Difficulty:** Hard | **Time:** 300s | **TCS Frequency:** Low

`nums = [5,2,6,1]`. For each element, count how many elements to its right are smaller.

**Full Solution (Modified Merge Sort tracking indices):**
Keep track of original indices while sorting. When merging, if right subarray element is picked, increment a count of smaller elements. When left subarray element is picked, add that count to its original index accumulator.

**Answer:** `[2, 1, 1, 0]`

---

### Q5 — Reverse Pairs (LeetCode 493)
**Difficulty:** Hard | **Time:** 300s | **TCS Frequency:** Low

Find count of pairs (i, j) where i < j and arr[i] > 2 * arr[j].

**Full Solution:**
Modified Merge Sort. Before merging, count pairs by checking `arr[i] > 2LL * arr[j]`.

---

### Q6 — Sort List (Linked List sorting)
**Difficulty:** Hard | **Time:** 200s | **TCS Frequency:** Medium

Sort a singly linked list in O(N log N) time and O(1) auxiliary space.

**Full Solution:**
Bottom-up Merge Sort on linked list.

---

### Q7 — Minimum Initial Energy to Complete Tasks
**Difficulty:** Hard | **Time:** 240s | **TCS Frequency:** Low

Tasks have `[actual, minimum]`. Sort tasks to minimize initial energy.

**Full Solution:**
Sort tasks by `(minimum - actual)` descending.

---

### Q8 — Wiggle Sort II
**Difficulty:** Hard | **Time:** 300s | **TCS Frequency:** Low

Rearrange array to `nums[0] < nums[1] > nums[2] < nums[3]...`.

**Full Solution:**
Find median using QuickSelect O(N) time. Partition around median and interleave large and small values using Virtual Indexing.

---

### Q9 — Car Fleet
**Difficulty:** Hard | **Time:** 240s | **TCS Frequency:** Medium

Sort cars by starting position descending. Compute time to reach target. If a car behind takes less or equal time, it joins the fleet ahead.

---

### Q10 — Queue Reconstruction by Height
**Difficulty:** Hard | **Time:** 240s | **TCS Frequency:** Low

`people = [[7,0],[4,4],[7,1],[5,0],[6,1],[5,2]]`.

**Full Solution:**
Sort by height descending, then by `k` ascending. Insert into list at index `k`.
Sorted: `[7,0], [7,1], [6,1], [5,0], [5,2], [4,4]`.
Insertions:
- `[7,0]` at 0 → `[[7,0]]`
- `[7,1]` at 1 → `[[7,0], [7,1]]`
- `[6,1]` at 1 → `[[7,0], [6,1], [7,1]]`
...
**Answer:** `[[5,0],[7,0],[5,2],[6,1],[4,4],[7,1]]`
