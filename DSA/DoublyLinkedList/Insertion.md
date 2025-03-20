# Doubly Linked List - Insertion at a Specific Position

---

#### **Definition**
A **Doubly Linked List (DLL)** is a data structure where each node contains:
- **Data**: The value stored in the node.
- **Prev Pointer**: Pointer to the previous node.
- **Next Pointer**: Pointer to the next node.

---

#### **Algorithm for Insertion at a Specific Position**
1. **Create a New Node**
   - Allocate memory for the new node.
   - Set `newNode->data = value`.

2. **Insert at Head (Position = 1)** 
   - Set `newNode->next = head`.
   - Update the previous pointer of the old head: `head->prev = newNode`.
   - Make the new node the new head.

3. **Insert at Any Other Position**
   - Traverse the list to reach the `(pos - 1)`th node.
   - Adjust the pointers:
     - `newNode->next = temp->next`
     - `newNode->prev = temp`
     - If the next node exists:
       - `temp->next->prev = newNode`
     - `temp->next = newNode`

---

#### **Edge Cases**
- If the position is `1`, insert at the beginning and update the head.
- If the position is out of bounds, display an error message.
- If the list is empty, insert the new node as the head.

---

#### **Time and Space Complexity**
- **Time Complexity:** O(N) → Traversing the list to the `(pos - 1)`th node.
- **Space Complexity:** O(1) → Only one new node is created.

---

#### **C++ Code**
```cpp
#include <iostream>
using namespace std;

class Node {
public:
    int data;
    Node* prev;
    Node* next;

    Node(int val) {
        data = val;
        prev = nullptr;
        next = nullptr;
    }
};

// Function to insert a node at a specific position
Node* insertAtPosition(Node* head, int pos, int newData) {
    Node* newNode = new Node(newData);

    // Insert at the head (position 1)
    if (pos == 1) {
        newNode->next = head;
        if (head) {
            head->prev = newNode;
        }
        return newNode;  // New node becomes the new head
    }

    Node* temp = head;
    int count = 1;

    // Traverse to the (pos - 1)th node
    while (temp != nullptr && count < pos - 1) {
        temp = temp->next;
        count++;
    }

    // If position is invalid
    if (!temp) {
        cout << "Position out of bounds!" << endl;
        return head;
    }

    // Insert the new node
    newNode->next = temp->next;
    newNode->prev = temp;

    if (temp->next) {
        temp->next->prev = newNode;
    }

    temp->next = newNode;

    return head;
}

// Function to print the doubly linked list
void printList(Node* head) {
    Node* temp = head;
    while (temp) {
        cout << temp->data;
        if (temp->next) cout << " <-> ";
        temp = temp->next;
    }
    cout << endl;
}

int main() {
    // Creating the linked list: 1 <-> 2 <-> 4
    Node* head = new Node(1);
    head->next = new Node(2);
    head->next->prev = head;
    head->next->next = new Node(4);
    head->next->next->prev = head->next;

    cout << "Original List: ";
    printList(head);

    // Inserting node with data = 3 at position 3
    int newData = 3, position = 3;
    head = insertAtPosition(head, position, newData);

    cout << "Updated List: ";
    printList(head);

    return 0;
}
```

---
