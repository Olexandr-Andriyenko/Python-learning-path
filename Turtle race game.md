# Turtle race game

Your task is to create a simple racing game.
For this you create 7 turtles which are placed on a starting line. After entering the color of the user, the game starts. The turtles move with a random step size straight ahead. All turtles have a different color. When a turtle reaches the goal, then it should be shown whether the user had guessed the right color or not.

The game should look like this:

<p align="center">
<img src="https://github.com/Olexandr-Andriyenko/Python-learning-path/blob/main/illustrations/img40.PNG" width="500">
<p> 

You can choose the background image by yourself!

<details>
 <summary>Solution</summary>

```python
import turtle
from turtle import Turtle, Screen
from random import randint

# Set a variable to check is the race on or not
is_race_on = False
screen = Screen()
# Let's set a custom background image (only gif!)
screen.bgpic("street.gif")
screen.update()
# Create a list of colors for the turtle
colors = ["red", "orange", "yellow", "green", "blue", "purple", "magenta"]
# Set the size of the screen window
turtle.setup(width=500, height=400)
# Create a list with y-coordinates
y_positions = [0, -50, -100, -150, 50, 100, 150]
# Create a list of all turtles
all_turtles = []
# Pop up a dialog window for input of a string
# Using a while loop to check for a valid input
while True:
    user_bet = screen.textinput(title="Make your bet", prompt="Which turtle will win the race? Enter a color: ")
    if user_bet in colors:
        break

# Create the objects (7 turtles)
for index in range(0, 7):
    # Object creation with turtle shape
    new_turtle = Turtle(shape="turtle")
    # Penup to avoid drawing
    new_turtle.penup()
    # Set color of turtles
    new_turtle.color(colors[index])
    # Move the turtles to the start line
    # The coordinate systems lies at the centre of the window x=0, y=0
    # So we can define the start line at the left edge of the window x=-250, y=0
    new_turtle.goto(x=-230, y=y_positions[index])
    # Add each new turtle to the list
    all_turtles.append(new_turtle)

# If the user choose a color the race should start
if user_bet:
    is_race_on = True

while is_race_on:
    # Interact with each turtle of our list
    for turtle in all_turtles:
        # Set random distance for the turtles
        rand_distance = randint(0, 10)
        # Move the turtle with that random distance
        turtle.forward(rand_distance)
        # A turtle object is a 40x40 object
        # So we have to check when did a turtle pass 250 -(40/2)=230 x axis coordinate
        if turtle.xcor() > 230:
            # Save the wining color of a turtle
            winning_color = turtle.pencolor()
            # Check if the user won or not and display it
            if winning_color == user_bet:
                print(f"You've won! The {winning_color} turtle is the winner!")
            else:
                print(f"You've lost! The {winning_color} turtle is the winner!")
            is_race_on = False

screen.exitonclick()

```
  
</details>
