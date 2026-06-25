# TCS NQT 2026 — DSA Patterns C++ Cheatsheet (Quick Reference)
**Exam Focus: Quick Ref & C++ STL Templates for last-minute prep**

This sheets is optimized in **C++ (4.9.2)** syntax for direct reference and last-minute study.

---

## 🔍 SECTION 1: Pattern Recognition Quick Guide

| If the problem mentions... | Use this pattern |
| :--- | :--- |
| "maximum sum, non-adjacent elements" | House Robber DP |
| "circular array, pick elements" | Circular House Robber DP (2 runs) |
| "minimum operations to transform" | BFS / Edit Distance DP |
| "all subsets / all combinations" | Recursion + backtracking |
| "K-th largest / smallest" | Min-heap / Max-heap of size K |
| "count paths in grid" | 2D DP |
| "GCD of pair across two arrays" | Divisor/multiple checking |
| "maximize XOR" | Bit-by-bit greedy |
| "task scheduler cooldown" | Max-heap + cooldown queue |
| "palindrome substring" | Expand around center |
| "minimum swaps to sort" | Cycle detection |
| "subarray sum equals K" | Prefix sum + Hash map |
| "shortest path in unweighted grid" | BFS with queue |
| "detect cycle in undirected graph" | Union-Find (DSU) |
| "prime numbers count / check" | Sieve of Eratosthenes |
| "rotate array by K positions" | Array reversal template |
| "equilibrium index in array" | Left/Right sum tracking |

---

## 💻 SECTION 2: C++ Templates (Copy-Paste Ready)

### 1. Binary Search
```cpp
#include <vector>
using namespace std;

int binarySearch(vector<int>& arr, int target) {
    int low = 0, high = arr.size() - 1;
    while (low <= high) {
        int mid = low + (high - low) / 2;
        if (arr[mid] == target) return mid;
        else if (arr[mid] < target) low = mid + 1;
        else high = mid - 1;
    }
    return -1;
}

int findFirstOccurrence(vector<int>& arr, int target) {
    int low = 0, high = arr.size() - 1, ans = -1;
    while (low <= high) {
        int mid = low + (high - low) / 2;
        if (arr[mid] == target) {
            ans = mid;
            high = mid - 1; // search left
        } else if (arr[mid] < target) low = mid + 1;
        else high = mid - 1;
    }
    return ans;
}
```

### 2. BFS on 2D Grid
```cpp
#include <queue>
#include <set>
#include <vector>
using namespace std;

struct Cell {
    int r, c, dist;
};

int bfsGrid(vector<vector<int>>& grid) {
    int m = grid.size(), n = grid[0].size();
    queue<Cell> q;
    q.push({0, 0, 1});
    vector<vector<bool>> visited(m, vector<bool>(n, false));
    visited[0][0] = true;
    
    int dr[] = {-1, 1, 0, 0};
    int dc[] = {0, 0, -1, 1};
    
    while (!q.empty()) {
        Cell curr = q.front();
        q.pop();
        
        if (curr.r == m - 1 && curr.c == n - 1) return curr.dist;
        
        for (int i = 0; i < 4; i++) {
            int nr = curr.r + dr[i];
            int nc = curr.c + dc[i];
            if (nr >= 0 && nr < m && nc >= 0 && nc < n && grid[nr][nc] == 1 && !visited[nr][nc]) {
                visited[nr][nc] = true;
                q.push({nr, nc, curr.dist + 1});
            }
        }
    }
    return -1;
}
```

### 3. DFS (Recursive & Iterative)
```cpp
#include <vector>
#include <set>
#include <stack>
using namespace std;

void dfsRecursive(vector<vector<int>>& graph, int node, set<int>& visited) {
    visited.insert(node);
    for (int neighbor : graph[node]) {
        if (visited.find(neighbor) == visited.end()) {
            dfsRecursive(graph, neighbor, visited);
        }
    }
}

void dfsIterative(vector<vector<int>>& graph, int start, set<int>& visited) {
    stack<int> s;
    s.push(start);
    while (!s.empty()) {
        int node = s.top();
        s.pop();
        if (visited.find(node) == visited.end()) {
            visited.insert(node);
            for (int neighbor : graph[node]) {
                if (visited.find(neighbor) == visited.end()) {
                    s.push(neighbor);
                }
            }
        }
    }
}
```

### 4. Dynamic Programming — 1D
```cpp
#include <vector>
#include <algorithm>
using namespace std;

long long robLinear(vector<int>& nums, int start, int end) {
    long long prev2 = 0, prev1 = 0;
    for (int i = start; i <= end; i++) {
        long long temp = max(prev1, prev2 + nums[i]);
        prev2 = prev1;
        prev1 = temp;
    }
    return prev1;
}
```

