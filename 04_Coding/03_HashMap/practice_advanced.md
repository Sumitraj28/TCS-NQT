# HashMap — Practice: Advanced / Prime Level (10 Questions)

> No overlap with basic or medium sets. Each includes a faster alternate method.

---

### Q1 — Continuous Subarray Sum (Multiple of K)
**Difficulty:** Hard | **Time:** 180s | **TCS Frequency:** Medium

`nums = [23, 2, 4, 6, 7]`, `k = 6`. Find if there is a contiguous subarray of size at least 2 that sums to a multiple of k.

**Full Solution (Prefix sum remainder index map):**
```cpp
#include <vector>
#include <unordered_map>

bool checkSubarraySum(std::vector<int>& nums, int k) {
    std::unordered_map<int, int> remMap;
    remMap[0] = -1;
    int sum = 0;
    
    for (int i = 0; i < nums.size(); ++i) {
        sum += nums[i];
        int rem = sum % k;
        if (remMap.count(rem)) {
            if (i - remMap[rem] >= 2) return true;
        } else {
            remMap[rem] = i;
        }
    }
    return false;
}
```
**Answer:** true (subarray `[2, 4]` sums to 6)

---

### Q2 — Subarray Sum Equals K (Negative Numbers)
**Difficulty:** Hard | **Time:** 120s | **TCS Frequency:** High

`nums = [1, -1, 0]`, `k = 0`. Find total subarrays with sum = 0.

**Full Solution:**
```cpp
#include <vector>
#include <unordered_map>

int subarraySumZero(std::vector<int>& nums, int k) {
    std::unordered_map<int, int> prefix;
    prefix[0] = 1;
    int sum = 0, count = 0;
    for (int num : nums) {
        sum += num;
        if (prefix.count(sum - k)) count += prefix[sum - k];
        prefix[sum]++;
    }
    return count;
}
```
**Answer:** 3 (subarrays: `[-1,0]`, `[0]`, `[1,-1,0]`)

---

### Q3 — First Unique Character (Optimized Stream logic)
**Difficulty:** Hard | **Time:** 180s | **TCS Frequency:** Medium

Implement a stream data structure that accepts characters and reports the first unique character.

**Full Solution (DLL + HashMap):**
Maintain a doubly-linked list of unique characters and a hash map (`nodeMap`) pointing to the list iterator. If a character is seen again, remove it from the list in O(1) and add it to a `duplicated` set/map so it's ignored in the future.

```cpp
#include <unordered_map>
#include <list>
#include <vector>

class FirstUnique {
private:
    std::list<int> uniqueList;
    std::unordered_map<int, std::list<int>::iterator> nodeMap;
    std::unordered_map<int, bool> duplicated;

public:
    FirstUnique(std::vector<int>& nums) {
        for (int num : nums) {
            add(num);
        }
    }
    
    int showFirstUnique() {
        if (uniqueList.empty()) return -1;
        return uniqueList.front();
    }
    
    void add(int value) {
        if (duplicated[value]) return;
        if (nodeMap.count(value)) {
            uniqueList.erase(nodeMap[value]);
            nodeMap.erase(value);
            duplicated[value] = true;
        } else {
            uniqueList.push_back(value);
            auto it = uniqueList.end();
            it--;
            nodeMap[value] = it;
        }
    }
};
```

**Complexity:** Time O(1) per operation | Space O(N)

---

### Q4 — Set Matrix Zeroes (Space-Optimized O(1) space)
**Difficulty:** Hard | **Time:** 200s | **TCS Frequency:** High

Solve Set Matrix Zeroes using O(1) extra space.

**Full Solution:**
Use the first row and first column of the matrix itself as markers. First, check if the first row and first column have any zeros. Then scan the rest of the matrix, setting `matrix[i][0] = 0` and `matrix[0][j] = 0` whenever `matrix[i][j] == 0`. Finally, use these markers to zero out the cells, and handle the first row/column zero status.

