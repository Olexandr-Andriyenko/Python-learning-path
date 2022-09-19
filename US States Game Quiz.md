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

```python
import turtle
import pandas as pd

screen = turtle.Screen()
screen.setup(width=750, height=550)
screen.title("U.S. States Game")
t = turtle.Turtle()
# Change the turtle shape to a custom
image = "img48.gif"
screen.addshape(image)
turtle.shape(image)
# Count the amount of guessed states
score = 0
# Load the csv in a data frame
data = pd.read_csv("50_states.csv")
# A list with the guessed states
guessed_states = []

while len(guessed_states) < 50:
    # Users input
    answer_state = screen.textinput(title=f"{score}/50 States Correct", prompt="What's another state's name?").title()
    # title() method returns the string where each word is capitalized
    for state in data["state"]:
        if state == answer_state:
            # Fill the list with guessed states
            guessed_states.append(answer_state)
            # Increase the amount of guessed states
            score += 1
            # Setup t object for writing
            t.hideturtle()
            t.penup()
            # Find the row with the momentum state
            row_state = data[data["state"] == answer_state]
            # Find the x value of current state
            x = row_state["x"]
            # Find the y value of current state
            y = row_state["y"]
            # Write the name of the state at the map
            t.goto(int(x), int(y))
            t.color("Red")
            t.write(answer_state)


screen.exitonclick()

```

To make the program work like a game, we will expand it. If you enter "exit" in the input window, the game should be closed. Then a csv file is created, which contains all the states that were not entered by the user.

```python
import turtle
import pandas as pd

screen = turtle.Screen()
screen.setup(width=750, height=550)
screen.title("U.S. States Game")
t = turtle.Turtle()
# Change the turtle shape to a custom
image = "img48.gif"
screen.addshape(image)
turtle.shape(image)
# Count the amount of guessed states
score = 0
# Load the csv in a data frame
data = pd.read_csv("50_states.csv")
# A list with the guessed states
guessed_states = []

while len(guessed_states) < 50:
    # Users input
    answer_state = screen.textinput(title=f"{score}/50 States Correct", prompt="What's another state's name?").title()
    # Extend the program with the exit and csv functionality
    if answer_state == "Exit":
        break
    # title() method returns the string where each word is capitalized
    for state in data["state"]:
        if state == answer_state:
            # Fill the list with guessed states
            guessed_states.append(answer_state)
            # Increase the amount of guessed states
            score += 1
            # Setup t object for writing
            t.hideturtle()
            t.penup()
            # Find the row with the momentum state
            row_state = data[data["state"] == answer_state]
            # Find the x value of current state
            x = row_state["x"]
            # Find the y value of current state
            y = row_state["y"]
            # Write the name of the state at the map
            t.goto(int(x), int(y))
            t.color("Red")
            t.write(answer_state)

# Save the not guessed states in a csv file
missing_states = []
for state in data["state"]:
    if state not in guessed_states:
        missing_states.append(state)
# Export list in a data frame
data_missing_states = pd.DataFrame(missing_states)
data_missing_states.to_csv("states_to_learn.csv")


# We don't need this line any more
# screen.exitonclick()

```
