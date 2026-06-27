# Strings — Common Mistakes (8 Specific Traps)

---

### Mistake 1 — Quadratic Concatenation in Loops
Doing `s = s + c;` inside loops. Creates a new copy of size `s.length()` in each iteration, resulting in O(N²) overall time complexity.
**Fix:** Use `s += c;` or `s.push_back(c);`. Appends in-place in O(1) amortized.

---

### Mistake 2 — Passing Large Strings by Value
Writing function definitions like `void solve(std::string s)`. This copies the entire string which takes O(N) time and memory.
**Fix:** Pass by const reference: `void solve(const std::string& s)`.

---

### Mistake 3 — std::stoi Out of Range Crash
Using `std::stoi` on strings with values larger than standard integer limit. Causes crash / throws exception.
**Fix:** Use `std::stoll` for `long long`, or check length and value bounds manually before casting.

---

### Mistake 4 — Calling .length() inside `for` loops
Calling `for (int i = 0; i < s.length(); i++)`. While `s.length()` is O(1) in C++ (stored size), if you modify the string length inside the loop, the loop condition changes, which can lead to infinite loops or out-of-bounds access.
**Fix:** Save length before loop: `int n = s.length(); for (int i = 0; i < n; i++)` if size shouldn't change.

---

### Mistake 5 — Array Indexing with Signed Char
Using negative char directly as array index (`count[s[i]]`). If character has ASCII value > 127 (extended ASCII), standard `char` might behave as signed and overflow to negative integers, crashing the program.
**Fix:** Cast index to `unsigned char`: `count[(unsigned char)s[i]]`.

---

### Mistake 6 — Off-by-One in `.substr(pos, len)`
Thinking `s.substr(pos, len)` works like Python's `s[start:end]` (where the second parameter is the end position). In C++, the second parameter is the **length** of the substring, not the end index.
**Fix:** If you want string from index `l` to `r`, length is `r - l + 1`. Use `s.substr(l, r - l + 1)`.

---

### Mistake 7 — Comparing char Array with `std::string`
Using `strcmp` or direct pointer comparison on C++ strings.
**Fix:** In C++, `std::string` has overloaded `==` and `!=` operators. Simply write `s1 == s2`.

---

### Mistake 8 — Forgetting `std::string::npos`
Checking if a string is found by doing `if (s.find("target") >= 0)`. If `"target"` is at index 0, it works, but if it is not found, `find` returns `std::string::npos` (which is typically -1 / max size_t). A check `>= 0` will evaluate to `true` (since `npos` as unsigned is a very large positive number).
**Fix:** Always check: `if (s.find("target") != std::string::npos)`.
