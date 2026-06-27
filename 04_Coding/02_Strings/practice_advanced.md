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

Implement matching with support for `'.'` and `'*'`. `'.'` matches any single character. `'*'` matches zero or more of the preceding element.

**Full Solution (Dynamic Programming):**
Use a 2D DP array `dp[i][j]` representing whether prefix `s[0..i-1]` matches pattern `p[0..j-1]`.
- If characters match or `p[j-1] == '.'`, `dp[i][j] = dp[i-1][j-1]`.
- If `p[j-1] == '*'`, it can match 0 occurrences of the character before '*' (`dp[i][j] = dp[i][j-2]`), or if the character before '*' matches `s[i-1]`, it can match 1 or more occurrences (`dp[i][j] = dp[i][j-2] || dp[i-1][j]`).

```cpp
#include <string>
#include <vector>

bool isMatch(const std::string& s, const std::string& p) {
    int m = s.length(), n = p.length();
    std::vector<std::vector<bool>> dp(m + 1, std::vector<bool>(n + 1, false));
    dp[0][0] = true;
    for (int j = 1; j <= n; ++j) {
        if (p[j - 1] == '*') {
            dp[0][j] = dp[0][j - 2];
        }
    }
    for (int i = 1; i <= m; ++i) {
        for (int j = 1; j <= n; ++j) {
            if (p[j - 1] == '.' || p[j - 1] == s[i - 1]) {
                dp[i][j] = dp[i - 1][j - 1];
            } else if (p[j - 1] == '*') {
                dp[i][j] = dp[i][j - 2];
                if (p[j - 2] == '.' || p[j - 2] == s[i - 1]) {
                    dp[i][j] = dp[i][j] || dp[i - 1][j];
                }
            }
        }
    }
    return dp[m][n];
}
```

**Complexity:** Time O(M * N) | Space O(M * N)
**Answer:** Returns `true` or `false` based on match status.

---

### Q5 — Longest Duplicate Substring
**Difficulty:** Hard | **Time:** 300s | **TCS Frequency:** Low

Find the longest duplicate substring in `s = "banana"`.

**Full Solution:**
Use Binary Search on the length of the substring (from `1` to `N-1`). For a fixed length `mid`, check if any duplicate substring of that length exists using the Rabin-Karp rolling hash algorithm. To minimize collisions, we use a hash map or unordered_set to store hashes.

```cpp
#include <string>
#include <vector>
#include <unordered_set>
#include <algorithm>

std::string search(const std::string& s, int len) {
    if (len == 0) return "";
    long long h = 0, base = 256, mod = 1000000007, power = 1;
    for (int i = 0; i < len; ++i) {
        h = (h * base + s[i]) % mod;
        if (i > 0) power = (power * base) % mod;
    }
    std::unordered_set<long long> seen;
    seen.insert(h);
    for (size_t i = len; i < s.length(); ++i) {
        h = (h - s[i - len] * power) % mod;
        h = (h * base + s[i]) % mod;
        if (h < 0) h += mod;
        if (seen.count(h)) {
            return s.substr(i - len + 1, len);
        }
        seen.insert(h);
    }
    return "";
}

std::string longestDupSubstring(const std::string& s) {
    int left = 1, right = s.length() - 1;
    std::string result = "";
    while (left <= right) {
        int mid = left + (right - left) / 2;
        std::string dup = search(s, mid);
        if (!dup.empty()) {
            result = dup;
            left = mid + 1;
        } else {
            right = mid - 1;
        }
    }
    return result;
}
```

**Complexity:** Time O(N log N) average | Space O(N)
**Answer:** "ana"

---

### Q6 — Shortest Palindrome
**Difficulty:** Hard | **Time:** 240s | **TCS Frequency:** Low

Add minimum characters at front of `s = "aacecaaa"` to make it a palindrome.

**Full Solution:**
Construct a combined string `temp = s + "#" + reverse(s)`. Run the KMP table generation (LPS array) on `temp`. The last value of the LPS array `lps[temp.length() - 1]` tells us the length of the longest palindromic prefix of `s`. We then reverse the remaining suffix of `s` and prepend it to `s`.

```cpp
#include <string>
#include <vector>
#include <algorithm>

std::string shortestPalindrome(const std::string& s) {
    std::string rev = s;
    std::reverse(rev.begin(), rev.end());
    std::string temp = s + "#" + rev;
    int n = temp.length();
    std::vector<int> lps(n, 0);
    for (int i = 1; i < n; ++i) {
        int j = lps[i - 1];
        while (j > 0 && temp[i] != temp[j]) {
            j = lps[j - 1];
        }
        if (temp[i] == temp[j]) {
            j++;
        }
        lps[i] = j;
    }
    return rev.substr(0, s.length() - lps[n - 1]) + s;
}
```

**Complexity:** Time O(N) | Space O(N)
**Answer:** "aaacecaaa"

---

### Q7 — Substring with Concatenation of All Words
**Difficulty:** Hard | **Time:** 240s | **TCS Frequency:** Low

Find indices of substrings that are concatenation of list of equal-length words.

**Full Solution:**
Store the frequency count of all search words in a hash map. Since each word has the same length `wordLen`, we can apply a sliding window of step size `wordLen`. We scan starting at offset `0` to `wordLen - 1` to find valid windows containing exactly the counts.

