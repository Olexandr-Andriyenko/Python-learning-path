# Operators

Operatoen are certain symbols that perform various actions. In mathematics, an operator refers to a formula character that performs a specific arithmetic operation. Programming is similar, but there are more than just simple calculation operators. The value that the operator operates on is called the operand. Let's go through all the necessary operators step by step.

## Arithmetic operators

Arithmetic operators are used to perform mathematical operations.

| Operator                          | Meaning                             | Example                                 |
| ----------------------------------|-------------------------------------|---------------------------------------- |
|  +                                | Add two operands                    | x + y                                   |
|  -                                | Subtract right operand from the left| x - y                                   |
|  *                                | Multiply two operands               | x * y                                   |
|  /                                | Divide left operand by the right one| x / y                                   |
|  %                                | Modulus (remainder of the division of left operand by the right)| x % y       |
|  //                               | Floor division (division that results into whole number) | x - y              |
|  **                               | Exponent                            | x ** n                                  |

Let's take a closer look at examples of arithmetic operations.

Example:
```python
# Create some variables for the calculations
x = 5
y = 3
n = 2
# Addition
print(x + y)
# Substraction
print(x - y)
# Multiplication
print(x * y)
# Division
print(x / y)
# Modulus
print(x % y)
# Floor division
print( x // y)
# Exponent
print(x ** n)
# The calculations gives the following outputs
# 8
# 2
# 15
# 1.6666666666666667
# 2
# 1
# 25
```

## Comparison  operators

Comparison operators are used to compare values. The output when using these operators can be either "True" or "False".

| Operator                          | Meaning                             | Example                                  |
| ----------------------------------|-------------------------------------|----------------------------------------- |
|    >                              | Greater than                        | x > y                                    |
|  <                                | Less than                           | x < y                                    |
|  ==                               | Equal to                            | x == y                                   |
|  !=                               | Not equal to                        | x != y                                   |
|  >=                               | Greater than or equal to            | x >= y                                   |
|  <=                               | Less than or equal to               | x <= y                                   |


Let's take a closer look at examples of comparison operations.

Example:
```python
# Create some variables for the operations
x = 5
y = 3
# Greater than
print(x > y)
# Less than
print(x < y)
# Equal to
print(x == y)
# Not Equal to
print(x != y)
# Greater than or equal to
print(x >= y)
# Less than or equal to
print( x <= y)
# The operations gives the following outputs
# True
# False
# False
# True
# True
# False
```

## Logical  operators

Python supports the logical operators "and", "or" and "not". Just like comparison operators, logical operators result in "True" or "False" after evaluation. The values "True" or "False" are also called Boolean values. The corresponding variables which are linked to each other by logical operators and are affected with boolean values are called boolean expressions. Thus, the logical operators allow a specific linkage between the variables. So called truth tables are often used to illustrate the evaluation of two variables that are linked together by logical operators.

### Logical "and"

| Variable x    | Variable y    | x and y   |
| ------------- | ------------- | --------- |
| True          | False         | False     |
| False         | True          | False     |
| True          | True          | True      |
| False         | False         | False     |

### Logical "or"

| Variable x    | Variable y    | x or y    |
| ------------- | ------------- | --------- |
| True          | False         | True      |
| False         | True          | True      |
| True          | True          | True      |
| False         | False         | False     |

### Logical "not"

| Variable x    | not x         | 
| ------------- | ------------- | 
| True          | False         | 
| False         | True          | 

Example:
```python
# Create some variables for the calculations
x = True
y = False
# Logical and
print(x and y)
# Logical or
print(x or y)
# Logical not
print(not y)
# Combination of logical operators
print((x and y) or (x or y))
print(not(x or y))
# The operations gives the following outputs
# False
# True
# True
# True
# False
```
## Identity  operators

It was already mentioned that variables actually refer to objects. The actual data is stored in objects. Using the identity operators it is possible to find out if the locations of objects in the memory match.


| Operator      | Description                                                                                  |
| ------------- | -------------------------------------------------------------------------------------------- |
| is            | Returns "True" if both variables are the same object                                         | 
| is not        | Returns "True" if both variables are not the same object                                     | 


Example:
```python
# Create some variables for the calculations
n1 = "alex"
n2 = "peter"
n3 = "chayenne"
n4 = "alex"
n = n1, n3
# Check the variable n
print(n)
# Let's try the operator "in"
print(n3 is n)
print(n2 is n)
print(n1 is n4)
# Let's try the operator "not in"
print(n1 is not n)
print(n2 is not n)

# The operations gives the following outputs
('alex', 'chayenne')
False
False
True
True
True
```

The variable "n1" and "n2" return the value "False", which means that the two variables reference not the same object. By using the "id()" function you can explain this behavior. The function "id()" returns a unique integer value for any object. This value equals the address where the object is stored in memory.

