# **Constructing a Doubly Linked List (DLL) from an Array in C++**

---

### **1. Introduction**

In this blog, we will learn how to construct a **Doubly Linked List (DLL)** from an array in C++. We'll cover:

- The **concept of a DLL**
- The **C++ implementation**
- **Common mistakes** and how to avoid them
- **Time and space complexities**

---

### **2. What is a Doubly Linked List?**

A **doubly linked list** is a data structure where:

- Each **node** contains:
    - `data`: the value of the node
    - `next`: pointer to the next node
    - `prev`: pointer to the previous node
- Unlike a **singly linked list**, DLLs allow **bidirectional traversal**.

---

### **3. Node Structure in C++**

To define a DLL, we create a `Node` class:

```cpp
class Node {
public:
    int data;
    Node* next;
    Node* prev;

    Node(int value) {
        data = value;
        next = nullptr;
        prev = nullptr;
    }
};

```

- `data`: Holds the value of the node.
- `next`: Pointer to the next node.
- `prev`: Pointer to the previous node.
- The **constructor** initializes the node with the given value and sets the `next` and `prev` pointers to `nullptr`.

---

### **4. Approach to Construct the DLL**

To build a DLL from an array:

1. **Create the head node** with the first element of the array.
2. **Iterate through the array**:
    - Create a **new node** for each element.
    - Link the **current node** to the new node using the `next` pointer.
    - Link the **new node** back to the current node using the `prev` pointer.
    - Move the `current` pointer forward.
3. **Return the head** of the DLL.

---

### **5. Flowchart**

```
Start
   ↓
Create Head Node
   ↓
Iterate Through Array
   ↓
For Each Element:
   → Create New Node
   → Link Current Node → Next
   → Link New Node → Prev
   → Move Current Pointer
   ↓
Return Head of DLL
   ↓
End

```

---

### **6. C++ Code Implementation**

```cpp
#include <iostream>
#include <vector>
using namespace std;

class Node {
public:
    int data;
    Node* next;
    Node* prev;

    Node(int value) {
        data = value;
        next = nullptr;
        prev = nullptr;
    }
};

class Solution {
public:
    Node* constructDLL(vector<int>& arr) {
        if (arr.empty()) return nullptr;  // Handle empty array

        // Create the head node
        Node* head = new Node(arr[0]);
        Node* current = head;

        // Iterate through the array and construct the DLL
        for (int i = 1; i < arr.size(); i++) {
            Node* newnode = new Node(arr[i]);

            // Forward and backward linking
            current->next = newnode;
            newnode->prev = current;

            // Move the current pointer forward
            current = newnode;
        }

        return head;  // Return the head of the DLL
    }
};

// Function to print the DLL for testing
void printDLL(Node* head) {
    Node* current = head;
    while (current != nullptr) {
        cout << current->data;
        if (current->next != nullptr) cout << " <-> ";
        current = current->next;
    }
    cout << endl;
}

int main() {
    Solution solution;
    vector<int> arr = {1, 2, 3, 4, 5};

    Node* head = solution.constructDLL(arr);

    cout << "Doubly Linked List: ";
    printDLL(head);

    return 0;
}

```

---

### **7. Output**

```
Doubly Linked List: 1 <-> 2 <-> 3 <-> 4 <-> 5

```

---

### **8. Key Points**

1. **Forward Linking**
    
    ```cpp
    current->next = newnode;
    
    ```
    
    - Links the current node to the newly created node.
2. **Backward Linking**
    
    ```cpp
    newnode->prev = current;
    
    ```
    
    - Links the new node back to the current node.
3. **Move the Current Pointer**
    
    ```cpp
    current = newnode;
    
    ```
    
    - Moves the pointer forward to the new node.

---

### **9. Table of Common Mistakes and Fixes**

| **Mistake** | **Explanation** | **Fix** |
| --- | --- | --- |
| Incorrect pointer type | Using `int` instead of `Node*` for the pointer | Use `Node* current = head;` |
| Forgetting to move the pointer | Causes incorrect linking | Add `current = newnode;` |
| Returning the wrong node | Returning the last node instead of the head | Return `head` |

---

### **10. Time and Space Complexities**

- **Time Complexity:** \(O(n)\) → Iterates through the array once.
- **Space Complexity:** \(O(n)\) → Creates \(n\) nodes, each using space for `next` and `prev` pointers.

---

### **11. Conclusion**

In this blog, you learned:

- How to construct a **doubly linked list** from an array in C++.
- The correct **implementation** with proper pointer management.
- The **common mistakes** and how to avoid them.
- The **complexity analysis**.

By following this approach, you can efficiently construct and traverse a DLL in C++.
