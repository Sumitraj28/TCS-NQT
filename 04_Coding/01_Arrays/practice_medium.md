# Arrays — Practice: Medium (15 Questions)

> **Tags:** Each question has Difficulty / Expected Time / TCS Frequency  
> No question overlaps with practice_basic.md

---

### Q1 — Two Sum (std::unordered_map)
**Difficulty:** Medium | **Time:** 90s | **TCS Frequency:** High

`nums = [3, 5, 2, 8, 1]`, target = 10. Find indices of two numbers adding to 10.

**Full Solution:**
- Use `std::unordered_map`: for each element, check if `target - element` is already in map.
- i=0, num=3: need=7, map empty, add {3:0}
- i=1, num=5: need=5, map has no 5, add {3:0, 5:1}
- i=2, num=2: need=8, map has no 8, add {3:0, 5:1, 2:2}
- i=3, num=8: need=2, map HAS 2 at index 2 → **return [2, 3]**

**Answer:** indices [2, 3] (values 2 and 8 sum to 10)

```cpp
#include <vector>
#include <unordered_map>

std::vector<int> twoSum(std::vector<int>& nums, int target) {
    std::unordered_map<int, int> map;
    for (int i = 0; i < nums.size(); ++i) {
        int complement = target - nums[i];
        if (map.count(complement)) return {map[complement], i};
        map[nums[i]] = i;
    }
    return {};
}
```

---

### Q2 — Maximum Subarray Sum (Kadane's)
**Difficulty:** Medium | **Time:** 90s | **TCS Frequency:** High

`nums = [-1, 4, -2, 3, -1, 1]`. Find the maximum subarray sum.

