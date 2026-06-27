# Stack & Queue — Coding Application (Full Problem Solutions)

---

## Problem 1 — Valid Parentheses
**LeetCode:** #20 | **Difficulty:** Easy | **TCS Frequency:** High

### Problem Statement
Given a string `s` containing just the characters `'('`, `')'`, `'{'`, `'}'`, `'['` and `']'`, determine if the input string is valid.

### Approach
Use a stack. Push opening brackets. When encountering a closing bracket, check if the stack is empty or the top of the stack does not match. Pop on match.

### C++ Solution
```cpp
#include <stack>
#include <string>

class Solution {
public:
    bool isValid(std::string s) {
        std::stack<char> st;
        for (char c : s) {
            if (c == '(' || c == '{' || c == '[') {
                st.push(c);
            } else {
                if (st.empty()) return false;
                if (c == ')' && st.top() != '(') return false;
                if (c == '}' && st.top() != '{') return false;
                if (c == ']' && st.top() != '[') return false;
                st.pop();
            }
        }
        return st.empty();
    }
};
```
**Complexity:** Time $O(N)$ | Space $O(N)$

---

## Problem 2 — Next Greater Element I
**LeetCode:** #496 | **Difficulty:** Easy | **TCS Frequency:** High

### Problem Statement
The next greater element of some element `x` in an array is the first greater element that is to the right of `x` in the same array. Given two arrays `nums1` and `nums2` (where `nums1` is a subset of `nums2`), return an array containing the next greater element for each value of `nums1` in `nums2`.

### Approach
Use a monotonic decreasing stack on `nums2`. Traverse `nums2` from right to left (or left to right), maintaining elements in stack. Pop elements smaller than current, record the top of stack as next greater, then push current. Store results in a hash map for $O(1)$ lookup.

### C++ Solution
```cpp
#include <vector>
#include <stack>
#include <unordered_map>

class Solution {
public:
    std::vector<int> nextGreaterElement(std::vector<int>& nums1, std::vector<int>& nums2) {
        std::unordered_map<int, int> nextGreater;
        std::stack<int> st;
        
        for (int num : nums2) {
            while (!st.empty() && st.top() < num) {
                nextGreater[st.top()] = num;
                st.pop();
            }
            st.push(num);
        }
        
        std::vector<int> result;
        for (int num : nums1) {
            if (nextGreater.count(num)) {
                result.push_back(nextGreater[num]);
            } else {
                result.push_back(-1);
            }
        }
        return result;
    }
};
```
**Complexity:** Time $O(N_1 + N_2)$ | Space $O(N_2)$

---

## Problem 3 — Implement Queue using Stacks
**LeetCode:** #232 | **Difficulty:** Easy | **TCS Frequency:** High

### Problem Statement
Implement a first in first out (FIFO) queue using only two stacks. The implemented queue should support all the functions of a normal queue (`push`, `peek`, `pop`, and `empty`).

### Approach
Use two stacks, `s1` and `s2`. We push elements onto `s1`. When we need to `pop` or `peek`, if `s2` is empty, we transfer all elements from `s1` to `s2`. This reverses the LIFO order to FIFO order.

### C++ Solution
```cpp
#include <stack>

class MyQueue {
private:
    std::stack<int> s1, s2;
    void transfer() {
        if (s2.empty()) {
            while (!s1.empty()) {
                s2.push(s1.top());
                s1.pop();
            }
        }
    }
public:
    MyQueue() {}
    
    void push(int x) {
        s1.push(x);
    }
    
    int pop() {
        transfer();
        int val = s2.top();
        s2.pop();
        return val;
    }
    
    int peek() {
        transfer();
        return s2.top();
    }
    
    bool empty() {
        return s1.empty() && s2.empty();
    }
};
```
**Complexity:** Push $O(1)$ | Pop $O(1)$ amortized | Space $O(N)$
