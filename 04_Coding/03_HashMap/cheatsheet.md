# HashMap — Cheat Sheet

## C++ Code Snippets

```cpp
#include <unordered_map>
#include <unordered_set>
#include <map>
#include <set>

// CHECK EXISTENCE (O(1))
if (map.count(key)) { /* exists */ }

// SINGLE LOOKUP AND RETRIEVAL (O(1))
auto it = map.find(key);
if (it != map.end()) { int val = it->second; }

// INSERT AND DETECT DUPLICATE (O(1))
if (!set.insert(x).second) { /* duplicate found */ }

// SORT MAP BY VALUE (FREQ)
std::vector<std::pair<int, int>> vec(map.begin(), map.end());
std::sort(vec.begin(), vec.end(), [](const auto& a, const auto& b){
  return a.second > b.second; // sort descending by value
});

// SUBARRAY SUM = K
std::unordered_map<int, int> pre; pre[0] = 1;
int sum=0, count=0;
for(int x : nums) {
  sum += x;
  if(pre.count(sum - k)) count += pre[sum - k];
  pre[sum]++;
}

// LONGEST SUBARRAY SUM = K
std::unordered_map<int, int> preIdx; preIdx[0] = -1;
int sum=0, maxLen=0;
for(int i=0; i<nums.size(); i++) {
  sum += nums[i];
  if(preIdx.count(sum - k)) maxLen = std::max(maxLen, i - preIdx[sum - k]);
  if(!preIdx.count(sum)) preIdx[sum] = i; // only leftmost
}

// GROUP ANAGRAMS
std::unordered_map<std::string, std::vector<std::string>> groups;
for(auto s : strs) {
  std::string key = s; std::sort(key.begin(), key.end());
  groups[key].push_back(s);
}
```

## Key Rules

| Rule | Detail |
|------|--------|
| Bracket Check | Do NOT check key using `if(map[key])` -> inserts key. Use `count()`. |
| Custom Keys | Do NOT use `pair` as key in `std::unordered_map` -> compilation error. Use `std::map`. |
| Subarray Base | Always seed prefix sum maps with `[0]=1` or `[0]=-1` before loops. |
| Duplicate Set | Set insertion returns `{iterator, success_bool}`. |
| Map Iteration | Iterate using `for(const auto& pair : map)` -> `.first` is key, `.second` is value. |
