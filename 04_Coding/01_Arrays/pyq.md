# Arrays — Previous Year Style Questions (TCS NQT)

> Tagged by difficulty, with solution in C++.
> No duplicates with practice or important_questions files.

---

### PYQ1
**TCS NQT Style | Difficulty:** Easy | **Time:** 60s | **TCS Frequency:** High

**Problem:** An array `arr[]` contains n integers. Write a program to find the sum of elements present at even positions (0-indexed: 0, 2, 4, ...) and odd positions separately.

Input: `arr = [5, 3, 8, 1, 9, 4]`  
Output: Even-index sum = 22, Odd-index sum = 8

**C++ Solution:**
```cpp
#include <iostream>
#include <vector>

void printSums(const std::vector<int>& arr) {
    int evenSum = 0, oddSum = 0;
    for (size_t i = 0; i < arr.size(); ++i) {
        if (i % 2 == 0) evenSum += arr[i];
        else            oddSum  += arr[i];
    }
    std::cout << "Even-index sum = " << evenSum << ", Odd-index sum = " << oddSum << "\n";
}
```

---

### PYQ2
**TCS NQT Style | Difficulty:** Easy | **Time:** 60s | **TCS Frequency:** High

**Problem:** Given an integer array, find the number of elements greater than their next element (i.e., arr[i] > arr[i+1]).

Input: `arr = [4, 2, 7, 3, 8, 5]`  
Output: 3

**C++ Solution:**
```cpp
#include <vector>

int countGreaterPairs(const std::vector<int>& arr) {
    int count = 0;
    for (size_t i = 0; i < arr.size() - 1; ++i) {
        if (arr[i] > arr[i + 1]) count++;
    }
    return count;
}
```

---

### PYQ3
**TCS NQT Style | Difficulty:** Medium | **Time:** 120s | **TCS Frequency:** High

**Problem:** Given an array of 0s and 1s only, find the position of 0 that when replaced by 1 gives the longest run of 1s.

Input: `arr = [1,1,0,1,1,1,0,0,1,1]`  
Output: Position 2, new max run = 6

**C++ Solution:**
```cpp
#include <vector>
#include <algorithm>

int findZeroToFlip(const std::vector<int>& arr) {
    int left = 0, maxLen = 0, lastZeroPos = -1, bestZeroIndex = -1;
    for (int right = 0; right < arr.size(); ++right) {
        if (arr[right] == 0) {
            left = lastZeroPos + 1;
            lastZeroPos = right;
        }
        if (right - left + 1 > maxLen) {
            maxLen = right - left + 1;
            bestZeroIndex = lastZeroPos;
        }
    }
    return bestZeroIndex;
}
```

---

### PYQ4
**TCS NQT Style | Difficulty:** Medium | **Time:** 150s | **TCS Frequency:** High

**Problem:** You are given `n` numbers. You need to rearrange them such that the sum of `|arr[i] - arr[i-1]|` is maximized.

Input: `arr = [1, 2, 4, 8]`  
Output: 10

**C++ Solution:**
```cpp
#include <vector>
#include <algorithm>
#include <cmath>

int maxDiffSum(std::vector<int>& arr) {
    int n = arr.size();
    std::sort(arr.begin(), arr.end());
    std::vector<int> res(n);
    int l = 0, r = n - 1;
    for (int i = 0; i < n; ++i) {
        if (i % 2 == 0) res[i] = arr[l++];
        else            res[i] = arr[r--];
    }
    int sum = 0;
    for (int i = 1; i < n; ++i) {
        sum += std::abs(res[i] - res[i-1]);
    }
    return sum;
}
```

---

### PYQ5
**TCS NQT Style | Difficulty:** Medium | **Time:** 120s | **TCS Frequency:** High

**Problem:** Given an array, rotate it left by d positions.

Input: `arr = [1,2,3,4,5,6,7]`, d=2  
Output: `[3,4,5,6,7,1,2]`

**C++ Solution:**
```cpp
#include <vector>
#include <algorithm>

void rotateLeft(std::vector<int>& arr, int d) {
    int n = arr.size();
    d = d % n;
    std::reverse(arr.begin(), arr.begin() + d);
    std::reverse(arr.begin() + d, arr.end());
    std::reverse(arr.begin(), arr.end());
}
```

---

