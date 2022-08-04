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
