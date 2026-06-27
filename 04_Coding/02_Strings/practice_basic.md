# Strings — Practice: Basic (15 Questions)

> Tags: Difficulty / Expected Time / TCS Frequency

---

### Q1 — Convert Uppercase to Lowercase
**Difficulty:** Easy | **Time:** 20s | **TCS Frequency:** High
Convert the character `'G'` to lowercase in C++ without using library functions.
**Answer:** `'g'`
**Explanation:** Add 32 or bitwise OR with space: `'G' | ' '` gives `'g'`.

---

### Q2 — Check If Character Is Digit
**Difficulty:** Easy | **Time:** 15s | **TCS Frequency:** High
How do you check if character `c` is a digit `0` to `9`?
**Answer:** `c >= '0' && c <= '9'`

---

### Q3 — ASCII Value of Zero Character
**Difficulty:** Easy | **Time:** 10s | **TCS Frequency:** Medium
What is the ASCII integer value of the character `'0'`?
**Answer:** 48

---

### Q4 — Count Vowels in String
**Difficulty:** Easy | **Time:** 30s | **TCS Frequency:** High
Count the number of vowels in `s = "education"`.
**Answer:** 5 (e, u, a, i, o)
**Explanation:** Loop through and increment counter if character matches a vowel.

---

### Q5 — Reverse String (Simple)
**Difficulty:** Easy | **Time:** 30s | **TCS Frequency:** High
Reverse string `s = "tcs"`.
**Answer:** "sct"
**Explanation:** Swap first and last characters: 't' and 's'.

---

### Q6 — Length of String Without size()
**Difficulty:** Easy | **Time:** 30s | **TCS Frequency:** Medium
How do you find the length of a null-terminated char array `char s[] = "hello"` manually?
**Answer:** Loop until `s[i] == '\0'`.
**Explanation:** Traverse starting from index 0 and count until you hit the null terminator.

---

### Q7 — Is String Empty
**Difficulty:** Easy | **Time:** 10s | **TCS Frequency:** Low
What C++ member function checks if string `s` contains no characters?
**Answer:** `s.empty()`

---

### Q8 — Check for Substring Presence
**Difficulty:** Easy | **Time:** 30s | **TCS Frequency:** High
How to check if substring `"nqt"` is present in `"tcsnqtprep"` in C++?
**Answer:** `s.find("nqt") != std::string::npos`

---

### Q9 — Concat String with Character
**Difficulty:** Easy | **Time:** 20s | **TCS Frequency:** High
What is the efficient way to append `'x'` to string `s`?
**Answer:** `s += 'x'` (or `s.push_back('x')`)

---

### Q10 — Compare Two Strings
**Difficulty:** Easy | **Time:** 20s | **TCS Frequency:** High
How do you check if two C++ strings `s1` and `s2` are equal?
**Answer:** `s1 == s2`

---

### Q11 — Find Character Index
**Difficulty:** Easy | **Time:** 25s | **TCS Frequency:** Medium
Find the first occurrence index of `'c'` in `"racecar"`.
**Answer:** 2
**Explanation:** `s.find('c')` returns index 2.

---

### Q12 — String to Integer
**Difficulty:** Easy | **Time:** 20s | **TCS Frequency:** High
Which C++ STL function converts string `"456"` to integer `456`?
**Answer:** `std::stoi("456")`

---

### Q13 — Check if Anagram (Sorting)
**Difficulty:** Easy | **Time:** 45s | **TCS Frequency:** High
Are `"silent"` and `"listen"` anagrams?
**Answer:** Yes
**Explanation:** Sorting both gives `"eilnst"`, which are identical.

---

### Q14 — Is Character Alphanumeric
**Difficulty:** Easy | **Time:** 15s | **TCS Frequency:** Low
Which function checks if a character is either a letter or a digit?
**Answer:** `std::isalnum(c)`

---

### Q15 — Remove Last Character
**Difficulty:** Easy | **Time:** 20s | **TCS Frequency:** Medium
How do you remove the last character from string `s`?
**Answer:** `s.pop_back()`
