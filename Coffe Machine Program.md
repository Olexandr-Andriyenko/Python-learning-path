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




