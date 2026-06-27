# Strings — 5 Worked Examples

---

## Example 1 — Valid Palindrome (Ignoring Alphanumeric & Case)

**Problem:** `s = "A man, a plan, a canal: Panama"`. Check if it's a valid palindrome.

**Trace:**
1. Two pointers: `left = 0`, `right = s.length() - 1`
2. Skip non-alphanumeric:
   - `left` moves past spaces and punctuation to 'A'.
   - `right` moves past spaces and punctuation to 'a'.
3. Compare lowercase: `tolower('A') == tolower('a')` → Match!
4. Move pointers: `left` goes to 'm', `right` goes to 'm' (from Panama).
5. Repeat until they meet at middle 'a'.

**C++ Code Snippet:**
```cpp
bool isPalindrome(const std::string& s) {
    int l = 0, r = s.length() - 1;
    while (l < r) {
        while (l < r && !std::isalnum(s[l])) l++;
        while (l < r && !std::isalnum(s[r])) r--;
        if (std::tolower(s[l++]) != std::tolower(s[r--])) return false;
    }
    return true;
}
```

---

## Example 2 — Reverse Vowels of a String

**Problem:** `s = "hello"`. Reverse only the vowels.

**Trace:**
- left=0 ('h'), right=4 ('o'): 'h' not vowel → left++.
- left=1 ('e'), right=4 ('o'): Both are vowels → swap → `s = "holle"`, left++, right--.
- left=2 ('l'), right=3 ('l'): Neither vowel → left++, right--.
- left > right → Done.

**Result:** "holle"

---

## Example 3 — String to Integer (atoi)

**Problem:** `s = "   -42"`. Convert to integer.

**Trace:**
1. Skip leading whitespaces: index moves to 3 (character '-').
2. Identify sign: `sign = -1`, index moves to 4.
3. Read digits: '4', '2'. Compute: `0 * 10 + 4 = 4`, then `4 * 10 + 2 = 42`.
4. Check overflow: 42 is well within `[INT_MIN, INT_MAX]`.
5. Apply sign: `-42`.

---

## Example 4 — Longest Common Prefix

**Problem:** `strs = ["flower","flow","flight"]`.

**Trace:**
1. Start prefix = `strs[0] = "flower"`.
2. Compare with "flow":
   - "flow".find("flower") != 0. Truncate prefix to "flowe".
   - "flow".find("flowe") != 0. Truncate prefix to "flow".
   - "flow".find("flow") == 0. Found! prefix = "flow".
3. Compare with "flight":
   - "flight".find("flow") != 0. Truncate to "flo".
   - "flight".find("flo") != 0. Truncate to "fl".
   - "flight".find("fl") == 0. Found! prefix = "fl".
4. Finish list.

**Result:** "fl"

---

## Example 5 — Valid Anagram

**Problem:** `s = "anagram"`, `t = "nagaram"`. Check if they are anagrams.

**Trace:**
1. Size check: both are size 7.
2. Initialize frequency array of size 26.
3. Count chars in `s`: count['a'-'a']+=3, count['n'-'a']+=1, count['g'-'a']+=1, count['r'-'a']+=1, count['m'-'a']+=1.
4. Decrement for chars in `t`: nagaram has 3 'a's, 1 'n', 1 'g', 1 'r', 1 'm'. All values decrement back to 0.
5. Verification: no counts are negative.

**Result:** True
