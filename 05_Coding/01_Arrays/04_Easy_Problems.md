---
title: "Arrays - Easy Problems"
section: "Coding"
---

# Array Easy Coding Problems

This set contains 10 easy problems commonly asked in the TCS NQT 35-minute coding section.

---

## 1. Find the Largest Element in an Array
*   **Problem Statement**: Given an array of $N$ integers, find the largest element.
    *   *Constraints*: $1 \le N \le 10^5$, $-10^9 \le arr[i] \le 10^9$.
    *   *Sample Input*: `[3, 5, 1, 9, 4]` $\implies$ *Sample Output*: `9`.
*   **Approach**: Linear scan. Maintain a `maxVal` variable initialized to the first element and update it if a larger element is found.
*   **Dry Run**:
    *   Initialize `maxVal = arr[0] = 3`.
    *   Compare `5 > 3` $\implies$ Update `maxVal = 5`.
    *   Compare `1 > 5` $\implies$ No change.
    *   Compare `9 > 5` $\implies$ Update `maxVal = 9`.
    *   Compare `4 > 9` $\implies$ No change.
    *   Return `9`.
*   **C++14 Solution**:
    ```cpp
    #include <iostream>
    #include <vector>
    #include <algorithm>

    int findLargest(const std::vector<int>& arr) {
        if (arr.empty()) return -1; // Edge Case: Empty array
        int maxVal = arr[0];
        for (size_t i = 1; i < arr.size(); i++) {
            if (arr[i] > maxVal) {
                maxVal = arr[i];
            }
        }
        return maxVal;
    }
    ```
*   **Complexity**: Time: $O(N)$, Space: $O(1)$.
*   **Edge Cases**: Single element array (returns the element), all negative numbers (correctly initializes to the first negative value).
*   **Wrong Approach**: Sorting the array first ($O(N \log N)$), which is slower than a linear scan.

---

## 2. Find the Second Largest Element in an Array
*   **Problem Statement**: Find the second largest element in an array of $N$ integers. If no second largest exists, return -1.
    *   *Constraints*: $2 \le N \le 10^5$, $-10^9 \le arr[i] \le 10^9$.
    *   *Sample Input*: `[12, 35, 1, 10, 34, 1]` $\implies$ *Sample Output*: `34`.
*   **Approach**: Maintain two variables `largest` and `secondLargest`. Update both in a single linear scan.
*   **C++14 Solution**:
    ```cpp
    #include <vector>
    #include <climits>

    int findSecondLargest(const std::vector<int>& arr) {
        int largest = INT_MIN;
        int secondLargest = INT_MIN;
        
        for (int num : arr) {
            if (num > largest) {
                secondLargest = largest;
                largest = num;
            } else if (num > secondLargest && num < largest) {
                secondLargest = num;
            }
        }
        return (secondLargest == INT_MIN) ? -1 : secondLargest;
    }
    ```
*   **Complexity**: Time: $O(N)$, Space: $O(1)$.
*   **Wrong Approach**: Sorting and returning `arr[n-2]` fails if duplicates exist (e.g. `[35, 35, 10]`).

---

## 3. Reverse an Array
*   **Problem Statement**: Reverse an array of integers in-place.
    *   *Sample Input*: `[1, 2, 3, 4]` $\implies$ *Sample Output*: `[4, 3, 2, 1]`.
*   **Approach**: Two Pointers. Swap elements at `left` and `right` indices, moving pointers inward.
*   **C++14 Solution**:
    ```cpp
    #include <vector>
    #include <algorithm>

    void reverseArray(std::vector<int>& arr) {
        int left = 0, right = arr.size() - 1;
        while (left < right) {
            std::swap(arr[left], arr[right]);
            left++;
            right--;
        }
    }
    ```
*   **Complexity**: Time: $O(N)$, Space: $O(1)$.

---

## 4. Count Even and Odd Elements
*   **Problem Statement**: Count the number of even and odd integers in an array.
    *   *Sample Input*: `[2, 3, 4, 5, 6]` $\implies$ *Sample Output*: `Even: 3, Odd: 2`.
*   **Approach**: Loop through array and check parity using `% 2`.
*   **C++14 Solution**:
    ```cpp
    #include <vector>
    #include <utility>

    std::pair<int, int> countEvenOdd(const std::vector<int>& arr) {
        int even = 0, odd = 0;
        for (int num : arr) {
            if (num % 2 == 0) even++;
            else odd++;
        }
        return {even, odd};
    }
    ```
