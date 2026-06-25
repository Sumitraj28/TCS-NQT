---
title: "Arrays - Visualization"
section: "Coding"
---

# Array Operations Visual Guide

## 1. Array Operations Diagram

### A. Insertion (in the middle)
Inserting `X` at index `2`. Remaining elements must shift right.

```
Before State:
Index:     0     1     2     3     4
        +-----+-----+-----+-----+-----+
Value:  | 10  | 20  | 30  | 40  |     |   (Size = 4, Capacity = 5)
        +-----+-----+-----+-----+-----+

Step 1: Shift elements at index 2 and 3 to the right by one position.
Index:     0     1     2     3     4
        +-----+-----+-----+-----+-----+
Value:  | 10  | 20  |     | 30  | 40  |
        +-----+-----+-----+-----+-----+

Step 2: Write X (e.g. 99) at index 2.
Index:     0     1     2     3     4
        +-----+-----+-----+-----+-----+
Value:  | 10  | 20  | 99  | 30  | 40  |   (Size = 5, Capacity = 5)
        +-----+-----+-----+-----+-----+
```

---

### B. Deletion (from the middle)
Deleting element at index `1`. Remaining elements must shift left.

```
Before State:
Index:     0     1     2     3     4
        +-----+-----+-----+-----+-----+
Value:  | 10  | 99  | 30  | 40  | 50  |   (Size = 5)
        +-----+-----+-----+-----+-----+

Step 1: Remove element at index 1 and shift remaining elements left.
Index:     0     1     2     3     4
        +-----+-----+-----+-----+-----+
Value:  | 10  | 30  | 40  | 50  |     |   (Size = 4)
        +-----+-----+-----+-----+-----+
```

---

### C. Search (Linear Search)
Searching for value `40` sequentially.

```
Step 1: Compare index 0 (10 == 40?) -> NO. Move pointer right.
Step 2: Compare index 1 (30 == 40?) -> NO. Move pointer right.
Step 3: Compare index 2 (40 == 40?) -> YES! Found at index 2.
```

---

### D. Traversal
Iterating through the array from left to right using a pointer/index.

```
Loop i = 0 to Size - 1:
   Pointer:   i=0    i=1    i=2    i=3
               |      |      |      |
               v      v      v      v
            [ 10 ] [ 30 ] [ 40 ] [ 50 ]
```

---

## 2. Memory Layout vs Linked List

The diagram below compares how arrays are laid out in hardware memory compared to a linked list:

```
Static Array (Contiguous memory slots):
Address: 0x100   0x104   0x108   0x10C
         +-----+-----+-----+-----+
Value:   | 10  | 20  | 30  | 40  |
         +-----+-----+-----+-----+

Linked List (Non-contiguous heap nodes connected by pointers):
Address: 0x100               0x1F4               0x302
         +-----+-----+       +-----+-----+       +-----+-----+
Node:    | 10  |0x1F4| ----> | 20  |0x302| ----> | 30  |NULL |
         +-----+-----+       +-----+-----+       +-----+-----+
```

---

## 3. Data Structure Comparison Table

| Property | Array / std::vector | Linked List |
| :--- | :--- | :--- |
| **Memory Allocation** | Contiguous block | Scattered heap nodes |
| **Access Time** | $O(1)$ (Constant) | $O(N)$ (Requires traversal) |
| **Insert/Delete (Start)**| $O(N)$ (Requires shifting) | $O(1)$ (Change pointers) |
| **Insert/Delete (End)** | $O(1)$ (Amortized) | $O(N)$ (or $O(1)$ if tail pointer is maintained) |
| **Cache Friendliness** | High (Locality of reference)| Low (Scattered pointer jumping) |
| **Memory Overhead** | Low (Values only) | High (Data + next node pointers) |
