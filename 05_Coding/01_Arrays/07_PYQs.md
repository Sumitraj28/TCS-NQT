---
title: "Arrays - PYQs"
section: "Coding"
---

# Array Previous Year Questions (PYQs)

> [!NOTE]
> These are **high-probability practice patterns** based on observed NQT exam coding questions. They are not guaranteed actual exam content.

---

## 1. PYQ Pattern: Leaders in an Array
*   **Problem Statement**: Write a program to print all the "Leaders" in an array. An element is a leader if it is strictly greater than all elements to its right. The rightmost element is always a leader.
    *   *Sample Input*: `[16, 17, 4, 3, 5, 2]` $\implies$ *Sample Output*: `17 5 2`.
*   **C++14 Solution**:
    ```cpp
    #include <iostream>
    #include <vector>
    #include <algorithm>

    std::vector<int> findLeaders(const std::vector<int>& arr) {
        int n = arr.size();
        std::vector<int> leaders;
        if (n == 0) return leaders;
        
        int max_from_right = arr[n - 1];
        leaders.push_back(max_from_right); // Rightmost is always a leader
        
        for (int i = n - 2; i >= 0; i--) {
            if (arr[i] > max_from_right) {
                max_from_right = arr[i];
                leaders.push_back(max_from_right);
            }
        }
        std::reverse(leaders.begin(), leaders.end()); // Keep original order
        return leaders;
    }
    ```
*   **Dry Run**:
    *   Initialize `max_from_right = arr[5] = 2`. Add `2` to leaders.
    *   `i = 4 (5)`: `5 > 2` $\implies$ Update `max_from_right = 5`. Add `5`.
    *   `i = 3 (3)`: `3 < 5` $\implies$ No change.
    *   `i = 2 (4)`: `4 < 5` $\implies$ No change.
    *   `i = 1 (17)`: `17 > 5` $\implies$ Update `max_from_right = 17`. Add `17`.
    *   `i = 0 (16)`: `16 < 17` $\implies$ No change.
    *   Reverse list: `[17, 5, 2]`.
*   **Complexity**: Time: $O(N)$, Space: $O(1)$ auxiliary.

---

## 2. PYQ Pattern: Find the Missing Number
*   **Problem Statement**: Given an array containing $N-1$ unique numbers in the range $[1, N]$, find the missing number.
    *   *Sample Input*: `[3, 1, 4, 5]`, $N = 5$ $\implies$ *Sample Output*: `2`.
*   **C++14 Solution**:
    ```cpp
    #include <vector>

    int findMissing(const std::vector<int>& arr, int n) {
        long long expectedSum = (long long)n * (n + 1) / 2;
        long long actualSum = 0;
        for (int x : arr) actualSum += x;
        return expectedSum - actualSum;
    }
    ```
*   **Complexity**: Time: $O(N)$, Space: $O(1)$.

---

## 3. PYQ Pattern: Rotate Array Left by K Steps
*   **Problem Statement**: Rotate an array of size $N$ to the left by $K$ positions.
    *   *Sample Input*: `[1, 2, 3, 4, 5]`, $K = 2$ $\implies$ *Sample Output*: `[3, 4, 5, 1, 2]`.
*   **C++14 Solution**:
    ```cpp
    #include <vector>
    #include <algorithm>

    void rotateLeft(std::vector<int>& arr, int k) {
        int n = arr.size();
        k = k % n;
        std::reverse(arr.begin(), arr.begin() + k);
        std::reverse(arr.begin() + k, arr.end());
        std::reverse(arr.begin(), arr.end());
    }
    ```
*   **Complexity**: Time: $O(N)$, Space: $O(1)$.

---

## 4. PYQ Pattern: Segregate Even and Odd Numbers
*   **Problem Statement**: Rearrange an array such that all even numbers appear first, followed by odd numbers, keeping original relative order.
    *   *Sample Input*: `[1, 2, 4, 3, 5, 6]` $\implies$ *Sample Output*: `[2, 4, 6, 1, 3, 5]`.
*   **C++14 Solution**:
    ```cpp
    #include <vector>

    std::vector<int> segregateEvenOdd(const std::vector<int>& arr) {
        std::vector<int> even, odd;
        for (int x : arr) {
            if (x % 2 == 0) even.push_back(x);
            else odd.push_back(x);
        }
        std::vector<int> result = even;
        result.insert(result.end(), odd.begin(), odd.end());
        return result;
    }
    ```
*   **Complexity**: Time: $O(N)$, Space: $O(N)$.

---

## 5. PYQ Pattern: Frequency of Each Element
*   **Problem Statement**: Count the occurrences of each element in an array and print them in sorted order of elements.
    *   *Sample Input*: `[4, 2, 2, 8]` $\implies$ *Sample Output*: `2: 2, 4: 1, 8: 1`.
