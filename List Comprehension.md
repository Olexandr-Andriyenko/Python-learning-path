# List Comprehension

With list comprehension you can a new list from a previous list much easier.
<br>
In many other languages you don't haver access to something like this. It will will cuts down the amount of typing and makes the code a lot shorter.
<br>
<br>
So far we created a new list by using a for loop:

```python
# Example:
# Creating a new list from another
numbers = [1, 2, 3, 4, 5]
new_list = []
# Add the numbers from the first list to the new list, but increased by one
for number in numbers:
    increased_num = number + 1
    new_list.append(increased_num)
print(new_list)

# Output is:
# [2, 3, 4, 5, 6]
```

Now by using the list comprehension we will reduce the amount of code:
```python
# Example:
# Creating a new list from another
numbers = [1, 2, 3, 4, 5]
# Now we will solve the same task but with list comprehension

# List comprehension looks like this:
# new_list = [new_item for item in list]
# Let's try it:
new_list = [(number + 1) for number in numbers]
print(new_list)

# Output is:
# [2, 3, 4, 5, 6]
```

We solved the task with just one line of code!
<br>
Just because it's called "list comprehension" it doesn't mean that you can only work with lists. You can work with other sequences like strings.
<br>
Example:

```python
# An string
name = "Olexandr"
new_list = [letter for letter in name]
print(new_list)

# Output is:
# ['O', 'l', 'e', 'x', 'a', 'n', 'd', 'r']
```
