# Array Cheat Sheet: C++14 & Algorithms

A condensed reference for rapid lookup of array operations, patterns, and C++ syntax.

---

## ⚡ Pattern Recognition Chart

| If the problem description says... | ...Immediately select this algorithm/technique |
| :--- | :--- |
| "find a contiguous subarray with maximum sum..." | **Kadane's Algorithm** ($O(N)$ time, $O(1)$ space) |
| "find a pair/triplet in a sorted array that sums to $K$..." | **Two-Pointer Approach** ($O(N)$ time, $O(1)$ space) |
| "find the longest/shortest subarray summing to $K$ (all elements $\ge 0$)..." | **Sliding Window** ($O(N)$ time, $O(1)$ space) |
| "find the number of subarrays summing to $K$ (contains negative elements)..." | **Prefix Sum + Hash Map (`unordered_map`)** ($O(N)$ time) |
| "rotate an array to the right by $D$ positions..." | **Three-Step Reversal Pattern** ($O(N)$ time, $O(1)$ space) |
| "find the first missing positive integer..." | **Index-as-Hash Map Mapping** (Cycle Sort placement, $O(N)$ time) |

---

## 📐 Mathematical Formulas & Derivations

### 1. Element Memory Address
The address of element at index $i$ in a contiguous 1D array is:
$$\text{Address}(A[i]) = \text{BaseAddress} + (i \times \text{SizeOf(DataType)})$$
*Example:* For `int A[5]` (size of `int` = 4 bytes) starting at Base Address `1000`, the address of `A[3]` is:
$$\text{Address}(A[3]) = 1000 + (3 \times 4) = 1012$$

### 2. Modulo Arithmetic Rules
Used to prevent integer overflow in large summation/product problems:
$$(A + B) \pmod M = ((A \pmod M) + (B \pmod M)) \pmod M$$
$$(A \times B) \pmod M = ((A \pmod M) \times (B \pmod M)) \pmod M$$

### 3. Sum of First $N$ Natural Numbers
Used to find missing numbers in continuous ranges:
$$\text{Sum} = \frac{N \times (N + 1)}{2}$$
*Derivation:*
$$\text{Sum} = 1 + 2 + 3 + \dots + N$$
$$\text{Sum} = N + (N-1) + \dots + 1$$
Adding both equations:
$$2 \times \text{Sum} = (N+1) + (N+1) + \dots + (N+1) \quad [N \text{ times}]$$
$$2 \times \text{Sum} = N(N + 1) \implies \text{Sum} = \frac{N(N+1)}{2}$$

---

## 💾 Core C++14 Quick-Code Snippets

### Fast I/O & Template
```cpp
#include <iostream>
#include <vector>
#include <algorithm>
#include <unordered_map>

using namespace std;

int main() {
    ios_base::sync_with_stdio(false);
    cin.tie(NULL);
    // Code starts here
    return 0;
}
```

### 1. Two-Pointer Sum Check
```cpp
bool hasTargetSum(int arr[], int n, int target) {
    int left = 0, right = n - 1;
    while (left < right) {
        int current_sum = arr[left] + arr[right];
        if (current_sum == target) return true;
        else if (current_sum < target) left++;
        else right--;
    }
    return false;
}
```

### 2. Sliding Window (Max Sum Subarray of Size K)
```cpp
long long maxWindowSum(int arr[], int n, int k) {
    if (n < k) return -1;
    long long window_sum = 0;
    for (int i = 0; i < k; i++) window_sum += arr[i];
    
    long long max_sum = window_sum;
    for (int i = k; i < n; i++) {
        window_sum += arr[i] - arr[i - k];
        max_sum = max(max_sum, window_sum);
    }
    return max_sum;
}
```

### 3. Kadane's Algorithm (Max Subarray Sum)
```cpp
long long maxSubarraySum(int arr[], int n) {
    long long max_so_far = arr[0];
    long long curr_max = arr[0];
    for (int i = 1; i < n; i++) {
        curr_max = max((long long)arr[i], curr_max + arr[i]);
        max_so_far = max(max_so_far, curr_max);
    }
    return max_so_far;
}
```

### 4. Array Reversal (Three-Step Rotation Helper)
```cpp
void reverseRange(int arr[], int start, int end) {
    while (start < end) {
        swap(arr[start], arr[end]);
        start++; end--;
    }
}
// To rotate right by K:
// 1. reverseRange(arr, 0, n - 1);
// 2. reverseRange(arr, 0, k - 1);
// 3. reverseRange(arr, k, n - 1);
```

---

## 🗃️ Time & Space Complexity Reference

| Operation | Array (Raw / Static) | Vector (Dynamic Array) |
| :--- | :--- | :--- |
| **Access (given index $i$)** | $O(1)$ | $O(1)$ |
| **Search (Unsorted)** | $O(N)$ | $O(N)$ |
| **Search (Sorted - Binary)** | $O(\log N)$ | $O(\log N)$ |
| **Insertion / Deletion (End)** | $O(1)$ (if pre-allocated) | $O(1)$ (Amortized) |
| **Insertion / Deletion (Middle/Start)** | $O(N)$ (due to element shifting) | $O(N)$ (due to shifts) |
| **Space Overhead** | $O(1)$ (no extra memory) | $O(N)$ capacity scaling factor (typically $1.5\times$ or $2\times$) |
