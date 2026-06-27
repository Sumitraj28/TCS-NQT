# HashMap — Quick Revision

## C++ Map & Set Types

| STL Type | Structure | Time Complexity (Avg) | Time Complexity (Worst) | Ordered |
|----------|-----------|------------------------|-------------------------|---------|
| `std::unordered_map` | Hash Table | O(1) | O(N) | No |
| `std::map` | Red-Black Tree | O(log N) | O(log N) | Yes (by key) |
| `std::unordered_set` | Hash Table | O(1) | O(N) | No |
| `std::set` | Red-Black Tree | O(log N) | O(log N) | Yes (by value) |

---

## 5 Essential Patterns

### 1. Count Frequencies
`freq[x]++;` (implicitly initializes to 0 and increments).

### 2. Check Existence
`if (map.count(key))` or `if (map.find(key) != map.end())`.

### 3. Duplicate Detection
`if (!set.insert(x).second)` -> duplicate found.

### 4. Subarray Sum = K
```cpp
prefixCount[0] = 1;
sum += num;
count += prefixCount[sum - k];
prefixCount[sum]++;
```

### 5. Longest Subarray Sum = K
```cpp
prefixIndex[0] = -1;
sum += num;
if (prefixIndex.count(sum - k)) maxLen = max(maxLen, i - prefixIndex[sum - k]);
if (!prefixIndex.count(sum)) prefixIndex[sum] = i;
```

---

## Core Mistakes to Avoid
1. **Never use `map[key] == 0` for checks** — implicitly inserts. Use `count()`.
2. **Never use `std::unordered_map` with pair keys** — compile crash. Use `std::map`.
3. **Always seed prefix maps** with `{0: 1}` or `{0: -1}` before subarray loops.
