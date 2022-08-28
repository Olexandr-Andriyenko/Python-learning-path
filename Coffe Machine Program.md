# Coffe Machine Program

![giphy](https://user-images.githubusercontent.com/92121260/185752640-e045ddad-3549-432f-af8e-a67ed4759cde.gif)


## Simulate a coffee machine with the following requirements:

1) Prompt user by asking What would you like? (Espresso/Latte/Cappuccino):
- Check the input of the user to decide what to do next
- The prompt should show every time that the action has completed
- Don’t forgeett to watch out for wrong inputs by the user
2) Turn off the Coffe Machine by entering a secret word:
- The maintence staff can turn off the machine any time by input „off“
- By input „report“ in the prompt (at program end), a report should be generated that shows the current resource values:
  - Water: 150ml
  - Milk: 50ml
  - Coffee: 75g
  - Money: 35,50€<br>
3) Check ingredients sufficient:
- Are enough ingredients for a drink inside the machine ?
- If not enough ingredients then don’t continue to make the drink but print „Sorry there is not enough water/coffee/milk“
- If it’s not possible to make a drink then go back to the initiaal conditions of the machine

4) The payment process:
- If there are sufficient resources to make the drink selected, then the machine should prompt the user to unsert coins.
- Acceptable coins are: 0,05€ / 0,10€ / 0,20€ / 0,50€ / 1€ / 2€
- Here we are making a assumption, the machine have infinite change coins.
- Check if the payment is complete, if not then the user can decide to continue with paying or get his money back.
- If the payment is complete the machine will check whether the user need a change or not.

5) Extend the program logically
- Give the user useful statements about the order process.
- Add your own ideas inside the program for the best user experience!
- Structure the code with functions!

6) Drink consumption
- Espresso need: 
  - 15 g coffee
  - 50 ml water
  - 100 ml milk
- Latte need:
  - 25 g coffee
  - 250 ml milk

- Cappuccino need:
  - 15 g coffee
  - 50 ml water
  - 200 ml milk

7) Secret keywords
- Input „Fill milk“ to reset the milk inside the machine.
- Input „Fill water“ to reset the water inside the machine.
- Input „Fill coffee“ to reset the coffee inside the machine.
- Input „Take money“ to reset the money inside the machine.
- The secret keywords can be used at the end of the program by the maintainer

## For a better overview I have created a flow chart diagram, which can be used as oriantation to solve the assignment step by step.

<p align="center">
<img src="https://github.com/Olexandr-Andriyenko/Python-learning-path/blob/main/illustrations/img30.png" width="550">
<p> 

## Use case diagram

A use case diagram is a graphical depiction of a user's possible interactions with a system.
Here i have created a superficial representation of the interactions without details.

<p align="center">
<img src="https://github.com/Olexandr-Andriyenko/Python-learning-path/blob/main/illustrations/img29.png" width="550">
<p> 

The use case diagrams can be a good communication tool for stakeholders.
Experts recommend working with use case diagrams to supplement and illustrate a textual description of the use case in question.

<details><summary>main.py</summary>

```python

# -------------------------------------- #
# Modules
# -------------------------------------- #
from Machine_data import drinks
from coffee_functions import check_ingredients
from coffee_functions import payment
from  coffee_functions import use_ingredients
from coffee_functions import secret_keyword



# -------------------------------------- #
# Main program
# -------------------------------------- #
# Variable to run the program whole time until user go in stand by mode
machine_standby = False
while machine_standby == False:
    # Variable to ask the user for a new drink until ingredients are available
    enough_ingredients = False
    while not enough_ingredients:

        print("Available drinks:\n--------------")
        # Variable for the order numbers
        drink_number = 1
        for drink in drinks:
            print(f"{drink_number} {drink}")
            drink_number += 1
        # Ask for a drink until a valid input
        while True:
            drink = input("--------------\nSelect a drink: ")
            if drink.capitalize() in drinks:
                break
        # Sets the variable to True or False to escape or continue the loop
        enough_ingredients = check_ingredients(drink)
    # The client have to pay now, for this we have to inform him how much the drink costs
    # If False is returned payment has failed
    payment_ok = payment(drink)
    if payment_ok:
        use_ingredients(drink)
        print("Your drink is ready!\n--------------")
        print("Enter standby mode!")
        # Torn standby mode on
        machine_standby = True
    else:
        print("--------------\nOrder canceled!\n--------------")

    if machine_standby:
        while  True:
            secret_word = input("Press 's' key to start: ")
            secret_keyword(secret_word.capitalize())
            if secret_word == "s":
                machine_standby = False
                break


```
  
</details>

<details><summary>coffee_functions.py</summary>

