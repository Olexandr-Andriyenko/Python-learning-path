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

