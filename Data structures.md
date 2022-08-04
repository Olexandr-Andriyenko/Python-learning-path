# Data structures

Data structures can be imagined as structures that hold some data together. In other words, they are used to store a collection of related data. There are three built-in data structures in Python - lists, tuples, and dictionaries. We will see how each of these three data structures can be used and how they simplify our lives at programing.

## Lists

A list is a data structure that contains an ordered collection of objects (variables are references to objects). This means that in a list you can store a sequence (a sequence) of objects (variables).You can imagine it like a shopping list, which is a list of things to buy, except that on your shopping list you probably have the things on separate lines. While in Python commas must be placed between the objects.
<br>
<br>
A variable must be surrounded by square brackets so that Python recognizes it as a list. Once you have created a list, you can add objects to it, remove them from it or search for specific objects in it. 

### Create lists:

In Python programming, a list is created by enclosing all elements (items) in square brackets, separated by commas.
It can contain any number of elements and they can be of different types (integer, float, string, etc.).



```python
# Creat an empty list
shopping_list_empty = []
# Creat a list with elements/objects of the same datatype
shopping_list_filled = ["Apple", "Sugar", "Flour"]
# Creat a list with elements/objects with different datatypes
shopping_list_filled_int_strg = ["42", "People"]
# 

```

### Access list elements:

We can use the index operator "[]" to access an element in a list. In Python, indexes start at 0, so a list with 3 elements has an index from 0 to 2.

```python
shopping_list_empty = []
shopping_list_filled = ["Apple", "Sugar", "Flour"]
shopping_list_filled_int_strg = ["42", "People"]
# Access elements
print(shopping_list_filled[0])
print(shopping_list_filled[1])
print(shopping_list_filled[2])
# Like strings, a negative indecision can be used
print(shopping_list_filled_int_strg[-1])
print(shopping_list_filled_int_strg[-2])

# Output is:
# Apple
# Sugar
# Flour
# People
# 42

```

We can access a range/interval of elements in a list by using the slicing operator ":".

```python
shopping_list_filled = ["Apple", "Sugar", "Flour", "Oil", "Bread", "Milk"]
# Access elements by using slicing operator:
print(shopping_list_filled[2:5])

# Output is:
# ['Flour', 'Oil', 'Bread']

```

### Add and change elements:

Lists are changeable, which means their elements can be changed, unlike strings or tuples. We can use the assignment operator "=" to change an element or a set of elements.


```python
shopping_list_filled = ["Apple", "Sugar", "Flour", "Oil", "Bread", "Milk"]
# Change Sugar to Salt and Bread to Cake
shopping_list_filled[1] = "Salt"
shopping_list_filled[4] = "Cake"
print(shopping_list_filled)

# Output is:
# ['Apple', 'Salt', 'Flour', 'Oil', 'Cake', 'Milk']

```

Unfortunately, at this point it is necessary to use a future topic. We can add an element to a list by using the append() method or add multiple elements using extend() method. What exactly methods are is explained in more detail in the chapter "Object Oriented Programming". For now it is enough to be able to use just the two commands if you want to extend your list. Methods are always introduced with the dot operator. Use the following examples as a guide:

```python
shopping_list_filled = ["Apple", "Sugar", "Flour", "Oil", "Bread", "Milk"]
# Add a element to the list
shopping_list_filled.append("New Element")
shopping_list_filled.extend(["One more Element", "Last Element"])
print(shopping_list_filled)


# Output is:
# ['Apple', 'Sugar', 'Flour', 'Oil', 'Bread', 'Milk', 'New Element', 'One more Element', 'Last Element']

```

The "insert" method can be used to add elements to a specific position in the list:

