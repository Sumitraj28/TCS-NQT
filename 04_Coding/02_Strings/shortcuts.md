# Strings — Shortcuts (C++ STL)

C++ STL provides native string manipulation functions that save coding time during exams.

---

## 1. Character Classification Functions

Available in `<cctype>` (or `<ctype.h>`):
```cpp
#include <cctype>

std::isalnum(c);  // returns true if c is alphanumeric (A-Z, a-z, 0-9)
std::isalpha(c);  // returns true if c is alphabetic (A-Z, a-z)
std::isdigit(c);  // returns true if c is a digit (0-9)
std::islower(c);  // returns true if c is lowercase
std::isupper(c);  // returns true if c is uppercase
std::isspace(c);  // returns true if c is whitespace (' ', '\t', '\n')
std::tolower(c);  // returns lowercase char
std::toupper(c);  // returns uppercase char
```

---

## 2. String Iteration & Reversing

```cpp
#include <algorithm>

// Reverse string in-place
std::reverse(s.begin(), s.end());

// Sort characters in a string (e.g. to check anagrams)
std::sort(s.begin(), s.end());
```

---

## 3. Conversions

```cpp
#include <string>

// String to Integer
int val = std::stoi("1234");
long long val_ll = std::stoll("123456789012");
double val_d = std::stod("3.1415");

// Integer/Float to String
std::string s1 = std::to_string(456);
std::string s2 = std::to_string(3.14);
```

---

## 4. Substring Search & Manipulation

```cpp
#include <string>

// Find character/substring
size_t pos = s.find("target");
if (pos != std::string::npos) {
    // found at index pos
}

// Find last occurrence
size_t last_pos = s.rfind('c');

// Extract Substring: substr(startIndex, length)
std::string sub = s.substr(2, 5); // returns s[2..6] (5 characters)

// Remove elements from string
s.erase(s.begin() + index); // removes char at index
s.erase(startIndex, length); // removes range
```

---

## 5. String Stream (Splitting Words)

Split a sentence into words based on spaces:
```cpp
#include <sstream>
#include <vector>
#include <string>

std::vector<std::string> splitWords(const std::string& sentence) {
    std::stringstream ss(sentence);
    std::string word;
    std::vector<std::string> words;
    while (ss >> word) {
        words.push_back(word);
    }
    return words;
}
```
*Useful for sentence processing and word-pattern matching.*
```
