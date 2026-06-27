# Strings — Cheat Sheet

## C++ Code Snippets

```cpp
// REVERSE STRING
int l=0, r=s.length()-1;
while(l<r) std::swap(s[l++], s[r--]);

// VALID PALINDROME (ignoring non-alphanumeric and case)
int l=0, r=s.length()-1;
while(l<r){
  while(l<r && !std::isalnum(s[l])) l++;
  while(l<r && !std::isalnum(s[r])) r--;
  if(std::tolower(s[l++]) != std::tolower(s[r--])) return false;
}

// VALID ANAGRAM (Frequency array)
if(s.length() != t.length()) return false;
int c[26] = {0};
for(int i=0; i<s.length(); i++){ c[s[i]-'a']++; c[t[i]-'a']--; }
for(int i=0; i<26; i++) if(c[i] != 0) return false;

// LONGEST COMMON PREFIX (Horizontal Scan)
std::string prefix = strs[0];
for(int i=1; i<strs.size(); i++){
  while(strs[i].find(prefix) != 0){
    prefix = prefix.substr(0, prefix.length()-1);
    if(prefix.empty()) return "";
  }
}

// VALID PARENTHESES (Stack)
std::stack<char> st;
for(char c:s){
  if(c=='(' || c=='{' || c=='[') st.push(c);
  else {
    if(st.empty()) return false;
    if(c==')' && st.top()!='(') return false;
    if(c=='}' && st.top()!='{') return false;
    if(c==']' && st.top()!='[') return false;
    st.pop();
  }
}

// LONGEST SUBSTRING WITHOUT REPEATING CHARACTERS (Sliding Window)
int l=0, mx=0;
int last[256]; std::fill(last, last+256, -1);
for(int r=0; r<s.length(); r++){
  if(last[(unsigned char)s[r]] >= l) l = last[(unsigned char)s[r]] + 1;
  last[(unsigned char)s[r]] = r;
  mx = std::max(mx, r-l+1);
}

// SPLIT WORDS
std::stringstream ss(s); std::string w;
std::vector<std::string> words;
while(ss >> w) words.push_back(w);
```

## Key Rules

| Rule | Detail |
|------|--------|
| Append | `s += c` (amortized O(1)), NOT `s = s + c` (O(N)) |
| Substring | `s.substr(pos, length)`, NOT `s.substr(pos, end)` |
| Param | Pass by `const std::string&` |
| Index | Cast signed char to `unsigned char` for array indexing |
| Search | `s.find()` returns `std::string::npos` on mismatch |
| Int conversion | `std::stoi()` (integer), `std::stoll()` (long long) |
| Digit offset | `int val = c - '0'` |
| Case change | `c ^ 32` toggles lower/upper case |
