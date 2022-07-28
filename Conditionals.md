# Conditionals

Control structures are used to determine which parts of the code should be executed. You will hardly be able to write a useful program without any kind of conditions. As a rule, every program has lots of instructions which are to be executed only in certain situations.
<br>
<br>
Conditionals may be best illustrated with a flowchart. Take a look at the following example:

<p align="center">
<img src="https://github.com/Olexandr-Andriyenko/Python-learning-path/blob/main/illustrations/img17.png" width="200">
<p> 

Such a flow as shown in the flowchart can only be created by conditionals. The diamond in the flowchart indicates a decision point which can be answered with true or false. Depending on true or false the program runs differently. With this tool we can make our programs much more flexible in terms of decisions.

  
  
## If statement
  
Such structures are implemented in most programming languages by the if statement. An "if statement" is written by using the if keyword, then the condition is written which should be checked. The condition can be either "True" or "False", so it is a Boolean value. Inside the indentation are statements which should be executed if the condition is true. If the condition is not "True" nothing happens and the program jumps to the next lines after the if statement. Let's recreate the flowchart shown above:
<br>
<br>
  
```python
print("Lamp doesn't work!")
# Ask the user whether the lamp is plugged
lamp_plugged = input("Is the lamp plugged in? (Yes / No): ")
# Check the users answer
if lamp_plugged == "No":
    print("Plug in the lamp!")


print("The lamp is plugged!")
# Ask the user whether the bulb is burned out
bulb_burned = input("Is the buld burned out? (Yes / No): ")
# Check users answer
if bulb_burned == "Yes":
    print("Replace the bulb!")

print("Repair the lamp!")  
```
Try different inputs by yourself and see what happens. But do not forget that only "Yes" or "No" can be accepted as input. How to force certain inputs follows later.

<br>
<br>
In general, the structure of an if statement looks like this:
 
<p align="center">
<img src="https://github.com/Olexandr-Andriyenko/Python-learning-path/blob/main/illustrations/img18.png" width="200">
<p>   
 
## If-else statement
  
The else is an extremely powerful word. This means that if none of the previous conditions are true, the code of the else statement will be executed. So here you can execute the code that should always run if the other conditions are not true.
<br>
<br>
In a flowchart it looks like this:
  
<p align="center">
<img src="https://github.com/Olexandr-Andriyenko/Python-learning-path/blob/main/illustrations/img19.png" width="250">
<p>   

<br>  
Example:
<br>
<br>
  
```python
# Ask users age
age = int(input("Enter your age: "))
# Check whether the user is minumum 18 years old or less
if age >= 18:
    print("users age is minimum 18 years old!")
else:
    print("Users age is over 18!")  
```
  
## Elif keyword

Another way to extend the if statement is provided by elif branches in Python. By using this we can even check multiple conditions within one if statement. So the "elif" stands for else-if and allows us to check another condition if the previous one was not true.  
<br>
<br>
In a flowchart it looks like this:

<p align="center">
<img src="https://github.com/Olexandr-Andriyenko/Python-learning-path/blob/main/illustrations/img20.png" width="450">
<p>   
