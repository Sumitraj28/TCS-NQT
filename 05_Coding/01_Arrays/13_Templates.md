---
title: "Arrays - Coding Templates"
section: "Coding"
---

# Array Coding Templates (C++14)

### 📋 Exam Checklist
*   [ ] Include all necessary headers (`#include <iostream>`, `<vector>`, `<algorithm>`, `<unordered_map>`, `<climits>`).
*   [ ] Optimize input/output operations (`std::ios_base::sync_with_stdio(false); std::cin.tie(NULL);`).
*   [ ] Check constraints: if array sum can exceed $2 \times 10^9$, use `long long` instead of `int`.
*   [ ] Add edge case guards (check `arr.empty()` or `arr.size() < 2`).

---

## 1. Two Pointers Template (Sorted Pair Sum)
```cpp
#include <iostream>
#include <vector>
#include <algorithm>

using namespace std;

void solveTwoPointers() {
    int n, target;
    if (!(cin >> n >> target)) return;
    
    vector<int> arr(n);
    for (int i = 0; i < n; i++) cin >> arr[i];
    
    // Sort if not already sorted (TCS inputs are often unsorted)
    sort(arr.begin(), arr.end());
    
    int left = 0, right = n - 1;
    bool found = false;
    
    while (left < right) {
        int current_sum = arr[left] + arr[right];
        if (current_sum == target) {
            cout << "Pair found: " << arr[left] << " and " << arr[right] << "\n";
            found = true;
            break;
        } else if (current_sum < target) {
            left++; // Increase sum by moving left pointer right
        } else {
            right--; // Decrease sum by moving right pointer left
        }
    }
    if (!found) cout << "No such pair exists\n";
}
```

---

## 2. Sliding Window Template (Fixed Size K Subarray Sum)
```cpp
#include <iostream>
#include <vector>
#include <algorithm>

using namespace std;

void solveSlidingWindow() {
    int n, k;
    if (!(cin >> n >> k)) return;
    
    vector<int> arr(n);
    for (int i = 0; i < n; i++) cin >> arr[i];
    
    if (n < k) {
        cout << "Invalid window size\n";
        return;
    }
    
    long long window_sum = 0;
    for (int i = 0; i < k; i++) window_sum += arr[i];
    
    long long max_sum = window_sum;
    
    for (int i = k; i < n; i++) {
        window_sum += arr[i] - arr[i - k]; // Add incoming, subtract outgoing
        max_sum = max(max_sum, window_sum);
    }
    cout << "Max Sum of size " << k << " is: " << max_sum << "\n";
}
```

---

## 3. Prefix Sum Template (equilibrium index finding)
```cpp
#include <iostream>
#include <vector>

using namespace std;

void solvePrefixSum() {
    int n;
    if (!(cin >> n)) return;
    
    vector<int> arr(n);
    long long total_sum = 0;
    for (int i = 0; i < n; i++) {
        cin >> arr[i];
        total_sum += arr[i];
    }
    
    long long left_sum = 0;
    int equilibrium_idx = -1;
    
    for (int i = 0; i < n; i++) {
        total_sum -= arr[i]; // total_sum now represents rightSum
        if (left_sum == total_sum) {
            equilibrium_idx = i;
            break;
        }
        left_sum += arr[i];
    }
    cout << "Equilibrium Index: " << equilibrium_idx << "\n";
}
```

---

## 4. Kadane's Algorithm Template (Max Subarray Sum)
```cpp
#include <iostream>
#include <vector>
#include <algorithm>
#include <climits>

using namespace std;

void solveKadane() {
    int n;
    if (!(cin >> n)) return;
    
    vector<int> arr(n);
    for (int i = 0; i < n; i++) cin >> arr[i];
    
    if (n == 0) return;
    
    long long max_so_far = arr[0];
    long long curr_max = arr[0];
    
    for (int i = 1; i < n; i++) {
        curr_max = max((long long)arr[i], curr_max + arr[i]);
        max_so_far = max(max_so_far, curr_max);
    }
    cout << "Max Subarray Sum: " << max_so_far << "\n";
}
```
