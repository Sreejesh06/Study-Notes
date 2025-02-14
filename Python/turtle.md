# Turtle Graphics in Python

## Introduction
Python's `turtle` module is used for creating simple graphics. It provides an easy way to draw shapes, patterns, and animations using a virtual pen (turtle) on a screen.

---

## Installation
The `turtle` module comes pre-installed with Python. To check if it's available, simply run:

```python
import turtle
```

If you get no errors, it's ready to use!

---

## Basic Commands
### 1. Creating a Turtle Window
```python
import turtle
screen = turtle.Screen()
screen.title("Turtle Graphics")
screen.bgcolor("white")
turtle.done()
```

### 2. Creating a Turtle Object
```python
pen = turtle.Turtle()
```

### 3. Moving the Turtle
```python
pen.forward(100)   # Move forward by 100 units
pen.backward(50)   # Move backward by 50 units
pen.left(90)       # Turn left by 90 degrees
pen.right(45)      # Turn right by 45 degrees
```

### 4. Changing Pen Attributes
```python
pen.color("blue")        # Change color to blue
pen.pensize(3)           # Set pen thickness to 3
pen.speed(5)             # Set speed (1 = slow, 10 = fast, 0 = instant)
pen.shape("turtle")      # Change turtle shape
```

### 5. Drawing a Circle
```python
pen.circle(50)  # Draw a circle with radius 50
```

### 6. Lifting and Placing the Pen
```python
pen.penup()   # Lift the pen (no drawing)
pen.goto(100, 100)  # Move without drawing
pen.pendown() # Place the pen down (start drawing again)
```

### 7. Filling a Shape
```python
pen.begin_fill()
pen.color("red")
pen.circle(50)
pen.end_fill()
```

### 8. Clearing and Resetting
```python
pen.clear()   # Clears the drawing without moving the turtle
pen.reset()   # Clears drawing and resets turtle to the starting position
```

### 9. Closing the Turtle Window
```python
turtle.done()
```

---

## Drawing Basic Shapes
### Drawing a Square
```python
import turtle
pen = turtle.Turtle()
for _ in range(4):
    pen.forward(100)
    pen.right(90)
turtle.done()
```

### Drawing a Triangle
```python
import turtle
pen = turtle.Turtle()
for _ in range(3):
    pen.forward(100)
    pen.left(120)
turtle.done()
```

### Drawing a Star
```python
import turtle
pen = turtle.Turtle()
for _ in range(5):
    pen.forward(100)
    pen.right(144)
turtle.done()
```

---

## Advanced Turtle Graphics
### Drawing a Spiral
```python
import turtle
pen = turtle.Turtle()
pen.speed(0)
for i in range(100):
    pen.forward(i * 2)
    pen.right(45)
turtle.done()
```

### Drawing a Pattern using Loops
```python
import turtle
pen = turtle.Turtle()
pen.speed(0)
for i in range(36):
    pen.circle(50)
    pen.right(10)
turtle.done()
```

---

## Event Handling with Turtle
### Detecting Key Presses
```python
import turtle
pen = turtle.Turtle()
screen = turtle.Screen()

def move_forward():
    pen.forward(50)

def turn_left():
    pen.left(30)

def turn_right():
    pen.right(30)

screen.listen()
screen.onkey(move_forward, "Up")
screen.onkey(turn_left, "Left")
screen.onkey(turn_right, "Right")
screen.mainloop()
```

---

## Conclusion
The `turtle` module is a powerful way to create graphics using Python. It is widely used for educational purposes to teach programming concepts. Experiment with different shapes and patterns to enhance your understanding!

---

