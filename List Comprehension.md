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

# Other example with the range() function
new_list = [(num + 1) for num in range(1, 5)]
print(new_list)

# Output is:
# ['O', 'l', 'e', 'x', 'a', 'n', 'd', 'r']
# [2, 4, 6, 8]
```

## Conditional List Comprehension

We can use conditionals in our list comprehension.
<br>
It will looks like this:

```python
new_list = [new_item for item in list if test]
```

A new "item" will be added to the "new_list" only if the condition "test" is true.
<br>
Example:

```python
# Using conditional list comprehension
names = ["Alex", "Beth", "Dave", "Eleanor", "Freddie"]
# Add only names to a new list which are up of four letters or less
new_names = [name for name in names if len(name) <= 4]
print(new_names)
# Create a new list of the names with five or more letters and turn each name to the uppercase version
names_uppercase = [name.upper() for name in names if len(name) >= 5]
print(names_uppercase)

# Output is:
# ['Alex', 'Beth', 'Dave']
# ['ELEANOR', 'FREDDIE']
```

## Exercise

1. You are going to write a liste comprehension to creaate a new list called `squared_numbers`.
This new list should contain every number in the list `numbers = [1, 1, 2, 3, 5, 8, 13, 21, 34, 55]` but each number should be squared.

<details>
 <summary>Solution</summary>

```python
numbers = [1, 1, 2, 3, 5, 8, 13, 21, 34, 55]
squared_numbers = [(num ** 2) for num in numbers]
print(squared_numbers)

# Output is:
# [1, 1, 4, 9, 25, 64, 169, 441, 1156, 3025]
```
    
</details>

2. You are going to write a list comprehension to create a new list called `result`. This new list should only contain
the even numbers from the list `numbers = [1, 1, 2, 3, 5, 8, 13, 21, 34, 55]`.

<details>
 <summary>Solution</summary>

```python
numbers = [1, 1, 2, 3, 5, 8, 13, 21, 34, 55]
result = [num for num in numbers if (num % 2 == 0)]
print(result)
    
# Output is:
# [2, 8, 34]
```
    
</details>

3. Take a look inside `file1.txt` and `file2.txt`. They each contain a bunch of numbers, each number on a new line.
You are going to create a list called `result` which contains the numbers that are common in both files.

</details>


<details>
 <summary>Files</summary>
    
<br>
file1.txt:
<br>
    
```
3
6
5
8
33
12
7
4
72
2
42
13

```

<br>
file2.txt:
<br>
    
```
3
6
13
5
7
89
12
3
33
34
1
344
42

```
    
</details>