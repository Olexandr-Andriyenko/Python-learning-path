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
 
Now we have a problem with the customized version of the game. After the game is completely finished, the "High Score" is not saved and is set to zero when the game is started again.
<br>
The solution for this problem is to writte the high score in a file, and then to read this file.
Permanent storage of data can be done in simple files or in databases.
<br>

## Open, read or write in a file
 
Firstly I will creat a new project with a text file inside the project folder:

<p align="left">
<img src="https://github.com/Olexandr-Andriyenko/Python-learning-path/blob/main/illustrations/img42.PNG" width="700">
<p> 
 
Lets open this the `my_text.txt` file with python:
 
```python
# Open my_text.txt
file = open("my_text.txt")
# Read the file (returns the content of this file as a string)
content = file.read()
print(content)
# At the end we have to close the file
file.close()
 
``` 
 
A file that is to be edited must be opened beforehand. This is done using the built-in function `open()`.<br>
It is assumed that the file to be opened is located in the same directory as the Python program.<br>
Otherwise, the absolute or relative path to the file must be specified.
<br>
<br>
Many python develepors use a diferent way to open a file.<br>
The use the `with` keyword:
 
```python
# Open my_text.txt
with open("my_text.txt") as file:
    # Read the file (returns the content of this file as a string)
    content = file.read()
    print(content)
    # You don't need to close the fil if you use the with keyword
 
``` 

How we can write inside a file?<br>
For this we use the `write` keyword:
 
```python
# Open my_text.txt
with open("my_text.txt", mode="w") as file:
    # If we like to write inside a file we have to set the
    # parameter mode to w (write)
    file.write("New text.")
```  
Inside the `my_text.txt` file you will find the sentence: New text.
<br>
The previous  text inside the file was overwritten!
<br>
<br>
You have different options to set the mode parameter:
 
| Mode                                            | Description      |
| ------------------------------------------------- | -------- | 
| r                                        | For reading (default setting)    | 
| w                                | To write     |  
| a                                  | To attach at the end of the file      |  
| r+                                 | For reading and writing, current position at the beginning     |  
| w+                                 | For reading and writing, file is emptied     |  
| a+                                 | For reading and writing, current position at the end     |  
| b                                 | To open a file in binary mode      |  

<br>
In this example we save the users input in a txt file:
 
```python
# Example to save names by input inside a file
player = input("Enter you name: ")
# Open my_text.txt
with open("my_text.txt", mode="a") as file:  # If file name doesn't exist, this file will be created
    # If we like to write inside a file we have to set the
    # parameter mode to w (write)
    file.write(f"\n{player}.")
 
```
 
Lets the new knoledge to impove our [Turtle Crossing Game](https://github.com/Olexandr-Andriyenko/Python-learning-path/blob/main/Turtle%20Crossing%20Game.md)! We will save the high score inside a file:
 
- The first step is to create a `high_score.txt` where is in the first line a 0 already written.
- Then we read the file and set our high_score variable to the 0 from the file.
- If we achieve new high score we will open the file and override the zero with new high score
- All changes did only inside the `scoreboard.py` file
 
<details>
 <summary>Solution</summary>

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
        # We open the file and read the first line where is a zero stored
        with open("high_score.txt") as data:
            self.high_score = int(data.read())
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
            # Now we will save our high score inside the text file, we override the content with the high score
            with open("high_score.txt", mode="w") as data:
                data.write(f"{self.high_score}")
            self.score = 0
        self.goto(x=0, y=0)
        self.write("GAME OVER", align="center", font=FONT)



```
  
</details>

## Relative and Absolute File Paths
 
Absolute paths contain the complete position of a file and can therefore be found unmistakably. The root directory (top level of the data structure of a computer) is always assumed.

 
Relative paths describe the position of a file relative to the file or folder you are currently in. Thus they are completely independent of the data structure of the computer system on which they are located. 
 

<p align="left">
<img src="https://github.com/Olexandr-Andriyenko/Python-learning-path/blob/main/illustrations/img43.PNG" width="400">
<p> 

 
| Description                                       | Path      |
| ------------------------------------------------- | -------- | 
| Sub-directory                                     | sub_directory/high_score.txt    | 
| Parent-directory                                  | ../high_score.txt     |  
| File in the parallel directory                    | ../parallel_directory/high_score.txt     |  
| In directory C:\Temp stored                       | C:/Temp/high_score.txt

## Exercise: Mail-Merge
 
We have this project structure: 
 
<p align="left">
<img src="https://github.com/Olexandr-Andriyenko/Python-learning-path/blob/main/illustrations/img44.PNG" width="400">
<p> 

Inside the `starting_letter.txt` file we have this text:
 
```
 Dear [name],

You are invited to my birthday this Saturday.

Hope you can make it!

Olexandr

```
 
Inside the `invited_names.txt` file we have this text:
 
```
Aang
Zuko
Appa
Katara
Sokka
Momo
Uncle Iroh
Toph
```
 
Inside the `ReadyToSend` folder you will find one example, we will store here our letters!
<br>
<br>
The task is to automate the letter writting. For this task you have to use your knowledge about paths.<br>
You have to open the `starting_letter.txt` and replace the name by each name of the `invited_names.txt`.<br>
Save for each name the letter inside the `ReadeToSend` folder which is inside the `Output` folder!
<br>
<br>
Python has a set of methods available for the file object.
 
| Method                                       | Description      |
| ------------------------------------------------- | -------- | 
| close()                                   | 	Closes the file    | 
| fileno()                 | 	Returns a number that represents the stream, from the operating system's perspective    |  
| flush()                       | 	Flushes the internal buffer |
 | isatty()                                | Returns whether the file stream is interactive or not  | 
| read()                                | 	Returns the file content   |  
| readable()               | Returns whether the file stream can be read or not    |  
| readline()                      | Returns one line from the file |
 | readlines()                                  | 		Returns a list of lines from the file  | 
| seek()                                | 	Change the file position    |  
| seekable()               | 	Returns whether the file allows us to change the file position    |  
| tell()                      | Returns the current file position |
 | truncate()                               | 	Resizes the file to a specified size   | 
| writable()                              | Returns whether the file can be written to or not    |  
| write()           | 	Writes the specified string to the file     |  
| writelines()                     | 	Writes a list of strings to the file |

