# Operators

Operatoen are certain symbols that perform various actions. In mathematics, an operator refers to a formula character that performs a specific arithmetic operation. Programming is similar, but there are more than just simple calculation operators. The value that the operator operates on is called the operand. Let's go through all the necessary operators step by step.

## Arithmetic operators

Arithmetic operators are used to perform mathematical operations.

| Operator                          | Meaning                             | Example                                 |
| ----------------------------------|-------------------------------------|---------------------------------------- |
| " + "                               | Add two operands                    | x + y                                   |
| " - "                               | Subtract right operand from the left| x - y                                   |
| " * "                               | Multiply two operands               | x * y                                   |
| " / "                               | Divide left operand by the right one| x / y                                   |
| " % "                               | Modulus (remainder of the division of left operand by the right)| x % y       |
| " // "                              | Floor division (division that results into whole number) | x - y              |
| " ** "                              | Exponent                            | x ** n                                  |

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
| " > "                             | Greater than                        | x > y                                    |
| " < "                             | Less than                           | x < y                                    |
| " == "                            | Equal to                            | x == y                                   |
| " != "                            | Not equal to                        | x != y                                   |
| " >= "                            | Greater than or equal to            | x >= y                                   |
| " <= "                            | Less than or equal to               | x <= y                                   |


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
| in            | Returns "True" if a sequence with the specified value is present in the object               | 
| not in        | Returns "True" if a sequence with the specified value is not present in the object           | 


Example:
```python
# Create some variables for the calculations
n1 = "alex"
n2 = "peter"
n3 = "chayenne"
n4 = "alex"
n = n1, n3
# Lets try the operator "in"
print(n3 in n)
print(n2 in n)
print(n1 in n4)
# Lets try the operator "not in"
print(n1 not in n)
print(n2 not in n)
# The operations gives the following outputs
True
False
True
False
True
```

The variable "n1" and "n2" return the value "True", which means that the two variables reference the same object. By using the "id()" function you can explain this behavior. The function "id()" returns a unique integer value for any object. This value equals the address where the object is stored in memory.

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
# The first address is equal to the fourth address, these two variables reference the same object in memory (this is why we have the value "True" using the "in" operator)
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
