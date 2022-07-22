# Type conversion/casting

Type conversion in computer science is the conversion of one data type into another data type. A distinction is made between explicit and implicit type conversion.

## Implicit type conversion

In implicit type conversion, Python automatically converts one data type to another data type. This process does not require the participation of the programmer. With the "type()" function you can display the data type of a variable, to be more precise of an object.
<br>
<br>
Example:
```python
num_int = 20
num_float = 3.141
new_num = num_int * num_float
# Which datatype has the variable "new_num"?
print(f"Datatype of num_int ist: {type(num_int)}")
print(f"Datatype of num_float ist: {type(num_float)}")
print(f"Datatype of new_num ist: {type(new_num)}")

# Gives the output:
# Datatype of num_int ist: <class 'int'>
# Datatype of num_float ist: <class 'float'>
# Datatype of new_num ist: <class 'float'>

# The datatype of "new_num" is determined automaticlly(implicit type conversion)
```

## Explicit type conversion

In explicit type conversion, the programmer converts the data type of an variable/object to the required data type. For this purpose we use the functions which are already included in Python.

| Function      |  Description                                                    |
| ------------- | --------------------------------------------------------------- |
| int()         | Converts the specified value into an integer number.            |
| float()       | Converts the specified value into a floating point number.      |
| str()         | Converts the specified value into a string.                     | 

Often you store data in variables using the "input()" function. Never forget that the variable becomes a string variable by using the "input()" function. Strictly speaking, it is not the variable that is of type string, but the object to which the variable refers. Because the data type is string, errors can easily happen if arithmetic operators are applied to the variable.
<br>
<br>
Example:
```python
num_1 = 10
# User inputs a number
num_2 = input("Pleaser enter a number: ")
# Both numbers should be added
print(num_1 + num_2)

# Gives output:
# Traceback (most recent call last):
#  File "C:\Users\olexa\PycharmProjects\QuizGam\main.py", line 3, in <module>
#    print(num_1 + num_2)
# TypeError: unsupported operand type(s) for +: 'int' and 'str'

# The error appears because the data type of "num_2" is a String
# To avoid this error you have to use type casting
# Convert the inputed string in the datatype int or float

num_1 = 10
# Now we use the "float()" function to convert the inputed value from a string in a float data type:
num_2 = float(input("Pleaser enter a number: "))
print(num_1 + num_2)

# Gives output:
# Pleaser enter a number: 2
# 12.0
```
By type casting you can always change the data type. If you are not sure which data type a variable/object has, then you can use the "type()" function.
<br>
<br>
Example:
```python
numb_1 = 5
numb_2 = input("Enter a number: ")
# Lets check which datatypes our variables/objects have:
print(type(numb_1))
print(type(numb_2))

# Gives output:
# Enter a number: 2
# <class 'int'>
# <class 'str'>

# What will happen if we multiply the two variables together?
print(numb_1 * numb_2)

# Gives Output:
# 22222

# The output is "22222" because numb_2 is a string and we multiply this string with 5 which gives us five times the string 2
# Actually we only have quintupled the String "2" which is saved in numb_2

# If we convert the numb_2 in a integer we can get the result "10" because we multiply two numbers and not a number with a string
numb_2 = int(numb_2)
print(numb_1 * numb_2)

# Gives Output:
# 10
```
It is important to note that data loss can also result from type casting. This often happens when converting a float number to an integer number (the numbers after the decimal point are neglected).
<br>
<br>
Example:
```python
a = 3.2
b = 3.8
c = 1.9999
print(int(a))
print(int(b))
print(int(c))

# Gives output:
3
3
1

# Data loss happend!
```
In implicit type conversion, python interpreter automatically converts one data type to another data type.In this Type Conversion the python interpreter converts lower datatype to higher datatype to avoid data loss.
