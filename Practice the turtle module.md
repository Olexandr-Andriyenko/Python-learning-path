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

4. Challenge:<br>
Draw a random walk! Find more information about it [here](https://en.wikipedia.org/wiki/Random_walk). <br>
Each time the turtle changes direction, a color should be chosen at random.<br>
Change the width of the drawn lines<br|
Change the speed of the turtle to the fastest as possible!
<br>
<br>
Note:<br>

- In physics, random walks are used as simplified models of physical Brownian motion and diffusion such as the random movement of molecules in liquids and gases. 
  See for example diffusion-limited aggregation. Also in physics, random walks and some of the self interacting walks play a role in quantum field theory.
- In financial economics, the random walk hypothesis is used to model shares prices and other factors.[31] Empirical studies found some deviations from 
  this theoretical model, especially in short term and long term correlations.
- In brain research, random walks and reinforced random walks are used to model cascades of neuron firing in the brain.

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
# How we could prevent the turtle from leaving the screen???
# Create a screen size
screen.screensize(canvwidth=800, canvheight=800)


# For this task I will create a function
def border():
    canvas_width = screen.canvwidth / 2
    canvas_height = screen.canvheight / 2
    current_position = timmy_the_turtle.position()
    t_x = current_position[0]
    t_y = current_position[1]
    if t_y > canvas_height or t_y < (- canvas_height) or t_x > canvas_width or t_x < (- canvas_height):
        timmy_the_turtle.undo()


# If you like you can create random RGB color instead using the list with colors
# For this we can create a function
turtle.colormode(255)  # You have to set this property to use rgb colors!


def random_color():
    r = random.randint(0, 255)
    g = random.randint(0, 255)
    b = random.randint(0, 255)
    rgb_random = (r, g, b)
    return rgb_random


# Colors
colors = ["peru", "lime", "gold", "medium spring green", "orange red", "yellow", "alice blue", "magenta",
          "dark olive green", "dark slate blue", "saddle brown", "light slate gray", "deep sky blue", "seashell",
          "beige", "lavender", "navajo white", "khaki"]
# Background color
screen.bgcolor("black")
# Valid angles
angles = [0, 90, 180, 270, 360]
# The pen size
thickness = 10
timmy_the_turtle.width(thickness)
# Turtle speed
timmy_the_turtle.speed(0)
# Movement
for _ in range(4000):
    timmy_the_turtle.color(random.choice(colors))
    # timmy_the_turtle.color(random_color()) # Set this to get random rgb colors!
    timmy_the_turtle.right(random.choice(angles))
    timmy_the_turtle.fd(25)
    border()

screen.exitonclick()

```
                                                                                       
</details>


5. Challenge:<br>
Build a spirograph! Spirograph is a geometric toy that allows you to draw different patterns or mathematical curves. Read more about it  [here](https://en.wikipedia.org/wiki/Spirograph).<br>
Draw this image:
 
<p align="center">
<img src="https://github.com/Olexandr-Andriyenko/Python-learning-path/blob/main/illustrations/img37.PNG" width="400">
<p>  
 
The color are generated randomly!

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
# If you like you can create random RGB color instead using the list with colors
# For this we can create a function
turtle.colormode(255)  # You have to set this property to use rgb colors!
# Set the speed of the turtle
timmy_the_turtle.speed(0)
# Set the background to Black
turtle.bgcolor("black")


def random_color():
    r = random.randint(0, 255)
    g = random.randint(0, 255)
    b = random.randint(0, 255)
    rgb_random = (r, g, b)
    return rgb_random


# Create the "art"
def draw_spirograph(gap):
    # Inside the range() the input has to be an integer
    for _ in range(int(360 / gap)):
        timmy_the_turtle.color(random_color())
        # Shift the turtle a little
        timmy_the_turtle.setheading(timmy_the_turtle.heading() + gap)
        timmy_the_turtle.circle(100)


# Main program
draw_spirograph(10)

screen.exitonclick()

```
                                                                                       
</details>

 
 ## Using screen events
 
 We need a way to listen to the user's actions, for example when the user presses a certain key. If you look into the ["turtle" documentation](https://docs.python.org/3/library/turtle.html), you will find a section called "using screen events".<br>
 The most important is the ["listen" method](https://docs.python.org/3/library/turtle.html#turtle.listen). This allows the "turtle" screen to listen and wait for events that the user might trigger.
<br>
Example:
 
```python
 from turtle import Turtle, Screen
# Create the objects
tim = Turtle()
screen = Screen()


# Create a simple function for movement
def move_forwards():
    tim.fd(10)
# Tell the screen object that he have to start to "listen"
screen.listen()
# Now we use an event listener, when the "space" key is pressed then trigger the function "move_forward"
screen.onkey(key="space", fun=move_forwards) # The method "onkey" listen that when the space key ist pressed
screen.exitonclick()

```
