# Pong Game
 Build the classic arcade game [ponr](https://de.wikipedia.org/wiki/Pong).
 <br>
 <br>
 You can breake the game in this parts:<br>
 - Create the screen
 - Create and move a paddle
 - Create another paddle
 - Create the ball and make it move
 - Detect collision wit hwall and bounce
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

```
  
</details>
