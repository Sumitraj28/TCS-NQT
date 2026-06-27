# Strings — Top 20 Important TCS NQT-Style Questions

---

### IQ1 — Reverse a given string in C++.
**Difficulty:** Easy | **Time:** 30s | **TCS Frequency:** High
**Answer:** `std::reverse(s.begin(), s.end());` or two-pointer swap.

---

### IQ2 — Check if a string is a palindrome.
**Difficulty:** Easy | **Time:** 45s | **TCS Frequency:** High
**Answer:** Two pointer check: `s[l++] == s[r--]` from outer boundaries inward.

---

### IQ3 — Count occurrences of each character.
**Difficulty:** Easy | **Time:** 45s | **TCS Frequency:** High
**Answer:** Frequency array of size 256.

---

### IQ4 — Check if two strings are anagrams.
**Difficulty:** Easy | **Time:** 60s | **TCS Frequency:** High
**Answer:** Size check + character counts in frequency array.

---

### IQ5 — Find the first non-repeating character in a string.
**Difficulty:** Medium | **Time:** 75s | **TCS Frequency:** High
**Answer:** Two pass: count frequencies in first pass, scan string for count==1 in second.

---

### IQ6 — Convert numeric string to integer (atoi).
**Difficulty:** Medium | **Time:** 90s | **TCS Frequency:** High
**Answer:** Parse sign and digits, check for `INT_MAX`/`INT_MIN` overflow.

---

### IQ7 — Remove duplicate characters.
**Difficulty:** Easy | **Time:** 45s | **TCS Frequency:** High
**Answer:** Boolean seen array of size 256.

---

### IQ8 — Find the longest common prefix.
**Difficulty:** Medium | **Time:** 75s | **TCS Frequency:** High
**Answer:** Horizontal scanning: reduce prefix iteratively against each string.

---

### IQ9 — Reverse vowels in a string.
**Difficulty:** Medium | **Time:** 75s | **TCS Frequency:** High
**Answer:** Two pointer: increment left if not vowel, decrement right if not vowel, swap when both are.

---

### IQ10 — Split sentence into words.
**Difficulty:** Easy | **Time:** 45s | **TCS Frequency:** High
**Answer:** Use `std::stringstream` to extract words.

---

### IQ11 — Valid Parentheses.
**Difficulty:** Medium | **Time:** 90s | **TCS Frequency:** High
**Answer:** Stack of open brackets.

---

### IQ12 — Longest substring without repeating characters.
**Difficulty:** Medium | **Time:** 120s | **TCS Frequency:** High
**Answer:** Sliding Window + hash map tracking last seen index.

---

### IQ13 — Find the added character in `t` vs `s`.
**Difficulty:** Easy | **Time:** 45s | **TCS Frequency:** High
**Answer:** XOR sum of all characters in both strings.

---

### IQ14 — Check if strings are isomorphic.
**Difficulty:** Medium | **Time:** 90s | **TCS Frequency:** High
**Answer:** Two map/array index tracking of last seen positions.

---

### IQ15 — Find all anagrams of pattern P in string S.
**Difficulty:** Medium | **Time:** 120s | **TCS Frequency:** Medium
**Answer:** Sliding window of size P length comparing counts.

---

### IQ16 — String compression (Run Length Encoding).
**Difficulty:** Medium | **Time:** 90s | **TCS Frequency:** High
**Answer:** Two pointer writing char + consecutive count if > 1.

---

### IQ17 — Find the first occurrence index of needle in haystack.
**Difficulty:** Easy | **Time:** 45s | **TCS Frequency:** High
**Answer:** `s.find(sub)` or two-pointer brute force.

---

### IQ18 — Reverse words in a string.
**Difficulty:** Medium | **Time:** 90s | **TCS Frequency:** High
**Answer:** Parse words into list, reverse list, join.

---

### IQ19 — Check if a string can be obtained by rotating another.
**Difficulty:** Medium | **Time:** 60s | **TCS Frequency:** Medium
**Answer:** Check if `s1.length() == s2.length()` and `(s1 + s1).find(s2) != std::string::npos`.

---

### IQ20 — Subarray/Substring count with equal 0s and 1s.
**Difficulty:** Medium | **Time:** 120s | **TCS Frequency:** Medium
**Answer:** Run consecutive counts, sum `min(count[i], count[i-1])`.
