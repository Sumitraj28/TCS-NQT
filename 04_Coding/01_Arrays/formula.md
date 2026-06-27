# Arrays — Time and Space Complexity Reference

## Core Operations

| Operation | Array (`int arr[n]`) | Vector (`std::vector<int>`) |
|-----------|--------------------|----------------------------|
| Access by index | O(1) | O(1) |
| Update by index | O(1) | O(1) |
| Append to end | N/A (fixed) | O(1) amortized |
| Insert at position i | O(n) | O(n) |
| Delete at position i | O(n) | O(n) |
| Search (unsorted) | O(n) | O(n) |
| Search (sorted, binary) | O(log n) | O(log n) |
| Sort | O(n log n) | O(n log n) |

---

## Pattern Complexity Summary

| Pattern | Time Complexity | Space Complexity | When to Use |
|---------|----------------|-----------------|-------------|
| Brute Force (nested loops) | O(n²) | O(1) | Never in exam if n > 1000 |
| Kadane's Algorithm | O(n) | O(1) | Max/min contiguous subarray |
| Prefix Sum (build) | O(n) | O(n) | Range queries, subarray sum |
| Prefix Sum (query) | O(1) after build | — | After O(n) pre-processing |
| Sliding Window (fixed k) | O(n) | O(1) | Fixed-size window operations |
| Sliding Window (variable) | O(n) | O(1) | Smallest/largest valid window |
| Two Pointer (sorted) | O(n) | O(1) | Pair sum, triplet sum |
| Two Pointer (same dir.) | O(n) | O(1) | Partition, move elements |
| Frequency Array | O(n + max_val) | O(max_val) | Count, find missing/duplicate |
| Hash Table approach | O(n) avg | O(n) | Two sum, subarray sum = k |
| Sorting + pointer | O(n log n) | O(1) | When order doesn't matter |
| Merge two sorted | O(m+n) | O(m+n) or O(1) in-place | Merge sorted arrays |
| Rotate (reverse method) | O(n) | O(1) | Rotation problems |
| Dutch National Flag | O(n) | O(1) | 3-way partition |

---

## Key Formulas

### Prefix Sum
```
prefix[0] = 0
prefix[i] = prefix[i-1] + nums[i-1]   (1-indexed prefix)
sum(l, r)  = prefix[r+1] - prefix[l]   (0-indexed l, r)
```

### Sliding Window — Fixed Size k
```
window_sum[0] = sum(nums[0..k-1])
window_sum[i] = window_sum[i-1] + nums[i+k-1] - nums[i-1]
```

### Rotation
```
Right rotate by k: effective rotation = k % n
Left rotate by k  = Right rotate by (n - k)
```

### Kadane's Recurrence
```
dp[i] = max(nums[i], dp[i-1] + nums[i])
answer = max(dp[0], dp[1], ..., dp[n-1])
```

### Subarray Count with Sum = k (using prefix sum + std::unordered_map)
```
For each index i:
  count += freq[prefixSum - k]
  freq[prefixSum]++
```

---

## Complexity Quick-Reference Table (One-Screen)

| n | O(n) OK? | O(n log n) OK? | O(n²) OK? |
|---|----------|---------------|-----------|
| 10⁸ | ✅ (marginal) | ❌ | ❌ |
| 10⁷ | ✅ | ❌ | ❌ |
| 10⁶ | ✅ | ✅ | ❌ |
| 10⁵ | ✅ | ✅ | ❌ |
| 10⁴ | ✅ | ✅ | ✅ (marginal) |
| 10³ | ✅ | ✅ | ✅ |

> In TCS NQT, typical constraints are n ≤ 10⁵. Always target O(n) or O(n log n).
