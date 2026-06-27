# Arrays — 5 Worked Examples

---

## Example 1 — Maximum Subarray Sum (Kadane's)

**Problem:** Given `nums = [-2, 3, -1, 5, -3, 2]`, find the maximum sum of a contiguous subarray.

**Pattern:** Kadane's Algorithm

**Step-by-step trace:**

| i | nums[i] | currentSum = max(nums[i], prev+nums[i]) | maxSum |
|---|---------|----------------------------------------|--------|
| 0 | -2 | max(-2, -) = **-2** | -2 |
| 1 | 3 | max(3, -2+3=1) = **3** | 3 |
| 2 | -1 | max(-1, 3-1=2) = **2** | 3 |
| 3 | 5 | max(5, 2+5=7) = **7** | 7 |
| 4 | -3 | max(-3, 7-3=4) = **4** | 7 |
| 5 | 2 | max(2, 4+2=6) = **6** | 7 |

**Answer: 7** (subarray `[3, -1, 5]`)

**Code:**
```cpp
#include <vector>
#include <algorithm>

int maxSubArray(std::vector<int>& nums) {
    int maxSum = nums[0], currentSum = nums[0];
    for (size_t i = 1; i < nums.size(); ++i) {
        currentSum = std::max(nums[i], currentSum + nums[i]);
        maxSum = std::max(maxSum, currentSum);
    }
    return maxSum;
}
```

---

## Example 2 — Subarray Sum Equals K

**Problem:** `nums = [1, 2, 3]`, `k = 3`. Count subarrays with sum exactly equal to 3.

**Pattern:** Prefix Sum + `std::unordered_map`

**Expected answer: 2** (subarrays `[1,2]` and `[3]`)

**Step-by-step trace:**
- Initialize: `map = {0:1}`, `sum = 0`, `count = 0`
- i=0, num=1: sum=1, need=sum−k=−2, map has no −2, count stays 0. Add sum=1: `map={0:1, 1:1}`
- i=1, num=2: sum=3, need=sum−k=0, map has 0 (count=1), count=1. Add sum=3: `map={0:1,1:1,3:1}`
- i=2, num=3: sum=6, need=sum−k=3, map has 3 (count=1), count=2. Add sum=6: `map={0:1,1:1,3:1,6:1}`

**Answer: 2** ✓

---

## Example 3 — Rotate Array Right by k

**Problem:** `nums = [1,2,3,4,5,6,7]`, rotate right by `k=3`.

**Pattern:** Three reverses

**Expected output:** `[5,6,7,1,2,3,4]`

**Steps:**
1. `k = 3 % 7 = 3`
2. Reverse entire array: `[7,6,5,4,3,2,1]`
3. Reverse first k=3 elements: `[5,6,7,4,3,2,1]`
4. Reverse remaining (index 3 to 6): `[5,6,7,1,2,3,4]` ✓

**Code:**
```cpp
#include <vector>
#include <algorithm>

void rotate(std::vector<int>& nums, int k) {
    k = k % nums.size();
    std::reverse(nums.begin(), nums.end());
    std::reverse(nums.begin(), nums.begin() + k);
    std::reverse(nums.begin() + k, nums.end());
}
```

---

## Example 4 — Two Pointer: Pair with Target Sum

**Problem:** `nums = [2, 7, 11, 15]` (sorted), find indices of two numbers that add to `target = 9`.

**Pattern:** Two Pointer (sorted array)

**Trace:**
- left=0 (val=2), right=3 (val=15): sum=17 > 9 → right--
- left=0 (val=2), right=2 (val=11): sum=13 > 9 → right--
- left=0 (val=2), right=1 (val=7): sum=9 == 9 → **FOUND** (indices 0, 1)

**Answer:** indices [0, 1], values [2, 7]

---

## Example 5 — Find All Disappeared Numbers (Frequency Array / In-Place Marking)

**Problem:** `nums = [4, 3, 2, 7, 8, 2, 3, 1]`. n=8. Find all numbers from 1 to 8 that are missing.

**Pattern:** In-place sign marking

**Step-by-step:**
Original: `[4, 3, 2, 7, 8, 2, 3, 1]`

For each num, mark index `|num|-1` as negative:
- num=4: mark idx=3 → `[4,3,2,-7,8,2,3,1]`
- num=3: mark idx=2 → `[4,3,-2,-7,8,2,3,1]`
- num=2: mark idx=1 → `[4,-3,-2,-7,8,2,3,1]`
- num=|-7|=7: mark idx=6 → `[4,-3,-2,-7,8,2,-3,1]`
- num=8: mark idx=7 → `[4,-3,-2,-7,8,2,-3,-1]`
- num=2: mark idx=1 (already negative, abs → same) → no change
- num=|-3|=3: mark idx=2 (already negative) → no change
- num=|-1|=1: mark idx=0 → `[-4,-3,-2,-7,8,2,-3,-1]`

After pass: `[-4,-3,-2,-7,8,2,-3,-1]`

Scan: indices where value > 0 → index 4 (value=8>0) and index 5 (value=2>0)
Missing numbers = index+1 = **5 and 6** ✓
