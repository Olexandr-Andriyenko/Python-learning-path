# Loops

Loops are needed to repeatedly execute a block of code, also known as a loop body. Using loops we can have action executed several times until a specified condition is met. There are two types of loops in Python:<br>
- while loop
- for loop
<br>
The loop header determines the condition of the loop. The program code that is repeated in a loop is also called the loop body. As soon as the loop body has been processed, the condition can cause a jump to the beginning of the loop, so that the loop body is processed from the beginning.
<br>
<br>
Most often, loops work with variables that change during the process of the loop. If the value of a variable matches the defined condition in a While loop, the program terminates the loop. The variable can also be a counter that defines how long the loop should be processed.

## While loop

The idea behind Python while loops is that they execute one or more statements until a condition is true. Then the loop is terminated.
<br
The while loop is illustrated in the following flowchart:
    
<p align="center">
<img src="https://github.com/Olexandr-Andriyenko/Python-learning-path/blob/main/illustrations/img21.png" width="200">
<p>  
    
Example:
    
```python
x = 0
while x < 10: # This is the condition
    # Here is the loop body         
    x += 1
    print(x)
             
# After loop body
print("while loop finished!")

# Output is:
# 1
# 2
# 3
# 4
# 5
# 6
# 7
# 8
# 9
# 10          
# while loop finished!             
```
As like with the conditions you can use the "else" keyword for an alternative "way". Look at the illustration below for the while-else-loop:
             
<p align="center">
<img src="https://github.com/Olexandr-Andriyenko/Python-learning-path/blob/main/illustrations/img22.png" width="200">
<p> 

Example:
    
```python
 x = 0
while x < 10:  # This is the condition
    # Here is the loop body
    x += 1
    print(x)
else:
    print("inside else")
# After loop body
print("while loop finished!")

# Output is:
# 1
# 2
# 3
# 4
# 5
# 6
# 7
# 8
# 9
# 10
# inside else               
# while loop finished!   
```

In Python, the "break" statement gives you the ability to exit a loop when an external condition is triggered. You place the break statement within the code block below your loop statement, usually after a conditional if statement.    
<br>
<br>
Example:
```python
x = 0
while x < 10:  # This is the condition
    # Here is the loop body
    x += 1
    print(x)
    # If x equals 5, loop ends 
    if x == 5:
        break
else:
    print("inside else")
# After loop body
print("while loop finished!")

# Output is:
# 1
# 2
# 3
# 4
# 5
# while loop finished!    
```
