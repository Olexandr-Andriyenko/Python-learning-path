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
  
  
<details>
 <summary>Second part of the solution</summary>
  
<br>
Now we rebuild the first solution to get a more OOP organisation! 
<br>
  
This is the `main.py` file:

```python
# Modules
from turtle import Screen
from snake import Snake
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
# Create the snake object from our own class
snake = Snake()

# Create a variable to check if the game is on or not
game_is_on = True
# As long as the game is on, the snake will move forward
while game_is_on:
    # Update the screen every 0.1 second!
    screen.update()
    time.sleep(0.1)
    # Every time the screen get refreshed, the snake have to move forward
    snake.move()

screen.exitonclick()

```
  
<br>
  
This is the `snake.py` file:
  
```python
from turtle import Turtle

# Create a list of the starting position (this is a constant, so we have tu use capital letter)
STARTING_POSITION = [(0, 0), (-20, 0), (-40, 0)]
# Constant with the distance, which the snake can move
DISTANCE = 20


class Snake:
    def __init__(self):
        # Use the starting position coordinates to create the snake body
        self.snake_body = []
        self.create_snake()

    # ----------------------------------------------- #
    # Create a snake body
    # ----------------------------------------------- #
    def create_snake(self):
        # This time we will create the snake body by using a for loop
        for position in STARTING_POSITION:
            new_segment = Turtle("square")
            new_segment.color("white")
            new_segment.penup()
            new_segment.goto(position)
            self.snake_body.append(new_segment)

    # ----------------------------------------------- #
    # Move the snake
    # ----------------------------------------------- #
    def move(self):
        # Implementation of the movement like inside the gif
        for segment in range(len(self.snake_body) - 1, 0, -1):
            new_x = self.snake_body[segment - 1].xcor()
            new_y = self.snake_body[segment - 1].ycor()
            self.snake_body[segment].goto(new_x, new_y)
        self.snake_body[0].fd(DISTANCE)
  
```
  
</details>

<details>
 <summary>Third part of the solution</summary>
  
<br>
  
Now we create the control by using the keyboard arrows
  
This is the `snake.py` file:

```python
from turtle import Turtle

# Create a list of the starting position (this is a constant, so we have tu use capital letter)
STARTING_POSITION = [(0, 0), (-20, 0), (-40, 0)]
# Constant with the distance, which the snake can move
DISTANCE = 20
# Constants to prevent going up or down, depending on the orientation
UP = 90
DOWN = 270
LEFT = 180
RIGHT = 0


class Snake:
    def __init__(self):
        # Use the starting position coordinates to create the snake body
        self.snake_body = []
        self.create_snake()
        self.snake_head = self.snake_body[0]

    # ----------------------------------------------- #
    # Create a snake body
    # ----------------------------------------------- #
    def create_snake(self):
        # This time we will create the snake body by using a for loop
        for position in STARTING_POSITION:
            new_segment = Turtle("square")
            new_segment.color("white")
            new_segment.penup()
            new_segment.goto(position)
            self.snake_body.append(new_segment)

    # ----------------------------------------------- #
    # Move the snake
    # ----------------------------------------------- #
    def move(self):
        # Implementation of the movement like inside the gif
        for segment in range(len(self.snake_body) - 1, 0, -1):
            new_x = self.snake_body[segment - 1].xcor()
            new_y = self.snake_body[segment - 1].ycor()
            self.snake_body[segment].goto(new_x, new_y)
        self.snake_head.fd(DISTANCE)

    # ----------------------------------------------- #
    # Control the snake
    # ----------------------------------------------- #
    # Create methods for snake control (create before head attribute!)
    # Read about "heading" inside the turtle documentation
    def up(self):
        # Snake can only go up, if it doesn't go down (using turtle heading() method)
        if self.snake_head.heading() != DOWN:
            self.snake_head.setheading(UP)

    def down(self):
        if self.snake_head.heading() != UP:
            self.snake_head.setheading(DOWN)

    def left(self):
        if self.snake_head.heading() != RIGHT:
            self.snake_head.setheading(LEFT)

    def right(self):
        if self.snake_head.heading() != LEFT:
            self.snake_head.setheading(RIGHT)

```
  
</details>

  
<details>
 <summary>Fifth part of the solution</summary>
  
<br>
Now we create the snake food! 
<br>
<br>
  
This is the `main.py` file:

```python
# Modules
from turtle import Screen
from snake import Snake
import time  # Simple module to use delay
from food import Food
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
# Create the snake object from our own class
snake = Snake()
# Create the food
food = Food()
# Start listening
screen.listen()
# Create even listener
screen.onkey(snake.up, "Up")
screen.onkey(snake.down, "Down")
screen.onkey(snake.left, "Left")
screen.onkey(snake.right, "Right")

# Create a variable to check if the game is on or not
game_is_on = True
# As long as the game is on, the snake will move forward
while game_is_on:
    # Update the screen every 0.1 second!
    screen.update()
    time.sleep(0.1)
    # Every time the screen get refreshed, the snake have to move forward
    snake.move()
    # Detect collision with food
    # Read about the turtle distance method
    if snake.snake_head.distance(food) < 15:
        food.refresh()


screen.exitonclick()

```
  
