# Snake game

Create the classic game snake! Study the [rules and the gameplay of snake](https://de.wikipedia.org/wiki/Snake_(Computerspiel)) and rebuild it by yourself.<br>
Use for this project the "turtle" module.
<br>
<br>
You can solve the project in many small steps:
- Create a snake body (created by three turtles)
- Move the snake (read about the [tracer](https://docs.python.org/3/library/turtle.html#turtle.tracer) method and use the [update method](https://docs.python.org/3/library/turtle.html#turtle.update) to update the screen. Also you need to read about the [sleep method](https://docs.python.org/3/library/time.html#time.sleep))
- Create snake food
- Detect collision with food
- Create a scoreboard
- Detect collision with wall
- Detect collision with tail
<br>
Idea how the movement of the snake can be created:

<p align="left">
<img src="https://github.com/Olexandr-Andriyenko/Python-learning-path/blob/main/illustrations/img41.gif" width="400">
<p>  

## Solution
  
<details>
 <summary>First part of the solution</summary>
  
<br>
  
This is the `main.py` file:

```python
# Modules
from turtle import Screen, Turtle
import time  # Simple module to use delay
# ----------------------------------------------- #
# Settings
# ----------------------------------------------- #
# Create objects
screen = Screen()
# Set up the screen
screen.setup(width=600, height=600)
screen.bgcolor("black")
screen.title("My Snake Game")
# Turn the turtle animation off and set a delay for update drawings
screen.tracer(0)
# ----------------------------------------------- #
# Create a snake body
# ----------------------------------------------- #
# A turtle has a dimension of 20x20, our snake will consist of 3 squares
segment_1 = Turtle()
# Set attributes of the "square"
segment_1.color("white")
segment_1.shape(name="square")
segment_1.penup()

segment_2 = Turtle()
# Set attributes of the "square"
segment_2.color("white")
segment_2.shape(name="square")
segment_2.penup()
segment_2.goto(x=-20, y=0)

segment_3 = Turtle()
# Set attributes of the "square"
segment_3.color("white")
segment_3.shape(name="square")
segment_3.penup()
segment_3.goto(x=-40, y=0)

# Note: Try to use a for loop to create the three segments! You will get less code.
# ----------------------------------------------- #
# Move the snake
# ----------------------------------------------- #
# Create a list with all segments
snake_body = [segment_1, segment_2, segment_3]

# Create a variable to check if the game is on or not
game_is_on = True
# As long as the game is on, the snake will move forward
while game_is_on:
    # Update the settings like tracer or speed
    # After this update we will se a change in our screen, if we don't update the screen
    # we will see no changes because tracer is off (screen.tracer(0))
    screen.update()
    time.sleep(0.1)  # Play with the time to understand how tracer works (0.1s are enough to update the display)
    # We tell the computer to do something, then we update the screen and show the results (we update the screen
    # every time if we move our segments)
    # for segment in snake_body: # Activate to test moving forward
        # segment.forward(20) # Activate to test moving forward

    # Implementation of the movement like inside the gif
    # Alle the segments will "follow" the first segment!
    for segment in range(len(snake_body) - 1, 0, -1):
        new_x = snake_body[segment - 1].xcor()
        new_y = snake_body[segment - 1].ycor()
        snake_body[segment].goto(new_x, new_y)
    snake_body[0].fd(20)
    # To turn the snake we have just to turn the first segment inside the snake body
    # Examples
    snake_body[0].left(90)

screen.exitonclick()

```
  
</details>