```python
shopping_list_filled = ["Apple", "Sugar"]
# Add element after the index 0
shopping_list_filled.insert(1, "New Element")
print(shopping_list_filled)
# Add multiple elements after index 1 with the slicing operator
shopping_list_filled[2:2]=["With", "Slicing"]
print(shopping_list_filled)

# Output is:
# ['Apple', 'New Element', 'Sugar']
# ['Apple', 'New Element', 'With', 'Slicing', 'Sugar']

```


### List concatenation

We can also use "+" operator to combine two lists. This is also called concatenation.

```python
shopping_list_filled = ["Apple", "Sugar", "Flour", "Oil", "Bread", "Milk"]
price = [1.95, 0.35, 0.45, 2.95, 1.45, 0.95]
print(shopping_list_filled + price)

# Output is:
# ['Apple', 'Sugar', 'Flour', 'Oil', 'Bread', 'Milk', 1.95, 0.35, 0.45, 2.95, 1.45, 0.95]
```

The "*" operator repeats a list for the specified number of times.

```python
shopping_list_filled = ["Apple", "Sugar"]
print(3 * shopping_list_filled)

# Output is:
# ['Apple', 'Sugar', 'Apple', 'Sugar', 'Apple', 'Sugar']

```

### Delete elements


We can delete one or more elements from a list with the keyword "del". It can even delete the list completely.

```python
shopping_list_filled = ["Apple", "Sugar", "Flour", "Oil", "Bread", "Milk"]
# Delete one element
del shopping_list_filled[1]
print(shopping_list_filled)
# Delete multiple elements
del shopping_list_filled[1:3]
print(shopping_list_filled)
# Delete whole list
del shopping_list_filled
print(shopping_list_filled)

# Output is:
# ['Apple', 'Flour', 'Oil', 'Bread', 'Milk']
# ['Apple', 'Bread', 'Milk']
# Traceback (most recent call last):
#   File "<string>", line 10, in <module>
# NameError: name 'shopping_list_filled' is not defined

```

This was a short overview of some important functionalities of lists. Depending on what you want to do with your list, you can use the Python documentation about lists. Because you don't have to know all the keywords by memory.
<br>
<br>
If you want to know all the methods defined for list objects, then get the details with "help(list)".

## Tuples

Tuples are just like lists except that they are unchanging like strings, this means you cannot modify tuples. Tuples are defined by specifying comma separated objects inside a normal pair of parentheses. Tuples are usually needed whenever a statement or user-defined function can be sure that the collection of values used will not change.
<br>
<br>
Once you enter a value, it remains the same until the end of the program. This is why this data structure is always useful when the values do not change.

### Create a tuple

```python
# Without elements
tuple_1 = ()
# With elements
tuple_2 = (1, 2 ,3 ,"a", "b", "c", True, "42a")
# If tuple have only one element it is IMPORTAN to use a comma, or python do not recognizes this object as a tuple
tuple_3 = ("One element",)
# At this"tuple" we do not use a comma, so it is not a tuple but a string
tuple_4 = ("This is not a tuple!")
print(type(tuple_4))
print(tuple_2)

# Output is:
# <class 'str'>
# (1, 2, 3, 'a', 'b', 'c', True, '42a')

```

### Access tuple elements:


Using the square brackets, it is possible to access the corresponding value by index. Also like with lists the index starts at 0.

```python
tuple_2 = (1, 2 ,3 ,"a", "b", "c", True, "42a")
# Access elements
print(tuple_2[0])
print(tuple_2[6])
print(tuple_2[3:6])

Output is:
# 1
# True
# ('a', 'b', 'c')

```

### Pack and unpack a tuple:


In Python, there is a very powerful tuple assignment function that assigns the right side of values to the left side. In another way, it is called unpacking a tuple of values into a variable. When packing we put values into a new tuple, while when unpacking we extract these values into a single variable.

```python

x = ("Guru99", 20, "Education")    # tuple packing
(company, emp, profile) = x    # tuple unpacking
print(company)
print(emp)
print(profile)

# Output is:
# Guru99
# 20
# Education

```
