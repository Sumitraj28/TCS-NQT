# TCS NQT 2026 — Medium Coding Complete C++ Guide
**Exam Focus: Advanced Algorithms in C++ (1 Question, 55 Minutes)**

This guide presents complete, compile-ready solutions in **C++ (4.9.2)** for the most frequent Medium Coding topics. It includes previous year questions (PYQs) and predicted questions for June 2026.

---

## 💻 PART A: Topic Deep-Dives

### TOPIC 1: Dynamic Programming Patterns

#### 1A. House Robber / Circular Array DP
* **Pattern Recognition**: "Find the maximum sum of non-adjacent elements in a circular array."
* **C++ Solution**:
  ```cpp
  #include <iostream>
  #include <vector>
  #include <algorithm>

  using namespace std;

  long long solveLinear(vector<int>& nums, int start, int end) {
      long long prev2 = 0, prev1 = 0;
      for (int i = start; i <= end; i++) {
          long long temp = max(prev1, prev2 + nums[i]);
          prev2 = prev1;
          prev1 = temp;
      }
      return prev1;
  }

  long long robCircular(vector<int>& nums) {
      int n = nums.size();
      if (n == 0) return 0;
      if (n == 1) return nums[0];
      return max(solveLinear(nums, 0, n - 2), solveLinear(nums, 1, n - 1));
  }
  ```

---

