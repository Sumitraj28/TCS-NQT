# Strings — Complexity and Reference Guide

## C++ `std::string` Time Complexity Reference

| Operation | C++ standard syntax | Time Complexity | Space Complexity |
|-----------|--------------------|-----------------|------------------|
| Access character | `s[i]` | O(1) | O(1) |
| Length of string | `s.length()` or `s.size()` | O(1) | O(1) |
| Concatenate char | `s += 'c'` | O(1) amortized | O(1) |
| Concatenate string | `s1 += s2` | O(len(s2)) | O(len(s2)) |
| Substring | `s.substr(pos, len)` | O(len) | O(len) |
| Search character | `s.find('c')` | O(N) | O(1) |
| Search substring | `s.find(sub)` | O(N * M) worst | O(1) |
| Convert to int | `std::stoi(s)` | O(len) | O(1) |
| Convert to string | `std::to_string(val)` | O(log₁₀(val)) | O(log₁₀(val)) |

---

## Frequency Array vs Hash Map

When counting character occurrences:
- If alphabet is bounded (e.g. lowercase only, or ASCII), use a **fixed-size array**:
  - `int count[26] = {0};` or `int count[256] = {0};`
  - Space complexity: O(1) (fixed size).
  - Time complexity: O(N) (extremely fast array lookups).
- If character space is arbitrary (Unicode / large value ranges), use `std::unordered_map<char, int>`.
  - Space complexity: O(U) where U is unique characters.
  - Time complexity: O(N) average, but with hash table overhead.

---

## Monotone String Conditions (Sliding Window Formulas)

### Substring Window Definition
- Left boundary: `l`
- Right boundary: `r`
- Window size: `r - l + 1`

### Longest Substring Condition
```cpp
for (int r = 0; r < n; ++r) {
    // Add right character to window
    // while (window is invalid) { remove left character; l++; }
    // maxLen = max(maxLen, r - l + 1);
}
```

### Anagram/Anagram Count Query
Comparing window frequency table `winFreq` to target frequency table `tarFreq` in O(1):
Track a `matchCount` variable representing how many characters match the required frequency.
- When `winFreq[c] == tarFreq[c]`, increment `matchCount`.
- When shifting, if frequency changes and no longer matches, decrement `matchCount`.
- If `matchCount == unique_characters_needed`, then window matches target.
