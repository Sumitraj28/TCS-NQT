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
Group consecutive counts. We can optimize the space to O(1) by tracking only the current run length of identical characters (`curr`) and the previous run length (`prev`). Every time the character changes, the number of valid substrings formed by transition is `min(prev, curr)`.

```cpp
#include <string>
#include <algorithm>

int countBinarySubstrings(const std::string& s) {
    int curr = 1, prev = 0, result = 0;
    for (size_t i = 1; i < s.length(); ++i) {
        if (s[i] == s[i - 1]) {
            curr++;
        } else {
            result += std::min(prev, curr);
            prev = curr;
            curr = 1;
        }
    }
    return result + std::min(prev, curr);
}
```

**Complexity:** Time O(N) | Space O(1)
**Answer:** 6

---

### Q5 — Fizz Buzz
**Difficulty:** Medium | **Time:** 60s | **TCS Frequency:** High

Generate string representations of numbers 1 to 15. Standard FizzBuzz rules.

**Full Solution:**
Loop from 1 to N, pushing "Fizz", "Buzz", "FizzBuzz", or the number representation to a vector of strings based on divisibility.

```cpp
#include <vector>
#include <string>

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
```

**Complexity:** Time O(N) | Space O(1) (excluding result storage)
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

**Full Solution:**
A word's capitalization is valid if all characters are capitals, all are lowercase, or only the first character is capital. We can check this by counting uppercase letters.

```cpp
#include <string>
#include <cctype>

bool detectCapitalUse(const std::string& word) {
    int uppers = 0;
    for (char c : word) {
        if (std::isupper(c)) uppers++;
    }
    return uppers == word.length() || uppers == 0 || (uppers == 1 && std::isupper(word[0]));
}
```

**Complexity:** Time O(N) | Space O(1)
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

**Full Solution:**
Maintain a sliding window defined by `left` and `right` indices. Use a hash map or direct access table to store the last-seen index of each character. When a character is seen inside the current window, move the left pointer past its last occurrence.

```cpp
#include <string>
#include <algorithm>
#include <vector>

int lengthOfLongestSubstring(const std::string& s) {
    std::vector<int> lastIdx(256, -1);
    int left = 0, maxLen = 0;
    for (int right = 0; right < s.length(); ++right) {
        unsigned char c = s[right];
        if (lastIdx[c] >= left) {
            left = lastIdx[c] + 1;
        }
        lastIdx[c] = right;
        maxLen = std::max(maxLen, right - left + 1);
    }
    return maxLen;
}
```

**Complexity:** Time O(N) | Space O(1) (fixed 256 vector)
**Answer:** 3 ("abc")

---

### Q10 — Reverse Words in a Sentence
**Difficulty:** Medium | **Time:** 120s | **TCS Frequency:** High

`s = "the sky is blue"`. Reverse word by word.

**Full Solution:**
Tokenize the string using `std::stringstream` to extract words, store them in a vector, reverse the vector, and concatenate back using space separators.

```cpp
#include <string>
#include <sstream>
#include <vector>
#include <algorithm>

std::string reverseWords(const std::string& s) {
    std::stringstream ss(s);
    std::string word;
    std::vector<std::string> words;
    while (ss >> word) {
        words.push_back(word);
    }
    std::reverse(words.begin(), words.end());
    std::string result = "";
    for (size_t i = 0; i < words.size(); ++i) {
        result += words[i];
        if (i < words.size() - 1) result += " ";
    }
    return result;
}
```

**Complexity:** Time O(N) | Space O(N)
**Answer:** "blue is sky the"

---

### Q11 — Find All Anagrams in a String
**Difficulty:** Medium | **Time:** 150s | **TCS Frequency:** Medium

`s = "cbaebabacd"`, `p = "abc"`. Find all start indices of anagrams of `p` in `s`.

**Full Solution:**
We use a sliding window of size `p.length()`. Maintain two frequency count tables of size 26. When sliding the window to the right, we add the new character and remove the oldest character from the window count, then compare counts.

```cpp
#include <vector>
#include <string>

std::vector<int> findAnagrams(const std::string& s, const std::string& p) {
    std::vector<int> result;
    if (s.length() < p.length()) return result;
    
    std::vector<int> pCount(26, 0);
    std::vector<int> sCount(26, 0);
    for (size_t i = 0; i < p.length(); ++i) {
        pCount[p[i] - 'a']++;
        sCount[s[i] - 'a']++;
    }
    if (sCount == pCount) result.push_back(0);
    
    for (size_t i = p.length(); i < s.length(); ++i) {
        sCount[s[i] - 'a']++;
        sCount[s[i - p.length()] - 'a']--;
        if (sCount == pCount) {
            result.push_back(i - p.length() + 1);
        }
    }
    return result;
}
```

