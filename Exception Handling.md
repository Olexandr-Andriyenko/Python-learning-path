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

```
