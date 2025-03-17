# **Understanding the Problem: Delete a Node in a Singly Linked List**

### **Key Observations:**

1. **You are given only the node to delete, not the head of the list.**
2. **You cannot access the previous node**, so you can't update its `next` pointer.
3. **The node to be deleted is not the last node**, which guarantees that there is a `next` node.

### **Approach to Solve the Problem:**

Since we don't have access to the previous node, we **cannot actually remove the given node directly**. Instead, we modify its value and links to mimic deletion:

1. **Copy the value of the next node into the given node.**
2. **Point the given node’s `next` to the next node’s `next` (bypassing the next node).**
3. **Effectively, this removes the next node while keeping the list structure intact.**

### **Example Walkthrough:**

### **Example 1:**

Input:

`head = [4,5,1,9]`, `node = 5`

Steps:

1. Copy `1` (next node’s value) into `5`, making the list:**`[4,1,1,9]`**
2. Point `5`’s next to `9`, skipping the original `1`:**`[4,1,9]`**

Output: `[4,1,9]`

### **Example 2:**

Input:

`head = [4,5,1,9]`, `node = 1`

Steps:

1. Copy `9` into `1`: `[4,5,9,9]`
2. Point `1`’s next to `nullptr`, effectively removing the duplicate `9`: `[4,5,9]`

---

### **Code Implementation in C++**

```cpp
cpp
CopyEdit
class Solution {
public:
    void deleteNode(ListNode* node) {
        node->val = node->next->val;   // Copy next node's value
        node->next = node->next->next; // Bypass next node
    }
};

```

---

### **Complexity Analysis**

- **Time Complexity:** `O(1)` → Only modifies a constant number of pointers.
- **Space Complexity:** `O(1)` → No extra space is used.

This approach efficiently "deletes" the node by shifting values instead of physically removing it.