*   **C++14 Solution**:
    ```cpp
    #include <iostream>
    #include <vector>
    #include <map>

    void printFrequency(const std::vector<int>& arr) {
        std::map<int, int> freq; // Sorted map
        for (int x : arr) freq[x]++;
        for (const auto& pair : freq) {
            std::cout << pair.first << ": " << pair.second << std::endl;
        }
    }
    ```
*   **Complexity**: Time: $O(N \log N)$ (due to map insertion), Space: $O(N)$.

---

## 6. PYQ Pattern: First Non-Repeating Element
*   **Problem Statement**: Find the first element in an array that does not repeat. If all elements repeat, return -1.
    *   *Sample Input*: `[9, 4, 9, 6, 7, 4]` $\implies$ *Sample Output*: `6`.
*   **C++14 Solution**:
    ```cpp
    #include <vector>
    #include <unordered_map>

    int firstNonRepeating(const std::vector<int>& arr) {
        std::unordered_map<int, int> freq;
        for (int x : arr) freq[x]++;
        for (int x : arr) {
            if (freq[x] == 1) return x;
        }
        return -1;
    }
    ```
*   **Complexity**: Time: $O(N)$, Space: $O(N)$.

---

## 7. PYQ Pattern: Intersection of Two Arrays
*   **Problem Statement**: Find the intersection of two unsorted arrays. Return only unique common elements.
    *   *Sample Input*: `[1, 2, 2, 1]`, `[2, 2]` $\implies$ *Sample Output*: `[2]`.
*   **C++14 Solution**:
    ```cpp
    #include <vector>
    #include <unordered_set>

    std::vector<int> intersection(const std::vector<int>& arr1, const std::vector<int>& arr2) {
        std::unordered_set<int> set1(arr1.begin(), arr1.end());
        std::vector<int> result;
        for (int x : arr2) {
            if (set1.erase(x)) { // erase returns 1 if element was present
                result.push_back(x);
            }
        }
        return result;
    }
    ```
*   **Complexity**: Time: $O(N + M)$, Space: $O(N)$.

---

## 8. PYQ Pattern: Maximum Difference (Stock Buy-Sell 1)
*   **Problem Statement**: Given an array representing daily stock prices, find the maximum profit you can achieve by buying on one day and selling on a future day.
    *   *Sample Input*: `[7, 1, 5, 3, 6, 4]` $\implies$ *Sample Output*: `5` (Buy at 1, sell at 6).
*   **C++14 Solution**:
    ```cpp
    #include <vector>
    #include <algorithm>
    #include <climits>

    int maxProfit(const std::vector<int>& prices) {
        int min_price = INT_MAX;
        int max_profit = 0;
        for (int price : prices) {
            min_price = std::min(min_price, price);
            max_profit = std::max(max_profit, price - min_price);
        }
        return max_profit;
    }
    ```
*   **Complexity**: Time: $O(N)$, Space: $O(1)$.

---

## 9. PYQ Pattern: Move Negatives to Left
*   **Problem Statement**: Rearrange an array such that all negative numbers appear on the left, and positive numbers on the right, in-place (relative order can change).
    *   *Sample Input*: `[1, -1, 3, -2, 7]` $\implies$ *Sample Output*: `[-1, -2, 3, 1, 7]` (or similar).
*   **C++14 Solution**:
    ```cpp
    #include <vector>
    #include <algorithm>

    void moveNegatives(std::vector<int>& arr) {
        int left = 0, right = arr.size() - 1;
        while (left < right) {
            if (arr[left] < 0) {
                left++;
            } else if (arr[right] >= 0) {
                right--;
            } else {
                std::swap(arr[left], arr[right]);
                left++;
                right--;
            }
        }
    }
    ```
*   **Complexity**: Time: $O(N)$, Space: $O(1)$.

---

## 10. PYQ Pattern: Second Smallest and Second Largest
*   **Problem Statement**: Find both the second smallest and second largest elements in an array.
    *   *Sample Input*: `[1, 2, 4, 6, 7]` $\implies$ *Sample Output*: `Second Smallest: 2, Second Largest: 6`.
*   **C++14 Solution**:
    ```cpp
    #include <vector>
    #include <utility>
    #include <climits>

    std::pair<int, int> findSecondMinMax(const std::vector<int>& arr) {
        int smallest = INT_MAX, secondSmallest = INT_MAX;
        int largest = INT_MIN, secondLargest = INT_MIN;
        
        for (int num : arr) {
            if (num < smallest) {
                secondSmallest = smallest;
                smallest = num;
            } else if (num < secondSmallest && num != smallest) {
                secondSmallest = num;
            }
            
            if (num > largest) {
                secondLargest = largest;
                largest = num;
            } else if (num > secondLargest && num != largest) {
                secondLargest = num;
            }
        }
        return {secondSmallest, secondLargest};
    }
    ```
*   **Complexity**: Time: $O(N)$, Space: $O(1)$.
