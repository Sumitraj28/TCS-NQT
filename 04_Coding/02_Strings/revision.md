# Strings — Quick Revision

## Core STL Shortcuts

```cpp
#include <algorithm>
#include <string>

std::reverse(s.begin(), s.end());                      // reverse in-place
std::sort(s.begin(), s.end());                         // sort character elements
size_t pos = s.find("sub");                            // search
if (pos != std::string::npos) { /* found */ }
std::string sub = s.substr(start, len);                // substring (pos, length!)
```

---

## Character Functions (`<cctype>`)

```cpp
std::isdigit(c);   // '0'-'9'
std::isalpha(c);   // 'A'-'Z', 'a'-'z'
std::isalnum(c);   // letter or digit
std::tolower(c);   // lower
std::toupper(c);   // upper
```

---

## Critical Fixes
1. **Append in loop:** Use `s += c` (O(1)), NOT `s = s + c` (O(N)).
2. **Substrings:** C++ `s.substr(start, length)` takes **length**, not end index.
3. **Pass by Reference:** Always use `const std::string&` in functions.
4. **Npos check:** `find` returns `std::string::npos` when not found. Check `!= std::string::npos`.

---

## Core Complexities
- Access / Size: O(1)
- Concat (char): O(1) amortized
- Substring extraction: O(len)
- Search: O(N) (char), O(N*M) (sub)
- Sort: O(N log N)
