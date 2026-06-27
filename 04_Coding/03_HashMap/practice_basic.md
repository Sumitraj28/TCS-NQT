# HashMap — Practice: Basic (15 Questions)

> Tags: Difficulty / Expected Time / TCS Frequency

---

### Q1 — Declare HashMap in C++
**Difficulty:** Easy | **Time:** 15s | **TCS Frequency:** High
How do you declare an unordered hash map with integer keys and values in C++?
**Answer:** `std::unordered_map<int, int> map;`

---

### Q2 — Check Key Existence
**Difficulty:** Easy | **Time:** 20s | **TCS Frequency:** High
What is the cleanest way to check if key `5` exists in `std::unordered_map<int, int> map`?
**Answer:** `map.count(5)` (returns 1 if exists, 0 if not).

---

### Q3 — Map Insertion
**Difficulty:** Easy | **Time:** 15s | **TCS Frequency:** High
How do you associate value `10` with key `2` in `map`?
**Answer:** `map[2] = 10;`

---

### Q4 — Count Unique Elements
**Difficulty:** Easy | **Time:** 30s | **TCS Frequency:** High
How to find the number of unique elements in a vector `v` using a set?
**Answer:** `std::unordered_set<int> s(v.begin(), v.end()); return s.size();`

---

### Q5 — Map Erase Key
**Difficulty:** Easy | **Time:** 20s | **TCS Frequency:** Medium
How do you remove key `3` from `map`?
**Answer:** `map.erase(3);`

---

### Q6 — Size of Map
**Difficulty:** Easy | **Time:** 10s | **TCS Frequency:** Low
Which function returns the number of active key-value pairs in a map?
**Answer:** `map.size()`

---

### Q7 — Iterating Map Elements
**Difficulty:** Easy | **Time:** 30s | **TCS Frequency:** High
How to print all keys and values in a map using a range-based loop?
**Answer:**
```cpp
for (const auto& pair : map) {
    std::cout << pair.first << ": " << pair.second << "\n";
}
```

---

### Q8 — Unordered Map Worst Case Complexity
**Difficulty:** Easy | **Time:** 15s | **TCS Frequency:** Medium
What is the worst-case search complexity of `std::unordered_map`?
**Answer:** O(N) (occurs due to hash collisions).

---

### Q9 — Standard Map Search Complexity
**Difficulty:** Easy | **Time:** 15s | **TCS Frequency:** High
What is the guaranteed search time complexity of `std::map`?
**Answer:** O(log N) (uses Red-Black Tree).

---

### Q10 — Clear All Elements
**Difficulty:** Easy | **Time:** 15s | **TCS Frequency:** Low
How do you delete all key-value entries from `map`?
**Answer:** `map.clear();`

---

### Q11 — Find Value iterator
**Difficulty:** Easy | **Time:** 25s | **TCS Frequency:** Medium
If `map.find(key)` does not locate the key, what does it return?
**Answer:** `map.end()`

---

### Q12 — Set Insertion Success
**Difficulty:** Easy | **Time:** 30s | **TCS Frequency:** Medium
How to check if `set.insert(x)` was successful (i.e. x was not already present)?
**Answer:** Check `set.insert(x).second` (evaluates to `true` if inserted).

---

### Q13 — Check for Empty Set
**Difficulty:** Easy | **Time:** 15s | **TCS Frequency:** Low
How to check if `std::unordered_set<int> s` has no elements?
**Answer:** `s.empty()`

---

### Q14 — Key and Value types
**Difficulty:** Easy | **Time:** 10s | **TCS Frequency:** High
In `std::unordered_map<string, double>`, what are the data types of `.first` and `.second`?
**Answer:** `.first` is `std::string`, `.second` is `double`.

---

### Q15 — Duplicate check in Vector
**Difficulty:** Easy | **Time:** 30s | **TCS Frequency:** High
Check if `std::vector<int> v` contains duplicate values.
**Answer:** `std::unordered_set<int> s(v.begin(), v.end()); return s.size() < v.size();`
