# Damien Hirst's Spot Paintings (Extract RGB values from images)

In this project we will recreate the the following picture: 

<p align="center">
<img src="https://github.com/Olexandr-Andriyenko/Python-learning-path/blob/main/illustrations/img38.png" width="400">
<p>  

The estimated price for this art is around [£350,000 - 550,00](https://www.phillips.com/detail/damien-hirst/UK010122/38).
<br>
<br>
We will create a Python code to find out the color palette of the image.<br>
After that we will use this color palette to create such a similar art.
<br>
<br>
For this project we will use the package [colorgram](https://pypi.org/project/colorgram.py/).
First step is to install "colorgram.py". For this go in pycharm to `File` -> `Settings` -> `Project:...` -> `Python Interpreter` -> press the `+` symbol -> search "colorgram.py" and install it.
<br>
<br>
Now we have to download the image above, and put it inside the project folder! Do not forget to convert the image to jpeg file, because pycharm can't open png files.
<br>
<br>
 
<details>
 <summary>Solution</summary>

```python
# Module import
from colorgram import extract
import turtle
import random

# Extract top 10 images from the image
colors = extract("img38.jpg", 10)
# Inside this list we will store the top 10 colors
list_of_colors = []
# Create a loop to read each object inside the "colors" variable
for index in range(0, len(colors)):
    # Save from each object the rgb values inside "color"
    color = colors[index].rgb
    # Because color is still an object, we have to find the rgb values and save them seperate as integers
    r = color.r
    g = color.g
    b = color.b
    # Store the rgb integer values inside a tuple
    color_tuple = (r, g, b)
    # Add each tuple to our list
    list_of_colors.append(color_tuple)

# I print the list to check the colors
print(list_of_colors)
# The first color is (233, 233, 232), this is the background color, I will delete it because I will
# create a white or black background, the second color looks similar to the first, that's why I will delete it too
del list_of_colors[0]
del list_of_colors[1]
print(list_of_colors)
# Now 8 colors left inside the list
# --------------------------------------------- #
# The image must have 10 x 10 rows of dots.
# The color of dots is randomly generated from the "list_of_colors"
# Each of these dots have a size of 20 and a gap of 50
# We have to use the turtle module
t = turtle.Turtle()
screen = turtle.Screen()
# For using rgb colors
screen.colormode(255)
# Set the speed
t.speed(0)
# Turtle don't draw a line
t.penup()
# Set the background color
turtle.bgcolor("black")


# Function to draw a line of dots
def draw_line_of_dots(amount_of_dots):
    for _ in range(0, amount_of_dots):
        t.dot(20, random.choice(list_of_colors))
        t.fd(50)


# Set the amount of dots
amount_of_dots = 10
# Move the turtle to a start position
# Then we have symmetric distribution to the x-axis inside the canvas
t.setheading(270)
t.fd(amount_of_dots / 2 * 50)
t.setheading(0)
# Start drawing the image
for _ in range(0, amount_of_dots):
    draw_line_of_dots(amount_of_dots)
    t.setheading(90)
    t.fd(50)
    t.setheading(180)
    t.fd(amount_of_dots * 50)
    t.setheading(0)

screen.exitonclick()

```
  
</details>  
  

 The created image looks like this:
<p align="center">
<img src="https://github.com/Olexandr-Andriyenko/Python-learning-path/blob/main/illustrations/img39.PNG" width="400">
<p>  
