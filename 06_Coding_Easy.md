# TCS NQT 2026 — Easy Coding Complete C++ Guide
**Exam Focus: Arrays, Strings, & Math in C++ (1 Question, 35 Minutes)**

This guide has been prepared entirely in **C++ (4.9.2)** to help you master the Easy Coding section. Under the exam interface, you must read inputs from standard input and print output to standard output.

> [!IMPORTANT]
> **TCS Compiler Rule**: You must click `"Compile Code"` AND `"Save Code"` (or `"Submit Code"`). If you do not click Save/Submit, your code will not be evaluated and you will get 0 marks.

---

## 💻 PART A: Topic-by-Topic Notes + C++ Solutions

### 1. Circular Array / House Robber Variant
* **Core Concept**: Maximizing a sum from a circular array where adjacent elements cannot be selected.
* **C++ Solution Template**:
  ```cpp
  #include <iostream>
  #include <vector>
  #include <algorithm>

  using namespace std;

  int solveLinear(vector<int>& nums, int start, int end) {
      int prev2 = 0, prev1 = 0;
      for (int i = start; i <= end; i++) {
          int temp = max(prev1, prev2 + nums[i]);
          prev2 = prev1;
          prev1 = temp;
      }
      return prev1;
  }

  int robCircular(vector<int>& nums) {
      int n = nums.size();
      if (n == 0) return 0;
      if (n == 1) return nums[0];
      return max(solveLinear(nums, 0, n - 2), solveLinear(nums, 1, n - 1));
  }
  ```
* **Edge Cases to Handle**: Single element ($N=1$), empty input, all zeros.
* **TCS NQT Trap**: For large constraints ($N = 10^9$), running a DP loop will result in TLE/MLE. Use a mathematical formula or index-based sum instead of looping.

---

### 2. Number Properties
* **Core Concept**: Modulo arithmetic, digit sum extractions, and square root limits.
* **C++ Solution Template (Prime Check)**:
  ```cpp
  #include <iostream>

  using namespace std;

  bool isPrime(int n) {
      if (n <= 1) return false;
      if (n <= 3) return true;
      if (n % 2 == 0 || n % 3 == 0) return false;
      for (int i = 5; i * i <= n; i += 6) {
          if (n % i == 0 || n % (i + 2) == 0) return false;
      }
      return true;
  }
  ```
* **Edge Cases**: $N \le 1$, negative numbers, extremely large values.
* **TCS NQT Trap**: Using a simple $O(N)$ loop for primality checks will fail on large prime test cases. Always use the $O(\sqrt{N})$ loop template.

---

### 3. String Operations
* **Core Concept**: Slicing, character frequency tracking, and sliding windows.
* **C++ Solution Template (Anagram Check)**:
  ```cpp
  #include <iostream>
  #include <string>
  #include <vector>
  #include <algorithm>

  using namespace std;

  bool isAnagram(string s1, string s2) {
      // Remove spaces and convert to lowercase
      string clean1 = "", clean2 = "";
      for (char c : s1) if (c != ' ') clean1 += tolower(c);
      for (char c : s2) if (c != ' ') clean2 += tolower(c);
      
      if (clean1.length() != clean2.length()) return false;
      
      vector<int> count(26, 0);
      for (char c : clean1) count[c - 'a']++;
      for (char c : clean2) count[c - 'a']--;
      
      for (int val : count) {
          if (val != 0) return false;
      }
      return true;
  }
  ```
* **Edge Cases**: Empty strings, mixed case, white spaces.
* **TCS NQT Trap**: Using nested loops ($O(N^2)$) to compare string character counts will time out. Use a frequency vector of size 26 for $O(N)$ execution.

---

### 4. Array Basics
* **Core Concept**: Pointers, relative ordering, and linear scans.
* **C++ Solution Template (Second Largest)**:
  ```cpp
  #include <iostream>
  #include <vector>
  #include <climits>

  using namespace std;

  int getSecondLargest(vector<int>& arr) {
      int n = arr.size();
      if (n < 2) return -1;
      
      int first = INT_MIN;
      int second = INT_MIN;
      
      for (int i = 0; i < n; i++) {
          if (arr[i] > first) {
              second = first;
              first = arr[i];
          } else if (arr[i] > second && arr[i] != first) {
              second = arr[i];
          }
      }
      return (second == INT_MIN) ? -1 : second;
  }
  ```
* **Edge Cases**: Less than 2 elements, all elements equal, negative elements.
* **TCS NQT Trap**: Sorting the array first ($O(N \log N)$), which times out on large arrays and fails to easily filter duplicate values. Use a single pass $O(N)$ solution.

---

