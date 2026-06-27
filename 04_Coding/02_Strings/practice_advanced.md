# Strings — Practice: Advanced / Prime Level (10 Questions)

> No overlap with basic or medium sets. Each includes a faster alternate method.

---

### Q1 — Minimum Window Substring
**Difficulty:** Hard | **Time:** 240s | **TCS Frequency:** Medium

`s = "ADOBECODEBANC"`, `t = "ABC"`. Find minimum window in `s` containing all chars of `t`.

**Full Solution (Sliding Window + two pointer frequency check):**

```cpp
#include <string>
#include <unordered_map>
#include <climits>

std::string minWindow(const std::string& s, const std::string& t) {
    int m[128] = {0};
    for (char c : t) m[(unsigned char)c]++;
    int count = t.length();
    int left = 0, right = 0, head = 0, minLen = INT_MAX;
    
    while (right < s.length()) {
        if (m[(unsigned char)s[right++]]-- > 0) count--;
        while (count == 0) {
            if (right - left < minLen) {
                minLen = right - left;
                head = left;
            }
            if (m[(unsigned char)s[left++]]++ == 0) count++;
        }
    }
    return minLen == INT_MAX ? "" : s.substr(head, minLen);
}
```

**Answer:** "BANC"

---

### Q2 — Longest Palindromic Substring
**Difficulty:** Hard | **Time:** 180s | **TCS Frequency:** High

`s = "babad"`. Find longest palindromic substring.

**Full Solution (Expand Around Center — O(N²)):**
```cpp
#include <string>
#include <algorithm>

int expand(const std::string& s, int left, int right) {
    while (left >= 0 && right < s.length() && s[left] == s[right]) {
        left--; right++;
    }
    return right - left - 1;
}

std::string longestPalindrome(const std::string& s) {
    if (s.empty()) return "";
    int start = 0, end = 0;
    for (int i = 0; i < s.length(); ++i) {
        int len1 = expand(s, i, i);     // odd length
        int len2 = expand(s, i, i + 1); // even length
        int len = std::max(len1, len2);
        if (len > end - start) {
            start = i - (len - 1) / 2;
            end = i + len / 2;
        }
    }
    return s.substr(start, end - start + 1);
}
```

**Alternate (Manacher's Algorithm — O(N)):** Linear time but complex to code. Expand around center is usually accepted in TCS due to N ≤ 1000 constraints.

---

### Q3 — Edit Distance (DP on Strings)
**Difficulty:** Hard | **Time:** 200s | **TCS Frequency:** Medium

Find minimum operations (insert, delete, replace) to convert `word1 = "horse"` to `word2 = "ros"`.

**Full Solution:**
```cpp
#include <string>
#include <vector>
#include <algorithm>

int minDistance(const std::string& word1, const std::string& word2) {
    int m = word1.length(), n = word2.length();
    std::vector<std::vector<int>> dp(m + 1, std::vector<int>(n + 1, 0));
    for (int i = 0; i <= m; ++i) dp[i][0] = i;
    for (int j = 0; j <= n; ++j) dp[0][j] = j;
    
    for (int i = 1; i <= m; ++i) {
        for (int j = 1; j <= n; ++j) {
            if (word1[i-1] == word2[j-1]) {
                dp[i][j] = dp[i-1][j-1];
            } else {
                dp[i][j] = 1 + std::min({dp[i-1][j], dp[i][j-1], dp[i-1][j-1]});
            }
        }
    }
    return dp[m][n];
}
```

**Answer:** 3

---

### Q4 — Regular Expression Matching
**Difficulty:** Hard | **Time:** 240s | **TCS Frequency:** Low

Implement matching with support for `'.'` and `'*'`.

---

### Q5 — Longest Duplicate Substring
**Difficulty:** Hard | **Time:** 300s | **TCS Frequency:** Low

Find the longest duplicate substring in `s = "banana"`.

**Full Solution:** Binary Search on length + Rabin-Karp Rolling Hash.

**Answer:** "ana"

---

### Q6 — Shortest Palindrome
**Difficulty:** Hard | **Time:** 240s | **TCS Frequency:** Low

Add minimum characters at front of `s = "aacecaaa"` to make it a palindrome.

**Full Solution:** KMP table suffix match.
**Answer:** "aaacecaaa"

---

### Q7 — Substring with Concatenation of All Words
**Difficulty:** Hard | **Time:** 240s | **TCS Frequency:** Low

Find indices of substrings that are concatenation of list of equal-length words.

---

### Q8 — Palindrome Partitioning II (Min Cuts)
**Difficulty:** Hard | **Time:** 240s | **TCS Frequency:** Low

Minimum cuts to partition `s = "aab"` into palindromes.

**Answer:** 1 (cut "aa" | "b")

---

### Q9 — Text Justification (Greedy Word Wrap)
**Difficulty:** Hard | **Time:** 240s | **TCS Frequency:** Low

Fully justify text to max width.

---

### Q10 — Distinct Subsequences (DP)
**Difficulty:** Hard | **Time:** 200s | **TCS Frequency:** Low

Count how many times `t = "rabbit"` appears as subsequence of `s = "rabbbit"`.

**Answer:** 3
