# HashMap — Common Mistakes (8 Specific Traps)

---

### Mistake 1 — Implicit Key Insertion
Checking key existence using `if (map[key] == 0)`. If the key doesn't exist, the `[]` operator implicitly inserts the key with a default value of 0, expanding the map size and consuming extra memory.
**Fix:** Check existence with `if (map.count(key))` or `if (map.find(key) != map.end())`.

---

### Mistake 2 — Using `std::unordered_map` with Custom Keys (compile crash)
Trying to use `std::pair<int, int>` or `std::vector<int>` as a key in `std::unordered_map`. C++ does not provide a default hash function for pairs or vectors, resulting in compile-time errors.
**Fix:** Use `std::map` instead, which only requires the `<` operator (predefined for pairs and vectors).

---

### Mistake 3 — Inefficient Double Lookups
Writing `if (map.count(key)) return map[key];`. This calculates the hash of the key twice.
**Fix:** Perform a single search using `find` and store the iterator:
```cpp
auto it = map.find(key);
if (it != map.end()) return it->second;
```

---

### Mistake 4 — Modifying Keys During Map Iteration
Changing the key value of a map element during a loop. Modifying a key corrupts the map's internal data structure (hash bucket placement or BST ordering).
**Fix:** To rename/modify a key, erase the old key-value pair and insert a new one.

---

### Mistake 5 — Incorrect Prefix Sum Map Initial State
In subarray problems (like Subarray Sum = K), forgetting to seed the map with `{0: 1}` or `{0: -1}`. Without it, subarrays that start at index 0 and sum to K will not be detected.
**Fix:** Always initialize: `prefixCount[0] = 1;` (for counting) or `prefixIndex[0] = -1;` (for length).

---

### Mistake 6 — Updating Leftmost Index in Longest Subarray Sum
In finding the longest subarray with sum K, writing `prefixIndex[sum] = i` even if `sum` has been seen before. This overwrites the leftmost index, reducing the calculated length of future matching subarrays.
**Fix:** Only insert if the sum is **not** in the map:
```cpp
if (prefixIndex.count(sum) == 0) {
    prefixIndex[sum] = i;
}
```

---

### Mistake 7 — Comparing Map Iterators of Different Maps
Using iterators from one map to compare against limits of another map (e.g. `it != map2.end()`). Leads to undefined behavior and runtime crashes.
**Fix:** Keep track of which iterator belongs to which map.

---

### Mistake 8 — Assuming Hash Maps have constant time guarantee in worst-case
Assuming `std::unordered_map` is always O(1). If a lot of hash collisions occur, lookups degrade to O(N).
**Fix:** Use `std::map` (O(log N) worst case guaranteed) if N is large and you encounter TLE.