*   **Complexity**: Time: $O(N)$, Space: $O(1)$.

---

## 5. Linear Search
*   **Problem Statement**: Find the index of target value $K$ in an array. Return -1 if not found.
    *   *Sample Input*: `[4, 2, 7, 1]`, Target $= 7$ $\implies$ *Sample Output*: `2`.
*   **C++14 Solution**:
    ```cpp
    #include <vector>

    int linearSearch(const std::vector<int>& arr, int target) {
        for (size_t i = 0; i < arr.size(); i++) {
            if (arr[i] == target) return i;
        }
        return -1;
    }
    ```
*   **Complexity**: Time: $O(N)$, Space: $O(1)$.

---

## 6. Sum of Array Elements
*   **Problem Statement**: Calculate the sum of all elements in an array.
    *   *Sample Input*: `[1, 2, 3, 4]` $\implies$ *Sample Output*: `10`.
*   **C++14 Solution**:
    ```cpp
    #include <vector>
    #include <numeric>

    long long getSum(const std::vector<int>& arr) {
        long long sum = 0;
        for (int num : arr) sum += num;
        return sum;
    }
    ```
*   **Complexity**: Time: $O(N)$, Space: $O(1)$.
*   **Edge Case**: Large numbers can overflow 32-bit integers; use `long long`.

---

## 7. Check if Array is Sorted
*   **Problem Statement**: Determine if an array is sorted in non-decreasing order.
    *   *Sample Input*: `[1, 2, 5, 4]` $\implies$ *Sample Output*: `false`.
*   **C++14 Solution**:
    ```cpp
    #include <vector>

    bool isSorted(const std::vector<int>& arr) {
        for (size_t i = 1; i < arr.size(); i++) {
            if (arr[i] < arr[i - 1]) return false;
        }
        return true;
    }
    ```
*   **Complexity**: Time: $O(N)$, Space: $O(1)$.

---

## 8. Remove Duplicates from Sorted Array
*   **Problem Statement**: Remove duplicates from a sorted array in-place, returning the size of unique elements.
    *   *Sample Input*: `[1, 1, 2, 2, 3]` $\implies$ *Sample Output*: `3` (Array updated to `[1, 2, 3, ...]`).
*   **Approach**: Two pointers. Pointer `i` marks the write position for unique elements, and `j` scans the array.
*   **C++14 Solution**:
    ```cpp
    #include <vector>

    int removeDuplicates(std::vector<int>& arr) {
        if (arr.empty()) return 0;
        int i = 0;
        for (size_t j = 1; j < arr.size(); j++) {
            if (arr[j] != arr[i]) {
                i++;
                arr[i] = arr[j];
            }
        }
        return i + 1;
    }
    ```
*   **Complexity**: Time: $O(N)$, Space: $O(1)$.

---

## 9. Count Occurrences of Element
*   **Problem Statement**: Count how many times target $X$ appears in an array.
    *   *Sample Input*: `[1, 2, 2, 3]`, Target $= 2$ $\implies$ *Sample Output*: `2`.
*   **C++14 Solution**:
    ```cpp
    #include <vector>

    int countOccurrences(const std::vector<int>& arr, int target) {
        int count = 0;
        for (int num : arr) {
            if (num == target) count++;
        }
        return count;
    }
    ```
*   **Complexity**: Time: $O(N)$, Space: $O(1)$.

---

## 10. Find Mean and Median of an Array
*   **Problem Statement**: Calculate the mean and median of an unsorted array of size $N$.
    *   *Sample Input*: `[1, 3, 4, 2, 6]` $\implies$ *Sample Output*: `Mean: 3.2, Median: 3`.
*   **Approach**: Mean is sum divided by $N$. Median is the middle element of the sorted array.
*   **C++14 Solution**:
    ```cpp
    #include <vector>
    #include <algorithm>
    #include <utility>

    std::pair<double, double> getMeanMedian(std::vector<int> arr) {
        int n = arr.size();
        double sum = 0;
        for (int num : arr) sum += num;
        double mean = sum / n;
        
        std::sort(arr.begin(), arr.end());
        double median;
        if (n % 2 == 0) {
            median = (arr[n / 2 - 1] + arr[n / 2]) / 2.0;
        } else {
            median = arr[n / 2];
        }
        return {mean, median};
    }
    ```
*   **Complexity**: Time: $O(N \log N)$ (due to sorting), Space: $O(1)$ (or $O(N)$ to copy input).
