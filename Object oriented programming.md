# Object oriented programming

Until now, we had worked according to the concept of procedural programming. With the increase in complexity and the number of relationships between functions and variables, programming projects quickly become confusing and difficult to understand. Using the programming paradigm of object-oriented programming, projects can often be significantly simplified and presented in a clearer way. The reason why the concept is called "Object Oriented Programming" is that you try to model an object of the "real" world.

## Introduction

In software development, object orientation (OO for short) is a view of complex systems in which a system is described by the interaction of cooperating objects. 
The term object is not very clear, the only important thing about an object is that it has certain attributes (properties) and methods assigned to it and that it is able to receive messages from other objects or send messages to them.
Object orientation is mostly used in the context of object-oriented programming to reduce the complexity of the resulting programs.
<br>
<br>
Object-oriented programming (OOP) is a common paradigm that is now used to program in almost all languages. And it's the one that almost every major software project is based on these days; sometimes more, sometimes less.
In object-oriented programming, the code is separated into "objects". Its opposite is procedural programming, in which a sequence of code is processed piece by piece.
<br>
<br>
Because object orientation is very similar to human thinking, this programming style can also be used very intuitive by a human programmer. So it is an easy concept for humans to understand and apply, as it is based on our natural human thinking.
<br>
<br>
An object is an exact description for example of our pen. The attributes (properties) have a value or a fixed state. For example, our pen had the outer color white and the writing color black. The class, on the other hand, is a generalization of all pen objects. It describes which attributes a pen can have without assigning a value to them. Only the object represents the thing pen, which we have in front of us with all its properties.


<p align="center">
<img src="https://github.com/Olexandr-Andriyenko/Python-learning-path/blob/main/illustrations/img28.png" width="500">
<p>  

Another example is the "Human" class. Even before birth, we know which characteristics (e.g. eye color, size, gender) and functions (e.g. speaking) a person will later have, but we do not know what value they have. A single person then corresponds to an object of the class "human" (even if the term object is perhaps a bit misplaced in this context), whose properties are set at creation (e.g. eye color=brown).
<br>
<br>
In object-oriented programming, each object belongs to a class. This has the attributes (properties) and the methods (interactions) of this class. In our class "pen" a method could be called "write". Methods are nothing more than functions that can only be executed by a specific object. So an object is just a way to combine some variables and functions into one "thing".
  
## Define classes, methods and objects
  
Using the example of the pen we will learn how to create classes, objects and methods.<br>

```python
# Define a class with the "class" keyword
class pen:
    # Let's create some attributes which the pen will have (We are using "None" to assign "no value"
    outside_color = None
    writing_color = None

    # Create some methods (what can the pen do?). The definition is the same as functions.
    # Methods have always minimum one parameter, the object itself "keyword self"
    def write(self):
        print("I am writing!")

    def refill(self):
        print("I refill the pen!")

    # Inside the f-string we have to use the "self" keyword to call the object "itself"
    def about_pen(self):
        print(f"My outside color is {self.outside_color} and my writing color is {self.writing_color}! ")


# Let's use our class inside the main program

# Firstly we create two objects of the class "pen", this process is called "create instance of class"
my_pen = pen()
workers_pen = pen()
# Let's set the values of the attributes with the "dot notation"
my_pen.outside_color = "red"
my_pen.writing_color = "blue"
workers_pen.outside_color = "yellow"
workers_pen.writing_color = "black"
# Let's do something with the pens by using the methods
my_pen.write()
workers_pen.refill()
# Display the information about the pen with the "about_pen" method
my_pen.about_pen()
workers_pen.about_pen()

# Output is:
# I am writing!
# I refill the pen!
# My outside color is red and my writing color is blue! 
# My outside color is yellow and my writing color is black!  
  
```
  
