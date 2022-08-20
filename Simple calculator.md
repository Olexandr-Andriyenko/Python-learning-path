# Simple calculator


This is a project I finished on my own during the course ["100 Days of Code: The Complete Python Pro Bootcamp for 2022 by Dr. Angela Yu"](https://www.udemy.com/course/100-days-of-code/?couponCode=CA914D89FB922E1090DF).
<br>
<br>
Buil a simple calculator which can use the operators "+", "-", "*" and "/".<br>
For the calculation the user have to enter two numbers.<br>
At the end of the calculation user can decide to continue calculation with the result and an another number.
<br>
<br>

<details><summary>Use the following ASCII art:</summary>

```python

_____________________
|  _________________  |
| | Pythonista   0. | |  .----------------.  .----------------.  .----------------.  .----------------. 
| |_________________| | | .--------------. || .--------------. || .--------------. || .--------------. |
|  ___ ___ ___   ___  | | |     ______   | || |      __      | || |   _____      | || |     ______   | |
| | 7 | 8 | 9 | | + | | | |   .' ___  |  | || |     /  \     | || |  |_   _|     | || |   .' ___  |  | |
| |___|___|___| |___| | | |  / .'   \_|  | || |    / /\ \    | || |    | |       | || |  / .'   \_|  | |
| | 4 | 5 | 6 | | - | | | |  | |         | || |   / ____ \   | || |    | |   _   | || |  | |         | |
| |___|___|___| |___| | | |  \ `.___.'\  | || | _/ /    \ \_ | || |   _| |__/ |  | || |  \ `.___.'\  | |
| | 1 | 2 | 3 | | x | | | |   `._____.'  | || ||____|  |____|| || |  |________|  | || |   `._____.'  | |
| |___|___|___| |___| | | |              | || |              | || |              | || |              | |
| | . | 0 | = | | / | | | '--------------' || '--------------' || '--------------' || '--------------' |
| |___|___|___| |___| |  '----------------'  '----------------'  '----------------'  '----------------' 
|_____________________|
  
```

</details>

<details><summary>Solution</summary>

```python
  
# Display ASCII art
print('''\
____________________
|  _________________  |
| | Pythonista   0. | |  .----------------.  .----------------.  .----------------.  .----------------. 
| |_________________| | | .--------------. || .--------------. || .--------------. || .--------------. |
|  ___ ___ ___   ___  | | |     ______   | || |      __      | || |   _____      | || |     ______   | |
| | 7 | 8 | 9 | | + | | | |   .' ___  |  | || |     /  \     | || |  |_   _|     | || |   .' ___  |  | |
| |___|___|___| |___| | | |  / .'   \_|  | || |    / /\ \    | || |    | |       | || |  / .'   \_|  | |
| | 4 | 5 | 6 | | - | | | |  | |         | || |   / ____ \   | || |    | |   _   | || |  | |         | |
| |___|___|___| |___| | | |  \ `.___.'\  | || | _/ /    \ \_ | || |   _| |__/ |  | || |  \ `.___.'\  | |
| | 1 | 2 | 3 | | x | | | |   `._____.'  | || ||____|  |____|| || |  |________|  | || |   `._____.'  | |
| |___|___|___| |___| | | |              | || |              | || |              | || |              | |
| | . | 0 | = | | / | | | '--------------' || '--------------' || '--------------' || '--------------' |
| |___|___|___| |___| |  '----------------'  '----------------'  '----------------'  '----------------' 
|_____________________|

''')


# -------------------------------------------------------------------------#
# Function which execute the calculation
# The input is two numbers and the operator symbol
def calculation(num_1, num_2, operator_symbol):
    # Addition
    if operator_symbol == "+":
        result = num_1 + num_2
    elif operator_symbol == "-":
        result = num_1 - num_2
    elif operator_symbol == "*":
        result = num_1 * num_2
    elif operator_symbol == "/":
        result = num_1 / num_2
    return result


# -------------------------------------------------------------------------#
# The actual program starts here
# Define a list of allowed operations
operations_allowed = ["+", "-", "*", "/"]
# Ask the user for the first number
# Valid that it is a number not a symbol!
wrong_input = True
while wrong_input:
    try:
        num_1 = float(input("What is the first number? "))
        wrong_input = False
    except:
        print("Wrong input, try again!")
# Ask the user to pick an operator
# Valid the input with a while loop
while True:
    print("|----------------------|")
    print("\t+\n\t-\n\t*\n\t/")
    print("|----------------------|")
    operator_symbol_pick = input("Pick an operator: ")
    if operator_symbol_pick in operations_allowed:
        break
    print("Wrong input!")
# Ask the user for the second number
# Valid that it is a number not a symbol!
wrong_input = True
while wrong_input:
    try:
        num_2 = float(input("What is the second number? "))
        wrong_input = False
    except:
        print("Wrong input, try again!")
# Calculation with the "calculation" function starts here
result_of_calculation = calculation(num_1, num_2, operator_symbol_pick)
# Display the calculation
print(f"{num_1} {operator_symbol_pick} {num_2} = {result_of_calculation}")
# Ask the user if he likes to continue calculation
valid_answers = ["y", "n", "e"]
continue_program = True
while continue_program:
    while True:
        continue_calculation = input(f"Type 'y' to continue calculating with {result_of_calculation},type 'n' to start a new "
                                     f"calculation or type 'e' to exit the program: ")
        if continue_calculation in valid_answers:
            if continue_calculation == "y":
                # Ask the user for the second number
                # Valid that it is a number not a symbol!
                wrong_input = True
                while wrong_input:
                    try:
                        num_2 = float(input("What is the second number? "))
                        wrong_input = False
                    except:
                        print("Wrong input, try again!")

                # Valid the input with a while loop
                while True:
                    print("|----------------------|")
                    print("\t+\n\t-\n\t*\n\t/")
                    print("|----------------------|")
                    operator_symbol_pick = input("Pick an operator: ")
                    if operator_symbol_pick in operations_allowed:
                        break
                    print("Wrong input!")
                # Start calculation
                result_of_calculation_new = calculation(result_of_calculation, num_2, operator_symbol_pick)
                # Display the calculation
                print(f"{result_of_calculation} {operator_symbol_pick} {num_2} = {result_of_calculation_new}")
                # Refresh the variable for next calculation (remember the nex result of last calculation)
                result_of_calculation = result_of_calculation_new
        if continue_calculation == "n":
            result_of_calculation = 0
            # Ask the user for the first number
            # Valid that it is a number not a symbol!
            wrong_input = True
            while wrong_input:
                try:
                    num_1 = float(input("What is the first number? "))
                    wrong_input = False
                except:
                    print("Wrong input, try again!")
            # Ask the user to pick an operator
            # Valid the input with a while loop
            while True:
                print("|----------------------|")
                print("\t+\n\t-\n\t*\n\t/")
                print("|----------------------|")
                operator_symbol_pick = input("Pick an operator: ")
                if operator_symbol_pick in operations_allowed:
                    break
                print("Wrong input!")
            # Ask the user for the second number
            # Valid that it is a number not a symbol!
            wrong_input = True
            while wrong_input:
                try:
                    num_2 = float(input("What is the second number? "))
                    wrong_input = False
                except:
                    print("Wrong input, try again!")
            # Calculation with the "calculation" function starts here
            result_of_calculation = calculation(num_1, num_2, operator_symbol_pick)
            # Display the calculation
            print(f"{num_1} {operator_symbol_pick} {num_2} = {result_of_calculation}")

        if continue_calculation == "e":
            print("Exit the calculator!")
            continue_program = False
            break
  
```
  
</details>
