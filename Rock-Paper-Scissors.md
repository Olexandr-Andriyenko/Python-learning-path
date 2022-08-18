# Rock-Paper-Scissors
This is a project I finished on my own during the course ["100 Days of Code: The Complete Python Pro Bootcamp for 2022 by Dr. Angela Yu"](https://www.udemy.com/course/100-days-of-code/?couponCode=CA914D89FB922E1090DF).
<br>
<br>
Creat a program which allows you to play Rock-Paper-Scissors game! <br>
Do not forget to check the input of the user. Use for this try, except and loops. <br>
You should use the modules "random" and "sys", read the documentation to use it!
Use the ASCII art:
```

        _______
    ---'   ____)
          (_____)
          (_____)
          (____)
    ---.__(___)
    
         _______
    ---'    ____)____
               ______)
              _______)
             _______)
    ---.__________)
    
        _______
    ---'   ____)____
              ______)
           __________)
          (____)
    ---.__(___)
    
    
```


<details open>
<summary>Solution</summary>

  ```python

# Import the random module
import random
# Import the sys module to stop the whole program
import sys

# Display information and let the user do an input, do not forget type casting!
try:
    my_choose = int(input("What do you choose? Type 0 for Rock, 1 for Paper or 2 for Scissors."))
except:
    print("This is not a number!")
    sys.exit()

# Check the input

if my_choose > 2 or my_choose < 0:
    print("Wrong number!")
    sys.exit()

# Create the choice of the computer which is random
# For this we need a random number between 0 and 2
computer_choice = random.randint(0, 2)
# Display the users choice with ASCII art
if my_choose == 0:
    print("""
        _______
    ---'   ____)
          (_____)
          (_____)
          (____)
    ---.__(___)
    """)
elif my_choose == 1:
    print("""
         _______
    ---'    ____)____
               ______)
              _______)
             _______)
    ---.__________)
    """)
elif my_choose == 2:
    print("""
        _______
    ---'   ____)____
              ______)
           __________)
          (____)
    ---.__(___)
    """)
# Display the computers choice with ASCII art
print("Computers choice:")
if computer_choice == 0:
    print("""
        _______
    ---'   ____)
          (_____)
          (_____)
          (____)
    ---.__(___)
    """)
elif computer_choice == 1:
    print("""
         _______
    ---'    ____)____
               ______)
              _______)
             _______)
    ---.__________)
    """)
elif computer_choice == 2:
    print("""
        _______
    ---'   ____)____
              ______)
           __________)
          (____)
    ---.__(___)
    """)
# Let's check the different choices and tell the user it is a win or lose for him
if my_choose == 0 and computer_choice == 0 or my_choose == 1 and computer_choice == 1 or my_choose == 2 and computer_choice == 2:
    print("It's a draw!")
elif my_choose == 0 and computer_choice == 2 or my_choose == 1 and computer_choice == 0 or my_choose == 2 and computer_choice == 1:
    print("You win!")
else:
    print("You lose!")



 ``` 
  
</details>
