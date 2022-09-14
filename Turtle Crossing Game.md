# Turtle Crossing Game

![giphy](https://user-images.githubusercontent.com/92121260/189979480-15d62061-e620-49fa-b7c6-d6705e9e87b5.gif)

In this project I am creating an intermadiate game with the "turtle" module. <br>
At the end the game looks like this: 
<br>


<img src="https://user-images.githubusercontent.com/92121260/189979699-e8dcdf5e-e4bf-4bff-b5b7-2eface550dc7.gif" width="350"/>

This game will prove previously learned knowledge about the turtle module and the OOP concepts.
<br>
<br>


<details>
 <summary>Use the following structure of the files to finish this project</summary>
  
<br>
  
This is the `main.py` file:

```python
import time
from turtle import Screen
from player import Player
from car_manager import CarManager
from scoreboard import Scoreboard

screen = Screen()
screen.setup(width=600, height=600)
screen.tracer(0)

game_is_on = True
while game_is_on:
    time.sleep(0.1)
    screen.update()

```
  
This is the `car_manager.py` file:

```python
COLORS = ["red", "orange", "yellow", "green", "blue", "purple"]
STARTING_MOVE_DISTANCE = 5
MOVE_INCREMENT = 10


class CarManager:
    pass

```
  
This is the `scoreboard.py` file:

```python
FONT = ("Courier", 24, "normal")


class Scoreboard:
    pass

```
  
This is the `player.py` file:

```python
STARTING_POSITION = (0, -280)
MOVE_DISTANCE = 10
FINISH_LINE_Y = 280


class Player:
    pass

```
  
</details>

Some rules for the game:
- A turtle moves forwards when you press the "Up" key. It can only move forwards, not back, left or right.
- Cars are randomly generated along the y-axis and will move from the right edge of the screen to the left edge.
- When the turtle hits the top edge of the screen, it moves back to the original position and the player levels up. On the next level, the car speed increases.
- When the turtle collides with a car, it's game over and everything stops.
<br>
<br>

Break the problem in smaller problems:
- Move the turtle with keypress
- Create and move the cars
- Detect collision with car
- Detect when turtle reaches the other side
- Create a scoreboard


<details>
 <summary>Solution</summary>
  

This is the `main.py` file:
<br>
 
```python
import time
from turtle import Screen, distance
from player import Player, FINISH_LINE_Y
from car_manager import CarManager
from scoreboard import Scoreboard

screen = Screen()
screen.setup(width=600, height=600)
screen.tracer(0)
# Objects
player = Player()
scoreboard = Scoreboard()
car_manager = CarManager()
screen.listen()
screen.onkey(player.move, "Up")

game_is_on = True
while game_is_on:
    time.sleep(0.1)
    screen.update()

    car_manager.create_car()
    car_manager.move_cars()

    # Create the finish line
    if player.ycor() > FINISH_LINE_Y:
        player.reset_position()
        scoreboard.increase_score()

    # Create car collision
    for car in car_manager.all_cars:
        if car.distance(player) < 20:
            #  Show GAME OVER
            scoreboard.game_over()
            game_is_on = False
screen.exitonclick()

```
 
This is the `player.py` file:
<br>
 
```python
from turtle import Turtle
STARTING_POSITION = (0, -280)
MOVE_DISTANCE = 10
FINISH_LINE_Y = 280


class Player(Turtle):
    def __init__(self):
        super().__init__()
        self.shape("turtle")
        self.color("black")
        self.penup()
        self.setheading(90)
        self.goto(STARTING_POSITION)

    def move(self):
        new_y = self.ycor() + MOVE_DISTANCE
        self.goto(0, new_y)

    def reset_position(self):
        self.goto(STARTING_POSITION)
```
 
This is the `car_manager.py` file:
<br>
 
```python
from turtle import Turtle
import random
COLORS = ["red", "orange", "yellow", "green", "blue", "purple"]
STARTING_MOVE_DISTANCE = 5
MOVE_INCREMENT = 10


class CarManager:

    def __init__(self):
        self.all_cars = []

    def create_car(self):
        # Create only cars if we get a one on our "dice"
        dice = random.randint(1, 6)
        if dice == 1:
            new_car = Turtle("square")
            new_car.shapesize(stretch_wid=1, stretch_len=2)
            new_car.penup()
            new_car.color(random.choice(COLORS))
            new_car.setheading(180)
            new_car.goto(x=300, y=random.randrange(-250, 250))
            self.all_cars.append(new_car)

    def move_cars(self):
        for car in self.all_cars:
            car.fd(STARTING_MOVE_DISTANCE)




```
 
This is the `scoreboard.py` file:
<br>
 
```python
from turtle import Turtle

FONT = ("Courier", 24, "normal")


class Scoreboard(Turtle):
    def __init__(self):
        super().__init__()
        self.color("black")
        self.penup()
        self.hideturtle()
        self.score = 0
        self.update_scoreboard()

    def update_scoreboard(self):
        self.clear()
        self.goto(x=-200, y=250)
        self.write(f"Level: {self.score}", align="center", font=FONT)

    def increase_score(self):
        self.score += 1
        self.update_scoreboard()

    def game_over(self):
        self.goto(x=0, y=0)
        self.write("GAME OVER", align="center", font=FONT)

```
  
</details>
