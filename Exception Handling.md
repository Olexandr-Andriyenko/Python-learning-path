# Exception Handling

Up to now, it was simplified to assume that the user had made correct entries using "input" function. If the user makes a wrong input after a prompt, the program will exit with an error message. A wrong input could be a text while a number is needed. Now we will learn how to intercept and avoid errors.
<br>
<br>
Consider the following example:
<br>

```python
# Input
num = input("Please enter a whole number: ")

# Using the input function we will get a string
# Now we have to converts the string to integer
num = int(num)

# Lets print the number in the console
print(f"You have entered the following number: {num}")
print("End of the program")

# Let's assume that we pass a 5 as input.
# The output will be:
# You have entered the following number: 5
# End of the program

# But what happens if we do not enter a number?
# Let's look at the following input:
# Let's assume that we pass a 5abc as input.

# The output will be:
#-------------------------------------------------------------------
# Traceback (most recent call last):
# File "<string>", line 7, in <module>
# ValueError: invalid literal for int() with base 10: '5abc'
#-------------------------------------------------------------------
# We are informed that an error has occurred and where it is located.
# The program is canceled

```

## Keywords "try" and "except"

How can we catch such an error as in the example above and avoid the termination of the program? To do this, you must first find out which part of the program is sensitive to such an error. To do this, you must first find out which part of the program is sensitive to such an error. We achieve this by using the keyword "try" and "except".
<br>
<br>
The keyword try is used to initiate exception handling. If the try block does not run without errors, the error can be caught by using an except statement, in this case, all statements of the given except block are executed.
<br>
<br>
Let's add "try" and "except" to the previous example:

```python
# Input
num = input("Please enter a whole number: ")

# Using the input function we will get a string
# Now we have to converts the string to integer
try:
  num = int(num)
  print("Converting from string to int successful")
  print(f"You have entered the following number: {num}")
except:
  print("Converting string in int failed")

# Lets print the number in the console
print("End of the program")

# Let's assume that we pass a 5abc as input.
# The output will be:
# Please enter a whole number: 5abc
# Converting string in int failed
# End of the program

```

Only the critical line is embedded in the exception handling. So you should think about which parts of your program are sensitive to errors. A command prompt is such a critical point.

## While loop for better exception handling

By using a "while" loop, the input can be repeated until the user makes the correct input. Let's put this into practice:


```python
# Variable for loop condition
error = True
# Use while loop to reapet input until no error
while error:
  # Input
  num = input("Please enter a whole number: ")

  # Using the input function we will get a string
  # Now we have to converts the string to integer
  try:
    num = int(num)
    print("Converting from string to int successful")
    print(f"You have entered the following number: {num}")
    error = False
  except:
    print("Converting string in int failed")

# Lets print the number in the console
print("End of the program")


# The output will be:
# Please enter a whole number: 5abc
# Converting string in int failed
# Please enter a whole number: 5aaa
# Converting string in int failed
# Please enter a whole number: 5
# Converting from string to int successful
# You have entered the following number: 5
# End of the program

```

## Keyword "finally"

The "finally" keyword lets you execute code at the end of the block, whether errors occurred or not. Code inside this block will be executed at the end of the exception handling in any case, no matter if the try block was executed without errors or an exception occurred. Lets add "finally" to previous example:

```python
# Variable for loop condition
error = True
# Use while loop to reapet input until no error
while error:
  # Input
  num = input("Please enter a whole number: ")

  # Using the input function we will get a string
  # Now we have to converts the string to integer
  try:
    num = int(num)
    print("Converting from string to int successful")
    print(f"You have entered the following number: {num}")
    error = False
  except:
    print("Converting string in int failed")
  finally:
    print("----------------------------------------------------------")
    print("This section inside 'finally' will be alwys executed")
    print("----------------------------------------------------------")

# Lets print the number in the console
print("End of the program")

# The output will be:
# Please enter a whole number: a
# Converting string in int failed
# ----------------------------------------------------------
# This section inside 'finally' will be alwys executed
# ----------------------------------------------------------
# Please enter a whole number: 5
# Converting from string to int successful
# You have entered the following number: 5
# ----------------------------------------------------------
# This section inside 'finally' will be alwys executed
# ----------------------------------------------------------
# End of the program

```

## Keyword "else"

If you use else, you can write code that will only be executed if no exceptions or errors have occurred.
<br>
<br>
Example:

```python
try:
  print("Hello my name is Olexandr")
except:
  print("Something went wrong")
else:
  print("Nothing went wrong")
```


## Summary




<p align="center">
<img src="https://github.com/Olexandr-Andriyenko/Python-learning-path/blob/main/illustrations/img26.png" width="750">
<p>  
