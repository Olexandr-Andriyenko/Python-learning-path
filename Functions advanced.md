# Functions advanced

This chapter describes more concepts from the topic Functions.

## Recursion

A function is recursive if it calls itself, that is, if a call to the same function exists in its body.
<br>
Let's look at this concept with a simple example:

- We want to calculate the factorial of a number by recursion

<p align="left">
<img src="https://github.com/Olexandr-Andriyenko/Python-learning-path/blob/main/illustrations/img50.PNG" width="400">
<p> 

```python
# Algorithm for faculty calculation
def recursive_function(num):
    if num == 0 or num == 1:
        return 1
    else:
        solution = num * recursive_function(num - 1)
        return solution


print(recursive_function(3))

# Output is:
# 6
```
If you like to visualize this code you can use this tool:
<br>
https://pythontutor.com/render.html#mode=display

Recursive functions use something called “the call stack.” When a program calls a function, that function goes on top of the call stack. This is similar to a stack of books. You add things one at a time. Then, when you are ready to take something off, you always take off the top item.    

<p align="left">
<img src="https://github.com/Olexandr-Andriyenko/Python-learning-path/blob/main/illustrations/img52.PNG" width="700">
<p> 

The following mechanism helps us understand what is happening:

- Each time your code makes a function call, Python puts information on the “call stack”, including
    - All values of parameters and local variables
    - The location in the code where the function call is being made.
- Python then makes the function call, switching execution to the start of the called function.
- This function in turn can make additional, potentially recursive, function calls, adding information to the top of the stack each time.
- When a function ends, Python looks at the top of the stack, and
    - restores the values of the local variables and parameters of the most recent calling function,
    - removes this information from the top of the stack,
    - inserts the returned value of the called function (if any) in the appropriate location of the calling function’s code, and
    - continues execution from the location where the call was made.
    
    
    
    
    
    
Another example ist the Fibonacci sequence:
    
<p align="left">
<img src="https://github.com/Olexandr-Andriyenko/Python-learning-path/blob/main/illustrations/img51.PNG" width="300">
<p> 

```python
def fib(num):
    if num == 0:
        return 0
    elif num == 1:
        return 1
    else:
        return fib(num - 1) + fib(num - 2)


num = 20
for index in range(num):
    print(fib(index))

```

Lets write a Python program to calculate the sum of a list of numbers, of course by using the concept of recursion:

```python
def sum_num(num_list):
    if len(num_list) == 1:
        return num_list[0]
    else:
        return num_list[0] + sum_num(num_list[1:])

# Given list
num_list = [1, 4, 3, 10, 7, 6]
print(sum_num(num_list))
```

## Default parameters in functions
    
When you define a function, you can specify a default value for each parameter.
<br>
By defining parameters in the definition, a variable number of parameters is possible. It is important that the unnamed parameters are placed before the named parameters.
<br>
To specify default values for parameters, you use the following syntax:

```python
def function_name(param_1, param_2 = value_2, param_3 = value_3):
```

When you call a function and pass an argument to the parameter that has a default value, the function will use that argument instead of the default value.
However, if you don’t pass the argument, the function will use the default value.
<br>

Example:

```python
def welcome(name, message='Hi'):
    return f"{message} {name}"

message = welcome("Olex")
print(message)

# Output is:
# Hi Olex

```
The following calls the welcome() function and passes the two arguments:

```python
def welcome(name, message='Hi'):
    return f"{message} {name}"

message = welcome("Olex", message="Hello")
print(message)

# Output is:
# Hello Olex
```

One more example:
<br>
Calculation of the capacity of an parallel-plate capacitor

<p align="left">
<img src="https://github.com/Olexandr-Andriyenko/Python-learning-path/blob/main/illustrations/img53.png" width="250">
<p> 

```python

def capacity(area, distance, permittivity, vacuum_permittivity = 8.854 * 10 ** (-12) ):
    capacity_value = permittivity * vacuum_permittivity * area / distance
    return capacity_value

solution = capacity(area=0.9, distance=0.0025, permittivity=1)
print(f"The capacity is {solution} Farad")

# Output is:
# The capacity is 3.1874399999999995e-09 Farad
```

## Multiple return values in functions

Unlike many other programming languages, functions in Python can return more than one return value. For example, a tuple or a list can be returned.
<br>

Example:

```python
def capacity(area, distance, permittivity, vacuum_permittivity=8.854 * 10 ** (-12), volatege=0):
    capacity_value = permittivity * vacuum_permittivity * area / distance
    if volatege > 0:
        # Calculate the energy
        energy = capacity_value * volatege
    return capacity_value, energy


capacity_value, energy = capacity(area=0.9, distance=0.0025, permittivity=1, volatege=6)
print(f"The capacity is {capacity_value} Farad")
print(f"The capacity is {energy} Coulomb")

# Output is:
# The capacity is 3.1874399999999995e-09 Farad
# The capacity is 1.912464e-08 Coulomb

```

## Global and Local variables
    
In Python, a variable declared outside of the function is known as a global variable. This means that a global variable can be accessed inside or outside of the function.
<br>
Example:

```python
def foo():
    x = x * 2
    print(f"x inside function: {x}")


x = 42
foo()
print(f"x outside function: {x}")

```

A variable cannot be both local and global within the same block, here the function body. That is why Python considered x to be a local variable within the body. Since this local variable is now accessed before it has been defined, it meaning it has not yet received a value, the error message occurs.
<br>
<br>
However, it is possible to access global variables within a function. To do this, however, you must explicitly declare them as global using the "global" keyword:

```python
def foo():
    global x
    x = x * 2
    print(f"x inside function: {x}")


x = 42
print(f"x before function: {x}")
foo()
print(f"x outside function: {x}")

```

With this, we have eliminated the multiple meaning!
<br>
<br>

Local variables of a function cannot be accessed from outside:

```python
def foo():
    global x
    x = x * 2
    print(f"x inside function: {x}")


print(f"x inside function: {x}")

```
   
## Arbitrary Arguments

Python allows us to have the arbitrary number of arguments. This is especially useful when we are not sure in the advance that how many arguments, the function would require.
<br>
<br>
We define the arbitrary arguments while defining a function using the asterisk (*) sign.
The arguments will be stored inside a tuple!
<br>
<br>
Example:

```python
def elements(*elements):
    # Function description which can be shown by using help(elements)
    """
    This function displays the element names
    """
    # Python stores the arguments inside a tuple:
    # print(elements)
    for element in elements:
        print(element)


# Input so many arguments as we like
elements("Hydrogen", "Oxygen", "Helium", "Silicon")

# Output is:
# Hydrogen
# Oxygen
# Helium
# Silicon
```

Python can accept multiple keyword arguments, better known as **kwargs. It behaves similarly to *args, but stores the arguments in a dictionary instead of tuples:

```python
def elements(**elements):
    # Function description which can be shown by using help(elements)
    """
    This function displays the element names inside a dictionary
    """
    # Python stores the arguments inside a dictionary:
    print(elements)
    # Since **kwargs is a dictionary, you can iterate over them like any other using the .items() method:
    for index, element in elements.items():
        print(index, "=", element)

# Input so many arguments as we like
elements(element_1="Hydrogen", element_2="Oxygen", element_3="Helium", element_4="Silicon")

# Output is:
# {'element_1': 'Hydrogen', 'element_2': 'Oxygen', 'element_3': 'Helium', 'element_4': 'Silicon'}
# element_1 = Hydrogen
# element_2 = Oxygen
# element_3 = Helium
# element_4 = Silicon
```
