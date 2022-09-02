# Practice the turtle module

In this chapter we will deal intensively with the python module or package `turtle`. As we have already seen this module is a way to draw graphics on the screen.
<br>
<br>
Firstly complete the challenges:
<br>
<br>
1. Challenge:<br>
Draw a square!

<details>
 <summary>Solution</summary>

```python
import turtle
from turtle import Turtle
from turtle import Screen

# Create an object
timmy_the_turtle = Turtle()
screen = Screen()
# Now the movement
for counter in range(0, 4):
    turtle.fd(100)
    turtle.lt(90)
    print(counter)

screen.exitonclick()  
```
  
</details>
 
2. Challenge:<br>
Draw a dashed line!

<details>
 <summary>Solution</summary>

```python
import turtle
from turtle import Turtle
from turtle import Screen

# Create an object
timmy_the_turtle = Turtle()
screen = Screen()


# Now the movement
def dashed_line(times):
    # draws "times" a black line and no line
    for counter in range(1, times + 1):
        timmy_the_turtle.fd(10)
        timmy_the_turtle.penup()
        timmy_the_turtle.fd(10)
        timmy_the_turtle.pendown()
        print(counter)


dashed_line(10)

screen.exitonclick()
 
```
  
</details>

3. Challenge:<br>
Draw a triangle, square, pentagon, hexagon, heptagon, octagon, nonagon and decagon!<br>
Each of this shapes is drawn in different color!<br>
All shapes lie approximately on top of each other.<br>
Note: Think about the angles of the shapes,  a square 360/4 = 90 degrees angles, a pentagon 360/5 = 72 degrees.....

<details>
 <summary>Solution</summary>

```python
import turtle
from turtle import Turtle
from turtle import Screen
import random

# Create an object
timmy_the_turtle = Turtle()
screen = Screen()
# Colors
colors = ["peru", "lime", "gold", "medium spring green", "orange red", "yellow", "alice blue", "magenta", "dark olive green", "dark slate blue" ]


# Now the movement
def draw_shapes(num_sides):
    angle = 360 / num_sides
    for counter in range(num_sides):
        timmy_the_turtle.forward(100)
        timmy_the_turtle.right(angle)

for counter in range(3, 10):
    timmy_the_turtle.color(random.choice(colors))
    draw_shapes(counter)

screen.exitonclick()

 
```
  
</details>