**Complexity:** Time O(N) | Space O(1)
**Answer:** [0, 6] (indices of "cba" and "bac")

---

### Q12 — String Compression
**Difficulty:** Medium | **Time:** 120s | **TCS Frequency:** Medium

`chars = ["a","a","b","b","c","c","c"]`. Compress in-place to `["a","2","b","2","c","3"]`.

**Full Solution:**
Use two pointers: `write` pointer to update the array in-place, and `i` pointer to read. Count occurrences of consecutive characters and write the character and its frequency (if > 1) in string representation.

```cpp
#include <vector>
#include <string>

int compress(std::vector<char>& chars) {
    int write = 0, i = 0;
    while (i < chars.size()) {
        char curr = chars[i];
        int count = 0;
        while (i < chars.size() && chars[i] == curr) {
            count++;
            i++;
        }
        chars[write++] = curr;
        if (count > 1) {
            std::string countStr = std::to_string(count);
            for (char c : countStr) {
                chars[write++] = c;
            }
        }
    }
    return write;
}
```

**Complexity:** Time O(N) | Space O(1)
**Answer:** length 6

---

### Q13 — Generate IP Addresses (IPv4 Validation)
**Difficulty:** Medium | **Time:** 120s | **TCS Frequency:** High

Check if `queryIP = "172.16.254.1"` is a valid IPv4 address.

**Full Solution:**
Split the string by `'.'`. Check that there are exactly 4 segments. For each segment, ensure: it's not empty, it contains only digits, its length is at most 3, there are no leading zeros if length > 1, and the numeric value is in the range `[0, 255]`.

```cpp
#include <string>
#include <vector>
#include <sstream>
#include <cctype>

bool isValidIPv4(const std::string& queryIP) {
    std::stringstream ss(queryIP);
    std::string token;
    std::vector<std::string> parts;
    while (std::getline(ss, token, '.')) {
        parts.push_back(token);
    }
    if (parts.size() != 4 || queryIP.back() == '.') return false;
    
    for (const std::string& part : parts) {
        if (part.empty() || part.length() > 3) return false;
        for (char c : part) {
            if (!std::isdigit(c)) return false;
        }
        if (part[0] == '0' && part.length() > 1) return false;
        int val = std::stoi(part);
        if (val < 0 || val > 255) return false;
    }
    return true;
}
```

**Complexity:** Time O(N) | Space O(N)

---

### Q14 — Multiply Strings (Big Integer Multiply)
**Difficulty:** Medium | **Time:** 150s | **TCS Frequency:** Medium

`num1 = "12"`, `num2 = "10"`. Multiply them without converting directly.

**Full Solution:**
Create a result vector of size `num1.length() + num2.length()` initialized to `0`. Loop backward through both strings, compute products of digits, and add to current position while handling carriage carries.

```cpp
#include <string>
#include <vector>

std::string multiply(std::string num1, std::string num2) {
    if (num1 == "0" || num2 == "0") return "0";
    int n1 = num1.size(), n2 = num2.size();
    std::vector<int> result(n1 + n2, 0);
    
    for (int i = n1 - 1; i >= 0; --i) {
        for (int j = n2 - 1; j >= 0; --j) {
            int mul = (num1[i] - '0') * (num2[j] - '0');
            int sum = mul + result[i + j + 1];
            result[i + j + 1] = sum % 10;
            result[i + j] += sum / 10;
        }
    }
    
    std::string s = "";
    for (int num : result) {
        if (!(s.empty() && num == 0)) {
            s += std::to_string(num);
        }
    }
    return s.empty() ? "0" : s;
}
```

**Complexity:** Time O(N * M) | Space O(N + M)
**Answer:** "120"

---

### Q15 — Compare Version Numbers
**Difficulty:** Medium | **Time:** 120s | **TCS Frequency:** Medium

`version1 = "1.01"`, `version2 = "1.001"`. Compare them.

**Full Solution:**
Traverse both version strings character by character. Split them into chunks separated by `'.'`. Convert each chunk to an integer (ignoring leading zeros) and compare. If one version runs out of chunks, treat its remaining values as `0`.

```cpp
#include <string>
#include <algorithm>

int compareVersion(std::string version1, std::string version2) {
    int i = 0, j = 0;
    int n1 = version1.length(), n2 = version2.length();
    while (i < n1 || j < n2) {
        int v1 = 0, v2 = 0;
        while (i < n1 && version1[i] != '.') {
            v1 = v1 * 10 + (version1[i] - '0');
            i++;
        }
        while (j < n2 && version2[j] != '.') {
            v2 = v2 * 10 + (version2[j] - '0');
            j++;
        }
        if (v1 < v2) return -1;
        if (v1 > v2) return 1;
        i++;
        j++;
    }
    return 0;
}
```

**Complexity:** Time O(N + M) | Space O(1)
**Answer:** 0 (equal)