The following should be kept in mind:<br>
- A class is generally a group of things, living things, or concepts that have common characteristics or properties.
- In OOP, a class specifies a set of objects with the same attributes and methods.
- The class has a mechanism to create objects. It is just the construction template for all newly required objects, while the objects "live" in the program system and   can be addressed.
- Different relationships can be established between different classes, or their objects, to represent relationships as in reality.
  
<br>
<br>
If you remember, we had already applied methods to objects. However, at that time we did not know what exactly a method or an object is.  We had used the method "append()" with the dot notation for the data structure "list". This method allowed us to add an entry at the end of the list.
 <br>
 <br>
 Example:
  
```python
# Create a list
my_list = ["Red", "Blue", "Yellow"]
# Display the list
print(my_list)
# Add a entry at the end of this list
my_list.append("Black")
# Display the list
print(my_list)
  
# Output is:
# ['Red', 'Blue', 'Yellow']
# ['Red', 'Blue', 'Yellow', 'Black']
```
  
Exercise:<br>
<br>
Write a class called "Cat". The class has three attributes: "name", " race" and "age". The "age" of a new "cat" object should be "0" at the beginning of its lifetime.<br>
Write three methods::<br>
- The first one is called "doMiau()". When the method is executed, the text "meow" is output.
- The second method you call "riseAge()". This method increases the value of the "age" attribute by 1.
- The third method is called "displayDetails()", it displays name, race and age meaningfully as text.
  
<details><summary>Solution:</summary>
  
```python
  
# Create the class
class Cat:
    # Attributes
    name = None
    race = None
    age = 0

    # Methods
    def doMiau(self):
        print("meow")

    def riseAge(self):
        self.age += 1

    def displayDetails(self):
        print(f"The name of the cat is {self.name}, the cat is {self.age} years old and the race is an {self.race}!")


# Main program
my_cat = Cat()
# Show me the age of my cate
print(f"My cat is {my_cat.age} years old")
# Lets rise the age of my cate
my_cat.riseAge()
# My cat get a name
my_cat.name = "Thanos"
# Define the race of the cat
my_cat.race = "American Shorthair"
# Show me all details about my cat
my_cat.displayDetails()
  
# Output is:
# My cat is 0 years old
# The name of the cat is Thanos, the cat is 1 years old and the race is an American Shorthair!
```
  
</details>
  
## Turtle libary
  
A library is an umbrella term referring to a reusable chunk of code. Usually, a Python library contains a collection of related modules and packages. Actually, this term is often used interchangeably with “Python package” because packages can also contain modules and other packages (subpackages). However, it is often assumed that while a package is a collection of modules, a library is a collection of packages.
<br>
<br>
To get some exerciese with the concept of OOP, we will work with the libary "turtle" for now.
<br>
<br>
By using "import turtle" we can use this libary.<br>
Now you can access the class "Turtle" which was defined inside this library.
  
<p align="center">
<img src="https://github.com/Olexandr-Andriyenko/Python-learning-path/blob/main/illustrations/img31.png" width="550">
<p>  
  
We can create an object of this class and save it inside a variable. I will call my turtle (variable) bob:

```python
import turtle

bob = turtle.Turtle()
# If we use "print()" on our object, we will see where our object is stored inside the computer memory
print(bob)
  
# Output is:
# <turtle.Turtle object at 0x000001F0556B6080>
```
  
Now we can do many different and interesting things with this object.<br>
One of the other interesting classes in the "turtle" library is the "Screen" class. It allows to display our object in a window.
  
```python
import turtle

bob = turtle.Turtle()
# Creat a "Screen" object:
my_screen = turtle.Screen()
# Use one of the Screen class attributes (this is the height of the screen, if you print it you will see 300 as default value)
my_screen.canvheight
# Let's use another attribute of the class Screen (we will see the screen until we press a key)
my_screen.exitonclick()


```
  
In the middle of the screen you can see the turtle "bob".

