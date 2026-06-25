---
title: "Arrays - Theory"
section: "Coding"
---

# Array Theoretical Foundation

## 1. Plain-English Explanation
An array is like a row of lockers numbered from `0` to `N-1`. Every locker in the row is identical in size and can hold exactly one item of the same type (e.g., all integers or all characters). Because the lockers are placed right next to each other in a continuous line, if you know the location of the first locker, you can instantly find any other locker by counting the offset steps from the start.

---

## 2. Memory Model & Visual Representation
In computer hardware, an array is allocated as a single, uninterrupted block of physical random access memory (RAM).

```
Index:         0       1       2       3       4
          +-------+-------+-------+-------+-------+
Value:    |  10   |  20   |  30   |  40   |  55   |
          +-------+-------+-------+-------+-------+
Address:   0x100   0x104   0x108   0x10C   0x110   (Assuming 4-byte integers)
```

### The Offset Formula:
Because memory is contiguous, the computer calculates the location of any element `arr[i]` instantly using multiplication:
$$\text{Address of } arr[i] = \text{Base Address} + \left(i \times \text{Size of Datatype}\right)$$
This arithmetic offset calculation is why array index lookups are extremely fast ($O(1)$ time complexity).

---

## 3. C++ Implementation from Scratch (Custom Dynamic Array)
This code shows how a dynamic array (similar to `std::vector` in C++) is implemented using raw memory management.

```cpp
#include <iostream>
#include <stdexcept>

class DynamicArray {
private:
    int* data;         // Pointer to raw array memory block
    int capacityCount; // Total allocated slots
    int currentSize;   // Number of filled slots

    // Resize the array when capacity is full
    void resize() {
        capacityCount *= 2; // Double the capacity
        int* temp = new int[capacityCount];
        
        // Copy elements from old block to new block
        for (int i = 0; i < currentSize; i++) {
            temp[i] = data[i];
        }
        
        delete[] data; // Free old memory block
        data = temp;   // Repoint data pointer
    }

public:
    // Constructor: Initialize with capacity of 2
    DynamicArray() {
        capacityCount = 2;
        currentSize = 0;
        data = new int[capacityCount];
    }

    // Destructor: Free allocated heap memory
    ~DynamicArray() {
        delete[] data;
    }

    // Insert element at the end
    void push_back(int value) {
        if (currentSize == capacityCount) {
            resize();
        }
        data[currentSize] = value;
        currentSize++;
    }

    // Access element with boundary checks
    int get(int index) const {
        if (index < 0 || index >= currentSize) {
            throw std::out_of_range("Index out of bounds");
        }
        return data[index];
    }

    // Return current size
    int size() const {
        return currentSize;
    }
};

int main() {
    DynamicArray arr;
    arr.push_back(10);
    arr.push_back(20);
    arr.push_back(30); // Triggers resize
    
    std::cout << "Element at index 2: " << arr.get(2) << std::endl; // Output: 30
    return 0;
}
```

---

## 4. C++ STL Equivalents
C++ standard template library provides two containers for arrays:
1.  **`std::array<type, size>`**: A static array wrapper. Size must be known at compile-time. Allocates on stack memory.
2.  **`std::vector<type>`**: A dynamic array wrapper. Resizes automatically when full. Allocates on heap memory.

---

## 5. Operations Complexity Table

| Operation | Time Complexity (Average) | Time Complexity (Worst) | Space Complexity | Reason for Complexity |
| :--- | :--- | :--- | :--- | :--- |
| **Access (Lookup)** | $O(1)$ | $O(1)$ | $O(1)$ | Uses base address offset math directly. |
| **Search (Linear)** | $O(N)$ | $O(N)$ | $O(1)$ | Must scan all elements if target is at the end. |
| **Search (Binary)** | $O(\log N)$ | $O(\log N)$ | $O(1)$ | Requires sorted array. Half search space each step. |
| **Insert (at end)** | $O(1)$ | $O(1)$ | $O(1)$ | Direct insertion. Amortized $O(1)$ for dynamic arrays. |
| **Insert (middle)** | $O(N)$ | $O(N)$ | $O(1)$ | Requires shifting remaining elements right. |
| **Delete (middle)** | $O(N)$ | $O(N)$ | $O(1)$ | Requires shifting remaining elements left. |