### PYQ6
**TCS NQT Style | Difficulty:** Medium | **Time:** 120s | **TCS Frequency:** High

**Problem:** Given an array of integers (possibly negative), find the maximum sum you can get by selecting at most one contiguous subarray or an empty subarray (sum = 0).

Input: `arr = [-3, -1, -2]`  
Output: 0

**C++ Solution:**
```cpp
#include <vector>
#include <algorithm>

int maxSubarraySumWithEmpty(const std::vector<int>& arr) {
    int maxSum = 0, currSum = 0;
    for (int num : arr) {
        currSum = std::max(0, currSum + num);
        maxSum = std::max(maxSum, currSum);
    }
    return maxSum;
}
```

---

### PYQ7
**TCS NQT Style | Difficulty:** Hard | **Time:** 200s | **TCS Frequency:** Medium

**Problem:** Given two sorted arrays A and B, find the k-th element of their merged sorted array without actually merging them.

Input: `A = [2,3,6,7,9]`, `B = [1,4,8,10]`, k=5  
Output: 6

**C++ Solution (O(log k)):**
```cpp
#include <vector>
#include <algorithm>

int findKth(const std::vector<int>& A, int aStart, const std::vector<int>& B, int bStart, int k) {
    if (aStart >= A.size()) return B[bStart + k - 1];
    if (bStart >= B.size()) return A[aStart + k - 1];
    if (k == 1) return std::min(A[aStart], B[bStart]);
    
    int aMid = aStart + k/2 - 1 < A.size() ? A[aStart + k/2 - 1] : 2e9;
    int bMid = bStart + k/2 - 1 < B.size() ? B[bStart + k/2 - 1] : 2e9;
    
    if (aMid < bMid) {
        return findKth(A, aStart + k/2, B, bStart, k - k/2);
    } else {
        return findKth(A, aStart, B, bStart + k/2, k - k/2);
    }
}
```

---

### PYQ8
**TCS NQT Style | Difficulty:** Medium | **Time:** 150s | **TCS Frequency:** High

**Problem:** Find the length of the longest subarray with equal number of 0s and 1s.

Input: `arr = [0,1,0,1,1,1,0]`  
Output: 4

**C++ Solution (Prefix Sum + Hash Map):**
```cpp
#include <vector>
#include <unordered_map>
#include <algorithm>

int findMaxLength(const std::vector<int>& arr) {
    std::unordered_map<int, int> map;
    map[0] = -1;
    int sum = 0, maxLen = 0;
    for (int i = 0; i < arr.size(); ++i) {
        sum += (arr[i] == 0) ? -1 : 1;
        if (map.count(sum)) {
            maxLen = std::max(maxLen, i - map[sum]);
        } else {
            map[sum] = i;
        }
    }
    return maxLen;
}
```

---

### PYQ9
**TCS NQT Style | Difficulty:** Easy | **Time:** 60s | **TCS Frequency:** Medium

**Problem:** Given an array, find the maximum absolute difference between any two elements.

Input: `arr = [2, 7, 3, -1, 9]`  
Output: 10

**C++ Solution:**
```cpp
#include <vector>
#include <algorithm>

int maxAbsDiff(const std::vector<int>& arr) {
    if (arr.empty()) return 0;
    auto p = std::minmax_element(arr.begin(), arr.end());
    return *p.second - *p.first;
}
```

---

### PYQ10
**TCS NQT Style | Difficulty:** Hard | **Time:** 240s | **TCS Frequency:** Low

**Problem:** Given array `arr` of positive integers and integer k, determine if there exists a contiguous subarray of length at least 2 whose elements sum to a multiple of k.

Input: `arr = [23,2,4,6,7]`, k=6  
Output: True (subarray [2,4] or [23,2,4,6,7])

**C++ Solution (Prefix Sum Modulo):**
```cpp
#include <vector>
#include <unordered_map>

bool checkSubarraySum(const std::vector<int>& arr, int k) {
    std::unordered_map<int, int> map;
    map[0] = -1;
    int sum = 0;
    for (int i = 0; i < arr.size(); ++i) {
        sum += arr[i];
        int rem = sum % k;
        if (map.count(rem)) {
            if (i - map[rem] >= 2) return true;
        } else {
            map[rem] = i;
        }
    }
    return false;
}
```
