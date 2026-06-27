# Arrays — Quick Revision (Scan in Under 2 Minutes)

## 7 Core Patterns — One Line Each

| Pattern | When | C++ Idiom |
|---------|------|-----------|
| **Kadane's** | Max subarray sum | `curr = max(num, curr+num)` |
| **Prefix Sum** | Range queries, subarray sum=k | `pre[i] = pre[i-1] + nums[i-1]` |
| **Sliding Window (fixed)** | Max/sum of subarray size k | `sum += nums[r] - nums[r-k]` |
| **Sliding Window (variable)** | Smallest/largest valid window | `while(cond) shrink left` |
| **Two Pointer (sorted)** | Pair/triplet sum | `if sum<target: l++ else r--` |
| **Two Pointer (same dir)** | Partition, move elements | `insertPos` pattern |
| **Frequency / Hash Map** | Count, find missing/dup | `map[key]++` |

---

## Critical Fixes (Most Common Bugs)

- **Kadane's** → init `maxSum = nums[0]`, NOT 0
- **Rotation** → always `k = k % n` first
- **Sign marking** → always `std::abs(num) - 1` for index
- **Dutch flag** → do NOT increment `mid` when swapping with `high`
- **Prefix sum** → use `long long` if values×count can exceed 2×10⁹
- **Subarray sum=k** → count BEFORE putting in map

---

## Complexity Quick-Ref

| Approach | Time | Space |
|----------|------|-------|
| Brute force (nested) | O(n²) | O(1) |
| Kadane's | O(n) | O(1) |
| Prefix sum | O(n) | O(n) |
| Sliding window | O(n) | O(1) |
| Two pointer | O(n) | O(1) |
| Hash Map | O(n) avg | O(n) |
| Sort + two pointer | O(n log n) | O(1) |

---

## TCS Pattern Keywords → Solution

- "contiguous subarray max" → Kadane's
- "subarray sum = k" → Prefix + std::unordered_map
- "window of size k" → Fixed Sliding Window
- "pair with sum" (sorted) → Two Pointer; (unsorted) → Hash Map
- "sort 0s 1s 2s" → Dutch National Flag
- "missing in 1..n" → n(n+1)/2 − actual sum
- "find duplicate (1..n)" → XOR or sign marking
- "rotate array" → Triple reverse

---

## C++ One-Liners Worth Memorizing

```cpp
std::sort(arr.begin(), arr.end());                      // sort ascending
std::reverse(arr.begin(), arr.end());                   // reverse vector
int max = *std::max_element(arr.begin(), arr.end());    // find max
int sum = std::accumulate(arr.begin(), arr.end(), 0);   // find sum
std::fill(arr.begin(), arr.end(), -1);                  // fill with -1
```
