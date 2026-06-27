# Strings — Coding Application (Full Problem Solutions)

> **Programming Language: C++.**  
> Every solution includes: Problem Statement → Approach → C++ code (line-by-line) → Complexity.

---

## Problem 1 — Reverse String
**LeetCode:** #344 | **Difficulty:** Easy | **TCS Frequency:** High

### Problem Statement
Write a function that reverses a string. The input string is given as an array of characters `s`. Modify the input array in-place with O(1) extra memory.

**Example:** `s = ["h","e","l","l","o"]` → Output: `["o","l","l","e","h"]`

### Approach
Use two pointers starting at opposite ends of the array. Swap the characters at both pointers and move the pointers toward the center.

### C++ Solution
```cpp
#include <vector>
#include <algorithm>

class Solution {
public:
    void reverseString(std::vector<char>& s) {
        int left = 0;
        int right = s.size() - 1;

        while (left < right) {
            std::swap(s[left++], s[right--]); // swap and shift inward
        }
    }
};
```

**Complexity:** Time O(N) | Space O(1)

---

## Problem 2 — Valid Palindrome
**LeetCode:** #125 | **Difficulty:** Easy | **TCS Frequency:** High

### Problem Statement
Given a string `s`, return `true` if it is a palindrome, or `false` otherwise, after converting all uppercase letters into lowercase letters and removing all non-alphanumeric characters.

**Example:** `s = "A man, a plan, a canal: Panama"` → Output: `true`

### Approach
Two pointers at both ends. Skip any non-alphanumeric characters. Compare lowercase versions of characters.

### C++ Solution
```cpp
#include <string>
#include <cctype>

class Solution {
public:
    bool isPalindrome(std::string s) {
        int left = 0;
        int right = s.length() - 1;

        while (left < right) {
            // Skip non-alphanumeric characters from left
            while (left < right && !std::isalnum(s[left])) left++;
            // Skip non-alphanumeric characters from right
            while (left < right && !std::isalnum(s[right])) right--;

            // Compare lowercase representations
            if (std::tolower(s[left++]) != std::tolower(s[right--])) {
                return false;
            }
        }
        return true;
    }
};
```

**Complexity:** Time O(N) | Space O(1)

---

## Problem 3 — Reverse Vowels of a String
**LeetCode:** #345 | **Difficulty:** Easy | **TCS Frequency:** High

### Problem Statement
Given a string `s`, reverse only all the vowels in the string and return it. The vowels are 'a', 'e', 'i', 'o', and 'u', and they can appear in both lower and upper cases.

**Example:** `s = "hello"` → Output: `"holle"`

### Approach
Two pointers. Increment left pointer until it hits a vowel, decrement right until it hits a vowel. Swap them, then increment/decrement both.

### C++ Solution
```cpp
#include <string>
#include <unordered_set>

class Solution {
private:
    bool isVowel(char c) {
        c = std::tolower(c);
        return c == 'a' || c == 'e' || c == 'i' || c == 'o' || c == 'u';
    }

public:
    std::string reverseVowels(std::string s) {
        int left = 0;
        int right = s.length() - 1;

        while (left < right) {
            while (left < right && !isVowel(s[left])) left++;
            while (left < right && !isVowel(s[right])) right--;

            if (left < right) {
                std::swap(s[left++], s[right--]);
            }
        }
        return s;
    }
};
```

**Complexity:** Time O(N) | Space O(1)

---

## Problem 4 — First Unique Character in a String
**LeetCode:** #387 | **Difficulty:** Easy | **TCS Frequency:** High

### Problem Statement
Given a string `s`, find the first non-repeating character in it and return its index. If it does not exist, return -1.

**Example:** `s = "loveleetcode"` → Output: `2` (character 'v')

### Approach
First pass: count frequencies of all 26 lowercase alphabet characters.  
Second pass: check each character in `s` from left to right; return index of first character with frequency = 1.

