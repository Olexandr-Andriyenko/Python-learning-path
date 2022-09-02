# Practice the turtle module

In this chapter we will deal intensively with the python module or package `turtle`. As we have already seen this module is a way to draw graphics on the screen.
<br>
<br>
Firstly complete the challenges:
<br>
<br>
1. Challenge:<br>
Draw a square!

<details>
 <summary>Solution</summary>

```python
import turtle
from turtle import Turtle
from turtle import Screen

# Create an object
timmy_the_turtle = Turtle()
screen = Screen()
# Now the movement
for counter in range(0, 4):
    turtle.fd(100)
    turtle.lt(90)
    print(counter)

screen.exitonclick()  
```
  
</details>
                
