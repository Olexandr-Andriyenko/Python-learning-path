# Pong Game
 Build the classic arcade game [ponr](https://de.wikipedia.org/wiki/Pong).
 <br>
 <br>
 You can breake the game in this parts:<br>
 - Create the screen
 - Create and move a paddle
 - Create another paddle
 - Create the ball and make it move
 - Detect collision with wall and bounce
 - Detect collision with paddle
 - Detect when paddle misses
 - Keep score
 
## Solution
  
<details>
 <summary>First part of the solution</summary>
  
<br>
  
This is the `main.py` file:

```python
from turtle import Screen, Turtle

# -------------------------------------------- #
# Create the screen
# -------------------------------------------- #
screen = Screen()
screen.bgcolor("black")
screen.setup(width=800, height=600)
screen.title("Pong Game")
# -------------------------------------------- #
# Create and move a paddle
# -------------------------------------------- #
paddle = Turtle(shape="square")
# Standard size of turtle is 20x20, We want to get a 20x100 size (we will stretch 20 by 5)
paddle.shapesize(stretch_wid=5, stretch_len=1)
paddle.color("white")
paddle.penup()
paddle.goto(x=350, y=0)


# Now I create the movement of the paddle
def go_up():
    new_y = paddle.ycor() + 20
    paddle.goto(paddle.xcor(), new_y)


def go_down():
    new_y = paddle.ycor() - 20
    paddle.goto(paddle.xcor(), new_y)


screen.listen()
screen.onkey(go_up, "Up")
screen.onkey(go_down, "Down")

screen.exitonclick()

```
  
</details>

<details>
 <summary>Second part of the solution</summary>

<br>
In this part we will remove the paddle positioning animation! 
<br>
<br>  
This is the `main.py` file:

```python
from turtle import Screen, Turtle

# -------------------------------------------- #
# Create the screen
# -------------------------------------------- #
screen = Screen()
screen.bgcolor("black")
screen.setup(width=800, height=600)
screen.title("Pong Game")
# Using tracer to "hidde" the paddle animation
# I f we turn of the tracer we have tp update the screen manually by refreshing it any time
screen.tracer(0)
# -------------------------------------------- #
# Create and move a paddle
# -------------------------------------------- #
paddle = Turtle(shape="square")
# Standard size of turtle is 20x20, We want to get a 20x100 size (we will stretch 20 by 5)
paddle.shapesize(stretch_wid=5, stretch_len=1)
paddle.color("white")
paddle.penup()
paddle.goto(x=350, y=0)


# Now I create the movement of the paddle
def go_up():
    new_y = paddle.ycor() + 20
    paddle.goto(paddle.xcor(), new_y)


def go_down():
    new_y = paddle.ycor() - 20
    paddle.goto(paddle.xcor(), new_y)


screen.listen()
screen.onkey(go_up, "Up")
screen.onkey(go_down, "Down")

game_is_on = True
while game_is_on:
    # Update the screen manually
    screen.update()

screen.exitonclick()

```
  
</details>

<details>
 <summary>Third part of the solution</summary>

<br>
In this part we will move our paddle in its own class! Then we can create a right and left paddle by using this class!
<br>
<br>  
 
This is the `main.py` file:
 
<br>

```python
from turtle import Screen, Turtle
from paddle import Paddle

# -------------------------------------------- #
# Create the screen
# -------------------------------------------- #
screen = Screen()
screen.bgcolor("black")
screen.setup(width=800, height=600)
screen.title("Pong Game")
# Using tracer to "hidde" the paddle animation
# I f we turn of the tracer we have tp update the screen manually by refreshing it any time
screen.tracer(0)
# -------------------------------------------- #
# Create and move a paddle / Create another paddle
# -------------------------------------------- #
r_paddle = Paddle((350, 0))
l_paddle = Paddle((-350, 0))

screen.listen()
# Movement keys for right paddle
screen.onkey(r_paddle.go_up, "Up")
screen.onkey(r_paddle.go_down, "Down")
# Movement keys for left paddle
screen.onkey(l_paddle.go_up, "w")
screen.onkey(l_paddle.go_down, "s")

game_is_on = True
while game_is_on:
    # Update the screen manually
    screen.update()

screen.exitonclick()

```
 
<br>  
 
This is the `paddle.py` file:

 
```python
from turtle import Turtle


# -------------------------------------------- #
# Create and move a paddle
# -------------------------------------------- #
class Paddle(Turtle):
    def __init__(self, position):
        super().__init__()
        # Standard size of turtle is 20x20, We want to get a 20x100 size (we will stretch 20 by 5)
        self.shape("square")
        self.shapesize(stretch_wid=5, stretch_len=1)
        self.color("white")
        self.penup()
        self.goto(position)

    # Now I create the movement of the paddle
    def go_up(self):
        new_y = self.ycor() + 20
        self.goto(self.xcor(), new_y)

    def go_down(self):
        new_y = self.ycor() - 20
        self.goto(self.xcor(), new_y)

```
  
</details>

<details>
 <summary>Fourth part of the solution</summary>

<br>
Create the ball and make it move
<br>
  
This is the `main.py` file:

```python
from turtle import Screen, Turtle
from paddle import Paddle
from ball import Ball
import time

# -------------------------------------------- #
# Create the screen
# -------------------------------------------- #
screen = Screen()
screen.bgcolor("black")
screen.setup(width=800, height=600)
screen.title("Pong Game")
# Using tracer to "hidde" the paddle animation
# I f we turn of the tracer we have tp update the screen manually by refreshing it any time
screen.tracer(0)
# -------------------------------------------- #
# Create and move a paddle / Create another paddle
# -------------------------------------------- #
r_paddle = Paddle((350, 0))
l_paddle = Paddle((-350, 0))
# -------------------------------------------- #
# Create the ball and make it move (width=20, height=20)
# -------------------------------------------- #
# Initialize a ball object
ball = Ball()

screen.listen()
# Movement keys for right paddle
screen.onkey(r_paddle.go_up, "Up")
screen.onkey(r_paddle.go_down, "Down")
# Movement keys for left paddle
screen.onkey(l_paddle.go_up, "w")
screen.onkey(l_paddle.go_down, "s")

game_is_on = True
while game_is_on:
    time.sleep(0.1)
    # Update the screen manually
    screen.update()
    # Let's move the ball
    ball.move()

screen.exitonclick()

```
 
This is the `ball.py` file:
 
```python
from turtle import Turtle

# -------------------------------------------- #
# Create the ball and make it move (width=20, height=20)
# -------------------------------------------- #
class Ball(Turtle):
    def __init__(self):
        super().__init__()
        self.color("white")
        self.shape("circle")
        self.penup()

    def move(self):
        new_x = self.xcor() + 10
        new_y = self.ycor() + 10
        self.goto(new_x, new_y)
```
  
</details>

<details>
 <summary>Fifth part of the solution</summary>

<br> 
Detect collision with wall and bounce 
<br>
  
This is the `main.py` file:

```python
from turtle import Screen, Turtle
from paddle import Paddle
from ball import Ball
import time

# -------------------------------------------- #
# Create the screen
# -------------------------------------------- #
screen = Screen()
screen.bgcolor("black")
screen.setup(width=800, height=600)
screen.title("Pong Game")
# Using tracer to "hidde" the paddle animation
# I f we turn of the tracer we have tp update the screen manually by refreshing it any time
screen.tracer(0)
# -------------------------------------------- #
# Create and move a paddle / Create another paddle
# -------------------------------------------- #
r_paddle = Paddle((350, 0))
l_paddle = Paddle((-350, 0))
# -------------------------------------------- #
# Create the ball and make it move (width=20, height=20)
# -------------------------------------------- #
# Initialize a ball object
ball = Ball()

screen.listen()
# Movement keys for right paddle
screen.onkey(r_paddle.go_up, "Up")
screen.onkey(r_paddle.go_down, "Down")
# Movement keys for left paddle
screen.onkey(l_paddle.go_up, "w")
screen.onkey(l_paddle.go_down, "s")

game_is_on = True
while game_is_on:
    time.sleep(0.1)
    # Update the screen manually
    screen.update()
    # Let's move the ball
    ball.move()
    # -------------------------------------------- #
    # Detect collision with wall and bounce
    # -------------------------------------------- #
    if ball.ycor() > 280 or ball.ycor() < -280:  # 280 instead 300 because the ball have a width of 20px
        # Needs to bounce the ball
        ball.bounce()

screen.exitonclick()

```
 
This is the `ball.py` file: 
 
```python
from turtle import Turtle


# -------------------------------------------- #
# Create the ball and make it move (width=20, height=20)
# -------------------------------------------- #
class Ball(Turtle):
    def __init__(self):
        super().__init__()
        self.color("white")
        self.shape("circle")
        self.penup()
        # Attributes to create movement
        self.x_move = 10
        self.y_move = 10

    def move(self):
        new_x = self.xcor() + self.x_move
        new_y = self.ycor() + self.y_move
        self.goto(new_x, new_y)

    # -------------------------------------------- #
    # Detect collision with wall and bounce
    # -------------------------------------------- #
    def bounce(self):
        self.y_move *= -1


```
  
</details>

 
<details>
 <summary>Sixth part of the solution</summary>
 
<br>
Detect collision with paddle
<br>
  
This is the `main.py` file:

```python
from turtle import Screen, Turtle
from paddle import Paddle
from ball import Ball
import time

# -------------------------------------------- #
# Create the screen
# -------------------------------------------- #
screen = Screen()
screen.bgcolor("black")
screen.setup(width=800, height=600)
screen.title("Pong Game")
# Using tracer to "hidde" the paddle animation
# I f we turn of the tracer we have tp update the screen manually by refreshing it any time
screen.tracer(0)
# -------------------------------------------- #
# Create and move a paddle / Create another paddle
# -------------------------------------------- #
r_paddle = Paddle((350, 0))
l_paddle = Paddle((-350, 0))
# -------------------------------------------- #
# Create the ball and make it move (width=20, height=20)
# -------------------------------------------- #
# Initialize a ball object
ball = Ball()

screen.listen()
# Movement keys for right paddle
screen.onkey(r_paddle.go_up, "Up")
screen.onkey(r_paddle.go_down, "Down")
# Movement keys for left paddle
screen.onkey(l_paddle.go_up, "w")
screen.onkey(l_paddle.go_down, "s")

game_is_on = True
while game_is_on:
    time.sleep(0.1)
    # Update the screen manually
    screen.update()
    # Let's move the ball
    ball.move()
    # -------------------------------------------- #
    # Detect collision with wall and bounce
    # -------------------------------------------- #
    if ball.ycor() > 280 or ball.ycor() < -280:  # 280 instead 300 because the ball have a width of 20px
        # Needs to bounce the ball
        ball.bounce_y()
    # -------------------------------------------- #
    # Detect collision with paddle
    # -------------------------------------------- #
    if ball.distance(r_paddle) < 50 and ball.xcor() > 320 or ball.distance(l_paddle) < 50 and ball.xcor() < - 320:
        ball.bounce_x()

screen.exitonclick()

```
 
This is the `ball.py` file:

```python
from turtle import Turtle


# -------------------------------------------- #
# Create the ball and make it move (width=20, height=20)
# -------------------------------------------- #
class Ball(Turtle):
    def __init__(self):
        super().__init__()
        self.color("white")
        self.shape("circle")
        self.penup()
        # Attributes to create movement
        self.x_move = 10
        self.y_move = 10

    def move(self):
        new_x = self.xcor() + self.x_move
        new_y = self.ycor() + self.y_move
        self.goto(new_x, new_y)

    # -------------------------------------------- #
    # Detect collision with wall and bounce
    # -------------------------------------------- #
    def bounce_y(self):  # (Used refactor)
        self.y_move *= -1

    def bounce_x(self):
        self.x_move *= -1

```
  
</details> 

 <details>
 <summary>Seventh part of the solution</summary>

<br>  
Detect when paddle misses  
<br>
  
This is the `main.py` file:

```python
from turtle import Screen, Turtle
from paddle import Paddle
from ball import Ball
import time

# -------------------------------------------- #
# Create the screen
# -------------------------------------------- #
screen = Screen()
screen.bgcolor("black")
screen.setup(width=800, height=600)
screen.title("Pong Game")
# Using tracer to "hidde" the paddle animation
# I f we turn of the tracer we have tp update the screen manually by refreshing it any time
screen.tracer(0)
# -------------------------------------------- #
# Create and move a paddle / Create another paddle
# -------------------------------------------- #
r_paddle = Paddle((350, 0))
l_paddle = Paddle((-350, 0))
# -------------------------------------------- #
# Create the ball and make it move (width=20, height=20)
# -------------------------------------------- #
# Initialize a ball object
ball = Ball()

screen.listen()
# Movement keys for right paddle
screen.onkey(r_paddle.go_up, "Up")
screen.onkey(r_paddle.go_down, "Down")
# Movement keys for left paddle
screen.onkey(l_paddle.go_up, "w")
screen.onkey(l_paddle.go_down, "s")

game_is_on = True
while game_is_on:
    time.sleep(0.1)
    # Update the screen manually
    screen.update()
    # Let's move the ball
    ball.move()
    # -------------------------------------------- #
    # Detect collision with wall and bounce
    # -------------------------------------------- #
    if ball.ycor() > 280 or ball.ycor() < -280:  # 280 instead 300 because the ball have a width of 20px
        # Needs to bounce the ball
        ball.bounce_y()
    # -------------------------------------------- #
    # Detect collision with paddle
    # -------------------------------------------- #
    if ball.distance(r_paddle) < 50 and ball.xcor() > 320 or ball.distance(l_paddle) < 50 and ball.xcor() < - 320:
        ball.bounce_x()
    # -------------------------------------------- #
    # Detect when paddle misses
    # -------------------------------------------- #
    if ball.xcor() > 380:
        ball.reset_position()

    if ball.xcor() < -380:
        ball.reset_position()

screen.exitonclick()

```
  
This is the `ball.py` file:

```python
from turtle import Turtle


# -------------------------------------------- #
# Create the ball and make it move (width=20, height=20)
# -------------------------------------------- #
class Ball(Turtle):
    def __init__(self):
        super().__init__()
        self.color("white")
        self.shape("circle")
        self.penup()
        # Attributes to create movement
        self.x_move = 10
        self.y_move = 10

    def move(self):
        new_x = self.xcor() + self.x_move
        new_y = self.ycor() + self.y_move
        self.goto(new_x, new_y)

    # -------------------------------------------- #
    # Detect collision with wall and bounce
    # -------------------------------------------- #
    def bounce_y(self):  # (Used refactor)
        self.y_move *= -1

    def bounce_x(self):
        self.x_move *= -1

    # -------------------------------------------- #
    # Detect when paddle misses
    # -------------------------------------------- #
    def reset_position(self):
        self.goto(0, 0)
        self.bounce_x()
```
  
</details>