```cpp
#include <vector>
#include <string>
#include <unordered_map>

std::vector<int> findSubstring(std::string s, std::vector<std::string>& words) {
    std::vector<int> result;
    if (s.empty() || words.empty()) return result;
    int wordLen = words[0].length();
    int numWords = words.size();
    int totalLen = wordLen * numWords;
    if (s.length() < totalLen) return result;
    
    std::unordered_map<std::string, int> wordCounts;
    for (const std::string& word : words) wordCounts[word]++;
    
    for (int i = 0; i < wordLen; ++i) {
        int left = i, count = 0;
        std::unordered_map<std::string, int> winCounts;
        for (int right = i; right + wordLen <= s.length(); right += wordLen) {
            std::string word = s.substr(right, wordLen);
            if (wordCounts.count(word)) {
                winCounts[word]++;
                count++;
                while (winCounts[word] > wordCounts[word]) {
                    std::string leftWord = s.substr(left, wordLen);
                    winCounts[leftWord]--;
                    count--;
                    left += wordLen;
                }
                if (count == numWords) {
                    result.push_back(left);
                }
            } else {
                winCounts.clear();
                count = 0;
                left = right + wordLen;
            }
        }
    }
    return result;
}
```

**Complexity:** Time O(N * L) where L is length of words | Space O(M) where M is total words
**Answer:** Returns indices vector.

---

### Q8 — Palindrome Partitioning II (Min Cuts)
**Difficulty:** Hard | **Time:** 240s | **TCS Frequency:** Low

Minimum cuts to partition `s = "aab"` into palindromes.

**Full Solution (Dynamic Programming):**
Use a DP array `cuts` where `cuts[i]` is the minimum cuts needed for suffix `s[0..i]`. Also use a 2D boolean array `pal[j][i]` to verify if substring `s[j..i]` is a palindrome. For each character `i`, find all valid palindromes ending at `i`, and minimize: `cuts[i] = min(cuts[i], cuts[j - 1] + 1)`.

```cpp
#include <string>
#include <vector>
#include <algorithm>

int minCut(std::string s) {
    int n = s.length();
    std::vector<int> cuts(n);
    std::vector<std::vector<bool>> pal(n, std::vector<bool>(n, false));
    for (int i = 0; i < n; ++i) cuts[i] = i;
    
    for (int i = 0; i < n; ++i) {
        for (int j = 0; j <= i; ++j) {
            if (s[i] == s[j] && (i - j <= 2 || pal[j + 1][i - 1])) {
                pal[j][i] = true;
                cuts[i] = (j == 0) ? 0 : std::min(cuts[i], cuts[j - 1] + 1);
            }
        }
    }
    return cuts[n - 1];
}
```

**Complexity:** Time O(N²) | Space O(N²)
**Answer:** 1 (cut "aa" | "b")

---

### Q9 — Text Justification (Greedy Word Wrap)
**Difficulty:** Hard | **Time:** 240s | **TCS Frequency:** Low

Fully justify text to max width.

**Full Solution:**
Iterate greedily through words to see how many can fit in a single line (sum of word lengths + spaces). If only one word fits or it is the last line, left-justify the text. Otherwise, distribute spaces evenly between words, placing any extra spaces from left to right.

```cpp
#include <vector>
#include <string>

std::vector<std::string> fullJustify(std::vector<std::string>& words, int maxWidth) {
    std::vector<std::string> result;
    int i = 0;
    while (i < words.size()) {
        int j = i + 1;
        int lineLen = words[i].length();
        while (j < words.size() && lineLen + 1 + words[j].length() <= maxWidth) {
            lineLen += 1 + words[j].length();
            j++;
        }
        int numWords = j - i;
        std::string line = "";
        if (j == words.size() || numWords == 1) {
            for (int k = i; k < j; ++k) {
                line += words[k];
                if (k < j - 1) line += " ";
            }
            line += std::string(maxWidth - line.length(), ' ');
        } else {
            int totalSpaces = maxWidth - (lineLen - (numWords - 1));
            int spacePerWord = totalSpaces / (numWords - 1);
            int extraSpaces = totalSpaces % (numWords - 1);
            for (int k = i; k < j - 1; ++k) {
                line += words[k];
                line += std::string(spacePerWord + (k - i < extraSpaces ? 1 : 0), ' ');
            }
            line += words[j - 1];
        }
        result.push_back(line);
        i = j;
    }
    return result;
}
```

**Complexity:** Time O(N) | Space O(1) (excluding output storage)
**Answer:** Fully justified lines.

---

### Q10 — Distinct Subsequences (DP)
**Difficulty:** Hard | **Time:** 200s | **TCS Frequency:** Low

Count how many times `t = "rabbit"` appears as subsequence of `s = "rabbbit"`.

**Full Solution:**
Using a 1D DP table `dp[j]` representing the number of subsequences of `t[0..j-1]` found in `s`. For each character of `s`, update the DP array backward to build count.

```cpp
#include <string>
#include <vector>

int numDistinct(std::string s, std::string t) {
    int m = s.length(), n = t.length();
    std::vector<double> dp(n + 1, 0);
    dp[0] = 1;
    for (int i = 1; i <= m; ++i) {
        for (int j = n; j >= 1; --j) {
            if (s[i - 1] == t[j - 1]) {
                dp[j] += dp[j - 1];
            }
        }
    }
    return (int)dp[n];
}
```

**Complexity:** Time O(M * N) | Space O(N)
**Answer:** 3
