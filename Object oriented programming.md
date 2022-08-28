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
  
![house](https://user-images.githubusercontent.com/92121260/187092239-6ddf52e6-4571-4ddd-9667-213f2024d81b.svg)
