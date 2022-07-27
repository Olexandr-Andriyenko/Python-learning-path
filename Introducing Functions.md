# Introducing Functions

Everyone had heard something about functions in their school days. If you do not remember the exact topic from the mathematics class it is not a problem. Because the functions in mathematics compared to the functions in programming are quite different. Until now, it was not exactly said what functions are, but we had already used them anyway, for example the print()-, input()-, int()-, float()- and str()-function. A function is often recognized by its identifier(name of the function) followed by round brackets.
<br>
<br>
In the round brackets we enter data so that they are processed somehow. A function can be imagined as a box that has an input and an output. Data goes into the input of this "box". They are processed in this "box" by specific operations which modify the data in some way. At the output, the processed data is returned, having some initial state due to the working steps.
<br>

<p align="center">
<img src="https://github.com/Olexandr-Andriyenko/Python-learning-path/blob/main/illustrations/img13.png" width="100">
<p>

<br>
A function is a group of related instructions that perform a specific task.
<br>
  
<p align="center">
<img src="https://github.com/Olexandr-Andriyenko/Python-learning-path/blob/main/illustrations/img14.png" width="400">
<p>  
  
<br>
  
## Types of functions

There are two different types of functions in python, built-in functions and user-defined functions.<br>

### Built-in functions

We know already the build-in functions like print(), input(), int().<br>
Built-in functions come included with the standard library of python. These are the functions that some programmers somewhere in the world defined a long time ago and now you can use these functions in your program without having to write them all over again. With time you will get to know many more useful built-in functions.<br>
When you are already interested to get to know some built-in functions then you can visit the python documentation about this topic: [Built-in Functions](https://docs.python.org/3/library/functions.html)
<br>
<br>
Let's look at some examples of built in functions:
```python
# 1. function "len()"
# Return the length (the number of items) of an object.
a = "Hello World"
b = len(a)
print(b)
# Output is:
# 11
# Inside the variable a we have 11 items (blank included)
  
# 2. function "divmod(a, b)"
# Take two (non-complex) numbers as arguments and return a pair of 
# numbers consisting of their quotient and remainder when using integer division.
a = 10
b = 3
c = divmod(a, b)
print(c)  
# Output is:
# (3, 1)
  
# 3. function "round()"
# Return number rounded to ndigits precision after the decimal point. 
# If ndigits is omitted or is None, it returns the nearest integer to its input.
a = 3.3
b = round(a)
c = 3.38
d = round(c, 1)
print(b)
print(d)
# Output is:
# 3
# 3.4
  
```

### User-defined functions

Python lets us define and use our own functions which we can use anywhere in our program (user defined functions). This functions help divide our program into smaller and modular blocks. As our program gets bigger, user-definedfunctions make it more organized and manageable. It also avoids repetition and makes the code reusable.
<br>
<br>
With the keyword "def" we create a user-defined function. We can also choose a name for our function, with these function name our own function can be called at any place in our code. For functions, the indentation is very important because it shows us the processing steps of the function.
<br>
<br>
Example for a user-defined function:
<br>
<br>
```python
# By using "def" we define a function called "welcome". 
def welcome():
    # In the indented area we write the functional processing steps
    print("Hello: Olexandr")
    print("Welcome to user-defined functions")

# Now somewhere in our code we need to call the function
welcome()  
# Output is:
# Hello: Olexandr
# Welcome to user-defined functions
```
<p align="center">
<img src="https://github.com/Olexandr-Andriyenko/Python-learning-path/blob/main/illustrations/img15.png" width="400">
<p>  
  
Our function with the name "welcome" can now be used again by calling the function at any point in our program. To call a function we need the function name followed by the round brackets. This way we can recycle code and save typing:
