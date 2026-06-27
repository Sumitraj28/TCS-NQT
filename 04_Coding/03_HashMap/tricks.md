# HashMap — Tricks, Traps, and TCS-Specific Patterns

## Trap 1 — Implicit Insertion via Square Brackets `[]`

**The trap:** Accessing `map[key]` to check if a key exists. If the key is not in the map, the `[]` operator **implicitly inserts** the key with a default value (e.g. 0 for `int`), increasing the map's size.

**Fix:** Use `map.count(key)` or `map.find(key)` to check existence without inserting.

```cpp
// INCORRECT (inserts key with value 0 if absent):
if (map[key] == 0) { ... }

// CORRECT:
if (map.count(key) == 0) { ... }
```

---

## Trap 2 — Custom Keys in `std::unordered_map` (Hashing Trap)

**The trap:** Attempting to use `std::pair<int, int>` or `std::vector<int>` as a key in `std::unordered_map`. C++ standard library does **not** provide a default hash function for pairs or vectors, resulting in a compilation error.

**Fix:** 
- **Option 1:** Use `std::map` instead, which only requires the `<` operator (which is defined for pairs/vectors).
- **Option 2:** Define a custom hash structure for `std::unordered_map`. (Option 1 is faster to write in an exam).

```cpp
// COMPILES: std::map supports pairs
std::map<std::pair<int, int>, int> coordinatesMap;

// DOES NOT COMPILE (without custom hash):
std::unordered_map<std::pair<int, int>, int> coordinatesMap;
```

---

## Trap 3 — O(N) Worst Case in `std::unordered_map` (Hash Collisions)

**The trap:** In competitive environments, standard hash maps can be attacked or hit worst-case scenarios where all elements collide into the same bucket, turning insertion/lookup into O(N) time.

**Fix:** If you experience TLE with `std::unordered_map`, switch to `std::map` (guaranteed O(log N)) or reserve capacity using `map.reserve(1024)`.

---

## Trap 4 — Double Lookup Overhead

**The trap:** Writing `if (map.count(key)) return map[key];`. This performs the hash function calculation twice: once to check, and once to access.

**Fix:** Use `map.find()` to do a single lookup, and save the iterator:
```cpp
auto it = map.find(key);
if (it != map.end()) {
    return it->second; // single hash calculation
}
```

---

## TCS Pattern Recognition

| Question Pattern | HashMap Strategy |
|------------------|------------------|
| "Find elements appearing once" | Frequency Map |
| "Intersection of two arrays" | Set (for unique elements) or Map (with count tracking) |
| "Subarray sum equals K" | Prefix Sum + `std::unordered_map` mapping sum to count |
| "Longest subarray sum equals K" | Prefix Sum + `std::unordered_map` mapping sum to leftmost index |
| "Group Anagrams" | Sort string as key, group string list in map |