#### 1B. Minimum Cost Path in Grid
* **Pattern Recognition**: "Find the minimum path sum from top-left to bottom-right in a grid."
* **C++ Solution**:
  ```cpp
  #include <iostream>
  #include <vector>
  #include <algorithm>

  using namespace std;

  int minPathSum(vector<vector<int>>& grid) {
      if (grid.empty() || grid[0].empty()) return 0;
      int m = grid.size();
      int n = grid[0].size();
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

---

#### 1C. Digit DP — Minimum N-Digit Perfect Square Sum (TCS NQT PYQ)
* **Problem**: Find the smallest $N$-digit number (no zeros) whose sum of squares of its digits is a perfect square.
* **C++ Solution**:
  ```cpp
  #include <iostream>
  #include <string>
  #include <vector>
  #include <cmath>
  #include <algorithm>

  using namespace std;

  bool isPerfectSquare(long long x) {
      if (x < 0) return false;
      long long s = round(sqrt(x));
      return s * s == x;
  }

  // Recursive search to find the smallest combination of remaining k digits
  bool findCombination(int idx, int k, int current_sum, vector<int>& current_combo, string& result, int n) {
      if (idx == k) {
          int total_sum = (n - k) + current_sum;
          if (isPerfectSquare(total_sum)) {
              // Construct the smallest number
              result = string(n - k, '1');
              vector<int> sorted_combo = current_combo;
              sort(sorted_combo.begin(), sorted_combo.end());
              for (int digit : sorted_combo) {
                  result += to_string(digit);
              }
              return true;
          }
          return false;
      }
      
      // Greedily search digits from 1 to 9
      for (int d = 1; d <= 9; d++) {
          current_combo.push_back(d);
          if (findCombination(idx + 1, k, current_sum + d * d, current_combo, result, n)) {
              return true;
          }
          current_combo.pop_back();
      }
      return false;
  }

  int main() {
      int n;
      if (!(cin >> n)) return 0;
      
      if (n <= 0) {
          cout << -1 << endl;
          return 0;
      }
      
      // We want to minimize k (the number of non-1 digits) to keep the number as small as possible
      string result = "";
      for (int k = 1; k <= min(6, n); k++) {
          vector<int> current_combo;
          if (findCombination(0, k, 0, current_combo, result, n)) {
              cout << result << endl;
              return 0;
          }
      }
      cout << -1 << endl;
      return 0;
  }
  ```

---

#### 1D. Project Selection / Knapsack Variant (TCS NQT PYQ)
* **Problem**: Select the project with the maximum Net Present Value (NPV) each year, satisfying: cost $\le$ budget and production $\ge$ requirement.
* **C++ Solution**:
  ```cpp
  #include <iostream>
  #include <vector>
  #include <algorithm>

  using namespace std;

  int main() {
      int years, projects;
      if (!(cin >> years >> projects)) return 0;
      
      vector<int> budgets(years);
      vector<int> requirements(years);
      for (int i = 0; i < years; i++) cin >> budgets[i];
      for (int i = 0; i < years; i++) cin >> requirements[i];
      
      vector<vector<int>> costs(years, vector<int>(projects));
      vector<vector<int>> productions(years, vector<int>(projects));
      vector<vector<int>> npvs(years, vector<int>(projects));
      
      for (int i = 0; i < years; i++) {
          for (int j = 0; j < projects; j++) {
              cin >> costs[i][j];
          }
      }
      for (int i = 0; i < years; i++) {
          for (int j = 0; j < projects; j++) {
              cin >> productions[i][j];
          }
      }
      for (int i = 0; i < years; i++) {
          for (int j = 0; j < projects; j++) {
              cin >> npvs[i][j];
          }
      }
      
      long long total_npv = 0;
      for (int y = 0; y < years; y++) {
          int max_npv = 0;
          int budget = budgets[y];
          int req = requirements[y];
          for (int p = 0; p < projects; p++) {
              if (costs[y][p] <= budget && productions[y][p] >= req) {
                  max_npv = max(max_npv, npvs[y][p]);
              }
          }
          total_npv += max_npv;
      }
      cout << total_npv << endl;
      return 0;
  }
  ```

---

### TOPIC 2: Greedy + Simulation

#### 2A. Task Scheduler with Cooldown (TCS NQT PYQ)
* **Problem**: Schedule tasks on a single processor. Identical tasks must have a cooldown period $N$ between them. Maximize throughput.
* **C++ Solution**:
  ```cpp
  #include <iostream>
  #include <vector>
  #include <unordered_map>
  #include <queue>
  #include <string>

  using namespace std;

  int main() {
      int n;
      string task;
      vector<string> tasks;
      if (!(cin >> n)) return 0;
      while (cin >> task) {
          tasks.push_back(task);
      }
      
      unordered_map<string, int> counts;
      for (string t : tasks) counts[t]++;
      
      priority_queue<int> max_heap;
      for (auto pair : counts) max_heap.push(pair.second);
      
      queue<pair<int, int>> cool_down_q; // pairs of (available_time, count)
      int time = 0;
      vector<string> schedule;
      
      while (!max_heap.empty() || !cool_down_q.empty()) {
          time++;
          if (!max_heap.empty()) {
              int cnt = max_heap.top() - 1;
              max_heap.pop();
              if (cnt > 0) {
                  cool_down_q.push({time + n, cnt});
              }
          } else {
              schedule.push_back("NOTHING");
          }
          
          if (!cool_down_q.empty() && cool_down_q.front().first == time) {
              max_heap.push(cool_down_q.front().second);
              cool_down_q.pop();
          }
      }
      
      for (int i = 0; i < schedule.size(); i++) {
          if (i > 0) cout << " ";
          cout << schedule[i];
      }
      cout << endl;
      return 0;
  }
  ```

---

### TOPIC 3: Bit Manipulation

#### 3A. Maximize XOR Sum with K Set Bits (TCS NQT PYQ)
* **Problem**: Find $X$ with exactly $K$ bits set that maximizes the sum of $(X \oplus \text{arr}[i])$.
* **C++ Solution**:
  ```cpp
  #include <iostream>
  #include <vector>
  #include <algorithm>

  using namespace std;

  struct BitGain {
      long long gain;
      int bit_pos;
  };

  bool compareGain(const BitGain& a, const BitGain& b) {
      if (a.gain != b.gain) {
          return a.gain > b.gain; // Higher gain first
      }
      return a.bit_pos < b.bit_pos; // Lower bit position first to minimize X value
  }

  int main() {
      int n, k;
      if (!(cin >> n)) return 0;
      vector<int> arr(n);
      for (int i = 0; i < n; i++) cin >> arr[i];
      cin >> k;
      
      vector<BitGain> gains(31);
      for (int b = 0; b < 31; b++) {
          long long zeros = 0;
          for (int val : arr) {
              if (!(val & (1 << b))) {
                  zeros++;
              }
          }
          gains[b] = {zeros * (1LL << b), b};
      }
      
      sort(gains.begin(), gains.end(), compareGain);
      
      long long x = 0;
      for (int i = 0; i < k; i++) {
          x |= (1LL << gains[i].bit_pos);
      }
      cout << x << endl;
      return 0;
  }
  ```

---

### TOPIC 4: Matrix Operations

#### 4A. Minimum Swaps to Center (TCS NQT PYQ)
* **Problem**: Find the minimum row/column swaps to move the maximum element of an $N \times N$ matrix to the center.
* **C++ Solution**:
  ```cpp
  #include <iostream>
  #include <vector>
  #include <cmath>
  #include <algorithm>

  using namespace std;

  int main() {
      int n;
      if (!(cin >> n)) return 0;
      vector<vector<int>> matrix(n, vector<int>(n));
      int center = n / 2;
      int max_val = -1e9;
      int best_dist = 1e9;
      
      for (int i = 0; i < n; i++) {
          for (int j = 0; j < n; j++) {
              cin >> matrix[i][j];
              int val = matrix[i][j];
              if (val > max_val) {
                  max_val = val;
                  best_dist = abs(i - center) + abs(j - center);
              } else if (val == max_val) {
                  best_dist = min(best_dist, abs(i - center) + abs(j - center));
              }
          }
      }
      cout << best_dist << endl;
      return 0;
  }
  ```

---

### TOPIC 5: Array + Math

#### 5A. Maximum GCD Pair with Maximum Absolute Difference (TCS NQT PYQ)
* **Problem**: Given two arrays $A$ and $B$, find a pair $(a, b)$ where $a \in A, b \in B$ that maximizes $\gcd(a, b)$. If multiple exist, maximize the absolute difference $|a - b|$.
* **C++ Solution**:
  ```cpp
  #include <iostream>
  #include <vector>
  #include <unordered_set>
  #include <cmath>
  #include <algorithm>

  using namespace std;

  int main() {
      int n;
      if (!(cin >> n)) return 0;
      vector<int> a(n), b(n);
      for (int i = 0; i < n; i++) cin >> a[i];
      for (int i = 0; i < n; i++) cin >> b[i];
      
      unordered_set<int> divisors_a;
      for (int val : a) {
          for (int i = 1; i * i <= val; i++) {
              if (val % i == 0) {
                  divisors_a.insert(i);
                  divisors_a.insert(val / i);
              }
          }
      }
      
      unordered_set<int> divisors_b;
      for (int val : b) {
          for (int i = 1; i * i <= val; i++) {
              if (val % i == 0) {
                  divisors_b.insert(i);
                  divisors_b.insert(val / i);
              }
          }
      }
      
      int max_gcd = 0;
      for (int divisor : divisors_a) {
          if (divisors_b.count(divisor)) {
              max_gcd = max(max_gcd, divisor);
          }
      }
      
      if (max_gcd == 0) {
          cout << "0 0" << endl;
          return 0;
      }
      
      vector<int> candidates_a, candidates_b;
      for (int x : a) if (x % max_gcd == 0) candidates_a.push_back(x);
      for (int y : b) if (y % max_gcd == 0) candidates_b.push_back(y);
      
      int best_diff = -1;
      for (int x : candidates_a) {
          for (int y : candidates_b) {
              best_diff = max(best_diff, abs(x - y));
          }
      }
      cout << max_gcd << " " << best_diff << endl;
      return 0;
  }
  ```

---

## 🔮 PART B: Predicted June 2026 Medium Questions

### 1. Predicted: DP on String Edit Distance with Swap
* **C++ Solution**:
  ```cpp
  #include <iostream>
  #include <string>
  #include <vector>
  #include <algorithm>

  using namespace std;

  int main() {
      string s1, s2;
      if (!(cin >> s1 >> s2)) return 0;
      int m = s1.length();
      int n = s2.length();
      vector<vector<int>> dp(m + 1, vector<int>(n + 1, 0));
      
      for (int i = 0; i <= m; i++) dp[i][0] = i;
      for (int j = 0; j <= n; j++) dp[0][j] = j;
      
      for (int i = 1; i <= m; i++) {
          for (int j = 1; j <= n; j++) {
              if (s1[i-1] == s2[j-1]) {
                  dp[i][j] = dp[i-1][j-1];
              } else {
                  dp[i][j] = min({dp[i-1][j] + 1, dp[i][j-1] + 1, dp[i-1][j-1] + 1});
              }
              if (i > 1 && j > 1 && s1[i-1] == s2[j-2] && s1[i-2] == s2[j-1]) {
                  dp[i][j] = min(dp[i][j], dp[i-2][j-2] + 1);
              }
          }
      }
      cout << dp[m][n] << endl;
      return 0;
  }
  ```

---

### 2. Predicted: Greedy Job Scheduling with Profit
* **C++ Solution**:
  ```cpp
  #include <iostream>
  #include <vector>
  #include <algorithm>

  using namespace std;

  struct Job {
      int profit, deadline;
  };

  bool compareJobs(const Job& a, const Job& b) {
      return a.profit > b.profit;
  }

  int main() {
      int n;
      if (!(cin >> n)) return 0;
      vector<Job> jobs(n);
      int max_deadline = 0;
      for (int i = 0; i < n; i++) {
          cin >> jobs[i].profit >> jobs[i].deadline;
          max_deadline = max(max_deadline, jobs[i].deadline);
      }
      
      sort(jobs.begin(), jobs.end(), compareJobs);
      vector<int> slots(max_deadline + 1, -1);
      long long total_profit = 0;
      
      for (int i = 0; i < n; i++) {
          for (int s = jobs[i].deadline; s > 0; s--) {
              if (slots[s] == -1) {
                  slots[s] = jobs[i].profit;
                  total_profit += jobs[i].profit;
                  break;
              }
          }
      }
      cout << total_profit << endl;
      return 0;
  }
  ```

---

### 3. Predicted: Matrix Path with Obstacles and K Skips
* **C++ Solution**:
  ```cpp
  #include <iostream>
  #include <vector>
  #include <queue>
  #include <algorithm>

  using namespace std;

  struct State {
      int cost, r, c, rem_k;
      bool operator>(const State& other) const {
          return cost > other.cost;
      }
  };

  int main() {
      int m, n, k;
      if (!(cin >> m >> n >> k)) return 0;
      vector<vector<int>> grid(m, vector<int>(n));
      for (int i = 0; i < m; i++) {
          for (int j = 0; j < n; j++) {
              cin >> grid[i][j];
          }
      }
      
      priority_queue<State, vector<State>, greater<State>> pq;
      pq.push({grid[0][0], 0, 0, k});
      
      vector<vector<int>> visited(m, vector<int>(n, -1));
      
      int dr[] = {-1, 1, 0, 0};
      int dc[] = {0, 0, -1, 1};
      
      while (!pq.empty()) {
          State curr = pq.top();
          pq.pop();
          
          if (curr.r == m - 1 && curr.c == n - 1) {
              cout << curr.cost << endl;
              return 0;
          }
          
          if (visited[curr.r][curr.c] >= curr.rem_k) continue;
          visited[curr.r][curr.c] = curr.rem_k;
          
          for (int i = 0; i < 4; i++) {
              int nr = curr.r + dr[i];
              int nc = curr.c + dc[i];
              if (nr >= 0 && nr < m && nc >= 0 && nc < n) {
                  bool is_obstacle = (grid[nr][nc] == -1);
                  if (is_obstacle && curr.rem_k > 0) {
                      pq.push({curr.cost + 1, nr, nc, curr.rem_k - 1});
                  } else if (!is_obstacle) {
                      pq.push({curr.cost + grid[nr][nc], nr, nc, curr.rem_k});
                  }
              }
          }
      }
      cout << -1 << endl;
      return 0;
  }
  ```

---

### 4. Predicted: Count of N-Digit Monotonic Numbers
* **C++ Solution**:
  ```cpp
  #include <iostream>
  #include <vector>
  #include <numeric>

  using namespace std;

  int main() {
      int n;
      if (!(cin >> n)) return 0;
      
      vector<vector<long long>> dp(n + 1, vector<long long>(10, 0));
      for (int j = 1; j <= 9; j++) dp[1][j] = 1;
      
      for (int i = 2; i <= n; i++) {
          for (int j = 1; j <= 9; j++) {
              for (int k = 1; k <= j; k++) {
                  dp[i][j] = (dp[i][j] + dp[i-1][k]) % 1000000007;
              }
          }
      }
      
      long long total = 0;
      for (int j = 1; j <= 9; j++) {
          total = (total + dp[n][j]) % 1000000007;
      }
      cout << total << endl;
      return 0;
  }
  ```