<p align="center">
<img src="https://github.com/Olexandr-Andriyenko/Python-learning-path/blob/main/illustrations/img32.PNG" width="450">
<p>  
  
But the shape of the turtle is actually an arrow, lets change it to a turtle by a attribute of the Turtle class.

```python
import turtle

bob = turtle.Turtle()
# Change the shape of "bob"
bob.shape("turtle")
# We can also change the color of bob
bob.color("green")
# Creat a "Screen" object:
my_screen = turtle.Screen()
# Let's use another attribute of the class Screen (we will see the screen until we press a key)
my_screen.exitonclick()


```

<p align="center">
<img src="https://github.com/Olexandr-Andriyenko/Python-learning-path/blob/main/illustrations/img33.PNG" width="450">
<p> 

Of course, you don't have to know all these classes and attributes by memory. You can find all this in the ["Turtle graphics libary documentation"](https://docs.python.org/3/library/turtle.html).
<br>
<br>
Exercise:
<br>
<br>
Create your own turtle and draw a rectangle200 with a height of 150 and width of 200.

<details><summary>Solution:</summary>
  
```python
 
import turtle

bob = turtle.Turtle()
# Change the shape of "bob"
bob.shape("turtle")
bob.color("green")
# Move turtle forward
bob.forward(150)
# Turn him 90 degrees left direction
bob.left(90)
# Move turtle forward
bob.forward(200)
bob.left(90)
bob.forward(150)
bob.left(90)
bob.forward(200)

# Creat a "Screen" object:
my_screen = turtle.Screen()
# Let's use another attribute of the class Screen (we will see the screen until we press a key)
my_screen.exitonclick()


  
```
</details>

Exercise:
<br>
<br>
Draw the following house with your turtle!
  
<p align="center">
<img src="https://github.com/Olexandr-Andriyenko/Python-learning-path/blob/main/illustrations/img34.PNG" width="250">
<p>  

<details><summary>Solution:</summary>
  
```python
import turtle
bob = turtle.Turtle()
# Set window size
turtle.setup(500, 500)
# Change the shape of "bob"
bob.shape("turtle")
bob.color("green")
bob.fd(80)
bob.lt(90)
bob.fd(80)
bob.lt(30)
bob.fd(80)
bob.lt(120)
bob.fd(80)
bob.lt(120)
bob.fd(80)
bob.rt(90)
bob.fd(80)
bob.rt(90)
bob.fd(20)
bob.rt(90)
bob.fd(40)
bob.lt(90)
bob.fd(40)
bob.lt(90)
bob.fd(40)
bob.rt(90)
bob.fd(20)
bob.rt(90)
bob.fd(80)
# Creat a "Screen" object:
my_screen = turtle.Screen()
# Let's use another attribute of the class Screen (we will see the screen until we press a key)
my_screen.exitonclick()
```
</details>  
  
  
<br>
<br>
  
  
## Prettytable
  
