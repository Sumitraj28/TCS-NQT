# Strings — Complete Notes

## 1. ASCII Basics & Character Math

A character in C++ (`char`) is a 1-byte integer representation using ASCII encoding.
- `'a'` to `'z'`: ASCII `97` to `122`
- `'A'` to `'Z'`: ASCII `65` to `90`
- `'0'` to `'9'`: ASCII `48` to `57`

### Useful Conversion Shortcuts:
- **Case conversion:** Difference between upper and lower case is exactly 32 (or `'a' - 'A' = 32`).
  - Convert to lower: `char lower = c | ' ';` or `tolower(c)`
  - Convert to upper: `char upper = c & '_';` or `toupper(c)`
- **Digit to integer:** `int val = c - '0';`
- **Integer to digit:** `char c = val + '0';`
- **Character index (0-25):** `int idx = c - 'a';` (for lowercase)

---

## 2. Reverse String & Palindrome Check

### Reverse String (Two Pointer)
Swap characters at `left` and `right` indices, moving inward.
```cpp
void reverseString(std::string& s) {
    int left = 0, right = s.length() - 1;
    while (left < right) {
        std::swap(s[left++], s[right--]);
    }
}
```

### Palindrome Check
A string is a palindrome if it reads the same forward and backward.
```cpp
bool isPalindrome(const std::string& s) {
    int left = 0, right = s.length() - 1;
    while (left < right) {
        if (s[left++] != s[right--]) return false;
    }
    return true;
}
```

---

## 3. Anagram Check & Character Frequency

An **Anagram** of a string is another string that contains the same characters, only in a different order.

### Frequency Array Method (O(N) time, O(1) space)
Use a fixed-size array of size 26 (for alphabet) or 256 (for all ASCII characters).
```cpp
bool isAnagram(const std::string& s, const std::string& t) {
    if (s.length() != t.length()) return false;
    
    int count[26] = {0};
    for (char c : s) count[c - 'a']++;
    for (char c : t) {
        if (--count[c - 'a'] < 0) return false;
    }
    return true;
}
```

---

## 4. Longest Common Prefix

Find the longest prefix shared by all strings in a list.
```cpp
std::string longestCommonPrefix(std::vector<std::string>& strs) {
    if (strs.empty()) return "";
    std::string prefix = strs[0];
    for (size_t i = 1; i < strs.size(); ++i) {
        while (strs[i].find(prefix) != 0) {
            prefix = prefix.substr(0, prefix.length() - 1);
            if (prefix.empty()) return "";
        }
    }
    return prefix;
}
```

---

## 5. Valid Parentheses (Stack)

Use a stack to match opening brackets with their corresponding closing brackets.
```cpp
#include <stack>
#include <string>

bool isValid(const std::string& s) {
    std::stack<char> st;
    for (char c : s) {
        if (c == '(' || c == '{' || c == '[') {
            st.push(c);
        } else {
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

---

## 6. Remove Duplicates

Remove duplicate characters from a string, keeping only unique characters.
Using a boolean visited array (works if only lowercase alphabets):
```cpp
std::string removeDuplicates(const std::string& s) {
    bool seen[256] = {false};
    std::string result = "";
    for (char c : s) {
        if (!seen[(unsigned char)c]) {
            seen[(unsigned char)c] = true;
            result += c;
        }
    }
    return result;
}
```

---

## 7. String to Integer (atoi) Logic

Convert a string representation of a number to an integer, handling signs, whitespace, and integer overflows.
```cpp
#include <string>
#include <climits>

int myAtoi(const std::string& s) {
    int i = 0, n = s.length();
    // 1. Skip leading whitespaces
    while (i < n && s[i] == ' ') i++;
    
    // 2. Check sign
    int sign = 1;
    if (i < n && (s[i] == '+' || s[i] == '-')) {
        sign = (s[i] == '-') ? -1 : 1;
        i++;
    }
    
    // 3. Parse digits & check overflow
    long long result = 0;
    while (i < n && s[i] >= '0' && s[i] <= '9') {
        result = result * 10 + (s[i] - '0');
        if (sign * result < INT_MIN) return INT_MIN;
        if (sign * result > INT_MAX) return INT_MAX;
        i++;
    }
    return sign * result;
}
```

---

## 8. Sliding Window on Strings

**Pattern:** Maintain a variable-size window defined by two pointers (`left` and `right`) to find substrings that satisfy a criteria (e.g. longest substring without repeating characters).

```cpp
#include <string>
#include <unordered_map>
#include <algorithm>

int lengthOfLongestSubstring(const std::string& s) {
    int left = 0, maxLen = 0;
    std::unordered_map<char, int> charMap; // char -> last seen index
    
    for (int right = 0; right < s.length(); ++right) {
        if (charMap.count(s[right])) {
            // Shrink window past the duplicate character
            left = std::max(left, charMap[s[right]] + 1);
        }
        charMap[s[right]] = right;
        maxLen = std::max(maxLen, right - left + 1);
    }
    return maxLen;
}
```
