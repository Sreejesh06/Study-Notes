# **Doubly Linked List (DLL) Deletion – Interview Notes**

---

## **1. Problem Statement**

Delete a node at a given position `x` from a **Doubly Linked List (DLL)**.

---

## **2. DLL Structure**

```cpp
class Node {
public:
    int data;
    Node* next;
    Node* back;

    // Constructor with data only
    Node(int data1) {
        data = data1;
        next = nullptr;
        back = nullptr;
    }

    // Constructor with data and links
    Node(int data1, Node* next1, Node* back1) {
        data = data1;
        next = next1;
        back = back1;
    }
};

```

---

## **3. Approaches**

### **a) Edge Cases**

- If DLL is **empty** → return `nullptr`.
- If the list has **only one node** → free the memory and return `nullptr`.
- If `x > DLL size` → return original head.

---

### **b) Node Deletion Logic**

1. **Head Deletion (x = 1)**
    - Move `head` to the next node.
    - Set `head->back = nullptr`.
    - Free the old head.
2. **Tail Deletion**
    - Traverse to the tail.
    - Set `tail->back->next = nullptr`.
    - Free the tail.
3. **Middle Node Deletion**
    - Connect the `back` and `front` nodes.
    - `back->next = front`
    - `front->back = back`
    - Free the current node.

---

## **4. Code Implementation**

```cpp
Node* deleteNode(Node* head, int x) {
    // Edge cases
    if (!head) return nullptr;  // Empty list
    if (x <= 0) return head;

    Node* curr = head;
    int count = 1;

    // Traverse to the position
    while (curr && count < x) {
        curr = curr->next;
        count++;
    }

    if (!curr) return head;  // Out of range

    // Case 1: Head Deletion
    if (!curr->back) {
        head = curr->next;
        if (head) head->back = nullptr;
    }
    // Case 2: Tail Deletion
    else if (!curr->next) {
        curr->back->next = nullptr;
    }
    // Case 3: Middle Node Deletion
    else {
        curr->back->next = curr->next;
        curr->next->back = curr->back;
    }

    delete curr;  // Free memory
    return head;
}

```

---

## **5. Time and Space Complexity**

- **Time Complexity:** O(N) → Traverse the DLL to reach the position.
- **Space Complexity:** O(1) → Only pointers are used.

---

## **6. Example Execution**

### **Input DLL**

```
1 <-> 2 <-> 3 <-> 4 <-> 5

```

### **Delete `x = 1` (Head)**

- New DLL:

```
2 <-> 3 <-> 4 <-> 5

```

---
