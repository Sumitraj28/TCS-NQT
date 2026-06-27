# Strings — Practice: Medium (15 Questions)

> **Tags:** Difficulty / Expected Time / TCS Frequency  
> No overlap with practice_basic.md

---

### Q1 — Valid Parentheses
**Difficulty:** Medium | **Time:** 90s | **TCS Frequency:** High

Check if `s = "{[()]}"` is valid.

**Full Solution:** Use a stack to track open brackets. Match closing brackets with the top of stack.
```cpp
#include <stack>
#include <string>

bool isValid(const std::string& s) {
    std::stack<char> st;
    for (char c : s) {
        if (c == '(' || c == '{' || c == '[') st.push(c);
        else {
            if (st.empty()) return false;
            if (c == ')' && st.top() != '(') return false;
            if (c == '}' && st.top() != '{') return false;
            if (c == ']' && st.top() != '[') return false;
            st.pop();
        }
    }
    return st.empty();
}
```
**Answer:** true

---

### Q2 — Word Pattern Matching
**Difficulty:** Medium | **Time:** 120s | **TCS Frequency:** High

`pattern = "abba"`, `s = "dog cat cat dog"`. Does `s` match the pattern?

**Full Solution (Two-way Map):**
```cpp
#include <string>
#include <sstream>
#include <vector>
#include <unordered_map>

bool wordPattern(const std::string& pattern, const std::string& s) {
    std::vector<std::string> words;
    std::stringstream ss(s);
    std::string w;
    while (ss >> w) words.push_back(w);
    if (words.size() != pattern.length()) return false;
    
    std::unordered_map<char, std::string> charToWord;
    std::unordered_map<std::string, char> wordToChar;
    for (int i = 0; i < pattern.length(); ++i) {
        char c = pattern[i];
        std::string word = words[i];
        if (charToWord.count(c) && charToWord[c] != word) return false;
        if (wordToChar.count(word) && wordToChar[word] != c) return false;
        charToWord[c] = word;
        wordToChar[word] = c;
    }
    return true;
}
```
**Answer:** true

---

### Q3 — Isomorphic Strings
**Difficulty:** Medium | **Time:** 90s | **TCS Frequency:** High

Are `s = "egg"` and `t = "add"` isomorphic?

**Full Solution:**
```cpp
#include <string>

bool isIsomorphic(const std::string& s, const std::string& t) {
    if (s.length() != t.length()) return false;
    int m1[256] = {0}, m2[256] = {0};
    for (int i = 0; i < s.length(); ++i) {
        if (m1[(unsigned char)s[i]] != m2[(unsigned char)t[i]]) return false;
        m1[(unsigned char)s[i]] = i + 1;
        m2[(unsigned char)t[i]] = i + 1;
    }
    return true;
}
```
**Answer:** true

---

### Q4 — Count Binary Substrings
**Difficulty:** Medium | **Time:** 120s | **TCS Frequency:** Medium

`s = "00110011"`. Count contiguous binary substrings with equal number of 0s and 1s.

**Full Solution:**
Group consecutive counts: 00110011 → `[2, 2, 2, 2]` (2 zeros, 2 ones, 2 zeros, 2 ones).
Result = sum of min of adjacent group counts = `min(2,2) + min(2,2) + min(2,2) = 2 + 2 + 2 = 6`.

**Answer:** 6

---

### Q5 — Fizz Buzz
**Difficulty:** Medium | **Time:** 60s | **TCS Frequency:** High

Generate string representations of numbers 1 to 15. Standard FizzBuzz rules.

**Full Solution:** Loop 1..15, build string based on divisibility.
**Answer:** `["1","2","Fizz","4","Buzz","Fizz","7","8","Fizz","Buzz","11","Fizz","13","14","FizzBuzz"]`

---

### Q6 — First Unique Character in a String
**Difficulty:** Medium | **Time:** 75s | **TCS Frequency:** High

`s = "loveleetcode"`. Find first non-repeating character index.

**Full Solution:**
```cpp
#include <string>

int firstUniqChar(const std::string& s) {
    int count[26] = {0};
    for (char c : s) count[c - 'a']++;
    for (int i = 0; i < s.length(); ++i) {
        if (count[s[i] - 'a'] == 1) return i;
    }
    return -1;
}
```
**Answer:** 2 (character 'v')

---

### Q7 — Detect Capital
**Difficulty:** Medium | **Time:** 75s | **TCS Frequency:** Medium

Check if capitalization of `word = "Google"` is valid.

**Full Solution:** Valid if all capital, all lower, or only first capital.
Count uppercase letters. If count == word.length() || count == 0 || (count == 1 && isupper(word[0])) → return true.

**Answer:** true

---

### Q8 — Find the Difference
**Difficulty:** Medium | **Time:** 60s | **TCS Frequency:** High

`s = "abcd"`, `t = "abcde"`. Find the added char.

**Full Solution (XOR approach):**
```cpp
char findTheDifference(const std::string& s, const std::string& t) {
    char res = 0;
    for (char c : s) res ^= c;
    for (char c : t) res ^= c;
    return res;
}
```
**Answer:** 'e'

---

### Q9 — Longest Substring Without Repeating Characters
**Difficulty:** Medium | **Time:** 120s | **TCS Frequency:** High

`s = "abcabcbb"`. Find length of longest substring without repeating characters.

**Full Solution:** Sliding window + last-seen map.
**Answer:** 3 ("abc")

---

### Q10 — Reverse Words in a Sentence
**Difficulty:** Medium | **Time:** 120s | **TCS Frequency:** High

`s = "the sky is blue"`. Reverse word by word.

**Full Solution:** Use `std::stringstream` to extract words, push to vector, reverse vector, and join with space.
**Answer:** "blue is sky the"

---

### Q11 — Find All Anagrams in a String
**Difficulty:** Medium | **Time:** 150s | **TCS Frequency:** Medium

`s = "cbaebabacd"`, `p = "abc"`. Find all start indices of anagrams of `p` in `s`.

**Full Solution (Sliding Window frequency comparison):**
Window size = 3. Maintain count arrays. Slide window and compare counts.
**Answer:** [0, 6] (indices of "cba" and "bac")

---

### Q12 — String Compression
**Difficulty:** Medium | **Time:** 120s | **TCS Frequency:** Medium

`chars = ["a","a","b","b","c","c","c"]`. Compress in-place to `["a","2","b","2","c","3"]`.

**Full Solution:** Two pointer compression write.

**Answer:** length 6

---

### Q13 — Generate IP Addresses (IPv4 Validation)
**Difficulty:** Medium | **Time:** 120s | **TCS Frequency:** High

Check if `queryIP = "172.16.254.1"` is a valid IPv4 address.

**Full Solution:** Split by '.', check each part: length is 1..3, consists only of digits, no leading zeros unless single '0', value is 0..255.

---

### Q14 — Multiply Strings (Big Integer Multiply)
**Difficulty:** Medium | **Time:** 150s | **TCS Frequency:** Medium

`num1 = "12"`, `num2 = "10"`. Multiply them without converting directly.

**Full Solution:**
Simulate long multiplication into a results array of size `n1 + n2`.

**Answer:** "120"

---

### Q15 — Compare Version Numbers
**Difficulty:** Medium | **Time:** 120s | **TCS Frequency:** Medium

`version1 = "1.01"`, `version2 = "1.001"`. Compare them.

**Full Solution:** Parse dot-separated numbers sequentially, compare values.
**Answer:** 0 (equal)
