# How to Identify Singly Linked List (SLL) vs Doubly Linked List (DLL)

### Key Differences Between SLL and DLL
| **Feature**        | **Singly Linked List (SLL)**                    | **Doubly Linked List (DLL)**               |
|---------------------|-----------------------------------------------|-------------------------------------------|
| **Next pointer**    | Each node has only a `next` pointer            | Each node has `next` and `prev` pointers  |
| **Backward traversal** | Only forward traversal is possible            | Can traverse both forward and backward    |
| **Memory usage**    | Less memory usage (1 pointer per node)         | More memory usage (2 pointers per node)   |
| **Complexity**       | Simpler operations but less flexible           | More complex operations but more flexible |

---

## Clues to Identify the List Type

#### 1. **Clue in the Node Definition**
- **Singly Linked List (SLL)** → Only `next` pointer is present:
```cpp
struct ListNode {
    int val;
    ListNode* next;      // Only next pointer (SLL)
};
```
- **Doubly Linked List (DLL)** → Both `next` and `prev` pointers are present:
```cpp
struct ListNode {
    int val;
    ListNode* next;      // Forward pointer
    ListNode* prev;      // Backward pointer (DLL)
};
```

---

#### 2. **Traversal Direction**
- **SLL:** Only forward traversal (`temp = temp->next`).
- **DLL:** Can traverse in both directions (`temp = temp->next` and `temp = temp->prev`).

---

#### 3. **Operations and Time Complexity**
- **SLL clues:**
    - No backward traversal.
    - Removing the last or middle node requires **iteration from the start**.
    - Example: Removing the nth node from the end → **SLL** (forward-only traversal).
- **DLL clues:**
    - Operations like `prev` or backward traversal.
    - Faster insert/delete in both directions.
    - Example: Removing the last node → **DLL** (backward traversal makes it easier).

---

#### 4. **Memory Management**
- **SLL:** Uses less memory (1 pointer per node).
- **DLL:** Uses more memory (2 pointers per node).

---

#### 5. **Leetcode/Interview Hints**
- **"Reverse the list"** → Usually SLL.
- **"Traverse backward"** → Definitely DLL.
- **"Random access is possible"** → Likely DLL or array-based list.

---

### Example Identification
1. **SLL Node Definition:**
```cpp
struct ListNode {
    int val;
    ListNode* next;
};
```
- Only `next` → **SLL**

2. **DLL Node Definition:**
```cpp
struct ListNode {
    int val;
    ListNode* next;
    ListNode* prev;
};
```
- `next` and `prev` → **DLL**

---

### ✅ **Key Takeaway**
To identify the list type:
- **Node Definition:**
    - `next` only → **SLL**  
    - `next` and `prev` → **DLL**  
- **Traversal clues:**
    - Forward-only → **SLL**
    - Backward traversal → **DLL**
- **Operations:**
    - Faster deletions from both ends → **DLL**
    - Iteration required for backward movement → **SLL**
- **Memory usage:**
    - More pointers → **DLL**
    - Fewer pointers → **SLL**

In interviews, **always check the class definition or observe the traversal operations** to determine whether you are working with an SLL or DLL.


