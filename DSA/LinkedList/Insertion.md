# **Inserting a Node at the End of a Singly Linked List**

### **Concepts**

A **Singly Linked List** consists of nodes, where each node has:

1. **Data** – Stores the value.
2. **Next Pointer** – Points to the next node in the list.

To insert a node at the **end**, we need to:

- Find the last node (where `next == nullptr`).
- Link its `next` pointer to the new node.

### **Methodology**

1. **Create a new node**
    - Allocate memory for a new node.
    - Store the given value in it.
2. **Handle edge case**
    - If the linked list is empty (`head == nullptr`), make the new node the head.
3. **Traverse to the last node**
    - Start from `head` and move until `next` is `nullptr`.
4. **Attach the new node**
    - Update the last node’s `next` pointer to point to the new node.

### **Code Implementation**

```cpp
cpp
CopyEdit
class Solution {
  public:
    Node *insertAtEnd(Node *head, int x) {
        Node* newnode = new Node(x);

        // If the list is empty, new node becomes the head
        if (head == nullptr) {
            return newnode;
        }

        // Traverse to the last node
        Node* temp = head;
        while (temp->next != nullptr) {
            temp = temp->next;
        }

        // Attach new node at the end
        temp->next = newnode;

        return head;
    }
};

```

### **Time and Space Complexity**

- **Time Complexity:** `O(n)` (since we traverse the list once)
- **Space Complexity:** `O(1)` (only a few extra pointers are used)

This method ensures efficient insertion at the end of a singly linked list.


