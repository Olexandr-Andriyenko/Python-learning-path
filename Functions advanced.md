# Functions advanced

This chapter describes more concepts from the topic Functions.

## Recursion

A function is recursive if it calls itself, that is, if a call to the same function exists in its body.
<br>
Let's look at this concept with a simple example:

- We want to calculate the factorial of a number by recursion

<p align="left">
<img src="https://github.com/Olexandr-Andriyenko/Python-learning-path/blob/main/illustrations/img50.PNG" width="400">
<p> 

```python
# Algorithm for faculty calculation
def recursive_function(num):
    if num == 0 or num == 1:
        return 1
    else:
        solution = num * recursive_function(num - 1)
        return solution


print(recursive_function(3))

# Output is:
# 6
```
