# **`Middle of the Linked List`** *using Tortoise and Hare Algorithm*

---

###  **1. Problem Analysis**
- You are given the **head of a singly linked list**.  
- You need to return the **middle node**.  
- If the list has two middle nodes (even length), return the **second middle node**.

---

###  **2. Example Walkthrough**

**Example 1:**  
Input: `1 → 2 → 3 → 4 → 5`  
- **Middle node** → `3`  
- Output: `3 → 4 → 5`

**Example 2:**  
Input: `1 → 2 → 3 → 4 → 5 → 6`  
- **Middle nodes** → `3` and `4`  
- Return the **second middle** → `4 → 5 → 6`

---

### **3. Approach**
We will use the **Tortoise and Hare Algorithm (Two-Pointer Technique)**:
- **Slow pointer** → Moves by **1 step** at a time.  
- **Fast pointer** → Moves by **2 steps** at a time.  

###  **Logic Insight**
- When the `fast` pointer reaches the end, the `slow` pointer will be at the **middle node**.  
- In **even-length lists**, `slow` will naturally land on the **second middle** due to the `fast` pointer moving by two steps.  

---

###  **4. Code**

```cpp
#include <iostream>
using namespace std;

// Definition for singly-linked list node.
class ListNode {
public:
    int val;
    ListNode* next;

    ListNode(int value) {
        val = value;
        next = NULL;
    }
};

class Solution {
public:
    ListNode* middleNode(ListNode* head) {
        // Edge case: empty list or single node
        if (head == NULL || head->next == NULL) {
            return head;
        }

        ListNode* slow = head;
        ListNode* fast = head;

        // Tortoise and Hare: slow moves by 1, fast by 2
        while (fast != NULL && fast->next != NULL) {
            slow = slow->next;          // Move slow by 1 step
            fast = fast->next->next;    // Move fast by 2 steps
        }

        // When fast reaches end, slow is at the middle
        return slow;
    }
};

// Helper function to create and print the list
void printList(ListNode* head) {
    while (head != NULL) {
        cout << head->val << " ";
        head = head->next;
    }
    cout << endl;
}

int main() {
    // Creating the linked list: 1 -> 2 -> 3 -> 4 -> 5 -> 6
    ListNode* head = new ListNode(1);
    head->next = new ListNode(2);
    head->next->next = new ListNode(3);
    head->next->next->next = new ListNode(4);
    head->next->next->next->next = new ListNode(5);
    head->next->next->next->next->next = new ListNode(6);

    Solution solution;
    ListNode* middle = solution.middleNode(head);

    cout << "Middle Node: ";
    printList(middle);

    return 0;
}
```

---

### **5. Execution Flow**

For the list `1 → 2 → 3 → 4 → 5 → 6`:  
- **Initial:**  
   - `slow = 1`  
   - `fast = 1`  
- **Iteration 1:**  
   - `slow → 2`  
   - `fast → 3`  
- **Iteration 2:**  
   - `slow → 3`  
   - `fast → 5`  
- **Iteration 3:**  
   - `slow → 4`  
   - `fast → NULL`  
- **Result:**  
   - `slow` points to `4` → the second middle node.

---

###  **6. Time and Space Complexity Analysis**
- **Time Complexity:** O(N)  
   - Both `slow` and `fast` traverse the list, but `fast` moves twice as fast.  
- **Space Complexity:** O(1)  
   - Only two pointers (`slow` and `fast`) are used.

---

###  **7. Common Mistakes and Tips**
1. **Edge Cases:**
   - When the list has only **one node** → return it directly.  
   - Check for `NULL` when accessing `fast->next->next` to avoid runtime errors.  
2. **Interview Tip:**
   - Always explain the **Tortoise and Hare Algorithm** clearly.  
   - Emphasize why the **second middle** is returned automatically in even-length lists due to the `fast` pointer moving by 2 steps.

---

###  **8. Key Takeaways**
- This problem uses the **Tortoise and Hare Algorithm** (Two-Pointer Technique).  
- **Fast** moves twice as fast as **slow**, landing **slow** on the middle node.  
- For even-length lists, the algorithm naturally returns the **second middle**.  
- **Time Complexity:** O(N) → Single traversal.  
- **Space Complexity:** O(1) → No extra space used.

---