```python
# Create some variables for the calculations
n1 = "alex"
n2 = "peter"
n3 = "chayenne"
n4 = "alex"

# Lets find out the adress of each variable
print(id(n1))
print(id(n2))
print(id(n3))
print(id(n4))
# The operations gives the following outputs
# 139943243577520
# 139943243577648
# 139943243577840
# 139943243577520
# The first address is equal to the fourth address, these two variables reference the same object in memory 
# (this is why we have the value "True" using the "in" operator)
```

Don't confuse the both operators "in" and "=="! There is a big difference between the two operators. The "is" operator will return "True" if two variables point to the same object. The "==" operator will return "True", if the values assigned to the variables are identical.
<br>
To illustrate the difference between "is" and "==" watch the following example:

```python
# Equality operator
a = 10
b = 10
print(a == b)

# Gives the output "True" because the value of the variables is identical
# Lets check the adress of the objects which refered by the variables
print(id(a))
print(id(b))
# Gives the output: "9789280" and "9789280"
# Both "a" and "b" is pointed to the same object

# That is why the "is" operator should output "True"
print(a is b)

# Lets increase the variable "a" by 1
a = a + 1

# Now the variable has got a different id and value and does not reference to the same object as b
print(id(a))
print(a is b)
print(a == b)
# Output is:
# 2363502494256
# False
# False
```

<p align="center">
<img src="https://github.com/Olexandr-Andriyenko/Python-learning-path/blob/main/illustrations/img11.png" width="700">
<p>

## Membership  operators

The membership operators are used to detect if variables are in a sequence (list, tuple, string, and dictionary) or not. A sequence is a data type that contains a sequence of similar or different elements. You already know a sequence, which is called a string. In the future you will get to know other sequences like lists, tuples and directories. The elements of a sequence have a defined order and so they can be accessed by indices. 
<br>
Let's have a look at how to address the single elements of a string.

<p align="center">
<img src="https://github.com/Olexandr-Andriyenko/Python-learning-path/blob/main/illustrations/img12.png" width="450">
<p>
  
You can see that the characters of a string are numbered from left to right starting with 0. From the back (right) you start counting with -1. Each character of a string can be addressed clearly by this way, they can index with square brackets, as you can see in the following example: 
 
```python
txt = "Hello World"
# Lets address and print single characters
  print(txt[0])
  print(txt[1])
  print(txt[2])
  print(txt[3])
  print(txt[4])
# Output is:
  # H
  # e
  # l
  # l
  # o
# Lets address and print other single characters
  print(txt[-5])
  print(txt[-4])
  print(txt[-3])
  print(txt[-2])
  print(txt[-1])
# Output is:
  # W
  # o
  # r
  # l
  # d
```

In this context, let's take a closer look at the membership operators.
  
| Operator      | Description                                                                                  |
| ------------- | -------------------------------------------------------------------------------------------- |
| in            | Returns "True" if a sequence with the specified value is present in the object               | 
| not in        | Returns "True" if a sequence with the specified value is not present in the object           | 
  
Let's look at an example:  
  
```python
txt = "Hello World"
print("H" in txt)
print("W" not in txt)
print("X" in txt) 
print("k" not in txt) 
# Output is:
# True
# False
# False
# True
```
In this code, "H" is present in the sequence (string), so "True" is returned. Similarly, "W" is present in "txt", so "True" is returned again because " not in" is used, and so on.
  
## Assignment   operators
  
Assignment operators are used to assign values to variables.
  
  
| Operator      | Example       | Same as      |
| ------------- | ------------- | ------------ |
| =             | x = 5         | x = 5        |
|  +            | x += 3        | x = x + 3    |
| -=            | x -= 3        | x = x - 3    |
| *=            | x *= 2        | x = x * 2    |
| /=            | x /= 2        | x = x / 2    |
| %=            | x %= 3        | x = x % 3    |
| //=           | x //= 2       | x = x // 2   |
| **=           | x **= 2       | x = x ** 2   |

Example:
  
```python
# Create variable for operation
x = 2
print(x)
# Use the assignment operations
x = 2
x += 3
print(x)
x = 2
x -= 3
print(x)
x = 2
x *= 2
print(x)
x = 2
x /= 2
print(x)
x = 2
x %= 3
print(x)
x = 2
x //= 2
print(x)
x = 2
x **= 2
print(x)  
# Output is:
# 2
# 5
# -1
# 4
# 1.0
# 2
# 1
# 4
```

There is one more type of operator which we will not cover here because it is not relevant for beginners. These are "bitwise operators" that allow us to change binary strings at the bit level. These few operations are required to work with device drivers, low-level graphics, cryptography, and network communications. These operators are easy to learn, but not necessary if you do not work with bits directly.
