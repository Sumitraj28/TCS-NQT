# HashMap — Complexity and Formulas

## C++ Map & Set Complexity Comparison

| Operation | `std::unordered_map` (Hash Table) | `std::map` (Red-Black Tree) |
|-----------|----------------------------------|-----------------------------|
| **Insert** | O(1) average / O(N) worst | O(log N) guaranteed |
| **Search** | O(1) average / O(N) worst | O(log N) guaranteed |
| **Delete** | O(1) average / O(N) worst | O(log N) guaranteed |
| **Space** | O(N) | O(N) |
| **Traversal Order** | Arbitrary | Sorted by key |

*Same complexities apply for `std::unordered_set` vs `std::set`.*

---

## Hash Collision & Load Factor Formulas

- **Load Factor ($\alpha$):** $\alpha = \frac{n}{k}$ where $n$ is number of elements, $k$ is number of buckets.
- If $\alpha$ exceeds a threshold (typically $1.0$ or $0.75$), the hash map performs a **rehash** operation (allocates more buckets and relocates elements) to maintain O(1) average time.
- **Worst-case O(N) search** happens when all $n$ elements hash to the same bucket (hash collision), creating a linked list of size $n$.

---

## Prefix Sum + HashMap Subarray Formulas

HashMap is critical for solving contiguous subarray problems.

### 1. Subarray Sum Equals K
Find number of contiguous subarrays summing to `k`.
- Let $S[i]$ be the prefix sum: $S[i] = \sum_{x=0}^{i} nums[x]$.
- Sum of subarray $nums[j..i]$ is $S[i] - S[j-1]$.
- We want: $S[i] - S[j-1] = k \implies S[j-1] = S[i] - k$.
- **Formula:** For each index $i$, check if prefix sum $(S[i] - k)$ exists in map. Count += map[$S[i] - k$].

---

### 2. Subarray Sum Divisible by K
Find number of contiguous subarrays whose sum is divisible by `k`.
- We want: $(S[i] - S[j-1]) \pmod k = 0 \implies S[i] \pmod k = S[j-1] \pmod k$.
- **Formula:** For each index $i$, compute remainder $rem = S[i] \pmod k$. Handle negative remainders: $rem = (rem + k) \pmod k$.
- Check if remainder $rem$ exists in map. Count += map[$rem$].

---

### 3. Longest Subarray with Sum = K
Find the maximum length of a subarray summing to `k`.
- Instead of keeping count of prefix sums, map the **first occurrence index** of each prefix sum: `map[prefixSum] = index`.
- **Formula:** If $(S[i] - k)$ exists in map, potential length = $i - map[S[i] - k]$. Track maximum. Do NOT update index if sum already exists (to maintain leftmost index).
