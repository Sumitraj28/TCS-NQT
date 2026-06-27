# Stack & Queue — Worked Examples

---

## Example 1 — Balanced Parentheses Check

**Problem:** `s = "()[]{}"`. Check if it is valid.

**Trace:**
1. `i = 0`: character `'('` $\rightarrow$ push to stack. `stack = ['(']`
2. `i = 1`: character `')'` $\rightarrow$ match found with top `'('`. Pop from stack. `stack = []`
3. `i = 2`: character `'['` $\rightarrow$ push to stack. `stack = ['[']`
4. `i = 3`: character `']'` $\rightarrow$ match found with top `'['`. Pop from stack. `stack = []`
5. `i = 4`: character `'{'` $\rightarrow$ push to stack. `stack = ['{']`
6. `i = 5`: character `'}'` $\rightarrow$ match found with top `'{'`. Pop from stack. `stack = []`
7. Loop finishes. Stack is empty. Return `true`.

---

## Example 2 — Next Greater Element I

**Problem:** Find NGE of elements in `nums2 = [1, 3, 4, 2]` for subsets `nums1 = [4, 1, 2]`.

**Trace on nums2:**
- `st` (stack), `map` (value $\rightarrow$ next greater)
- `num = 1`: push 1. `st = [1]`
- `num = 3`: top 1 < 3 $\rightarrow$ `map[1] = 3`. Pop 1. Push 3. `st = [3]`
- `num = 4`: top 3 < 4 $\rightarrow$ `map[3] = 4`. Pop 3. Push 4. `st = [4]`
- `num = 2`: top 4 $\geq$ 2 $\rightarrow$ push 2. `st = [4, 2]`
- End. Elements left in stack `[4, 2]` have no NGE (default -1).
- Map lookup for nums1 `[4, 1, 2]`:
  - 4 $\rightarrow$ not in map $\rightarrow$ `-1`
  - 1 $\rightarrow$ `map[1]` $\rightarrow$ `3`
  - 2 $\rightarrow$ not in map $\rightarrow$ `-1`
- Result: `[-1, 3, -1]`.

**C++ Code Snippet:**
```cpp
#include <vector>
#include <stack>
#include <unordered_map>

std::vector<int> nextGreaterElement(const std::vector<int>& nums1, const std::vector<int>& nums2) {
    std::unordered_map<int, int> map;
    std::stack<int> st;
    for (int num : nums2) {
        while (!st.empty() && st.top() < num) {
            map[st.top()] = num;
            st.pop();
        }
        st.push(num);
    }
    std::vector<int> ans;
    for (int num : nums1) {
        ans.push_back(map.count(num) ? map[num] : -1);
    }
    return ans;
}
```
*Time Complexity: $O(N_1 + N_2)$ | Space Complexity: $O(N_2)$*