Another library useful for practicing OOP is the "prettytable" libary. It allows you to quickly create simple tables in the console. Compared to the libary "turtle" you have to install it first because it is not standard. You can install it inside pycharm IDE:<br>
Go to File > Settings > Project: > Python Interpreter > press the + symbol > search prettytabble > install
<br>
<br>
Like every time to practice this libary your best friend is the [documentation](https://pypi.org/project/prettytable/) about prettytable!
<br>
<br>
Example:
  
```python
  # import this libary
import prettytable
# Create a object
my_table = prettytable.PrettyTable()
# Add data
my_table.add_column("Pokemon Name", ["Pikachu", "Squirtle", "Charmander"])
my_table.add_column("Type", ["Electric", "Water", "Fire"])
# Display the table
print(my_table)
# Change properties
my_table.align = "l"
print(my_table)  
```
Exercise:
<br>
Create with "prettytable" a simple to-do list! The user can select a day and enter a to-do. Then he can select to continue for a new entry or exit the to-do list.

  
<details><summary>Solution:</summary>
  
```python
# Example using prettytable
import prettytable
# Inside this dictionary we will store the to-dos
to_dos = {
    "monday": [],
    "tuesday": [],
    "wednesday": [],
    "thursday": [],
    "friday": [],
    "saturday": [],
    "sunday": []
  }
to_do_on = True
while to_do_on:
    # Variable which will be filled by the user
    day = "place holder"
    valid_days = ["monday", "tuesday", "wednesday", "thursday", "friday", "saturday", "sunday"]
    # Loop until the user enter the valid day
    while True:
        if day.lower() in valid_days:
            break
        # Display all days which the user can select
        print("------------------------\nWelcome to your to-do list!\n------------------------")
        day = input(""
                    "\t1-Monday\n"
                    "\t2-Tuesday\n"
                    "\t3-Wednesday\n"
                    "\t4-Thursday\n"
                    "\t5-Friday\n"
                    "\t6-Saturday\n"
                    "\t7-Sunday\n"
                    "------------------------\n"
                    "Select a day: ")
    # Now we search inside the dictionary the selected day and enter a to-do
    to_do = input("Enter a to-do: ")
    to_dos[day].append(to_do)
    # Create an object of the class "PrettyTable"
    table = prettytable.PrettyTable()
    # Create the captions
    table.field_names = ["Day", "To-Do"]
    # Create all rows with the days
    table.add_rows(
        [
            ["Monday", to_dos["monday"]],
            ["Tuesday", to_dos["tuesday"]],
            ["Wednesday", to_dos["wednesday"]],
            ["Thursday", to_dos["thursday"]],
            ["Friday", to_dos["friday"]],
            ["Saturday", to_dos["saturday"]],
            ["Sunday", to_dos["sunday"]]
        ]
    )
    # Display the table
    print(table)
    # Ask the user if he likes to exit
    while True:
        valid_input = ["yes", "no"]
        exit_to_do = input("You like to exit the to-do list? (Yes/No): ")
        if exit_to_do in valid_input:
            if exit_to_do.lower() == "yes":
                # Set this variable to False for breaking the main while loop
                to_do_on = False
        break
```
</details>  
  
  
<br>
Exersice:
<br>
The table shows the recorded values of a free fall experiment.<br>

<p align="center">
<img src="https://github.com/Olexandr-Andriyenko/Python-learning-path/blob/main/illustrations/img35.png" width="500">
<p> 

Display the following table using prettytable and complete the empty cells.<br>
Sorry but the table is writen in german language, use a translator :) <br>
You need this formulas:
<br>
<br>