### 5. GCD / LCM / HCF Problems
* **Core Concept**: Euclidean division algorithm.
* **C++ Solution Template**:
  ```cpp
  #include <iostream>

  using namespace std;

  long long getGCD(long long a, long long b) {
      while (b != 0) {
          long long temp = a % b;
          a = b;
          b = temp;
      }
      return a;
  }

  long long getLCM(long long a, long long b) {
      if (a == 0 || b == 0) return 0;
      return (a * b) / getGCD(a, b);
  }
  ```
* **Edge Cases**: Zero values, large numbers causing overflow.
* **TCS NQT Trap**: Multiplying `a * b` without casting to `long long` first, which causes integer overflow. Always compute LCM as `(a / GCD) * b` to prevent intermediate overflows.

---

### 6. Fibonacci & Factorial
* **Core Concept**: Accumulator variables and modulo arithmetic.
* **C++ Solution Template (Iterative Fibonacci)**:
  ```cpp
  #include <iostream>

  using namespace std;

  long long getFibonacci(int n) {
      if (n <= 0) return 0;
      if (n == 1) return 1;
      long long prev2 = 0, prev1 = 1;
      for (int i = 2; i <= n; i++) {
          long long curr = (prev2 + prev1) % 1000000007; // Modulo arithmetic to prevent overflow
          prev2 = prev1;
          prev1 = curr;
      }
      return prev1;
  }
  ```
* **Edge Cases**: $N = 0$, negative inputs.
* **TCS NQT Trap**: Using recursion. Large values of $N$ cause stack overflows and TLE. Use iteration.

---

## 📋 PART B: Actual TCS NQT PYQ-Matching Problems

### Problem 1: The Ritual of Circular Kriya (Nov 2024 Shift 1 Q1)
* **Problem Statement**: An array of integers represents values in a circle. You must select elements such that no two adjacent elements are chosen. Maximize the sum.
* **C++ Solution**:
  ```cpp
  #include <iostream>
  #include <vector>
  #include <algorithm>

  using namespace std;

  long long solveLinear(vector<int>& arr, int start, int end) {
      long long prev2 = 0, prev1 = 0;
      for (int i = start; i <= end; i++) {
          long long temp = max(prev1, prev2 + arr[i]);
          prev2 = prev1;
          prev1 = temp;
      }
      return prev1;
  }

  int main() {
      int n;
      if (!(cin >> n)) return 0;
      vector<int> arr(n);
      for (int i = 0; i < n; i++) {
          cin >> arr[i];
      }
      
      if (n == 0) {
          cout << 0 << endl;
      } else if (n == 1) {
          cout << arr[0] << endl;
      } else {
          long long ans = max(solveLinear(arr, 0, n - 2), solveLinear(arr, 1, n - 1));
          cout << ans << endl;
      }
      return 0;
  }
  ```

---

### Problem 2: Longest Palindromic Substring (Nov 2024 Shift 2 Q1)
* **Problem Statement**: Find the longest contiguous substring that reads the same forward and backward.
* **C++ Solution**:
  ```cpp
  #include <iostream>
  #include <string>
  #include <algorithm>

  using namespace std;

  string expandAroundCenter(string s, int left, int right) {
      while (left >= 0 && right < s.length() && s[left] == s[right]) {
          left--;
          right++;
      }
      return s.substr(left + 1, right - left - 1);
  }

  int main() {
      string s;
      if (!(cin >> s)) return 0;
      
      if (s.empty()) {
          cout << "" << endl;
          return 0;
      }
      
      string longest = "";
      for (int i = 0; i < s.length(); i++) {
          // Odd length palindromes
          string p1 = expandAroundCenter(s, i, i);
          if (p1.length() > longest.length()) {
              longest = p1;
          }
          // Even length palindromes
          string p2 = expandAroundCenter(s, i, i + 1);
          if (p2.length() > longest.length()) {
              longest = p2;
          }
      }
      cout << longest << endl;
      return 0;
  }
  ```

---

### Problem 3: Decrypting King's Secret Message (Nov 2024 Shift 1 Q2)
* **Problem Statement**: A string is encrypted using a substitution cipher. You are given the encrypted string and a list of integers representing shift values. Decrypt the message.
* **C++ Solution**:
  ```cpp
  #include <iostream>
  #include <string>
  #include <vector>

  using namespace std;

  int main() {
      string s;
      if (!(cin >> s)) return 0;
      
      int num;
      vector<int> shifts;
      while (cin >> num) {
          shifts.push_back(num);
      }
      
      if (shifts.empty()) {
          cout << s << endl;
          return 0;
      }
      
      string decrypted = "";
      for (int i = 0; i < s.length(); i++) {
          char char_val = s[i];
          if (isalpha(char_val)) {
              int shift = shifts[i % shifts.size()];
              char base = isupper(char_val) ? 'A' : 'a';
              // Perform backward shift and wrap around modulo 26
              int decrypted_char_val = (char_val - base - shift) % 26;
              if (decrypted_char_val < 0) {
                  decrypted_char_val += 26;
              }
              decrypted += (base + decrypted_char_val);
          } else {
              decrypted += char_val;
          }
      }
      cout << decrypted << endl;
      return 0;
  }
  ```