**Full Solution (Kadane's):**

| i | num | curr = max(num, prev+num) | maxSum |
|---|-----|--------------------------|--------|
| 0 | -1 | -1 | -1 |
| 1 | 4 | max(4, -1+4=3) = 4 | 4 |
| 2 | -2 | max(-2, 4-2=2) = 2 | 4 |
| 3 | 3 | max(3, 2+3=5) = 5 | 5 |
| 4 | -1 | max(-1, 5-1=4) = 4 | 5 |
| 5 | 1 | max(1, 4+1=5) = 5 | 5 |

**Answer:** 5 (subarray [4, -2, 3] or [4, -2, 3, -1, 1])

---

### Q3 — Best Time to Buy and Sell Stock
**Difficulty:** Medium | **Time:** 75s | **TCS Frequency:** High

`prices = [7, 1, 5, 3, 6, 4]`. Max profit from one buy-sell transaction?

**Full Solution:**
- Track `minPrice` as we scan left to right.
- At each day, profit = prices[i] − minPrice. Update maxProfit.

| i | price | minPrice | profit | maxProfit |
|---|-------|----------|--------|-----------|
| 0 | 7 | 7 | 0 | 0 |
| 1 | 1 | 1 | 0 | 0 |
| 2 | 5 | 1 | 4 | 4 |
| 3 | 3 | 1 | 2 | 4 |
| 4 | 6 | 1 | 5 | 5 |
| 5 | 4 | 1 | 3 | 5 |

**Answer:** 5 (buy at 1, sell at 6)

---

### Q4 — Move All Zeros to End
**Difficulty:** Medium | **Time:** 60s | **TCS Frequency:** High

`nums = [0, 1, 0, 3, 12]`. Move all zeros to end, maintain relative order of non-zeros.

**Full Solution (Two Pointer — same direction):**
- `insertPos = 0`. Scan array.
- Write every non-zero at insertPos, then fill rest with zeros.

Step 1: insertPos=0, pass 1: write 1→[1,1,0,3,12] pos=1; write 3→[1,3,0,3,12] pos=2; write 12→[1,3,12,3,12] pos=3.  
Step 2: fill zeros from pos=3 → [1,3,12,0,0]

**Answer:** `[1, 3, 12, 0, 0]`

---

### Q5 — Container With Most Water
**Difficulty:** Medium | **Time:** 120s | **TCS Frequency:** Medium

`height = [1, 8, 6, 2, 5, 4, 8, 3, 7]`. Max water between two vertical lines.

**Full Solution (Two Pointer):**
- Water = min(height[left], height[right]) × (right − left). Move the shorter side inward.

Key steps: l=0(h=1), r=8(h=7): water=min(1,7)×8=8. left is shorter→l++.
l=1(h=8), r=8(h=7): water=min(8,7)×7=49. right is shorter→r--.
...
**Max found = 49**

**Answer:** 49

---

### Q6 — Maximum Consecutive 1s
**Difficulty:** Medium | **Time:** 45s | **TCS Frequency:** High

`nums = [1,1,0,1,1,1,0,1]`. Find the length of the longest run of 1s.

**Full Solution:**
- Scan with `count = 0` and `maxCount = 0`.
- Increment count on 1; reset to 0 on 0; update max each step.

Trace: 1→1, 1→2, 0→0, 1→1, 1→2, 1→3, 0→0, 1→1. Max=3.

**Answer:** 3

---

### Q7 — Count Pairs with Sum Equal to Target
**Difficulty:** Medium | **Time:** 90s | **TCS Frequency:** High

`arr = [1, 5, 3, 7, 2, 5]`, target = 8. Count all pairs (i < j) with arr[i] + arr[j] = 8.

**Full Solution (std::unordered_map):**
- For each element, check if `target - element` has been seen. Count += freq[target-num]. Then add current num to freq.

Trace: seen={}
- 1: need 7, not seen. seen={1:1}
- 5: need 3, not seen. seen={1:1,5:1}
- 3: need 5, seen has 5 (count=1). count=1. seen={1:1,5:1,3:1}
- 7: need 1, seen has 1 (count=1). count=2. seen={...,7:1}
- 2: need 6, not seen. seen={...,2:1}
- 5: need 3, seen has 3 (count=1). count=3. seen={...,5:2}

**Answer:** 3 pairs: (1,7), (5,3), (3,5→second 5)

---

### Q8 — Minimum Size Subarray Sum ≥ Target
**Difficulty:** Medium | **Time:** 120s | **TCS Frequency:** Medium

`nums = [2, 3, 1, 2, 4, 3]`, target = 7. Find minimum length subarray with sum ≥ 7.

**Full Solution (Variable Sliding Window):**
- right pointer expands; left shrinks when sum ≥ target.

| right | left | sum | minLen |
|-------|------|-----|--------|
| 0 | 0 | 2 | INF |
| 1 | 0 | 5 | INF |
| 2 | 0 | 6 | INF |
| 3 | 0 | 8≥7 → shrink | 4; sum=6 |
| 4 | 1 | 9≥7 → shrink | 4; sum=6 → l=2, sum still… |

Final: minLen = 2 (subarray [4,3])

**Answer:** 2

---

### Q9 — Sort Array by Parity (Even Before Odd)
**Difficulty:** Medium | **Time:** 75s | **TCS Frequency:** Medium

`nums = [3, 1, 2, 4]`. Return array with all even numbers first, then odd.

**Full Solution (Two Pointer):**
- left starts at 0, right at end. Move left past evens, move right past odds. Swap when both stuck.
- l=0(3 odd), r=3(4 even): swap → [4,1,2,3], l=1, r=2.
- l=1(1 odd), r=2(2 even): swap → [4,2,1,3], l=2, r=1.
- l > r: done.

**Answer:** `[4, 2, 1, 3]`

---

### Q10 — Majority Element (>n/2)
**Difficulty:** Medium | **Time:** 90s | **TCS Frequency:** High

`nums = [3, 2, 3]`. Find the element appearing more than n/2 times.

**Full Solution (Boyer-Moore Voting):**
- candidate=3, count=1; num=2: count-- →0; num=3: count=0→candidate=3,count=1.
**Answer:** 3

---

### Q11 — Find All Duplicates
**Difficulty:** Medium | **Time:** 90s | **TCS Frequency:** High

`nums = [4,3,2,7,8,2,3,1]`. Find all elements appearing twice (values in [1,n]).

**Full Solution (In-place sign marking):**
- For each num, mark nums[|num|-1] negative. If it's already negative → it's a duplicate.

Process: 4→negate idx3; 3→negate idx2; 2→negate idx1; 7→negate idx6; 8→negate idx7; 2→idx1 already negative → **2 is duplicate**; 3→idx2 already negative → **3 is duplicate**; 1→negate idx0.

**Answer:** [2, 3]

---

### Q12 — Prefix Sum Range Query
**Difficulty:** Medium | **Time:** 75s | **TCS Frequency:** Medium

`nums = [1, 4, 2, 5, 3]`. Answer 3 range queries: sum(0,2), sum(1,3), sum(2,4).

**Full Solution:**
- Build prefix: [0, 1, 5, 7, 12, 15]
- sum(0,2) = prefix[3] - prefix[0] = 7 - 0 = 7
- sum(1,3) = prefix[4] - prefix[1] = 12 - 1 = 11
- sum(2,4) = prefix[5] - prefix[2] = 15 - 5 = 10

**Answers:** 7, 11, 10

---

### Q13 — Product of Array Except Self
**Difficulty:** Medium | **Time:** 120s | **TCS Frequency:** High

`nums = [1, 2, 3, 4]`. Return array where `result[i]` = product of all elements except `nums[i]`.

**Full Solution (Left×Right pass, no division):**
Left pass (result[i] = product of all elements to the left):
- result = [1, 1, 2, 6]

Right pass (multiply by product of all elements to the right):
- rightProd=1; i=3: result[3]*=1=6, rightProd=4
- i=2: result[2]*=4=8, rightProd=12
- i=1: result[1]*=12=12, rightProd=24
- i=0: result[0]*=24=24, rightProd=24

**Answer:** `[24, 12, 8, 6]`

---

### Q14 — Longest Subarray with Sum Divisible by k
**Difficulty:** Medium | **Time:** 150s | **TCS Frequency:** Medium

`nums = [2, 7, 6, 1, 4, 5]`, k = 3. Find length of longest subarray with sum divisible by 3.

**Full Solution (Prefix Sum + Modulo std::unordered_map):**
- Store first occurrence of each remainder.
- map = {0: -1}; sum=0

| i | num | sum | rem | map check | maxLen |
|---|-----|-----|-----|-----------|--------|
| 0 | 2 | 2 | 2 | not in map, store {2:0} | 0 |
| 1 | 7 | 9 | 0 | in map at -1, len=1-(-1)=2 | 2 |
| 2 | 6 | 15 | 0 | in map at -1, len=3-(-1)=4 | 4 |
| 3 | 1 | 16 | 1 | not in map, store {1:3} | 4 |
| 4 | 4 | 20 | 2 | in map at 0, len=4-0=4 | 4 |
| 5 | 5 | 25 | 1 | in map at 3, len=5-3=2 | 4 |

**Answer:** 4 (subarray [2,7,6,1] or [7,6,1,4])

---

### Q15 — Subarray Sum Equals K (with Negatives)
**Difficulty:** Medium | **Time:** 120s | **TCS Frequency:** High

`nums = [1, -1, 5, -2, 3]`, k = 3. Count subarrays with sum = 3.

**Full Solution (Prefix Sum + std::unordered_map):**
- map={0:1}, sum=0, count=0

| i | num | sum | need=sum-k | count |
|---|-----|-----|-----------|-------|
| 0 | 1 | 1 | -2: not in map | 0 |
| 1 | -1 | 0 | -3: not in map | 0 |
| 2 | 5 | 5 | 2: not in map | 0 |
| 3 | -2 | 3 | 0: in map (count=1) | 1 |
| 4 | 3 | 6 | 3: in map (count=1 from step above) | 2 |

**Answer:** 2 subarrays: [1,-1,5,-2] (sum=3) and [5,-2,3] (sum=6... wait let me recheck)

Recheck: sum=3 at i=3 → subarray [1,-1,5,-2] (indices 0..3) = 3 ✓  
sum=6 at i=4, need=3, map has prefix_sum=3 at i=3 → subarray [3] (indices 4..4) = 3 ✓

**Answer:** 2
