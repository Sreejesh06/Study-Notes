
## **Lists in Python**

A **list** is an ordered, mutable (changeable) collection that can store different data types.

### **1. Processing Array Elements in Lists**

- Lists in Python can be used like arrays in other languages.
- Elements can be accessed using indexing, iterated, modified, and processed.

### **Example: Accessing and Processing Elements**

```python
python
CopyEdit
numbers = [10, 20, 30, 40, 50]

# Accessing elements
print(numbers[0])  # Output: 10
print(numbers[-1]) # Output: 50

# Processing (Doubling all elements)
processed_numbers = [num * 2 for num in numbers]
print(processed_numbers)  # Output: [20, 40, 60, 80, 100]

```