```cpp
#include <vector>

void setZeroes(std::vector<std::vector<int>>& matrix) {
    int m = matrix.size(), n = matrix[0].size();
    bool firstRowZero = false, firstColZero = false;
    
    for (int i = 0; i < m; ++i) {
        if (matrix[i][0] == 0) firstColZero = true;
    }
    for (int j = 0; j < n; ++j) {
        if (matrix[0][j] == 0) firstRowZero = true;
    }
    
    for (int i = 1; i < m; ++i) {
        for (int j = 1; j < n; ++j) {
            if (matrix[i][j] == 0) {
                matrix[i][0] = 0;
                matrix[0][j] = 0;
            }
        }
    }
    for (int i = 1; i < m; ++i) {
        for (int j = 1; j < n; ++j) {
            if (matrix[i][0] == 0 || matrix[0][j] == 0) {
                matrix[i][j] = 0;
            }
        }
    }
    if (firstColZero) {
        for (int i = 0; i < m; ++i) matrix[i][0] = 0;
    }
    if (firstRowZero) {
        for (int j = 0; j < n; ++j) matrix[0][j] = 0;
    }
}
```

**Complexity:** Time O(M * N) | Space O(1)

---

### Q5 — Find the Duplicate Number (O(1) space, O(N) time)
**Difficulty:** Hard | **Time:** 180s | **TCS Frequency:** High

Solve Find the Duplicate Number without modifying the array and in O(1) space.

