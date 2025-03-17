
## **Lists in Python**

A **list** is an ordered, mutable (changeable) collection that can store different data types.

### **1. Processing Array Elements in Lists**

- Lists in Python can be used like arrays in other languages.
- Elements can be accessed using indexing, iterated, modified, and processed.

### **Example: Accessing and Processing Elements**

```python
 
numbers = [10, 20, 30, 40, 50]

# Accessing elements
print(numbers[0])  # Output: 10
print(numbers[-1]) # Output: 50

# Processing (Doubling all elements)
processed_numbers = [num * 2 for num in numbers]
print(processed_numbers)  # Output: [20, 40, 60, 80, 100]

```
### **2. Slices in Lists**

- Slicing allows accessing a subset of a list.
- Format: `list[start:end:step]` (end index is exclusive)

### **Example: List Slicing**

```python
 
nums = [1, 2, 3, 4, 5, 6, 7, 8]

print(nums[1:5])  # Output: [2, 3, 4, 5]
print(nums[:3])   # Output: [1, 2, 3]
print(nums[4:])   # Output: [5, 6, 7, 8]
print(nums[::2])  # Output: [1, 3, 5, 7] (every second element)

```

### **3. List Methods**

Lists have various built-in methods.

| Method | Description |
| --- | --- |
| `append(x)` | Adds an element `x` at the end |
| `insert(i, x)` | Inserts `x` at index `i` |
| `remove(x)` | Removes the first occurrence of `x` |
| `pop(i)` | Removes and returns element at index `i` |
| `reverse()` | Reverses the list |
| `sort()` | Sorts the list |
| `count(x)` | Returns occurrences of `x` |
| `index(x)` | Returns index of first occurrence of `x` |

### **Example: Using List Methods**

```python
 
fruits = ["apple", "banana", "cherry"]

fruits.append("mango")
print(fruits)  # ['apple', 'banana', 'cherry', 'mango']

fruits.insert(1, "orange")
print(fruits)  # ['apple', 'orange', 'banana', 'cherry', 'mango']

fruits.remove("banana")
print(fruits)  # ['apple', 'orange', 'cherry', 'mango']

fruits.reverse()
print(fruits)  # ['mango', 'cherry', 'orange', 'apple']

```