### 5. Dynamic Programming — 2D Grid
```cpp
#include <vector>
#include <algorithm>
using namespace std;

int minPathSum(vector<vector<int>>& grid) {
    int m = grid.size(), n = grid[0].size();
    vector<vector<int>> dp(m, vector<int>(n, 1e9));
    dp[0][0] = grid[0][0];
    for (int i = 0; i < m; i++) {
        for (int j = 0; j < n; j++) {
            if (i > 0) dp[i][j] = min(dp[i][j], dp[i-1][j] + grid[i][j]);
            if (j > 0) dp[i][j] = min(dp[i][j], dp[i][j-1] + grid[i][j]);
        }
    }
    return dp[m-1][n-1];
}
```

### 6. Sliding Window — Fixed Size
```cpp
#include <vector>
#include <numeric>
#include <algorithm>
using namespace std;

int maxSubarraySum(vector<int>& arr, int k) {
    int n = arr.size();
    if (n < k) return 0;
    int curr_sum = 0;
    for (int i = 0; i < k; i++) curr_sum += arr[i];
    int max_sum = curr_sum;
    for (int i = k; i < n; i++) {
        curr_sum += arr[i] - arr[i-k];
        max_sum = max(max_sum, curr_sum);
    }
    return max_sum;
}
```

### 7. Sliding Window — Variable Size
```cpp
#include <string>
#include <unordered_map>
#include <algorithm>
using namespace std;

int longestUniqueSubstring(string s) {
    unordered_map<char, int> char_map;
    int left = 0, max_len = 0;
    for (int right = 0; right < s.length(); right++) {
        if (char_map.find(s[right]) != char_map.end()) {
            left = max(left, char_map[s[right]] + 1);
        }
        char_map[s[right]] = right;
        max_len = max(max_len, right - left + 1);
    }
    return max_len;
}
```

### 8. Two Pointer
```cpp
#include <vector>
using namespace std;

pair<int, int> targetSum(vector<int>& arr, int target) {
    int left = 0, right = arr.size() - 1;
    while (left < right) {
        int sum = arr[left] + arr[right];
        if (sum == target) return {left, right};
        else if (sum < target) left++;
        else right--;
    }
    return {-1, -1};
}
```

### 9. Max Heap / Min Heap (priority_queue)
```cpp
#include <queue>
#include <unordered_map>
#include <vector>
using namespace std;

vector<int> topKFrequent(vector<int>& nums, int k) {
    unordered_map<int, int> counts;
    for (int num : nums) counts[num]++;
    
    // min-heap storing pair of (count, element)
    priority_queue<pair<int, int>, vector<pair<int, int>>, greater<pair<int, int>>> pq;
    for (auto pair : counts) {
        pq.push({pair.second, pair.first});
        if (pq.size() > k) pq.pop();
    }
    vector<int> result;
    while (!pq.empty()) {
        result.push_back(pq.top().second);
        pq.pop();
    }
    return result;
}
```

### 10. Union-Find (DSU)
```cpp
#include <vector>
#include <numeric>
using namespace std;

class DSU {
    vector<int> parent, rank;
public:
    DSU(int n) {
        parent.resize(n);
        iota(parent.begin(), parent.end(), 0);
        rank.assign(n, 0);
    }
    int find(int x) {
        if (parent[x] != x) parent[x] = find(parent[x]); // Path compression
        return parent[x];
    }
    bool unionSets(int x, int y) {
        int rx = find(x), ry = find(y);
        if (rx != ry) {
            if (rank[rx] > rank[ry]) parent[ry] = rx;
            else if (rank[rx] < rank[ry]) parent[rx] = ry;
            else {
                parent[ry] = rx;
                rank[rx]++;
            }
            return true;
        }
        return false;
    }
};
```

### 11. GCD & LCM
```cpp
long long gcd(long long a, long long b) {
    while (b != 0) {
        long long t = a % b;
        a = b;
        b = t;
    }
    return a;
}

long long lcm(long long a, long long b) {
    if (a == 0 || b == 0) return 0;
    return (a / gcd(a, b)) * b;
}
```

### 12. Bit Manipulation
```cpp
// Check if k-th bit is set
bool isBitSet(int n, int k) { return (n >> k) & 1; }

// Set k-th bit
int setBit(int n, int k) { return n | (1 << k); }

// Clear k-th bit
int clearBit(int n, int k) { return n & ~(1 << k); }

// Count set bits
int countSetBits(int n) {
    int count = 0;
    while (n) {
        n &= (n - 1);
        count++;
    }
    return count;
}
```

