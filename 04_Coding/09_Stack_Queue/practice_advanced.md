# Stack & Queue — Practice: Advanced / Prime Level (10 Questions)

---

### Q1 — Sliding Window Maximum
Find the maximum element in each sliding window of size $K$.
**Full Solution (Monotonic Deque):**
Maintain a deque of indices where values are in decreasing order. Remove elements from front if they fall outside the current window. Remove elements from back if they are smaller than the incoming element.
```cpp
#include <vector>
#include <deque>

class Solution {
public:
    std::vector<int> maxSlidingWindow(std::vector<int>& nums, int k) {
        std::deque<int> dq;
        std::vector<int> result;
        for (int i = 0; i < (int)nums.size(); ++i) {
            // Remove elements outside current window
            if (!dq.empty() && dq.front() == i - k) {
                dq.pop_front();
            }
            // Remove smaller elements in current window
            while (!dq.empty() && nums[dq.back()] < nums[i]) {
                dq.pop_back();
            }
            dq.push_back(i);
            // Append result when window is formed
            if (i >= k - 1) {
                result.push_back(nums[dq.front()]);
            }
        }
        return result;
    }
};
```
**Complexity:** Time $O(N)$ | Space $O(K)$

---

### Q2 — Largest Rectangle in Histogram
Given height values of histogram bars, find area of largest rectangle.
**Full Solution (Monotonic Stack):**
```cpp
#include <vector>
#include <stack>
#include <algorithm>

class Solution {
public:
    int largestRectangleArea(std::vector<int>& heights) {
        std::stack<int> st;
        heights.push_back(0); // sentinel to flush stack at the end
        int maxArea = 0;
        for (int i = 0; i < (int)heights.size(); ++i) {
            while (!st.empty() && heights[st.top()] > heights[i]) {
                int h = heights[st.top()];
                st.pop();
                int w = st.empty() ? i : i - st.top() - 1;
                maxArea = std::max(maxArea, h * w);
            }
            st.push(i);
        }
        return maxArea;
    }
};
```
**Complexity:** Time $O(N)$ | Space $O(N)$

---

### Q3 — Daily Temperatures
Find days wait until warmer temperature.
**Full Solution:** Monotonic index stack matching smaller elements.

---

### Q4 — Trapping Rain Water
Compute trapped water inside elevation map bars.
**Full Solution:**
```cpp
#include <vector>
#include <stack>
#include <algorithm>

int trap(std::vector<int>& height) {
    std::stack<int> st;
    int water = 0;
    for (int i = 0; i < (int)height.size(); ++i) {
        while (!st.empty() && height[st.top()] < height[i]) {
            int bottom = st.top();
            st.pop();
            if (st.empty()) break;
            int distance = i - st.top() - 1;
            int bounded_height = std::min(height[i], height[st.top()]) - height[bottom];
            water += distance * bounded_height;
        }
        st.push(i);
    }
    return water;
}
```

---

### Q5 — Asteroid Collision
Simulate asteroid collisions where positive value moves right, negative moves left.
**Full Solution:** Push to stack, check collisions when negative meets positive top.

---

### Q6 — Basic Calculator (Evaluating infix with parentheses)
Solve basic calculator string with `+`, `-`, `(`, `)`.
**Full Solution:** Use stack for keeping track of running sum and signs before parentheses.

---

### Q7 — LRU Cache (Design using List + Map)
Design Least Recently Used Cache.
**Full Solution:** Double-linked list containing key-value nodes, map mapping keys to list iterators.

---

### Q8 — LFU Cache (Design)
Design Least Frequently Used Cache.
**Full Solution:** Map of frequencies pointing to double-linked lists of elements.

---

### Q9 — Remove K Digits
Remove $K$ digits from number to make it smallest possible.
**Full Solution:** Monotonic increasing stack. Pop if top > incoming digit and $K > 0$.

---

### Q10 — Design Min Stack without Extra Stack
Design a Min Stack using $O(1)$ auxiliary space.
**Full Solution:** Store difference values or encrypted values `2 * x - minVal` in stack.
```cpp
#include <stack>

class MinStackO1 {
private:
    std::stack<long long> st;
    long long minVal;
public:
    void push(int val) {
        if (st.empty()) {
            st.push(0);
            minVal = val;
        } else {
            st.push((long long)val - minVal);
            if (val < minVal) minVal = val;
        }
    }
    void pop() {
        long long diff = st.top();
        st.pop();
        if (diff < 0) minVal = minVal - diff; // restore previous min
    }
    int top() {
        long long diff = st.top();
        return diff < 0 ? minVal : minVal + diff;
    }
    int getMin() {
        return minVal;
    }
};
```
**Complexity:** All operations $O(1)$ | Space $O(1)$ auxiliary
