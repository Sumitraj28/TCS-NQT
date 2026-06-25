# Coding Revision Guide: Arrays

This file is a high-speed preparation roadmap designed for rapid recall under exam conditions. Use the checklists below depending on the time remaining before your TCS NQT coding section.

---

## 🗺️ High-Speed Array Decision Map (Visual Guide)

Use this flowchart to immediately identify which array technique to apply based on the problem signature.

```mermaid
graph TD
    A[Read Array Problem] --> B{Does it ask for subarray sum/product/property?}
    B -- Yes --> C{Are elements all positive or mixed?}
    C -- Positives Only --> D[Sliding Window - O(N)]
    C -- Mixed Negatives --> E[Prefix Sum + Hash Map - O(N)]
    B -- No --> F{Does it involve search/target sum in sorted array?}
    F -- Yes --> G[Two Pointers - O(N)]
    F -- No --> H{Does it ask for max subarray sum?}
    H -- Yes --> I[Kadane's Algorithm - O(N)]
    H -- No --> J[Frequency Map / Multi-Pointer / Array Shifting]
    
    style A fill:#f9f,stroke:#333,stroke-width:2px
    style D fill:#bbf,stroke:#333,stroke-width:2px
    style E fill:#bbf,stroke:#333,stroke-width:2px
    style G fill:#bbf,stroke:#333,stroke-width:2px
    style I fill:#bbf,stroke:#333,stroke-width:2px
```

---

## ⚡ The 1-Minute Checklist (Last-Minute Recall)

Execute this checklist in the final minute before the coding window begins.

- [ ] **Address Offset Derivation**: Remember that the address of element at index $i$ in a 1D array is:
  $$\text{Address}(A[i]) = \text{BaseAddress} + (i \times \text{SizeOf(DataType)})$$
  This guarantees $O(1)$ random access memory lookup.
- [ ] **Fast I/O Syntax**: Ensure the first lines inside `main()` decouple C and C++ streams:
  ```cpp
  ios_base::sync_with_stdio(false);
  cin.tie(NULL);
  ```
- [ ] **Overflow Prevention**: When calculating cumulative sums, array product, or counting combinations, use `long long` instead of `int` to prevent overflow at $2^{31}-1$.
- [ ] **Array Decay Warning**: Remember that passing `int arr[]` to a function decays it to a pointer (`int*`). You must pass size `N` explicitly: `void solve(int arr[], int n)`.

---

## ⏱️ The 5-Minute Checklist (Core Pattern Mental Maps)

Verify your understanding of these five foundational array patterns.

| Pattern | Code Signature | Typical NQT Questions | Time Complexity |
| :--- | :--- | :--- | :--- |
| **Two Pointers** | `while(left < right)` | Pair with given sum, sorted array square merge | $O(N)$ |
| **Sliding Window** | `right` expands, `left` shrinks | Longest subarray with sum $K$, max sum window | $O(N)$ |
| **Prefix Sum** | `prefix[i] = prefix[i-1] + arr[i]` | Subarray sum equals $K$, equilibrium index | $O(N)$ |
| **Kadane's** | `curr_max = max(arr[i], curr_max + arr[i])` | Maximum sum subarray | $O(N)$ |
| **Frequency Hash** | `unordered_map<int, int>` / Array as Map | First missing positive, find duplicates | $O(N)$ |

### Immediate Worked Example: Sliding Window on real numbers
Let array $A = [1, 4, 2, 10, 23]$, find max sum of $K=3$ consecutive elements.
- Initial Window $[1, 4, 2]$: Sum $= 1+4+2 = 7$.
- Slide window by adding $10$, subtracting $1$: Sum $= 7 + 10 - 1 = 16$.
- Slide window by adding $23$, subtracting $4$: Sum $= 16 + 23 - 4 = 35$.
- Result is $35$.

---

## ⌛ The 15-Minute Checklist (Common Bugs & Fast Templates)

Scan this checklist to debug common failures in test cases.

1. **Array Out of Bounds**:
   - Check if you accessed `arr[n]` or `arr[-1]`.
   - In loops, ensure condition is `i < n` and not `i <= n`.
2. **Empty Array Input**:
   - If $N=0$ is possible, check `if (n == 0) return 0;` at the absolute beginning of your function.
3. **Array Reversal Code Recitation**:
   - Swap elements from outer boundaries moving inward:
     ```cpp
     void reverseArray(int arr[], int n) {
         int l = 0, r = n - 1;
         while (l < r) {
             std::swap(arr[l], arr[r]);
             l++; r--;
         }
     }
     ```
4. **Modulo Operations**:
   - If the problem description asks for answer modulo $10^9+7$, apply `% 1000000007` on every addition/multiplication:
     $$\text{Sum} = (\text{Sum} \pmod M + A[i] \pmod M) \pmod M$$

---

## 🌙 The Night-Before Checklist

Maximize rest while locking in structural code memory.

- [ ] **Zero-Warning Compilation**: Practice compilation with strict warnings enabled to spot implicit pointer casts.
- [ ] **Time Limit Awareness**: If $N \le 10^5$, write $O(N)$ or $O(N \log N)$ code. If $N \le 10^3$, $O(N^2)$ is acceptable.
- [ ] **Solve 1 Easy, 1 Medium**: Code one clean two-pointer and one sliding window problem to keep muscle memory fresh.
- [ ] **Sleep**: Get 7+ hours of sleep. Exam anxiety causes syntax mistakes and poor dry-runs.

---

## 🏫 The Exam-Hall Checklist (Test Case Strategy)

Follow this step-by-step pipeline when the coding prompt opens.

```
[Start Coding Task]
        |
        v
[1. Read Constraints] 
    Is N <= 10^5? -> Plan O(N) or O(N log N)
        |
        v
[2. Handle Edge Cases]
    N = 0, N = 1, Negatives, Duplicates, Sorted vs Unsorted
        |
        v
[3. Run Sample Test Cases]
    Verify inputs manually using a trace table
        |
        v
[4. Implement Code]
    Include Fast I/O, long long for totals
        |
        v
[5. Submit & Check Hidden Cases]
    If TLE -> optimize loops; If SIGSEGV -> check out-of-bounds indices
```

### Action Items for Hidden Test Case Failures
- **Runtime Error (SIGSEGV/SIGFPE)**: Check for division by zero (e.g. `sum % count` where `count == 0`) or out-of-bounds array access (`arr[i]` when `i >= n` or `i < 0`).
- **Time Limit Exceeded (TLE)**: Remove nested loops that rerun redundant computations. Use prefix sum or sliding window instead of brute-force checking subarrays.
- **Wrong Answer (WA) on large inputs**: Ensure sum variables are typed `long long` and verify that negative integers are handled correctly.
