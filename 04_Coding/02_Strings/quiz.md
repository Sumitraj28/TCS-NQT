# Strings — Quiz

## 10 Q&A Flashcard Pairs

**Q1:** What is the time complexity of `s = s + c;` inside a loop of size N in C++?
**A1:** O(N²) — because the addition operator creates a copy of the entire string each time. Use `s += c;` for O(N).

**Q2:** Why should we pass strings by reference (e.g. `const std::string&`) in function calls?
**A2:** Passing by value copies the entire string in memory taking O(N) time and space. Passing by reference is O(1) time.

**Q3:** In C++, what does the second parameter of `s.substr(pos, len)` represent?
**A3:** It represents the **length** of the substring, not the end position index.

**Q4:** What does `s.find("target")` return if the string `"target"` is not present?
**A4:** It returns `std::string::npos`.

**Q5:** How do you convert a digit character `'5'` to its integer value `5` in C++?
**A5:** Subtract the char `'0'`: `int val = c - '0';`.

**Q6:** How do you count binary substrings with equal consecutive 0s and 1s?
**A6:** Count consecutive block sizes, then sum the minimum of adjacent block counts (e.g., `sum(min(blocks[i], blocks[i-1]))`).

**Q7:** What data structure is used to validate balanced brackets like `{[()]}`?
**A7:** A Stack (`std::stack<char>`).

**Q8:** Why does using signed char as array index (`count[s[i]]`) sometimes crash programs in C++?
**A8:** Extended ASCII chars can evaluate to negative numbers, resulting in negative array indexing (segmentation fault). Cast index to `(unsigned char)s[i]`.

**Q9:** What is the average time complexity of `std::stoi`?
**A9:** O(L) where L is the length of the string.

**Q10:** How does sliding window find the longest unique substring?
**A10:** Maintain two pointers `left` and `right`. Track the last seen index of each char. If `s[right]` was seen inside the window, shift `left` to index after last seen.

---

## 5 True / False Statements

**TF1:** In C++, `std::tolower(c)` modifies the input character in-place.
**→ FALSE.** It returns the lowercase version of `c` without modifying the original variable.

**TF2:** In C++, `s.find('a')` takes O(log N) time if the string is sorted.
**→ FALSE.** `std::string::find` is a linear search taking O(N) time. To do O(log N) on a sorted string, you must use binary search.

**TF3:** Two strings of different lengths can be isomorphic.
**→ FALSE.** Isomorphic mapping requires a one-to-one character bijection, which is impossible if their lengths differ.

**TF4:** In C++, `std::reverse(s.begin(), s.end())` takes O(N) time and O(N) auxiliary space.
**→ FALSE.** It takes O(N) time but works in-place using O(1) auxiliary space.

**TF5:** A string of all identical characters (e.g., "aaaa") is a palindrome.
**→ TRUE.** It reads the same forwards and backwards.