<br>
  
This is the `food.py` file:
  
```python
from turtle import Turtle
import random
from snake import Snake


# ----------------------------------------------- #
# Create snake food
# ----------------------------------------------- #
# Subclass of "Turtle"
class Food(Turtle):
    def __init__(self):
        super().__init__()
        self.shape("circle")
        self.penup()
        # Stretch the turtle (20*0.5=10, it's a 10x10 circle)
        self.shapesize(stretch_len=0.5, stretch_wid=0.5)
        self.color("blue")
        self.speed("fastest")
        # Create random position
        # Min x-value=-300 and Max x-value=300, y-axis same properties (20px space)
        random_x = random.randint(-280, 280)
        random_y = random.randint(-280, 280)
        self.goto(random_x, random_y)

    # Set new coordinated to the food
    def refresh(self):
        random_x = random.randint(-280, 280)
        random_y = random.randint(-280, 280)
        self.goto(random_x, random_y)

```
  
</details>  

  
<details>
 <summary>sixth part of the solution</summary>
  
<br>
We will create the scoreboard
<br>
  
This is the `main.py` file:

```python
# Modules
from turtle import Screen
from snake import Snake
import time  # Simple module to use delay
from food import Food
from scoreboard import Scoreboard
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
# Create the snake object from our own class
snake = Snake()
# Create the food
food = Food()
# Create the scoreboard
scoreboard = Scoreboard()
# Start listening
screen.listen()
# Create even listener
screen.onkey(snake.up, "Up")
screen.onkey(snake.down, "Down")
screen.onkey(snake.left, "Left")
screen.onkey(snake.right, "Right")

# Create a variable to check if the game is on or not
game_is_on = True
# As long as the game is on, the snake will move forward
while game_is_on:
    # Update the screen every 0.1 second!
    screen.update()
    time.sleep(0.1)
    # Every time the screen get refreshed, the snake have to move forward
    snake.move()
    # Detect collision with food
    # Read about the turtle distance method
    if snake.snake_head.distance(food) < 15:
        food.refresh()
        scoreboard.increase_score()




screen.exitonclick()

```
  
This is the `scoreboard.py` file:

```python
import turtle
from turtle import Turtle
ALIGNMENT = "center"
FONT = ("Arial", 24, "normal")


# ----------------------------------------------- #
# Create scoreboard
# ----------------------------------------------- #

class Scoreboard(Turtle):
    def __init__(self):
        super().__init__()
        self.score = 0
        self.color("white")
        self.penup()
        self.goto(0, 260)
        self.hideturtle()
        self.update_scoreboard()

    def update_scoreboard(self):
        self.write(f"Score: {self.score}", align=ALIGNMENT, font=FONT)

    def increase_score(self):
        self.score += 1
        self.clear()
        self.update_scoreboard()

```
  
</details>
  
<details>
 <summary>Seventh part of the solution</summary>

<br>  
Detect colision with the wall
<br>
  
This is the `main.py` file:

```python
# Modules
from turtle import Screen
from snake import Snake
import time  # Simple module to use delay
from food import Food
from scoreboard import Scoreboard
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
# Create the snake object from our own class
snake = Snake()
# Create the food
food = Food()
# Create the scoreboard
scoreboard = Scoreboard()
# Start listening
screen.listen()
# Create even listener
screen.onkey(snake.up, "Up")
screen.onkey(snake.down, "Down")
screen.onkey(snake.left, "Left")
screen.onkey(snake.right, "Right")

# Create a variable to check if the game is on or not
game_is_on = True
# As long as the game is on, the snake will move forward
while game_is_on:
    # Update the screen every 0.1 second!
    screen.update()
    time.sleep(0.1)
    # Every time the screen get refreshed, the snake have to move forward
    snake.move()
    # Detect collision with food
    # Read about the turtle distance method
    if snake.snake_head.distance(food) < 15:
        food.refresh()
        scoreboard.increase_score()
    # Detect collision with wall
    if snake.snake_head.xcor() > 280 or snake.snake_head.xcor() < -280 or snake.snake_head.ycor() > 280 or snake.snake_head.ycor() < -280:
        game_is_on = False
        scoreboard.game_over()


screen.exitonclick()

```
  
This is the `scoreboard.py` file:

```python
import turtle
from turtle import Turtle
ALIGNMENT = "center"
FONT = ("Arial", 24, "normal")


# ----------------------------------------------- #
# Create scoreboard
# ----------------------------------------------- #

class Scoreboard(Turtle):
    def __init__(self):
        super().__init__()
        self.score = 0
        self.color("white")
        self.penup()
        self.goto(0, 260)
        self.hideturtle()
        self.update_scoreboard()

    def update_scoreboard(self):
        self.write(f"Score: {self.score}", align=ALIGNMENT, font=FONT)

    def increase_score(self):
        self.score += 1
        self.clear()
        self.update_scoreboard()

    def game_over(self):
        self.goto(0, 0)
        self.write(f"GAME OVER", align=ALIGNMENT, font=FONT)

```
  
</details>
  
<details>
 <summary>Eighth part of the solution</summary>

<br>  
Extend the snake body with new segments, if the snake eats food!  
<br>
  
This is the `main.py` file:

```python
# Modules
from turtle import Screen
from snake import Snake
import time  # Simple module to use delay
from food import Food
from scoreboard import Scoreboard
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
# Create the snake object from our own class
snake = Snake()
# Create the food
food = Food()
# Create the scoreboard
scoreboard = Scoreboard()
# Start listening
screen.listen()
# Create even listener
screen.onkey(snake.up, "Up")
screen.onkey(snake.down, "Down")
screen.onkey(snake.left, "Left")
screen.onkey(snake.right, "Right")

# Create a variable to check if the game is on or not
game_is_on = True
# As long as the game is on, the snake will move forward
while game_is_on:
    # Update the screen every 0.1 second!
    screen.update()
    time.sleep(0.1)
    # Every time the screen get refreshed, the snake have to move forward
    snake.move()
    # Detect collision with food
    # Read about the turtle distance method
    if snake.snake_head.distance(food) < 15:
        food.refresh()
        scoreboard.increase_score()
        # Extend the snake
        snake.extend()
    # Detect collision with wall
    if snake.snake_head.xcor() > 280 or snake.snake_head.xcor() < -280 or snake.snake_head.ycor() > 280 or snake.snake_head.ycor() < -280:
        game_is_on = False
        scoreboard.game_over()
    # Detect collision with the tail
    for segment in snake.snake_body:
        if segment == snake.snake_head:
            pass
        elif snake.snake_head.distance(segment) < 10:
            game_is_on = False
            scoreboard.game_over()
    # If head collides with any segment in the tail then trigger game_over

screen.exitonclick()

```
  
This is the `snake.py` file:

```python
from turtle import Turtle

# Create a list of the starting position (this is a constant, so we have tu use capital letter)
STARTING_POSITION = [(0, 0), (-20, 0), (-40, 0)]
# Constant with the distance, which the snake can move
DISTANCE = 20
# Constants to prevent going up or down, depending on the orientation
UP = 90
DOWN = 270
LEFT = 180
RIGHT = 0


class Snake:
    def __init__(self):
        # Use the starting position coordinates to create the snake body
        self.snake_body = []
        self.create_snake()
        self.snake_head = self.snake_body[0]

    # ----------------------------------------------- #
    # Create a snake body
    # ----------------------------------------------- #
    def create_snake(self):
        # This time we will create the snake body by using a for loop
        for position in STARTING_POSITION:
            self.add_segment(position)

    # ----------------------------------------------- #
    # Extend the snake
    # ----------------------------------------------- #
    def extend(self):
        # Add new segment to the snake
        self.add_segment(self.snake_body[-1].position())

    def add_segment(self, position):
        new_segment = Turtle("square")
        new_segment.color("white")
        new_segment.penup()
        new_segment.goto(position)
        self.snake_body.append(new_segment)

    # ----------------------------------------------- #
    # Move the snake
    # ----------------------------------------------- #
    def move(self):
        # Implementation of the movement like inside the gif
        for segment in range(len(self.snake_body) - 1, 0, -1):
            new_x = self.snake_body[segment - 1].xcor()
            new_y = self.snake_body[segment - 1].ycor()
            self.snake_body[segment].goto(new_x, new_y)
        self.snake_head.fd(DISTANCE)

    # ----------------------------------------------- #
    # Control the snake
    # ----------------------------------------------- #
    # Create methods for snake control (create before head attribute!)
    # Read about "heading" inside the turtle documentation
    def up(self):
        # Snake can only go up, if it doesn't go down (using turtle heading() method)
        if self.snake_head.heading() != DOWN:
            self.snake_head.setheading(UP)

    def down(self):
        if self.snake_head.heading() != UP:
            self.snake_head.setheading(DOWN)

    def left(self):
        if self.snake_head.heading() != RIGHT:
            self.snake_head.setheading(LEFT)

    def right(self):
        if self.snake_head.heading() != LEFT:
            self.snake_head.setheading(RIGHT)



```
  
</details>
