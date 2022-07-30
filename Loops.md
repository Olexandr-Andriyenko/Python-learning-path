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
## For loop
             
             
A for statement is another looping statement that iterates over a sequence of objects, which means it iterates through each object in the sequence(lists, tuples, strings...). What you need to know right now is just that a sequence is simply an ordered sequence of individual objects.
<br>
<br>
Example:
```python
# Create a string
name = "Olexandr"
# We want to print each letter of this string using a for loop
for letter in name:
    print(letter)
    
# Output is:
# O
# l
# e
# x
# a
# n
# d
# r
```
Look at the illustration below for the for-loop:
    
<p align="center">
<img src="https://github.com/Olexandr-Andriyenko/Python-learning-path/blob/main/illustrations/img23.png" width="250">
<p>     

How the for loop is constructed:
    
<p align="center">
<img src="https://github.com/Olexandr-Andriyenko/Python-learning-path/blob/main/illustrations/img24.png" width="450">
<p>       

    
## For loop and the range() function
    
    
The range() function is a mini-program and creates numbers for you in your required range.  You specify your range in the brackets after the name of the function. Commonly this function is used together with a for loop.    
<br>
<br>
Example:
```python
for number in range(0, 10, 2):
    print(number)

Output is:
# 0
# 2
# 4
# 6
# 8 
    
```
    
In this example, the numbers from 0 to 10 were output in two steps without the 10. The first number inside the range() function is the start, the next number the end and the last number the steps. The start is included as a number but the end not. 

# Nested loops
    
Python allows to include a another loop in a loop, this is called a nested loop. In fact, this happens a lot in coding. It is called that the loops are nested, that is, one is contained in the other: just as you can put one box in another.
<br>
<br>
Example: We create a multiplication table

```python
# Creat numbers from 1 until 10
for first_num in range(1, 11):
    # Crear numbers from 1 until 10
    for sec_num in range(1, 11):
        # Multiply both numbers and print them
        multiply = first_num * sec_num
        print(f"{first_num} * {sec_num} = {multiply}")
        # Just to make it better readable we create a "line"
        if sec_num == 10:
            print("---------------")    

# Output is:    
# 1 * 1 = 1
# 1 * 2 = 2
# 1 * 3 = 3
# 1 * 4 = 4
# 1 * 5 = 5
# 1 * 6 = 6
# 1 * 7 = 7
# 1 * 8 = 8
# 1 * 9 = 9
# 1 * 10 = 10
# ---------------
# 2 * 1 = 2
# 2 * 2 = 4
# 2 * 3 = 6
# 2 * 4 = 8
# 2 * 5 = 10
# 2 * 6 = 12
# 2 * 7 = 14
# 2 * 8 = 16
# 2 * 9 = 18
# 2 * 10 = 20
# ---------------
# 3 * 1 = 3
# 3 * 2 = 6
# 3 * 3 = 9
# 3 * 4 = 12
# 3 * 5 = 15
# 3 * 6 = 18
# 3 * 7 = 21
# 3 * 8 = 24
# 3 * 9 = 27
# 3 * 10 = 30
# ---------------  
# And so on....    
````
