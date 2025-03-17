# **Searching for a Key in a Singly Linked List**

## **Introduction**

A **singly linked list** consists of nodes, where each node has:

- A **data field** (stores the value).
- A **pointer to the next node** (next).

Given a linked list and a **key**, our goal is to check if the key exists in the list.

---

## **Approach to Solve the Problem**

To check if the key is present in the linked list:

1. **Start from the head** node.
2. **Traverse the list node by node.**
3. **Compare each node's data with the key.**
    - If found, return `true`.
    - If the list ends and the key is not found, return `false`.

---

## **Example Walkthrough**

### **Example 1**

### **Input:**

```
n = 4, key = 3
Linked List: 1 -> 2 -> 3 -> 4

```

### **Steps:**

- Compare `1` with `3` → Not equal.
- Compare `2` with `3` → Not equal.
- Compare `3` with `3` → **Found!** → Return `true`.

### **Output:**

```
true

```

### **Example 2**

### **Input:**

```
n = 5, key = 7
Linked List: 10 -> 20 -> 30 -> 40 -> 50

```

### **Steps:**

- Compare `10` with `7` → Not equal.
- Compare `20` with `7` → Not equal.
- Compare `30` with `7` → Not equal.
- Compare `40` with `7` → Not equal.
- Compare `50` with `7` → Not equal.

### **Output:**

```
false

```

---

## **Code Implementation in C++**

```cpp
class Solution {
public:
    // Function to search for a key in a linked list.
    bool searchKey(int n, Node* head, int key) {
        Node* temp = head;  // Pointer to traverse the list

        while (temp != nullptr) {  // Traverse each node
            if (temp->data == key)  // Check if data matches the key
                return true;  // Key found

            temp = temp->next;  // Move to the next node
        }

        return false;  // Key not found
    }
};

```

---

## **Common Mistakes and How to Avoid Them in Interviews**

### ❌ **Mistake 1: Checking `temp->next` Instead of `temp->data`**

### **Mistake:**

```cpp
if (temp->next == key)  // Incorrect comparison

```

### **Why is it wrong?**

- `temp->next` is a pointer to the next node, **not the value inside the node**.
- We need to compare `temp->data` instead of `temp->next`.

✅ **Fix:**

```cpp
if (temp->data == key)  // Correct comparison

```

---

### ❌ **Mistake 2: Using `while (temp->next != NULL)` Instead of `while (temp != NULL)`**

### **Mistake:**

```cpp
while (temp->next != NULL)  // Incorrect condition

```

### **Why is it wrong?**

- If the key is in the **last node**, it won't be checked.
- The loop stops at the second-last node.

✅ **Fix:**

```cpp
while (temp != NULL)  // Correct condition

```

---

### ❌ **Mistake 3: Not Handling the Case When `head == NULL`**

### **Mistake:**

- Assuming the list is **always non-empty**.

### **Why is it wrong?**

- If `head == NULL`, `temp->data` will cause an error.

✅ **Fix:**

- The `while (temp != NULL)` condition **automatically handles this case**.

---

### ❌ **Mistake 4: Not Returning the Correct Boolean Values**

### **Mistake:**

```cpp
if (temp->data == key)
    return 1;  // Incorrect: should return `true`

```

### **Why is it wrong?**

- Returning `1` instead of `true` makes code **less readable**.

✅ **Fix:**

```cpp
return true;  // Correct and readable

```

---

## **Time and Space Complexity Analysis**

- **Time Complexity:** `O(n)` → We traverse each node once.
- **Space Complexity:** `O(1)` → No extra space used.

This ensures an efficient and optimal solution for searching in a linked list.

---

## **Conclusion**

By understanding **common mistakes** and **best practices**, you can write clean and efficient code in interviews. Always **validate conditions carefully** and ensure that **edge cases are covered** for robust solutions. 