```python
# -------------------------------------- #
# Modules
# -------------------------------------- #
from Machine_data import drinks
from Machine_data import ingredients
import Machine_data


# -------------------------------------- #
# Functions
# -------------------------------------- #

# This function will check whether there are enough ingredients, if not it returns "False", if yes "True"
def check_ingredients(drink):
    if drink.capitalize() == "Espresso":
        if ingredients["Milk"] < 100 or ingredients["Water"] < 50 or ingredients["Coffee"] < 15:
            print("Sorry, not enough ingredients!\nPlease choose an another drink!")
            return False
    if drink.capitalize() == "Cappuccino":
        if ingredients["Milk"] < 200 or ingredients["Water"] < 50 or ingredients["Coffee"] < 15:
            print("Sorry, not enough ingredients!\nPlease choose an another drink!")
            return False
    if drink.capitalize() == "Latte":
        if ingredients["Milk"] < 250 or ingredients["Coffee"] < 15:
            print("Sorry, not enough ingredients!\nPlease choose an another drink!")
            return False
    return True


# Function for payment
def payment(drink):
    # Search for price inside the dictionary
    price = drinks[drink.capitalize()]
    inserted_coins_sum = 0
    inserted_coins_change = 0
    while inserted_coins_sum < drinks[drink.capitalize()]:
        print(f"---------------\nPlease pay {price} €\n---------------")
        print("Following coins accepted:\n0.05€\n0.10€\n0,20€\n0,50€\n1€\n2€")
        acctepted_coins = [0.05, 0.10, 0.20, 0.50, 1, 2]
        while True:
            while True:
                try:
                    inserted_coins = float(input("Insert now:"))
                    break
                except ValueError:
                    print("This coin is not accepted!")
            if inserted_coins in acctepted_coins:
                price = round(price - inserted_coins, 2)
                inserted_coins_sum += inserted_coins
                inserted_coins_change = inserted_coins_sum
                break
            print("This coin is not accepted!")
        while True:
            accepted_answer = ["yes", "no"]
            return_money = input("You like to get your money back and exit? (Yes / No): ")
            while return_money not in accepted_answer:
                return_money = input("You like to get your money back and exit? (Yes / No): ")
            if return_money.lower() == "yes":
                print(f"You will get {inserted_coins_sum} € back!")
                inserted_coins_sum = 999
                return False
            if return_money.lower() == "no":
                break
    # Add payment to the start money of the machine
    Machine_data.start_money += drinks[drink.capitalize()]
    # Check for return
    if inserted_coins_change > drinks[drink.capitalize()]:
        change = round(inserted_coins_sum - drinks[drink.capitalize()], 2)
        print(f"---------------\nYou will get {change} € change!\n---------------")
    return True


# Function for reducing the ingredients
def use_ingredients(drink):
    if drink.capitalize() == "Espresso":
        ingredients["Coffee"] -= 15
        ingredients["Water"] -= 50
        ingredients["Milk"] -= 100
    elif drink.capitalize() == "Latte":
        ingredients["Coffee"] -= 25
        ingredients["Milk"] -= 250
    elif drink.capitalize() == "Cappuccino":
        ingredients["Coffee"] -= 15
        ingredients["Milk"] -= 200
        ingredients["Water"] -= 50


# Function for secret keywords
def secret_keyword(secret_word):
    if secret_word == "Fill milk":
        ingredients["Milk"] = 500
        print("Milk filled!")
    elif secret_word == "Fill water":
        ingredients["Water"] = 500
        print("Water filled!")
    elif secret_word == "Fill coffee":
        ingredients["Coffee"] = 100
        print("Coffee filled!")
    elif secret_word == "Take money":
        money_taken = round(Machine_data.start_money - 77, 2)
        Machine_data.start_money = 77
        print(f"{money_taken} € was taken!")
    elif secret_word == "Report":
        print(f"--------------\nWater: {ingredients['Water']}\nMilk: {ingredients['Milk']}\nCoffee: {ingredients['Coffee']}\nMoney: {Machine_data.start_money} €\n--------------")  
  
```

</details>
  
  
<details><summary>Machine_data.py</summary>

```python
  
# Dictionary with drinks and prices
drinks = {
    "Espresso": 5.80,
    "Cappuccino": 5.20,
    "Latte": 4.80
}
# Amount of the Ingredients (units are gram and milliliter)
ingredients = {
    "Milk": 500,
    "Water": 500,
    "Coffee": 100
}
# How much money is inside the automat (first value is the coin, second value the amount)
# At the start each coin is 20times available
money = {
    0.05: 20,
    0.1: 20,
    0.2: 20,
    0.5: 20,
    1: 20,
    2: 20
}
# Money at the beginning in EUR
start_money = 77

```
 
</details>
