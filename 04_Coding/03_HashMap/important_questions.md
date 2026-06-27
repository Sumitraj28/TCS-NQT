# HashMap — Top 20 Important TCS NQT-Style Questions

---

### IQ1 — Count character frequencies.
**Difficulty:** Easy | **Time:** 30s | **TCS Frequency:** High
**Answer:** Map character to integer counts.

---

### IQ2 — Find the first unique character.
**Difficulty:** Easy | **Time:** 60s | **TCS Frequency:** High
**Answer:** Frequency count + scan vector.

---

### IQ3 — Two Sum using HashMap.
**Difficulty:** Medium | **Time:** 75s | **TCS Frequency:** High
**Answer:** For each `x`, check if `target - x` is in map.

---

### IQ4 — Find majority element.
**Difficulty:** Easy | **Time:** 60s | **TCS Frequency:** High
**Answer:** Check if any frequency > n/2.

---

### IQ5 — Find intersection of two arrays.
**Difficulty:** Easy | **Time:** 60s | **TCS Frequency:** High
**Answer:** Build set from first array, filter elements of second array.

---

### IQ6 — Find duplicate elements in array.
**Difficulty:** Easy | **Time:** 45s | **TCS Frequency:** High
**Answer:** Insert into set, check if insertion fails.

---

### IQ7 — Group Anagrams.
**Difficulty:** Medium | **Time:** 120s | **TCS Frequency:** High
**Answer:** Sort string to create signature key, group values.

---

### IQ8 — Subarray sum equals K.
**Difficulty:** Medium | **Time:** 120s | **TCS Frequency:** High
**Answer:** Prefix sum + hash map.

---

### IQ9 — Longest subarray with sum equals K.
**Difficulty:** Medium | **Time:** 120s | **TCS Frequency:** High
**Answer:** Prefix sum + leftmost index map.

---

### IQ10 — Subarrays with sum divisible by K.
**Difficulty:** Medium | **Time:** 120s | **TCS Frequency:** High
**Answer:** Prefix sum modulo remainder map.

---

### IQ11 — Find if an array can be divided into pairs whose sum is divisible by K.
**Difficulty:** Medium | **Time:** 120s | **TCS Frequency:** High
**Answer:** Remainder frequency map: match count of remainder `r` and `k-r`.

---

### IQ12 — Longest consecutive sequence.
**Difficulty:** Hard | **Time:** 150s | **TCS Frequency:** High
**Answer:** Set: start sequence only if `num - 1` is absent.

---

### IQ13 — Top K frequent elements.
**Difficulty:** Medium | **Time:** 90s | **TCS Frequency:** High
**Answer:** Map count + Bucket Sort / Min-Heap.

---

### IQ14 — Group items by key (buckets).
**Difficulty:** Easy | **Time:** 60s | **TCS Frequency:** High
**Answer:** `map[key].push_back(value)`.

---

### IQ15 — Set Matrix Zeroes.
**Difficulty:** Medium | **Time:** 90s | **TCS Frequency:** High
**Answer:** Row and Column sets tracker.

---

### IQ16 — Find the duplicate number.
**Difficulty:** Hard | **Time:** 120s | **TCS Frequency:** High
**Answer:** Floyd's cycle detection.

---

### IQ17 — Find all pairs with given sum.
**Difficulty:** Medium | **Time:** 90s | **TCS Frequency:** High
**Answer:** For each `x`, check if `target - x` is in frequency map.

---

### IQ18 — Longest Subarray with equal 0s and 1s.
**Difficulty:** Medium | **Time:** 120s | **TCS Frequency:** High
**Answer:** Convert 0 to -1, Prefix sum index map.

---

### IQ19 — Check if array elements are consecutive.
**Difficulty:** Easy | **Time:** 60s | **TCS Frequency:** Medium
**Answer:** Check max - min + 1 == n, and set size == n.

---

### IQ20 — Top K frequent words.
**Difficulty:** Medium | **Time:** 120s | **TCS Frequency:** High
**Answer:** Map count + custom sort comparator.
```
