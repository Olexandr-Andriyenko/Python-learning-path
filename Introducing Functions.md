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

### User-defined functions with parameters and arguments
  
After the function name there are empty round brackets, but they do not necessarily have to be empty. Inside these brackets you can pass data/values to the function. In coding, these values are called arguments or parameters (depending on whether they are in the call or in the definition of the function). 
<br>
<br>
Example:
  
```python
# We create a function with an parameter
def welcome(name):
    print(f"Hello: {name} ")
    print("Welcome to user-defined functions")

# We create an argument
users_name = input("Please enter your name: ")
# Now we call the function  
welcome(users_name)
  
# Output is:
# Please enter your name: Olex
# Hello: Olex
# Welcome to user-definition functions
```
The terms parameter and argument are used synonymously by many programmers, but both have different meanings.For this reason, the difference between parameter and argument should be explained at this point:
<br>
<br>
Parameter
<br>
<br>
A parameter is the variable defined in parentheses during the function definition. They are simply written when we declare a function like in the example before (name is the parameter).
<br>
<br>
Argument
<br>
<br>
An argument is a value that is passed to a function when it is called. This can be a variable, value or object passed as input to a function. They are written when we call the function. We did it in the example before (users_name ist the argument).

<p align="center">
<img src="https://github.com/Olexandr-Andriyenko/Python-learning-path/blob/main/illustrations/img16.png" width="400">
<p> 
  
When defining a function with parameters, the function expects an input of a value. It is not allowed to call the function without a value or with more than one value, otherwise the program will cancel with an error message.  
<br>
<br>  
It is also possible to write functions that have multiple parameters. It is important to verify that the number and sequence of the parameters are the same. If there is more than one parameter, they must be separated by a comma in the function definition or function call.
<br>
<br> 
Example:
```python
# We create a user-defined function with two parameters
def welcome(name, city):
    print(f"Hello: {name} ")
    print(f"Your are from: {city}")
    print("Welcome to user-defined functions")

# We create the first argument
users_name = input("Please enter your name: ")
# The second argument we generate directly inside the function call
welcome(users_name, "Berlin")  
```
What actually happens when we assign the function to a variable and then check this variable? Let's take a look at this.
```python
# We create a user-defined function with two parameters
def welcome(name, city):
    print(f"Hello: {name} ")
    print(f"Your are from: {city}")
    print("Welcome to user-defined functions")

# We create the first argument
users_name = input("Please enter your name: ")
# The second argument we generate directly inside the function call
check = welcome(users_name, "Berlin")  
print(check)
# Output is:
# Please enter your name: olex
# Hello: olex 
# Your are from: Berlin
# Welcome to user-defined functions
# None
```
Because the function has no return value, the variable "check" is empty and prints in the console "None".
<br>
<br>
Functions are often used to calculate results. To continue working with these results, the functions must output them as return values. These return values can then be stored in a variable. To generate a return value you have to use the keyword "return" inside the function body.
<br>
<br>
Example:
```python
  # Create a function which add two numbers
def addition(num_1, num_2):
    print(f"Addition of the numbers {num_1} and {num_2} started! ")
    sum = num_1 + num_2
    # Function returns the sum, which can be user for further processing
    return sum


# Generate two numbers for the input
a = 3
b = 2
# Use the function to calculate the sum of two number and save the result inside a variable
sum = addition(a, b)
# Print the calculated number which was saved in the variable "sum"
print(sum)
  
# Output is:
# Addition of the numbers 3 and 2 started! 
# 5
´´´
  
