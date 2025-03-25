# **Reversing a Doubly Linked List (DLL) – In-Depth Explanation**


---

### **1. Understand the Problem**

You are given a **doubly linked list (DLL)**, and your task is to **reverse** it. In a DLL:
- Each node contains:
  - `data`: The value stored in the node.
  - `prev`: A pointer to the **previous** node.
  - `next`: A pointer to the **next** node.

The goal is to:
- Swap the `prev` and `next` pointers of each node.
- Return the **new head** of the reversed list.

---

### **2. How to Approach**

Think of the reversal process as:
1. **Swapping the Directions:** For each node, you need to **flip the connections** by swapping:
   - `prev` → becomes `next`
   - `next` → becomes `prev`
2. **Iterating through the DLL:** Use a loop to traverse the list node by node and apply the swap logic.
3. **Return the new head:** The last node in the original list becomes the new head.

---

### **3. Example with Visualization**

Let's consider a simple DLL:
```
  Original:  1 <-> 2 <-> 3
```
After reversing:
```
Reversed:  3 <-> 2 <-> 1
```

In detail:
- `1` → `prev = NULL`, `next = 2`
- `2` → `prev = 1`, `next = 3`
- `3` → `prev = 2`, `next = NULL`

After reversing:
- `1` → `prev = 2`, `next = NULL`
- `2` → `prev = 3`, `next = 1`
- `3` → `prev = NULL`, `next = 2`

---

### **4. Code Walkthrough**
```cpp
class Solution {
  public:
    DLLNode* reverseDLL(DLLNode* head) {
        // Base case: If DLL is empty or has only one node
        if (head == NULL || head->next == NULL) {
            return head;
        }
        
        DLLNode* last = NULL;      // To store the previous node
        DLLNode* curr = head;      // Pointer to traverse the DLL
        
        // Loop through the entire DLL
        while (curr != NULL) {
            last = curr->prev;         // Store the previous node
            curr->prev = curr->next;   // Swap the prev and next
            curr->next = last;         // Swap next with prev
            
            curr = curr->prev;         // Move to the next node (which is actually prev now)
        }
        
        // Return the new head
        return last->prev;
    }
};
```

---

### **5. Step-by-Step Execution**

Let's go through the logic with an example DLL:
```
1 <-> 2 <-> 3
```

- **Iteration 1:**
  - `curr = 1`
  - Store `last = curr->prev` → `last = NULL`
  - Swap:
    - `curr->prev = curr->next` → `prev = 2`
    - `curr->next = last` → `next = NULL`
  - Move to the next node:
    - `curr = curr->prev` → `curr = 2`

- **Iteration 2:**
  - `curr = 2`
  - Store `last = curr->prev` → `last = 1`
  - Swap:
    - `prev = 3`
    - `next = 1`
  - Move to the next node:
    - `curr = curr->prev` → `curr = 3`

- **Iteration 3:**
  - `curr = 3`
  - Store `last = curr->prev` → `last = 2`
  - Swap:
    - `prev = NULL`
    - `next = 2`
  - Move to the next node:
    - `curr = curr->prev` → `curr = NULL`

After the loop:
- `last = 2`
- `last->prev = 3` → this is the new head.

---

### **6. Key Takeaways and Interview Tips**

- **Base cases to handle first:**
  - If the list is empty or has only one node, return `head` immediately.
- **Swapping the pointers:**
  - In each iteration:
    - Swap `prev` with `next`.
    - Move the `curr` pointer using `curr = curr->prev`.
- **Edge case handling:**
  - After the loop, return `last->prev` instead of `last` because `last` points to the second last node, while `last->prev` is the new head.
- **Time and Space Complexity:**
  - **Time complexity:** O(N) → You iterate through all N nodes once.
  - **Space complexity:** O(1) → You only use a few pointers, no extra space.

---

### **7. Common Mistakes to Avoid**
1. **Incorrect head return:** 
   - Do not return `last`. Instead, return `last->prev` because it points to the new head.
2. **Not handling empty or single-node lists:** 
   - Failing to include the base case can cause runtime errors.
3. **Incorrect traversal after swapping:** 
   - After swapping, the next node is actually the **previous** one, so use `curr = curr->prev`.

---


