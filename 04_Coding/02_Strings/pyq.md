# Strings — Previous Year Style Questions (TCS NQT)

---

### PYQ1 — Word Reverse
**Difficulty:** Medium | **Time:** 90s | **TCS Frequency:** High

**Problem:** Reverse each word in a given sentence while keeping the relative order of the words the same.

Input: `s = "Hello World"`  
Output: "olleH dlroW"

**C++ Solution:**
```cpp
#include <iostream>
#include <string>
#include <sstream>
#include <algorithm>

std::string reverseEachWord(const std::string& s) {
    std::stringstream ss(s);
    std::string word, result = "";
    while (ss >> word) {
        std::reverse(word.begin(), word.end());
        result += word + " ";
    }
    if (!result.empty()) result.pop_back(); // remove trailing space
    return result;
}
```

---

### PYQ2 — Run Length Encoding (RLE)
**Difficulty:** Easy | **Time:** 60s | **TCS Frequency:** High

**Problem:** Compress a string by replacing consecutive repeating characters with the character followed by its count.

Input: `"aabbbcccc"`  
Output: "a2b3c4"

**C++ Solution:**
```cpp
#include <string>

std::string compress(const std::string& s) {
    if (s.empty()) return "";
    std::string res = "";
    int count = 1;
    for (size_t i = 1; i <= s.length(); ++i) {
        if (i < s.length() && s[i] == s[i-1]) {
            count++;
        } else {
            res += s[i-1];
            res += std::to_string(count);
            count = 1;
        }
    }
    return res;
}
```

---

### PYQ3 — Remove Vowels
**Difficulty:** Easy | **Time:** 45s | **TCS Frequency:** High

**Problem:** Remove all vowels from a given string.

Input: `"TCS NQT"`  
Output: "TCS NQT"

**C++ Solution:**
```cpp
#include <string>

bool isVowel(char c) {
    c = tolower(c);
    return c == 'a' || c == 'e' || c == 'i' || c == 'o' || c == 'u';
}

std::string removeVowels(const std::string& s) {
    std::string res = "";
    for (char c : s) {
        if (!isVowel(c)) res += c;
    }
    return res;
}
```

---

### PYQ4 — Count Vowels, Consonants, Spaces, and Digits
**Difficulty:** Easy | **Time:** 60s | **TCS Frequency:** High

**Problem:** Count the occurrences of vowels, consonants, spaces, and digits in a string.

**C++ Solution:**
```cpp
#include <string>
#include <cctype>

struct Counts {
    int vowels = 0;
    int consonants = 0;
    int spaces = 0;
    int digits = 0;
};

Counts countAll(const std::string& s) {
    Counts counts;
    for (char c : s) {
        if (std::isdigit(c)) {
            counts.digits++;
        } else if (std::isspace(c)) {
            counts.spaces++;
        } else if (std::isalpha(c)) {
            char lower = std::tolower(c);
            if (lower == 'a' || lower == 'e' || lower == 'i' || lower == 'o' || lower == 'u') {
                counts.vowels++;
            } else {
                counts.consonants++;
            }
        }
    }
    return counts;
}
```
**Complexity:** Time O(N) | Space O(1)

---

### PYQ5 — Non-Repeating Character
**Difficulty:** Medium | **Time:** 90s | **TCS Frequency:** High

**Problem:** Find the first non-repeating character in a string.

Input: `"apple"`  
Output: 'a'

**C++ Solution:**
```cpp
#include <string>

char firstNonRepeating(const std::string& s) {
    int freq[256] = {0};
    for (char c : s) {
        freq[(unsigned char)c]++;
    }
    for (char c : s) {
        if (freq[(unsigned char)c] == 1) {
            return c;
        }
    }
    return '\0';
}
```
**Complexity:** Time O(N) | Space O(1) (fixed 256 size array)
```