### C++ Solution
```cpp
#include <string>
#include <vector>

class Solution {
public:
    int firstUniqChar(std::string s) {
        int count[26] = {0}; // frequency array

        // Pass 1: count frequency
        for (char c : s) {
            count[c - 'a']++;
        }

        // Pass 2: find first character with count == 1
        for (int i = 0; i < s.length(); ++i) {
            if (count[s[i] - 'a'] == 1) {
                return i;
            }
        }
        return -1;
    }
};
```

**Complexity:** Time O(N) | Space O(1) (fixed size 26 array)

---

## Problem 5 — Detect Capital
**LeetCode:** #520 | **Difficulty:** Easy | **TCS Frequency:** Medium

### Problem Statement
We define the usage of capitals in a word to be right when one of the following cases holds:
1. All letters in this word are capitals, like "USA".
2. All letters in this word are not capitals, like "leetcode".
3. Only the first letter in this word is capital, like "Google".

Given a string `word`, return `true` if the usage of capitals in it is right.

**Example:** `word = "USA"` → Output: `true`

### Approach
Count the total number of uppercase letters in the string.
The usage is correct if:
- All letters are uppercase: `count == length`
- All letters are lowercase: `count == 0`
- Only the first letter is uppercase: `count == 1 && isupper(word[0])`

### C++ Solution
```cpp
#include <string>
#include <cctype>

class Solution {
public:
    bool detectCapitalUse(std::string word) {
        int uppers = 0;
        for (char c : word) {
            if (std::isupper(c)) uppers++;
        }

        return uppers == word.length() || 
               uppers == 0 || 
               (uppers == 1 && std::isupper(word[0]));
    }
};
```

**Complexity:** Time O(N) | Space O(1)

---

## Problem 6 — Find the Difference
**LeetCode:** #389 | **Difficulty:** Easy | **TCS Frequency:** High

### Problem Statement
You are given two strings `s` and `t`. String `t` is generated by random shuffling string `s` and then adding one more letter at a random position. Return the letter that was added to `t`.

**Example:** `s = "abcd"`, `t = "abcde"` → Output: `'e'`

### Approach
Since only one character is added and all others are duplicated, we can XOR all character values in both strings. All duplicate characters will cancel out to 0, leaving only the added character.

### C++ Solution
```cpp
#include <string>

class Solution {
public:
    char findTheDifference(std::string s, std::string t) {
        char result = 0;
        for (char c : s) result ^= c;
        for (char c : t) result ^= c;
        return result;
    }
};
```

**Complexity:** Time O(N) | Space O(1)

---

## Problem 7 — Valid Anagram
**LeetCode:** #242 | **Difficulty:** Easy | **TCS Frequency:** High

### Problem Statement
Given two strings `s` and `t`, return `true` if `t` is an anagram of `s`, and `false` otherwise.

**Example:** `s = "anagram"`, `t = "nagaram"` → Output: `true`

### Approach
Use a frequency array of size 26. Increment counts for letters in `s`, decrement for letters in `t`. If any final count != 0, they are not anagrams.

### C++ Solution
```cpp
#include <string>

class Solution {
public:
    bool isAnagram(std::string s, std::string t) {
        if (s.length() != t.length()) return false;

        int counts[26] = {0};
        for (int i = 0; i < s.length(); ++i) {
            counts[s[i] - 'a']++;
            counts[t[i] - 'a']--;
        }

        for (int i = 0; i < 26; ++i) {
            if (counts[i] != 0) return false;
        }
        return true;
    }
};
```

**Complexity:** Time O(N) | Space O(1)

---

## Problem 8 — Isomorphic Strings
**LeetCode:** #205 | **Difficulty:** Easy | **TCS Frequency:** High

### Problem Statement
Given two strings `s` and `t`, determine if they are isomorphic. Two strings `s` and `t` are isomorphic if the characters in `s` can be replaced to get `t` while preserving character order.

**Example:** `s = "egg"`, `t = "add"` → Output: `true`

### Approach
Track the last seen index position (+1 to avoid default 0 value confusion) for each character in both strings. If their mapping history deviates at any step, they are not isomorphic.

