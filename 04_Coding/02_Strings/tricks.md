# Strings — Tricks, Traps, and TCS-Specific Patterns

## Trap 1 — Quadratic String Concatenation in Loops

**The trap:** Writing `s = s + c;` inside a loop of size N. In C++, `s + c` creates a brand new string copy of size `s.length()`, copying all characters over. This makes the loop run in O(N²) time instead of O(N), which results in a Time Limit Exceeded (TLE).

**Fix:** Use `s += c;` or `s.push_back(c);`. These append in-place in O(1) amortized time, keeping the loop O(N).

```cpp
// SLOW O(N²):
s = s + c;

// FAST O(N):
s += c;
```

---

## Trap 2 — Passing Strings by Value

**The trap:** Passing a large string to a helper function as `void solve(std::string s)`. C++ copies the entire string, which takes O(N) time and memory per function call.

**Fix:** Pass by reference or const reference: `void solve(const std::string& s)`.

---

## Trap 3 — Case Conversion with offset

**The trap:** Hardcoding ASCII offsets like `c - 32` or `c + 32` for case conversion. If you get the sign wrong, or apply it to a non-alphabetic character, it produces corrupt characters.

**Fix:** Use standard library functions `tolower(c)` and `toupper(c)`. Or use bitwise operations on letters:
- Convert to lower: `c | 32`
- Convert to upper: `c & ~32` (or `c & 95`)

---

## Trap 4 — Substring Search is O(N * M)

**The trap:** Doing `s.find(sub)` repeatedly. In worst case (e.g. `s="aaaaaaaaab"`, `sub="aaab"`), it runs in O(N * M) time.

**Fix:** Use a single-pass KMP algorithm if N and M are large (rare in TCS), or avoid nested searches.

---

## Trap 5 — std::stoi Overflow Crash

**The trap:** Using `std::stoi` on a string representing a number that exceeds integer limits (e.g. "99999999999"). It throws a `std::out_of_range` exception and crashes the program.

**Fix:** Use `long long` with `std::stoll()`, or write custom parse loops (like atoi) that check for overflows manually.

---

## Trap 6 — Removing Elements with `.erase()`

**The trap:** Using `s.erase(i, 1)` inside a loop to remove characters. Erase shifts all remaining elements, taking O(N) time. In a loop, this leads to O(N²) overall time complexity.

**Fix:** Use a Two-Pointer write approach. Read elements from left to right, write valid ones to `insertPos`, then truncate the string at the end.

---

## TCS Pattern Recognition

| Keyword in Problem | Pattern to Use |
|-------------------|---------------|
| "check anagram" | Frequency array of size 26 |
| "words in sentence" | `std::stringstream` |
| "longest prefix" | Vertical scanning or sorting first |
| "numeric value" | custom `atoi` loop checking `INT_MAX/INT_MIN` |
| "balanced parenthesis" | `std::stack<char>` |
| "distinct character substring" | Sliding Window + last-seen map |
