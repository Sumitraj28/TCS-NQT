# Linked List — Practice: Basic (15 Questions)

---

### Q1 — Define Singly Linked List Node struct
**Answer:**
```cpp
struct Node {
    int data;
    Node* next;
    Node(int val) : data(val), next(nullptr) {}
};
```

---

### Q2 — Singly Linked List Traversal
**Answer:**
```cpp
void traverse(Node* head) {
    while (head != nullptr) {
        std::cout << head->data << " ";
        head = head->next;
    }
}
```

---

### Q3 — Insert Node at Head
**Answer:**
```cpp
Node* insertAtHead(Node* head, int val) {
    Node* newNode = new Node(val);
    newNode->next = head;
    return newNode;
}
```

---

### Q4 — Find Size of Linked List
**Answer:** Traverse the list, maintaining an integer count of elements.

---

### Q5 — Search Element in Linked List
**Answer:** Check `curr->data == target` while traversing.

---

### Q6 — Insert Node at End
**Answer:**
```cpp
Node* insertAtEnd(Node* head, int val) {
    Node* newNode = new Node(val);
    if (!head) return newNode;
    Node* temp = head;
    while (temp->next) temp = temp->next;
    temp->next = newNode;
    return head;
}
```

---

### Q7 — Delete Node at Head
**Answer:** Save head's next, delete head, return next.

---

### Q8 — Print Linked List Elements in Reverse (Recursively)
**Answer:**
```cpp
void printReverse(Node* head) {
    if (!head) return;
    printReverse(head->next);
    std::cout << head->data << " ";
}
```

---

### Q9 — Find Last Node of Linked List
**Answer:** Loop while `curr->next != nullptr`.

---

### Q10 — Free Entire Linked List Memory
**Answer:**
```cpp
void freeList(Node* head) {
    while (head) {
        Node* temp = head;
        head = head->next;
        delete temp;
    }
}
```

---

### Q11 — Find N-th Node (0-indexed)
**Answer:** Traverse $N$ steps starting from head, verifying boundaries.

---

### Q12 — Create Circular Node Link
How to link the last node back to head?
**Answer:** `lastNode->next = head;`

---

### Q13 — Delete Node at End
**Answer:** Traverse to second-to-last node, delete its `next` node, set it to `nullptr`.

---

### Q14 — Double Linked List Node struct
**Answer:**
```cpp
struct DLLNode {
    int data;
    DLLNode* next;
    DLLNode* prev;
    DLLNode(int val) : data(val), next(nullptr), prev(nullptr) {}
};
```

---

### Q15 — Compare arrays and linked lists
**Answer:** Arrays support $O(1)$ random access but have fixed size. Linked lists have dynamic size but require $O(N)$ sequential traversal.
