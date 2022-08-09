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