**Full Solution (Floyd's Cycle Detection):**
Treat array indices as linked list pointers.
```cpp
int findDuplicateCycle(const std::vector<int>& nums) {
    int slow = nums[0], fast = nums[0];
    do {
        slow = nums[slow];
        fast = nums[nums[fast]];
    } while (slow != fast);
    
    int p1 = nums[0], p2 = slow;
    while (p1 != p2) {
        p1 = nums[p1];
        p2 = nums[p2];
    }
    return p1;
}
```

---

### Q6 — Subarrays with K Different Integers
**Difficulty:** Hard | **Time:** 240s | **TCS Frequency:** Low

`nums = [1,2,1,2,3]`, `k = 2`. Find number of subarrays with exactly k different integers.

**Full Solution:**
The number of subarrays with exactly K distinct integers can be computed as: `exact(K) = atMost(K) - atMost(K-1)`. The `atMost(K)` function uses sliding window where we increment a count when adding elements and shrink when unique keys count exceeds `K`.

```cpp
#include <vector>
#include <unordered_map>

int atMost(std::vector<int>& nums, int k) {
    std::unordered_map<int, int> count;
    int left = 0, result = 0;
    for (int right = 0; right < nums.size(); ++right) {
        if (count[nums[right]]++ == 0) k--;
        while (k < 0) {
            if (--count[nums[left]] == 0) k++;
            left++;
        }
        result += right - left + 1;
    }
    return result;
}

int subarraysWithKDistinct(std::vector<int>& nums, int k) {
    return atMost(nums, k) - atMost(nums, k - 1);
}
```

**Complexity:** Time O(N) | Space O(N)
**Answer:** 7

---

### Q7 — Longest Consecutive Sequence
**Difficulty:** Hard | **Time:** 180s | **TCS Frequency:** High

`nums = [100, 4, 200, 1, 3, 2]`. Find length of longest consecutive sequence in O(N) time.

**Full Solution:**
```cpp
#include <vector>
#include <unordered_set>
#include <algorithm>

int longestConsecutive(const std::vector<int>& nums) {
    std::unordered_set<int> s(nums.begin(), nums.end());
    int maxLen = 0;
    
    for (int num : nums) {
        if (!s.count(num - 1)) { // sequence start
            int curr = num;
            int len = 1;
            while (s.count(curr + 1)) {
                curr++;
                len++;
            }
            maxLen = std::max(maxLen, len);
        }
    }
    return maxLen;
}
```
**Answer:** 4 (sequence `[1, 2, 3, 4]`)

---

### Q8 — Max Points on a Line
**Difficulty:** Hard | **Time:** 240s | **TCS Frequency:** Low

Find max points on a line using slopes map.

**Full Solution:**
For each point `i`, compute the slopes to all other points `j`. To avoid precision issues with floating-point slope representation, represent the slope as a normalized ratio `(dy / gcd, dx / gcd)`. Store the slope frequencies in a map and take the maximum.

```cpp
#include <vector>
#include <map>
#include <algorithm>

int gcd(int a, int b) {
    while (b) {
        int temp = b;
        b = a % b;
        a = temp;
    }
    return a;
}

int maxPoints(std::vector<std::vector<int>>& points) {
    int n = points.size();
    if (n <= 2) return n;
    int maxVal = 0;
    for (int i = 0; i < n; ++i) {
        std::map<std::pair<int, int>, int> slopeMap;
        int duplicate = 1;
        for (int j = i + 1; j < n; ++j) {
            int dy = points[j][1] - points[i][1];
            int dx = points[j][0] - points[i][0];
            if (dy == 0 && dx == 0) {
                duplicate++;
                continue;
            }
            int g = gcd(dy, dx);
            dy /= g;
            dx /= g;
            if (dx < 0 || (dx == 0 && dy < 0)) {
                dy = -dy;
                dx = -dx;
            }
            slopeMap[{dy, dx}]++;
        }
        int localMax = 0;
        for (const auto& pair : slopeMap) {
            localMax = std::max(localMax, pair.second);
        }
        maxVal = std::max(maxVal, localMax + duplicate);
      }
      return maxVal;
}
```

**Complexity:** Time O(N² log N) | Space O(N)

---

### Q9 — Subarray Product Less Than K
**Difficulty:** Hard | **Time:** 150s | **TCS Frequency:** Low

Find count of contiguous subarrays whose product is strictly less than k. Use sliding window.

**Full Solution:**
Maintain a sliding window where the product of elements is less than `k`. Every time `right` advances, if product exceeds `k`, divide by elements from the `left` pointer. The number of valid subarrays ending at `right` is `right - left + 1`.

```cpp
#include <vector>

int numSubarrayProductLessThanK(std::vector<int>& nums, int k) {
    if (k <= 1) return 0;
    int prod = 1, count = 0, left = 0;
    for (int right = 0; right < nums.size(); ++right) {
        prod *= nums[right];
        while (prod >= k) {
            prod /= nums[left++];
        }
        count += right - left + 1;
    }
    return count;
}
```

**Complexity:** Time O(N) | Space O(1)

---

### Q10 — Fraction to Recurring Decimal
**Difficulty:** Hard | **Time:** 240s | **TCS Frequency:** Low

Convert fraction to decimal representation. If recurring, wrap inside parenthesis.
Use map to track fractional remainder positions.

**Full Solution:**
Use integer division to get the integral part. Compute remainder. If remainder is non-zero, append `.` and proceed with fractional division. Maintain a hash map mapping each remainder value to its index in the result string. If a remainder repeats, insert open parenthesis `(` at its index and append `)`.

```cpp
#include <string>
#include <unordered_map>
#include <algorithm>
#include <cmath>

std::string fractionToDecimal(int numerator, int denominator) {
    if (numerator == 0) return "0";
    std::string result = "";
    if ((numerator < 0) ^ (denominator < 0)) result += "-";
    
    long long num = std::abs((long long)numerator);
    long long den = std::abs((long long)denominator);
    
    result += std::to_string(num / den);
    long long rem = num % den;
    if (rem == 0) return result;
    
    result += ".";
    std::unordered_map<long long, int> remMap;
    while (rem != 0) {
        if (remMap.count(rem)) {
            result.insert(remMap[rem], "(");
            result += ")";
            break;
        }
        remMap[rem] = result.length();
        rem *= 10;
        result += std::to_string(rem / den);
        rem %= den;
    }
    return result;
}
```

**Complexity:** Time O(Denominator) | Space O(Denominator) (based on period length)
