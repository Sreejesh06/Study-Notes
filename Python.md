# Interpreter vs Compiler

## 1. Introduction
Both **interpreters** and **compilers** are used to convert high-level programming languages (like Python, C, Java) into machine code that computers can understand.

## 2. Interpreter
- Translates and executes code **line by line**.
- Stops execution if an error is found.
- Slower execution due to repeated translation.
- Example languages: **Python, JavaScript, Ruby**.

## 3. Compiler
- Translates the entire code **at once** into machine code.
- Displays all errors after compilation.
- Faster execution since translation happens only once.
- Example languages: **C, C++, Java**.

## 4. Interactive Mode vs Script Mode
### **Interactive Mode**
- Executes code **immediately** after writing.
- Used for testing and debugging small code snippets.
- Example: Python shell (`python` in terminal).

### **Script Mode**
- Executes an entire script file at once.
- Suitable for writing long programs.
- Example: Running a Python script (`python script.py`).

## 5. Identifiers and Keywords
### **Identifiers**
- Names used to identify variables, functions, classes, etc.
- Must start with a letter (A-Z or a-z) or underscore (_) and can be followed by letters, digits (0-9), or underscores.
- Cannot be a **keyword**.
- Case-sensitive.
- Example: `myVariable`, `_privateVar`, `ClassName`.

### **Keywords**
- Reserved words that have special meanings in a programming language.
- Cannot be used as identifiers.
- Example Python keywords: `if`, `else`, `while`, `for`, `return`, `def`, `class`, `import`.

## 6. Key Differences

| Feature         | Interpreter | Compiler |
|---------------|-----------|---------|
| Execution     | Line by line | Whole code at once |
| Speed        | Slower | Faster |
| Error Handling | Stops at first error | Shows all errors after compilation |
| Example Languages | Python, JavaScript | C, C++, Java |