![CodeCogsEqn](https://user-images.githubusercontent.com/92121260/187521471-70e529ea-c54d-462b-9bd9-10bd5e865c2d.gif)

![CodeCogsEqn (1)](https://user-images.githubusercontent.com/92121260/187522535-531f2d3f-77c8-4170-822a-4bb7a418ecb5.gif)
  

<details><summary>Solution:</summary>
  
```python
# Import everything from this libary
from prettytable import *
# Create dictionary with data
data_table = {
    "Nr.": [1, 2, 3, 4, 5, 6, 7, 8, 9, 10],
    "Fallstrecke": [0, 0.115, 0.245, 0.285, 0.38, 0.49, 0.59, 0.67, 0.76, 0.835],
    "Messung 1": [0, 0.1568, 0.2072, 0.3404, 0.2811, 0.3173, 0.3488, 0.3705, 0.3937, 0.4183],
    "Messung 2": [0, 0.1561, 0.2075, 0.2427, 0.2846, 0.3172, 0.3477, 0.3703, 0.3941, 0.4176],
    "Messung 3": [0, 0.1566, 0.2578, 0.2403, 0.2814, 0.3172, 0.3483, 0.3693, 0.3946, 0.4116],
    "Mittelwert": [],
    "Geschwindigkeit": []
}

# Calculate the first value
for index in data_table["Nr."]:
    # Calculating the "Mittelwert"
        messung_1 = data_table["Messung 1"][index - 1]
        messung_2 = data_table["Messung 2"][index - 1]
        messung_3 = data_table["Messung 3"][index - 1]
        # Do not forget to round
        mittelwert = round((messung_1 + messung_2 + messung_3) / 3, 4)
        data_table["Mittelwert"].append(mittelwert)
    # Calculating the "Geschwindigkeit"
        geschwindigkeit = round(9.81 * mittelwert, 2)
        data_table["Geschwindigkeit"].append(geschwindigkeit)


# Create object
my_table = PrettyTable()
# Fill table with data
my_table.add_column("Nr.", [1, 2, 3, 4, 5, 6, 7, 8, 9, 10])
my_table.add_column("Fallstrecke in m", data_table["Fallstrecke"])
my_table.add_column("Messung 1 in s", data_table["Messung 1"])
my_table.add_column("Messung 2 in s", data_table["Messung 2"])
my_table.add_column("Messung 3 in s", data_table["Messung 3"])
my_table.add_column("Mittelwert in s", data_table["Mittelwert"])
my_table.add_column("Geschwindigkeit in m/s", data_table["Geschwindigkeit"])
# Display table
print(my_table)

# Save this table as txt file! (You wil find the file inside the project directory)
# More about this later...
with open('file', 'w') as w:
    w.write(str(my_table))
```
</details>

## math — Mathematical functions
  
This module provides access to the mathematical functions defined by the C standard. When working on financial or scientific projects, it is sometimes necessary to implement mathematical calculations into the project. Python provides the mathematical module to deal with such calculations. By using this modul you need to use methods, attributes, classes and objects, perfect to practice OOP. Don't forget to read the [documentation](https://docs.python.org/3/library/math.html#trigonometric-functions) about this math modul!
<br>
<br>
Some examples using this modul:
  
```python
# Examples using the "math" modul
# ---------------------------------------- #
# import the modul
import math
# ---------------------------------------- #
# 1. Example
# You must all be familiar with pi. Pi is represented as either 22/7 or 3.14.
pi = math.pi
print(pi)
# You can use pi to calculate the area of a circle
# Define the radius of the circle
r = 5
circle_area = math.pi * r ** 2
print(circle_area)
# ---------------------------------------- #
# 2. Example
# Even the circle number tau is included (Ratios of circumference and radius)
circle_number = math.tau
print(circle_number)
# ---------------------------------------- #
# 3. Example
# Using infinity numbers in python
print(math.inf)
print(-math.inf)
# Divide a number by infinite number
print(1 / math.inf)
# ---------------------------------------- #
# 4. Example
# Faculty of a number
a = 5
print(math.factorial(a))
# ---------------------------------------- #
# 5. Example
# Power functions (German: Potenzfunktionen)
exponentiation_numbers = [0, 5, -2, math.pi]
print(math.exp((exponentiation_numbers[0])))
print(math.exp((exponentiation_numbers[1])))
print(math.exp((exponentiation_numbers[2])))
print(math.exp((exponentiation_numbers[3])))
# ---------------------------------------- #
# 6. Example
# Square root
print(math.sqrt(9))
# ---------------------------------------- #
# 7. Example
# Trigonometric functions
print(math.sin(math.pi / 2))
print(math.sin(90))
# ---------------------------------------- #
# 8. Example
# Convert degrees in radians
degree = 90
radians = math.pi
print(math.degrees(radians))
print(math.radians(degree))  
  
# Output is:
# 3.141592653589793
# 78.53981633974483
# 6.283185307179586
# inf
# -inf
# 0.0
# 120
# 1.0
# 148.4131591025766
# 0.1353352832366127
# 23.140692632779267
# 3.0
# 1.0
# 0.8939966636005579
# 180.0
# 1.5707963267948966
```
  
Exercice:<br>
Write a program that calculates the hypotenuse of a right triangle.<br>
Divide the program into input, processing and output:<br>
- In the input part, read the length of the two cathets
- Use the function math.sqrt() for the calculation
- Output the result to the screen
  
<details><summary>Solution:</summary>
  
```python
# import the modul
import math
# -------------------------------------------------- #
# Function
def calc_hypetenuse(cathet_1, cathet_2):
    hypotenuse = math.sqrt((cathet_1 ** 2) + (cathet_2 ** 2))
    return hypotenuse
# -------------------------------------------------- #
# Main program
# Input part
try:
    cathete_1 = float(input("Input the first cathet: "))
    cathete_2 = float(input("Input the second cathet: "))
except:
    print("Wrong input!")
# Processing part
hypotenuse = round(calc_hypetenuse(cathete_1, cathete_2), 2)
# Output part
print(f"The hypotenuse is: {hypotenuse}")
```
</details>

Exercice:<br>
Write a program to plot functions with the "turtle" libary and the "math" module.<br>
Draw a parable and a linear function!

<details><summary>Solution:</summary>
  
```python
# Import modules
import turtle
import prettytable
# -------------------------------------------------- #
# Create a window
turtle.getscreen()
# Create a object from the "Turtle()" class
t = turtle.Turtle()
# Variable to "zoom" later
scale = 10
# -------------------------------------------------- #
# Generate a table for x square with x = -20 to +20
my_table = prettytable.PrettyTable()
my_table.field_names = ["x", "x^2"]
for x in range(-20, 21, 1):
    x_square = x ** 2
    my_table.add_row([x, x_square])
print(my_table)
# -------------------------------------------------- #
# Draw the axes
# penup() will lift the turtle off the “digital canvas” and if you move the turtle in penup state it won’t draw.
t.penup()
# Move turtle to an absolute position
t.goto(-400, 0)
# Put the turtle back in the "canvas" to draw
t.pendown()
# Lets draw
t.goto(400, 0)
t.penup()
t.goto(0, -400)
t.pendown()
t.goto(0, 400)
t.penup()
t.home()
# -------------------------------------------------- #
# Prepare the turtle
t.pensize(2)
# Location of the first coordinates (-20;400)
# You can try without the scale variable
t.goto(-20 * scale, 400)
# -------------------------------------------------- #
# Draw the curve
for x in range(-20, 21, 1):
    x_square = x ** 2
    t.dot(10, "RED")
    # You can try without the scale variable
    t.goto(x * scale, x_square)
# -------------------------------------------------- #
# Bring the turtle back
t.penup()
t.home()
# -------------------------------------------------- #
# Lets draw f(x) = 2*x
t.penup()
t.goto(-20 * scale, -40)
t.pendown()
t.pencolor("GREEN")
for x in range(-20, 21, 1):
    x_2 = x * 2
    t.goto(x * scale, x_2)
# -------------------------------------------------- #
# Bring the turtle back
t.penup()
t.home()
# -------------------------------------------------- #
turtle.exitonclick()

```
</details>

Exercise:<br>
Draw the sinus function by using the tuertle and math moduls.
  
<details><summary>Solution:</summary>
  
```python
# Import modules
import math
import turtle
import prettytable
# -------------------------------------------------- #
# Create a window
turtle.getscreen()
# Create an object from the "Turtle()" class
t = turtle.Turtle()
# Variable to "zoom" later
scale = 100
# -------------------------------------------------- #
# Draw the axis
t.backward(180)
t.forward(360)
t.stamp()
t.backward(180)
t.left(90)
t.forward(100)
t.stamp()
t.backward(200)
t.forward(100)
t.right(90)
t.backward(180)
# Draw the curve
for i in range(-180, 181):
    t.color("RED")
    t.goto(i, math.sin(math.radians(i)) * scale)

turtle.exitonclick()

```
</details>
