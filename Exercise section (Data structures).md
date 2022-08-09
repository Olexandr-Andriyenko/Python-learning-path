# Exercise section (Data structures)

### 1. Assignment

Merge two previously defined lists into one and return it.<br>
Example:

```python
list_01 = [3,8,9,2]
list_02 = [4,2]
# Output should look like:
[3,8,9,2,4,2]

```

<details open>
<summary>Solution</summary>

  ```python
 # Create two lists
list_01 = [3,8,9,2]
list_02 = [4,2]

# Use list concatenation
print(list_01 + list_02)

# Output is:
# [3, 8, 9, 2, 4, 2]  
 ``` 
  
</details>


### 2. Assignment

Remove a specific element from a specified list.
Note: If an element appears more than once, it should be removed everywhere.

Example:

```python
list_01 = [3,8,9,5,1,3,6,4]
# Remove "3"

# Output should look like:
[8,9,5,1,6,4]

```

<details open>
<summary>Solution</summary>

  ```python
# Create a list
list_01 = [3,8,9,5,1,3,6,4]
# Variable which corresponds with the element position inside the list
index = 0
# Loop the list
for value in list_01:
    # If value is three the element at the index position
    if value == 3:
        del list_01[index]
    # the next element is at a "higher" index
    index += 1

print(list_01)

# By searching the python documentation u can find easier methods to remove an element
# Try to use the "remove" method !

# Output is:
# [8, 9, 5, 1, 6, 4]
 ``` 

### 3. Assignment
  
Separate a list at an index into two partial lists.
Note:  If a list is to be separated at index 0, then the first list is list is empty.
  
<details open>
<summary>Solution</summary>

  ```python
# Create a list
list_given = [3,8,9,5,1,3,6,4]
# Ask the user at which index to split the list
index = int(input("Index: "))
# Spliting with "range" function
# Usin the "len" function to find the last index out
list_1 = list_given[0:index]
list_2 = list_given[index:len(list_given)]
# Print the lists
print(list_1)
print(list_2)

# Output is:
# Index: 3
# [3, 8, 9]
# [5, 1, 3, 6, 4]
  
 ``` 

  ### 4. Assignment
  
Reverse a specified list.<br>
Note: list.reverse() is nice, but not the point of this task!
  
  
<details open>
<summary>Solution</summary>

  ```python

# Create a list
list_given = [3,8,9,5,1,3,6,4]
# Empty list where to store elements but reverse
list_reverse = []
# Start with the last index of the list
list_length = len(list_given) - 1

while list_length != -1:
    # Add the elements to reverse list
    list_reverse.append(list_given[list_length])
    list_length -= 1

print(list_reverse)
  
# Output is:
# [4, 6, 3, 1, 5, 9, 8, 3]
  
 ``` 
