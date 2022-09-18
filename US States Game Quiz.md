# US States Game Quiz

The task ist to replicate this [quiz game](https://www.sporcle.com/games/g/states) by using the turtle module and csv data.
<br>
For this project you have to use this image:

<p align="left">
<img src="https://github.com/Olexandr-Andriyenko/Python-learning-path/blob/main/illustrations/img48.gif" width="500">
<p>

The csv data you will find here:
<br>
Download [50_states](https://github.com/Olexandr-Andriyenko/Python-learning-path/blob/main/Files/50_states.csv) data

## Solution
  
The first step is to find out which coordinates has each state:

```python
import turtle

screen = turtle.Screen()
screen.title("U.S. States Game")
# Change the turtle shape to a custom
image = "img48.gif"
screen.addshape(image)
turtle.shape(image)


# How we can find out which coordinates each stat has?
def get_mouse_click_coor(x, y):
    print(x, y)


# Event listener
turtle.onscreenclick(get_mouse_click_coor)  # Returns in click the x and y coordinate
# We want to click on the screen to get the coordinates, we have to remove next line
# screen.exitonclick()
turtle.mainloop()  # Alternative to exitonclick()

```

Inside the csv file you will find the coordinates to each state. So you don't have to do this time stealing work!
