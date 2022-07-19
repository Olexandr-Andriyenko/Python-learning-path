# Input and output


A computer works according to the IPO principle (input-processing-output). Input data from a computer is processed by a program and then output data is generated, which is then displayed by the computer to the user. To illustrate this principle, consider the following example:
<br>
- A person enters information into a program, on the computer through the keyboard, which is available in the computer as data (input). 
- Then, inside the program, the text can be processed so that the font size is adjusted or the color of the text is changed (processing). 
- Then the user decides to print this text or display it as an image on the screen (output).

Since you are consistently dealing with the input, processing, and output of data, it is important to know how to input and output data in Python. For this we will learn two important functions "print()" and "input()".

## Output by the print() function

For the output of data there is the function called "print()". Inside the brackets a string can be entered, which will be displayed on the screen. It is important that a string is enclosed in the brackets by quotation marks. It does not matter whether double or single quotation marks are used.
<br>
<br>
Example:
```python
print("Hello world, I am a string!")
```
Gives the Output:
```
Hello world, I am a string!
```
However, you often have the case that you want to output the value of a variable. To do this, you can simply pass the variables inside the parenthesis to the print function. 
<br>
<br>
Example:
Example:
```python
name = "Chayenne"
age = 18
print(name)
print(age)
```
Gives the Output:
```
Chayenne
18
```
Within the print function a variable can also be combined with a string.
<br>
<br>
Example:
```python
name = "Chayenne"
age = 18
print("Hello my name is, " + name + " and I am" + age + " years old")
```
Gives the Output:
```
Hello my name is Chayenne, and I am 18 years old
```
You can achieve the same result without using a plus sign.
<br>
<br>
Example:
```python
name = "Chayenne"
age = 18
print("Hello my name is,", name, "and I am", age, "years old")
```
Gives the Output:
```
Hello my name is Chayenne, and I am 18 years old
```
So within the print function you can bring a string together with a variable by a comma or a plus. When using the comma method, a space is created and when using plus, a space must be added for a "nicer" output.
<br>
<br>
If you want to output multiple variables and character using the print function, you should use the so-called f-string. To do this, the letter "f" must be placed before the quotation marks in the print function. All variables which should be output must be marked by curly brackets. 
<br>
<br>
Example:
```python
name = "Chayenne"
age = 18
print(f"Hello my name is {name} and I am {age} years old")
```
Gives the Output:
```
Hello my name is Chayenne, and I am 18 years old
```
For a formatted output the knowledge of string literals is helpful. They are usually introduced within a string with a backslash "\" and have a formatted effect on the output.
| String literal  | Name |
| ------------- | --------------- |
| " "           | Space           |
| "\n"          | Line feed       |
| "\v"          | Vertical tab    |
| "\t"          | Horizontal tab  |
| "\f"          | Formfeed        |
| "\r"          | Carriage Return |

Example:
```python
name = "Chayenne"
age = 18
print(f"Hello my name is:\n{name} and I am:\n{age} years old")
```
Gives the Output:
```
Hello my name is:
Chayenne and I am:
18 years old
```
Try to use the other string literals by yourself and find out their meaning!
<br>
<br>
### Assignments about the print() function

1. Let the words Tea, Coffee and Latte appear on the console in that order with a space between them. 
<br> Expected output:
```
Tea Coffee Latte
```
2. Write code that does the following. Define a variable text that is assigned the value Hello World! Use this variable to make Hello World! appear on the console. Then, change the value of this variable to MINT first. and print these words on the console. 
<br> Expected output:
```
Hello World!
MINT first
```
3. Look at the following code. Write down exactly (including the spaces) what will appear on the console when this code is executed. 
```python
age = 30
print("In two years you will be", age + 2, "years old.")
```
4. Make the following text appear on the console using a print function. 
```
Hello Alex!
Awesome, that you improve your python-skills.
Do not give up!
```
## Input by the input() function

The easiest way to create an input of data and store it in a variable is using the "input()" function. The data is entered by the keyboard. In the parenthesis of the "input()" function a string can be passed in quotation marks, which will be printed in the console to inform the user about the input of data.
<br> Example:
```python
age = input("Enter your age here: ")
```
The console will display the text "Enter your age here: " Then Python will wait for the user's input to continue processing. After the user has made a console input, the variable name "age" is assigned the entered value and saved. If you print the variable "age" using the print() function, the output will be the assigned age-value.
```python
# After the input the number "18" in the last code block
print(age)
# Gives the output "18"
```