---

## 🔮 PART C: Easy Coding Question Patterns for June 2026

### 1. Predicted: Modified Fibonacci with Condition
* **Problem Statement**: Generate Fibonacci numbers up to $N$ and print only those that are even and divisible by 3.
* **C++ Solution**:
  ```cpp
  #include <iostream>
  #include <vector>

  using namespace std;

  int main() {
      long long n;
      if (!(cin >> n)) return 0;
      
      long long prev2 = 0, prev1 = 1;
      bool first = true;
      while (prev2 <= n) {
          if (prev2 % 2 == 0 && prev2 % 3 == 0 && prev2 != 0) {
              if (!first) cout << " ";
              cout << prev2;
              first = false;
          }
          long long curr = prev2 + prev1;
          prev2 = prev1;
          prev1 = curr;
      }
      cout << endl;
      return 0;
  }
  ```

---

### 2. Predicted: String Consonant Encoding
* **Problem Statement**: Shift all consonants in a string forward by $K$ positions, while vowels remain unchanged.
* **C++ Solution**:
  ```cpp
  #include <iostream>
  #include <string>
  #include <unordered_set>

  using namespace std;

  bool isVowel(char c) {
      char lower = tolower(c);
      return (lower == 'a' || lower == 'e' || lower == 'i' || lower == 'o' || lower == 'u');
  }

  int main() {
      string s;
      int k;
      if (!(cin >> s >> k)) return 0;
      
      for (int i = 0; i < s.length(); i++) {
          char c = s[i];
          if (isalpha(c) && !isVowel(c)) {
              char base = isupper(c) ? 'A' : 'a';
              s[i] = (c - base + k) % 26 + base;
          }
      }
      cout << s << endl;
      return 0;
  }
  ```

---

### 3. Predicted: Circular Array K Rotations Element Lookup
* **Problem Statement**: Given an array, rotate it right by $K$ positions and return the element at a specific index $I$.
* **C++ Solution**:
  ```cpp
  #include <iostream>
  #include <vector>

  using namespace std;

  int main() {
      int n, k, target_idx;
      if (!(cin >> n >> k >> target_idx)) return 0;
      vector<int> arr(n);
      for (int i = 0; i < n; i++) {
          cin >> arr[i];
      }
      
      int effective_rotation = k % n;
      int original_idx = (target_idx - effective_rotation + n) % n;
      cout << arr[original_idx] << endl;
      return 0;
  }
  ```

---

### 4. Predicted: Digit Product Sum Equality
* **Problem Statement**: Find all numbers between $A$ and $B$ (inclusive) where the sum of digits is equal to the product of digits.
* **C++ Solution**:
  ```cpp
  #include <iostream>
  #include <string>

  using namespace std;

  bool isSumProductEqual(int num) {
      int sum = 0;
      int prod = 1;
      int temp = num;
      while (temp > 0) {
          int digit = temp % 10;
          sum += digit;
          prod *= digit;
          temp /= 10;
      }
      return sum == prod;
  }

  int main() {
      int a, b;
      if (!(cin >> a >> b)) return 0;
      bool first = true;
      for (int i = a; i <= b; i++) {
          if (isSumProductEqual(i)) {
              if (!first) cout << " ";
              cout << i;
              first = false;
          }
      }
      cout << endl;
      return 0;
  }
  ```

---

### 5. Predicted: Pattern Value Discovery
* **Problem Statement**: Output the $N$-th value of the series: $1, 2, 6, 15, 31, 56, \dots$. (First differences are squares: $+1, +4, +9, \dots$).
* **C++ Solution**:
  ```cpp
  #include <iostream>

  using namespace std;

  int main() {
      long long n;
      if (!(cin >> n)) return 0;
      
      if (n <= 1) {
          cout << 1 << endl;
      } else {
          long long ans = 1 + ((n - 1) * n * (2 * n - 1)) / 6;
          cout << ans << endl;
      }
      return 0;
  }
  ```

---

## 🧹 PART D: Coding Hygiene Checklist for TCS NQT (C++ Specific)

### 1. Fast I/O Setup
Always write these lines at the beginning of your `main()` function to speed up console input-output operations.
```cpp
ios_base::sync_with_stdio(false);
cin.tie(NULL);
```

### 2. Reading Inputs till EOF
For problems where the size is not given first, read using a `while` loop:
```cpp
int val;
vector<int> arr;
while (cin >> val) {
    arr.push_back(val);
}
```

### 3. Preventing Integer Overflow
TCS NQT test cases contain values that exceed standard 32-bit limits ($2^{31}-1$). Always use `long long` instead of `int` for sums, factorials, and products.

### 4. Vector Safety
Ensure you do not access indices like `arr[-1]` or `arr[size]`. Always wrap boundaries using `(idx + size) % size`.
