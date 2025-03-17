# **Counting Nodes in a Singly Linked List**

## **Introduction**

A **singly linked list** consists of nodes, where each node contains:

- A **value (data)**
- A **pointer to the next node (next)**

The goal is to count the number of nodes in the linked list. The length of the list is defined as the total number of nodes present.

---

## **Approach to Solve the Problem**

To count the nodes, we can use a simple traversal method:

1. **Initialize a counter `length = 0`**
2. **Start from the head node and traverse the list**
    - For each node, increase `length` by `1`
    - Move to the next node (`temp = temp->next`)
3. **Stop when `temp == nullptr`** (end of the list)
4. **Return `length`** as the final count

---

## **Example Walkthrough**

### **Example 1**

Input:

```
rust
CopyEdit
1 -> 2 -> 3 -> 4 -> 5

```

Steps:

- `length = 1` (at node `1`)
- `length = 2` (at node `2`)
- `length = 3` (at node `3`)
- `length = 4` (at node `4`)
- `length = 5` (at node `5`)Output: **`5`**

### **Example 2**

Input:

```
rust
CopyEdit
2 -> 4 -> 6 -> 7 -> 5 -> 1 -> 0

```

Steps:

- `length = 1` (at node `2`)
- `length = 2` (at node `4`)
- `length = 3` (at node `6`)
- `length = 4` (at node `7`)
- `length = 5` (at node `5`)
- `length = 6` (at node `1`)
- `length = 7` (at node `0`)Output: **`7`**

---

## **Code Implementation in C++**

```cpp
cpp
CopyEdit
class Solution {
public:
    // Function to count nodes of a linked list.
    int getCount(struct Node* head) {
        int length = 0;  // Initialize length to 0
        Node* temp = head;

        while (temp != nullptr) { // Traverse the list
            length++;
            temp = temp->next;
        }

        return length;
    }
};

```

---

## **Complexity Analysis**

- **Time Complexity:** `O(n)` → We visit each node once.
- **Space Complexity:** `O(1)` → No extra space is used.

This approach ensures an efficient and optimal way to count the number of nodes in a singly linked list.
