---
title: "Arrays - Common Mistakes"
section: "Coding"
---

# Array Coding Common Mistakes

Avoid these 15 common coding bugs during the NQT to prevent runtime errors and TLEs.

---

## 1. Off-by-One Buffer Overflow (Accessing `arr[N]`)
*   **What it Looks Like**:
    ```cpp
    for (int i = 0; i <= n; i++) { // Loop goes up to index n
        cout << arr[i] << endl;
    }
    ```
*   **What it Produces**: Accesses out-of-bounds memory. Leads to a **Segmentation Fault** or prints garbage values.
*   **Correct Version**:
    ```cpp
    for (int i = 0; i < n; i++) { // Strict inequality (<)
        cout << arr[i] << endl;
    }
    ```

---

## 2. Integer Sum Overflow
*   **What it Looks Like**:
    ```cpp
    int sum = 0;
    for (int num : arr) sum += num;
    ```
*   **What it Produces**: If $N = 10^5$ and elements are $10^5$, sum fits in `int`. But if elements are $10^9$, `sum` overflows the $2 \times 10^9$ limit of 32-bit `int`, wrapping around to negative values.
*   **Correct Version**:
    ```cpp
    long long sum = 0;
    for (int num : arr) sum += num;
    ```

---

## 3. Uninitialized Sum or Pointer Variables
*   **What it Looks Like**:
    ```cpp
    int sum; // Uninitialized
    for (int x : arr) sum += x;
    ```
*   **What it Produces**: `sum` starts with arbitrary garbage data from memory, yielding random incorrect results.
*   **Correct Version**:
    ```cpp
    int sum = 0;
    ```

---

## 4. Sliding Window Out-of-Bounds Outflow
*   **What it Looks Like**:
    ```cpp
    for (int i = 0; i < n; i++) {
        window_sum += arr[i] - arr[i - k]; // i - k can be negative
    }
    ```
*   **What it Produces**: Accesses negative index array values, triggering segfaults.
*   **Correct Version**:
    Start loop from `k` and initialize the first window sum separately:
    ```cpp
    for (int i = 0; i < k; i++) window_sum += arr[i];
    for (int i = k; i < n; i++) window_sum += arr[i] - arr[i - k];
    ```

---

## 5. Signed/Unsigned Comparison Warning
*   **What it Looks Like**:
    ```cpp
    for (int i = 0; i < arr.size(); i++) // arr.size() is unsigned (size_t)
    ```
*   **What it Produces**: Compiler warnings. If `arr.size()` is 0, comparisons with negative `i` can yield incorrect boolean paths.
*   **Correct Version**:
    Cast or match types:
    ```cpp
    for (size_t i = 0; i < arr.size(); i++)
    // or
    for (int i = 0; i < (int)arr.size(); i++)
    ```

---

## 6. Returning Pointer to Local Array
*   **What it Looks Like**:
    ```cpp
    int* getArray() {
        int temp[5] = {1, 2, 3, 4, 5};
        return temp;
    }
    ```
*   **What it Produces**: Stack memory is reclaimed when the function returns. The pointer points to cleared stack space, causing garbage outputs.
*   **Correct Version**:
    Allocate on the heap or return a vector:
    ```cpp
    std::vector<int> getArray() {
        return {1, 2, 3, 4, 5};
    }
    ```

---

## 7. Using `sizeof` on Function Parameters
*   **What it Looks Like**:
    ```cpp
    void printSize(int arr[]) {
        int n = sizeof(arr) / sizeof(arr[0]); // arr has decayed to pointer
    }
    ```
*   **What it Produces**: `sizeof(arr)` yields the size of the pointer (typically 4 or 8 bytes), not the size of the array block.
*   **Correct Version**:
    Always pass the size `N` as a separate parameter:
    ```cpp
    void printSize(int arr[], int n)
    ```

---

## 8. Division by Zero on Empty Arrays
*   **What it Looks Like**:
    ```cpp
    double average = (double)sum / arr.size();
    ```
*   **What it Produces**: Division by zero if `arr.size() == 0`, crashing the execution thread.
*   **Correct Version**:
    ```cpp
    double average = arr.empty() ? 0.0 : (double)sum / arr.size();
    ```

---

## 9. Reversing Sub-segments in Wrong Order for Rotation
*   **What it Looks Like**:
    Rotating right by $K$:
    ```cpp
    reverse(arr.begin(), arr.begin() + k);
    reverse(arr.begin() + k, arr.end());
    reverse(arr.begin(), arr.end());
    ```
*   **What it Produces**: Rotates the array incorrectly.
*   **Correct Version**:
    Reverse all elements first, then reverse the sub-segments:
    ```cpp
    reverse(arr.begin(), arr.end());
    reverse(arr.begin(), arr.begin() + k);
    reverse(arr.begin() + k, arr.end());
    ```

---

## 10. Modulo with Negative Indices
*   **What it Looks Like**:
    ```cpp
    int idx = (curr_idx - k) % n; // can be negative
    ```
*   **What it Produces**: Negative indexes in C++ are not handled correctly by `%`. `idx` remains negative, causing out-of-bounds access.
*   **Correct Version**:
    Add `n` before applying modulo:
    ```cpp
    int idx = ((curr_idx - k) % n + n) % n;
    ```

---

## 11. Forgetting to Clear Frequency Maps in Multiple Test Cases
*   **What it Looks Like**:
    ```cpp
    unordered_map<int, int> freq;
    void solve() {
        // missing freq.clear()
        for (int x : arr) freq[x]++;
    }
    ```
*   **What it Produces**: Frequency values carry over across test cases, causing incorrect answers.
*   **Correct Version**:
    Declare variables locally inside functions, or clear them explicitly.

---

## 12. Using slow `std::unordered_map` under TLE Constraints
*   **What it Looks Like**:
    Checking numbers in range $[1, N]$ using `unordered_map<int, bool>`.
*   **What it Produces**: Map overhead can trigger **Time Limit Exceeded** on large datasets.
*   **Correct Version**:
    Use a simple, fast boolean array/vector:
    ```cpp
    vector<bool> visited(n + 1, false);
    ```

---

## 13. Modifying Loop Variable Inside `for` Loops
*   **What it Looks Like**:
    ```cpp
    for (int i = 0; i < n; i++) {
        if (arr[i] == target) i += 2; // Accidental double jump
    }
    ```
*   **What it Produces**: Skips elements, leading to missed targets.
*   **Correct Version**: Keep loop variable modifications strictly in the `for` iteration expression.

---

## 14. 1-Based vs 0-Based Index Mismatch in Outputs
*   **What it Looks Like**:
    Question asks for 1-based indices (standard in NQT). You return the raw 0-based array index.
*   **What it Produces**: Wrong answers.
*   **Correct Version**:
    Always add `+1` to indexes when printing outputs.

---

## 15. Clicking "Compile" but forgetting to "Save/Submit"
*   **What it Looks Like**:
    Writing code, clicking "Compile", passing the public test cases, and moving to the next section without clicking "Save/Submit Code".
*   **What it Produces**: Evaluates your code block as blank, receiving 0 marks.
*   **Correct Version**:
    Always click the final save or submit button before time runs out.