### C++ Solution
```cpp
#include <string>

class Solution {
public:
    bool isIsomorphic(std::string s, std::string t) {
        if (s.length() != t.length()) return false;

        int mapS[256] = {0};
        int mapT[256] = {0};

        for (int i = 0; i < s.length(); ++i) {
            if (mapS[(unsigned char)s[i]] != mapT[(unsigned char)t[i]]) {
                return false;
            }
            mapS[(unsigned char)s[i]] = i + 1;
            mapT[(unsigned char)t[i]] = i + 1;
        }
        return true;
    }
};
```

**Complexity:** Time O(N) | Space O(1)

---

## Problem 9 — Longest Common Prefix
**LeetCode:** #14 | **Difficulty:** Easy | **TCS Frequency:** High

### Problem Statement
Write a function to find the longest common prefix string amongst an array of strings. If there is no common prefix, return an empty string `""`.

**Example:** `strs = ["flower","flow","flight"]` → Output: `"fl"`

### Approach
Initialize common prefix as the first string `strs[0]`. Compare it against each string in the array, reducing the prefix character-by-character from the end until it matches the beginning of the string.

### C++ Solution
```cpp
#include <vector>
#include <string>

class Solution {
public:
    std::string longestCommonPrefix(std::vector<std::string>& strs) {
        if (strs.empty()) return "";

        std::string prefix = strs[0];

        for (size_t i = 1; i < strs.size(); ++i) {
            // While the current prefix is not found at the start of strs[i]
            while (strs[i].find(prefix) != 0) {
                // Shorten the prefix from the right end by 1 character
                prefix = prefix.substr(0, prefix.length() - 1);
                if (prefix.empty()) return "";
            }
        }
        return prefix;
    }
};
```

**Complexity:** Time O(S) where S is the sum of all characters in all strings | Space O(1)

---

## Problem 10 — String to Integer (atoi)
**LeetCode:** #8 | **Difficulty:** Medium | **TCS Frequency:** High

### Problem Statement
Implement the `myAtoi(string s)` function, which converts a string into a 32-bit signed integer. Read whitespace, sign, parse digits, and cap at `[INT_MIN, INT_MAX]` overflow limits.

**Example:** `s = "   -42"` → Output: `-42`

### Approach
Follow parsing rules sequentially: skip spaces, read sign, read digit chars, compute running sum using `long long` to prevent internal overflow, checking boundaries before casting.

### C++ Solution
```cpp
#include <string>
#include <climits>

class Solution {
public:
    int myAtoi(std::string s) {
        int i = 0, n = s.length();

        // 1. Skip leading whitespaces
        while (i < n && s[i] == ' ') i++;

        // 2. Read sign
        int sign = 1;
        if (i < n && (s[i] == '+' || s[i] == '-')) {
            sign = (s[i] == '-') ? -1 : 1;
            i++;
        }

        // 3. Convert digit characters
        long long result = 0;
        while (i < n && s[i] >= '0' && s[i] <= '9') {
            result = result * 10 + (s[i] - '0');

            // 4. Handle 32-bit signed integer overflow
            if (sign == 1 && result > INT_MAX) return INT_MAX;
            if (sign == -1 && -result < INT_MIN) return INT_MIN;
            i++;
        }

        return sign * result;
    }
};
```

**Complexity:** Time O(N) | Space O(1)

---

## Problem 11 — Count Binary Substrings
**LeetCode:** #696 | **Difficulty:** Easy | **TCS Frequency:** Medium

### Problem Statement
Given a binary string `s`, return the number of non-empty substrings that have the same number of 0's and 1's, and all those 0's and all those 1's are grouped consecutively.

**Example:** `s = "00110011"` → Output: `6`

### Approach
Count consecutive groups of identical characters: e.g. "00110011" → groups `[2, 2, 2, 2]`. The number of valid substrings between any two adjacent groups of size `A` and `B` is `min(A, B)`.

### C++ Solution
```cpp
#include <string>
#include <algorithm>

class Solution {
public:
    int countBinarySubstrings(std::string s) {
        int count = 0;
        int prev = 0; // count of previous block
        int curr = 1; // count of current block

        for (size_t i = 1; i < s.length(); ++i) {
            if (s[i] == s[i-1]) {
                curr++;
            } else {
                count += std::min(prev, curr);
                prev = curr;
                curr = 1;
            }
        }
        count += std::min(prev, curr); // add last transition
        return count;
    }
};
```

