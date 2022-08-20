# Guess-The-Number-Game



This is a project I finished on my own during the course ["100 Days of Code: The Complete Python Pro Bootcamp for 2022 by Dr. Angela Yu"](https://www.udemy.com/course/100-days-of-code/?couponCode=CA914D89FB922E1090DF).
<br>
<br>
Build a game which creats a random number between 0 and 100 and the player have to guess this number.<br>
But the player have 5 tries at the "hard" mode and 10 tries at the "easy" mode.<br>
Every time of the guess is wrong, the player lose a live (try) until he has 0 tries.<br>
Of course at 0 tries the game is over an the playe lost the game.<br>
If the playe do a guess the program should tell the user if the guess is to high or to low, so the player can get a better estimation of the number<br>

<details><summary>Use the following ASCII art in your project:</summary>

```python
  
  / _ \_   _  ___  ___ ___  /__   \ |__   ___    /\ \ \_   _ _ __ ___ | |__   ___ _ __ 
 / /_\/ | | |/ _ \/ __/ __|   / /\/ '_ \ / _ \  /  \/ / | | | '_ ` _ \| '_ \ / _ \ '__|
/ /_\| |_| |  __/\__ \__ \  / /  | | | |  __/ / /\  /| |_| | | | | | | |_) |  __/ |   
\____/ \__,_|\___||___/___/  \/   |_| |_|\___| \_\ \/  \__,_|_| |_| |_|_.__/ \___|_|  
  
```

</details>

<details><summary>Solution</summary>
  
```python
# Import random module to creat a random number
import random
# Display the ASCII art
print('''\
  
  / _ \_   _  ___  ___ ___  /__   \ |__   ___    /\ \ \_   _ _ __ ___ | |__   ___ _ __ 
 / /_\/ | | |/ _ \/ __/ __|   / /\/ '_ \ / _ \  /  \/ / | | | '_ ` _ \| '_ \ / _ \ '__|
/ /_\| |_| |  __/\__ \__ \  / /  | | | |  __/ / /\  /| |_| | | | | | | |_) |  __/ |   
\____/ \__,_|\___||___/___/  \/   |_| |_|\___| \_\ \/  \__,_|_| |_| |_|_.__/ \___|_|  
  
''')
# Create a random number which is between 0 and 100
number_to_guess = random.randint(0, 100)
# Ask the user which mode he likes to play
# Valid the input
valid_options = ["easy", "hard"]
while True:
    mode = input("Choose a difficulty. Type 'easy' or 'hard': ")
    if mode in valid_options:
        break
    print("Wrong input!")
# Display information about the game
print(f"\nWelcome to the Number Guessing Game!\nI'm thinking of a number between 1 and 100.\nPssst, the correct answer "
      f"is {number_to_guess}\n")
# Set the tries (lives) to guess the number
if mode == "easy":
    lives = 10
else:
    lives = 5
# As longthe lives above 0 the player can guess
while lives > 0:
    # Inform the player about the amount of tries
    print(f"You have {lives} attempts remaining to guess the number.")
    # The input can be only integers, valid it!
    while True:
        try:
            guess = int(input("Make a guess: "))
            break
        except:
            print("Wrong input!")
    # Check the guess
    if guess == number_to_guess:
        print(f"You got it! The answer was {number_to_guess}")
        # Escape the while loop if the guess is correct
        break
    if guess > number_to_guess:
        print("\nTo high!")
        lives -= 1
    if guess < number_to_guess:
        print("\nTo low!")
        lives -= 1
    # Display that the player can guess again as long he has more than 0 lives
    if lives >0:
        print("Guess again.\n")
if lives == 0:
    # Display the player that he lost the game
    print("You've run out of guesses, you lose.")  
```
  
</details>