### 13. Circular Array DP (House Robber II)
```cpp
#include <vector>
#include <algorithm>
using namespace std;

long long robLinear(vector<int>& nums, int s, int e) {
    long long p2 = 0, p1 = 0;
    for (int i = s; i <= e; i++) {
        long long temp = max(p1, p2 + nums[i]);
        p2 = p1;
        p1 = temp;
    }
    return p1;
}

long long robCircular(vector<int>& nums) {
    int n = nums.size();
    if (n == 0) return 0;
    if (n == 1) return nums[0];
    return max(robLinear(nums, 0, n - 2), robLinear(nums, 1, n - 1));
}
```

### 14. String Palindrome Expand
```cpp
#include <string>
using namespace std;

string expand(string s, int l, int r) {
    while (l >= 0 && r < s.length() && s[l] == s[r]) {
        l--;
        r++;
    }
    return s.substr(l + 1, r - l - 1);
}
```

### 15. Prefix Sum (1D & 2D)
```cpp
#include <vector>
using namespace std;

vector<long long> getPrefixSum(vector<int>& arr) {
    int n = arr.size();
    vector<long long> prefix(n + 1, 0);
    for (int i = 0; i < n; i++) prefix[i+1] = prefix[i] + arr[i];
    return prefix;
}
```

### 16. Modular Arithmetic
```cpp
long long powerMod(long long base, long long exp, long long mod) {
    long long res = 1;
    base %= mod;
    while (exp > 0) {
        if (exp % 2 == 1) res = (res * base) % mod;
        base = (base * base) % mod;
        exp /= 2;
    }
    return res;
}
```

### 17. Sieve of Eratosthenes
```cpp
#include <vector>
using namespace std;

vector<int> getPrimes(int n) {
    vector<bool> isPrime(n + 1, true);
    isPrime[0] = isPrime[1] = false;
    for (int p = 2; p * p <= n; p++) {
        if (isPrime[p]) {
            for (int i = p * p; i <= n; i += p) {
                isPrime[i] = false;
            }
        }
    }
    vector<int> primes;
    for (int i = 2; i <= n; i++) {
        if (isPrime[i]) primes.push_back(i);
    }
    return primes;
}
```

### 18. Fast Input Reading
```cpp
#include <iostream>
using namespace std;

void fastIO() {
    ios_base::sync_with_stdio(false);
    cin.tie(NULL);
}
```

---

## ⏱️ SECTION 3: Complexity & Safe Constraints Reference

| Algorithm / Pattern | Time Complexity | Space Complexity | Max Safe $N$ in 1 Second |
| :--- | :--- | :--- | :--- |
| **Brute Force $O(N^2)$** | $O(N^2)$ | $O(1)$ | $N \le 10,000$ |
| **Sort-based $O(N \log N)$** | $O(N \log N)$ | $O(N)$ or $O(1)$ | $N \le 10^6$ |
| **Binary Search** | $O(\log N)$ | $O(1)$ | Any $N$ (up to $10^{18}$) |
| **BFS/DFS Traversal** | $O(V + E)$ | $O(V)$ | $10^5$ nodes / edges |
| **1D Dynamic Programming** | $O(N)$ | $O(N) \to O(1)$ | $N \le 10^7$ |
| **2D Dynamic Programming** | $O(N^2)$ | $O(N^2)$ | $N \le 1,000$ |
| **Sliding Window** | $O(N)$ | $O(1)$ | $N \le 10^7$ |
| **Heap-based $O(N \log K)$** | $O(N \log K)$ | $O(K)$ | $N \le 10^6$ |

---

## ⚠️ SECTION 4: Common C++ Bugs in TCS NQT

1. **Integer Overflow**: Using standard `int` instead of `long long`. For sums, multiplications, or modular exponentiations, always use `long long` variables.
2. **Buffer Issues in `getline()`**: Mixing `cin >>` and `getline()` causes the trailing newline to be read. Write `cin.ignore()` before invoking `getline()`.
3. **Out-of-bounds in Arrays/Vectors**: Accessing `arr[size]` causes runtime errors. Use `arr.at(idx)` or verify indices manually.
4. **Incorrect STL Sorting**: Sorting a vector of structs requires custom comparators. Ensure the comparator returns `false` for equal values to prevent strict weak ordering crashes.
5. **Slow I/O Overhead**: For large test cases, C++ stream overhead causes TLE. Unlink them immediately inside `main()` using:
   ```cpp
   ios_base::sync_with_stdio(false);
   cin.tie(NULL);
   ```
6. **Forgetting `return 0;`**: Standard compilers in NQT platforms require the `main()` function to return `0`.
7. **Modulus of Negative Numbers**: In C++, `-5 % 3` returns `-2` instead of `1`. Correct negative modulus arithmetic using `(val % mod + mod) % mod`.
