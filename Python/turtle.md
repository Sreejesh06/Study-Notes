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
- `turtle.Screen()` creates a new window (canvas) where the turtle moves.
- `screen.title("Turtle Graphics")` sets the title of the window.
- `screen.bgcolor("white")` changes the background color of the canvas.
- `turtle.done()` tells Python that we're done giving commands.

### 2. Creating a Turtle Object
```python
pen = turtle.Turtle()
```
- Creates a new turtle named `pen`.
- This turtle is used to draw on the screen.

### 3. Moving the Turtle
```python
pen.forward(100)   # Move forward by 100 units
pen.backward(50)   # Move backward by 50 units
pen.left(90)       # Turn left by 90 degrees
pen.right(45)      # Turn right by 45 degrees
```
- Moves the turtle forward and backward.
- Turns the turtle left or right by specified degrees.

### 4. Changing Pen Attributes
```python
pen.color("blue")        # Change color to blue
pen.pensize(3)           # Set pen thickness to 3
pen.speed(5)             # Set speed (1 = slow, 10 = fast, 0 = instant)
pen.shape("turtle")      # Change turtle shape
```
- Sets the color, thickness, speed, and shape of the turtle.

### 5. Drawing a Circle
```python
pen.circle(50)  # Draw a circle with radius 50
```
- Draws a circle with a specified radius.

### 6. Lifting and Placing the Pen
```python
pen.penup()   # Lift the pen (no drawing)
pen.goto(100, 100)  # Move without drawing
pen.pendown() # Place the pen down (start drawing again)
```
- Lifts the pen to move without drawing.
- Moves the turtle to a specified position.
- Lowers the pen to resume drawing.

### 7. Filling a Shape
```python
pen.begin_fill()
pen.color("red")
pen.circle(50)
pen.end_fill()
```
- Begins and ends filling a shape with the chosen color.

### 8. Clearing and Resetting
```python
pen.clear()   # Clears the drawing without moving the turtle
pen.reset()   # Clears drawing and resets turtle to the starting position
```
- Clears the drawing without moving or resets to the starting position.

### 9. Closing the Turtle Window
```python
turtle.done()
```
- Keeps the turtle window open after execution.

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
- Uses a loop to repeat movements 4 times to form a square.

### Drawing a Triangle
```python
import turtle
pen = turtle.Turtle()
for _ in range(3):
    pen.forward(100)
    pen.left(120)
turtle.done()
```
- Turns left by 120 degrees to form a triangle.

### Drawing a Star
```python
import turtle
pen = turtle.Turtle()
for _ in range(5):
    pen.forward(100)
    pen.right(144)
turtle.done()
```
- Moves forward and turns right by 144 degrees to form a star.

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
- Creates a spiral by gradually increasing the distance moved forward.

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
- Repeats drawing circles while turning slightly to create a pattern.

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
- `screen.listen()` allows keyboard inputs.
- Key bindings move the turtle when keys are pressed.

---

## Conclusion
- The `turtle` module is great for drawing and learning programming concepts.
- Experimenting with different shapes and animations enhances understanding.

---
