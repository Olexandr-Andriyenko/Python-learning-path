# Treasure island project

This is a project I finished on my own during the course ["100 Days of Code: The Complete Python Pro Bootcamp for 2022 by Dr. Angela Yu"](https://www.udemy.com/course/100-days-of-code/?couponCode=CA914D89FB922E1090DF).
<br>
<br>
Convert the following flowchart into a program:


<p align="center">
<img src="https://github.com/Olexandr-Andriyenko/Python-learning-path/blob/main/illustrations/Treasure%20island%20flow%20chart.png" width="450">
<p> 

Use the following ASCII art at the welcome display:

```
*******************************************************************************
          |                   |                  |                     |
 _________|________________.=""_;=.______________|_____________________|_______
|                   |  ,-"_,=""     `"=.|                  |
|___________________|__"=._o`"-._        `"=.______________|___________________
          |                `"=._o`"=._      _`"=._                     |
 _________|_____________________:=._o "=._."_.-="'"=.__________________|_______
|                   |    __.--" , ; `"=._o." ,-"""-._ ".   |
|___________________|_._"  ,. .` ` `` ,  `"-._"-._   ". '__|___________________
          |           |o`"=._` , "` `; .". ,  "-._"-._; ;              |
 _________|___________| ;`-.o`"=._; ." ` '`."\` . "-._ /_______________|_______
|                   | |o;    `"-.o`"=._``  '` " ,__.--o;   |
|___________________|_| ;     (#) `-.o `"=.`_.--"_o.-; ;___|___________________
____/______/______/___|o;._    "      `".o|o_.--"    ;o;____/______/______/____
/______/______/______/_"=._o--._        ; | ;        ; ;/______/______/______/_
____/______/______/______/__"=._o--._   ;o|o;     _._;o;____/______/______/____
/______/______/______/______/____"=._o._; | ;_.--"o.--"_/______/______/______/_
____/______/______/______/______/_____"=.o|o_.--""___/______/______/______/____
/______/______/______/______/______/______/______/______/______/______/_____ /
*******************************************************************************
```

<details open>
<summary>Solution</summary>

  ```python
# Display the ASCII art at the beginning
print('''\
*******************************************************************************
          |                   |                  |                     |
 _________|________________.=""_;=.______________|_____________________|_______
|                   |  ,-"_,=""     `"=.|                  |
|___________________|__"=._o`"-._        `"=.______________|___________________
          |                `"=._o`"=._      _`"=._                     |
 _________|_____________________:=._o "=._."_.-="'"=.__________________|_______
|                   |    __.--" , ; `"=._o." ,-"""-._ ".   |
|___________________|_._"  ,. .` ` `` ,  `"-._"-._   ". '__|___________________
          |           |o`"=._` , "` `; .". ,  "-._"-._; ;              |
 _________|___________| ;`-.o`"=._; ." ` '`."\` . "-._ /_______________|_______
|                   | |o;    `"-.o`"=._``  '` " ,__.--o;   |
|___________________|_| ;     (#) `-.o `"=.`_.--"_o.-; ;___|___________________
____/______/______/___|o;._    "      `".o|o_.--"    ;o;____/______/______/____
/______/______/______/_"=._o--._        ; | ;        ; ;/______/______/______/_
____/______/______/______/__"=._o--._   ;o|o;     _._;o;____/______/______/____
/______/______/______/______/____"=._o._; | ;_.--"o.--"_/______/______/______/_
____/______/______/______/______/_____"=.o|o_.--""___/______/______/______/____
/______/______/______/______/______/______/______/______/______/______/_____ /
*******************************************************************************
''')
print("Welcome to Treasure Island\nYour mission is to find the treasure")
print()
print("*******************************************************************************")
# Ask the user questions and then check them
user_decision = input('You are at a cross road. Where do you want to go? Type "left" or "right" ')
if user_decision.lower() == "left":
    user_decision = input('You have come to a lake. There is an island in the middle of the lake.'
                          'Type "wait" to wait for a boat. Type "swim" to swim across.')

    if user_decision.lower() == "wait":
        user_decision = input("You arrive at the island unharmed."
                              " There is a house with 3 doors. "
                              "One red, one yellow and one blue. Which colour do you choose? ")
        if user_decision.lower() == "yellow":
            print("You found the treasure! You Win!")
        elif user_decision.lower() == "red":
            print("It's a room full of fire. Game Over.")
        elif user_decision.lower() == "blue":
            print("You enter a room of beasts. Game Over.")
        else:
            print("You chose a door that doesn't exist. Game Over.")
    else:
        print("You get attacked by an angry trout. Game Over.")
else:
    print("You fell into a hole. Game Over")



 ``` 
  
</details>