**Complexity:** Time O(N) | Space O(1)

---

## Problem 12 — Fizz Buzz
**LeetCode:** #412 | **Difficulty:** Easy | **TCS Frequency:** High

### Problem Statement
Given an integer `n`, return a string array answer (1-indexed) where:
- `answer[i] == "FizzBuzz"` if i is divisible by 3 and 5.
- `answer[i] == "Fizz"` if i is divisible by 3.
- `answer[i] == "Buzz"` if i is divisible by 5.
- `answer[i] == std::to_string(i)` if none of the above conditions are true.

**Example:** `n = 3` → Output: `["1","2","Fizz"]`

### C++ Solution
```cpp
#include <vector>
#include <string>

class Solution {
public:
    std::vector<std::string> fizzBuzz(int n) {
        std::vector<std::string> result;
        for (int i = 1; i <= n; ++i) {
            if (i % 3 == 0 && i % 5 == 0) {
                result.push_back("FizzBuzz");
            } else if (i % 3 == 0) {
                result.push_back("Fizz");
            } else if (i % 5 == 0) {
                result.push_back("Buzz");
            } else {
                result.push_back(std::to_string(i));
            }
        }
        return result;
    }
};
```

**Complexity:** Time O(N) | Space O(1)

---

## Problem 13 — Longest Substring Without Repeating Characters
**LeetCode:** #3 | **Difficulty:** Medium | **TCS Frequency:** High

### Problem Statement
Given a string `s`, find the length of the longest substring without repeating characters.

**Example:** `s = "abcabcbb"` → Output: `3`

### Approach (Sliding Window)
Maintain left boundary pointer `left`. Scan with `right` pointer. If `s[right]` was seen, move `left` to index after its last seen position.

### C++ Solution
```cpp
#include <string>
#include <algorithm>

class Solution {
public:
    int lengthOfLongestSubstring(std::string s) {
        int charIdx[256];
        std::fill(charIdx, charIdx + 256, -1); // fill all with -1

        int left = 0;
        int maxLen = 0;

        for (int right = 0; right < s.length(); ++right) {
            // If character is present in the current window
            if (charIdx[(unsigned char)s[right]] >= left) {
                left = charIdx[(unsigned char)s[right]] + 1;
            }

            charIdx[(unsigned char)s[right]] = right;
            maxLen = std::max(maxLen, right - left + 1);
        }
        return maxLen;
    }
};
```

**Complexity:** Time O(N) | Space O(1) (fixed size 256 array)

---

## Problem 14 — Word Pattern
**LeetCode:** #290 | **Difficulty:** Easy | **TCS Frequency:** High

### Problem Statement
Given a `pattern` and a string `s`, find if `s` follows the same pattern. Two-way bijection mapping between pattern characters and words in `s`.

**Example:** `pattern = "abba"`, `s = "dog cat cat dog"` → Output: `true`

### C++ Solution
```cpp
#include <string>
#include <vector>
#include <sstream>
#include <unordered_map>

class Solution {
public:
    bool wordPattern(std::string pattern, std::string s) {
        std::vector<std::string> words;
        std::stringstream ss(s);
        std::string word;

        while (ss >> word) {
            words.push_back(word);
        }

        if (words.size() != pattern.length()) return false;

        std::unordered_map<char, std::string> charToWord;
        std::unordered_map<std::string, char> wordToChar;

        for (int i = 0; i < pattern.length(); ++i) {
            char c = pattern[i];
            std::string w = words[i];

            if (charToWord.count(c) && charToWord[c] != w) return false;
            if (wordToChar.count(w) && wordToChar[w] != c) return false;

            charToWord[c] = w;
            wordToChar[w] = c;
        }
        return true;
    }
};
```

**Complexity:** Time O(N + M) | Space O(N + M) (where N is pattern length, M is words size)
