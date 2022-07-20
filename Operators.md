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
