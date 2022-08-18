# Passwort Generator
This is a project I finished on my own during the course ["100 Days of Code: The Complete Python Pro Bootcamp for 2022 by Dr. Angela Yu"](https://www.udemy.com/course/100-days-of-code/?couponCode=CA914D89FB922E1090DF).
<br>
<br>
Create a passwort generator to get a random passwort.<br>
The program should ask the user about the amount of numbers, symbols and letters in the passwort.<br>
Of course the user have to input how long the passwort should be.<br>
You habe to use the "random" module!
<br>
<br>
Use the following lists for your passwort:

```python

letters = ['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j', 'k', 'l', 'm', 'n', 'o', 'p', 'q', 'r', 's', 't', 'u', 'v', 'w', 'x', 'y', 'z', 'A', 'B', 'C', 'D', 'E', 'F', 'G', 'H', 'I', 'J', 'K', 'L', 'M', 'N', 'O', 'P', 'Q', 'R', 'S', 'T', 'U', 'V', 'W', 'X', 'Y', 'Z']
numbers = ['0', '1', '2', '3', '4', '5', '6', '7', '8', '9']
symbols = ['!', '#', '$', '%', '&', '(', ')', '*', '+']

```

<details open>
<summary>Solution</summary>

```python

# Import the random module
import random
# Define the lists which include the characters for the passwort
letters = ['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j', 'k', 'l', 'm', 'n', 'o', 'p', 'q', 'r', 's', 't', 'u', 'v', 'w', 'x', 'y', 'z', 'A', 'B', 'C', 'D', 'E', 'F', 'G', 'H', 'I', 'J', 'K', 'L', 'M', 'N', 'O', 'P', 'Q', 'R', 'S', 'T', 'U', 'V', 'W', 'X', 'Y', 'Z']
numbers = ['0', '1', '2', '3', '4', '5', '6', '7', '8', '9']
symbols = ['!', '#', '$', '%', '&', '(', ')', '*', '+']
# Ask the user questions about the passwort and store them in variables
print("Welcome to the PyPassword Generator!")
# Number of letters, do not forget type casting!
letters_num = int(input("How many letters would you like in your password?"))
# Number of symbols, do not forget type casting!
symbols_num = int(input("How many symbols would you like?"))
# Number of numbers, do not forget type casting!
numbers_num = int(input("How many numbers would you like?"))
# Choose a random amount of letters, numbers and symbols and store them inside a list
# Methon "choices": Choose multiple random items from a list
random_letters = random.choices(letters, k = letters_num)
random_numbers = random.choices(numbers, k = numbers_num)
random_symbols = random.choices(symbols, k = symbols_num)
passwort = random_symbols + random_numbers + random_letters
# Use shuffle method to mix the elements of "passwort" list
random.shuffle(passwort)
print(f"Your passwort is:{passwort}!")
# You can search for methods to print the passwort without the square brackets, but it is okay for now

  
``` 
  
</details>
