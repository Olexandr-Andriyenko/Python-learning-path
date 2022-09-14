# Files, Directories and Paths

In this chapter I will learn how to work with local files and understand the diretories.<br>

## Add high score to the snake game

Download and open the files of the [Turtle Crossing Game](https://github.com/Olexandr-Andriyenko/Python-learning-path/blob/main/Turtle%20Crossing%20Game.md) which I created inside my intermediate projects. Now we will add a counter for the high score!

I changed the files, that we get a new counter called "High Score". <br>
Also we got an input window which will aks the user whether he likes to continue playing the game.<br>
You can download the files below and try the game!

<details>
 <summary>Adjusted version</summary>
  
<br>
  
This is the `main.py` file:

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
            scoreboard.update_scoreboard()
            game_is_on = False
            while True:
                answer = screen.textinput("Snake Restart", "Play again? (Y/N): ")
                valid_answer = ["y", "n"]
                if answer.lower() in valid_answer:
                    break
            if answer.lower() == "y":
                player.reset_position()
                game_is_on = True
                screen.listen()


screen.exitonclick()

```
  
This is the `player.py` file:

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
        self.high_score = 0
        self.update_scoreboard()

    def update_scoreboard(self):
        self.clear()
        self.goto(x=-200, y=250)
        self.write(f"Level: {self.score}", align="center", font=FONT)
        self.goto(x=150, y=250)
        self.write(f"High Score: {self.high_score}", align="center", font=FONT)

    def increase_score(self):
        self.score += 1
        self.update_scoreboard()

    def game_over(self):
        if self.score > self.high_score:
            self.high_score = self.score
            self.score = 0
        self.goto(x=0, y=0)
        self.write("GAME OVER", align="center", font=FONT)





```
  
</details>
 
Now we have a problem with the customized version of the game. After the game is completely finished, the "High Score" is not saved and is set to zero when the game is started again
