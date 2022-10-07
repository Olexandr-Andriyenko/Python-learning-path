# Flash Card App

We are building an app which has flash cards. At the front of the cards you will see a english word and at the back the german translation.
<br>
We are using the common 1000 english words for this project!
<br>
<br>
Use the [CSV file](https://github.com/Olexandr-Andriyenko/Python-learning-path/blob/main/Files/data_flash_card.csv) to get the data for this project!
<br>
<br>
You will find the images for this projects [inside this folder](https://github.com/Olexandr-Andriyenko/Python-learning-path/tree/main/illustrations/flash_card_images).
<br>
<br>
Uhse this background-color `#B1DDC6`!
<br>

UI looks like this:

<p align="left">
<img src="https://github.com/Olexandr-Andriyenko/Python-learning-path/blob/main/illustrations/img59.PNG" width="450">
<p>

## Solution



<details>
 <summary>Part 1 of solution</summary>

Set up the UI!
  
  ```python
# ------------ MODULES ------------ #
import tkinter as tk


# ------------ CONSTANTS ------------ #
BACKGROUND_COLOR = "#B1DDC6"
FRONT_1= ("Ariel", 40, "italic")
FRONT_2 = ("Ariel", 60, "bold")

# ------------ UI SETUP ------------ #
root = tk.Tk()
root.title("Flash Card")
root.config(padx=50, pady=50, background=BACKGROUND_COLOR)

# Canvas
image_front = tk.PhotoImage(file="card_front.png")
canvas = tk.Canvas(height=526, width=800, background=BACKGROUND_COLOR, highlightthickness=0)
canvas.create_image(400, 263, image=image_front)
canvas.grid(row=0, column=0, columnspan=2)
# Text on Canvas
canvas.create_text(400, 150, text="Title", font=FRONT_1)
canvas.create_text(400, 263, text="word", font=FRONT_2)

# Buttons
cross_image = tk.PhotoImage(file="wrong.png")
unknown_button = tk.Button(image=cross_image)
unknown_button.grid(row=1, column=0)

check_image = tk.PhotoImage(file="right.png")
know_button = tk.Button(image=check_image)
know_button.grid(row=1, column=1)

root.mainloop()
  ```
  
</details>

<details>
 <summary>Part 2 of solution</summary>

 Pick a random word and change the words randomly by pressing one of the buttons.
 Use the pandas libary to read the csv!
  
  ```python
# ------------ MODULES ------------ #
import tkinter as tk
import pandas as pd

# ------------ CONSTANTS ------------ #
BACKGROUND_COLOR = "#B1DDC6"
FRONT_1= ("Ariel", 40, "italic")
FRONT_2 = ("Ariel", 60, "bold")
import random

# ------------ DATA READ ------------ #
# Save the csv file inside a dataframe
df = pd.read_csv("data_flash_card.csv")
df_dict = df.to_dict(orient="records")  # Convert df to dictionary

# ------------ FUNCTIONS ------------ #
def next_card():
    current_card = random.choice(df_dict)
    random_word = current_card["English"]
    canvas.itemconfig(card_title, text="English")
    canvas.itemconfig(card_word, text=random_word)


# ------------ UI SETUP ------------ #
root = tk.Tk()
root.title("Flash Card")
root.config(padx=50, pady=50, background=BACKGROUND_COLOR)

# Canvas
image_front = tk.PhotoImage(file="card_front.png")
canvas = tk.Canvas(height=526, width=800, background=BACKGROUND_COLOR, highlightthickness=0)
canvas.create_image(400, 263, image=image_front)
canvas.grid(row=0, column=0, columnspan=2)
# Text on Canvas
card_title = canvas.create_text(400, 150, text="Title", font=FRONT_1)
card_word = canvas.create_text(400, 263, text="word", font=FRONT_2)

# Buttons
cross_image = tk.PhotoImage(file="wrong.png")
unknown_button = tk.Button(image=cross_image, command=next_card)
unknown_button.grid(row=1, column=0)

check_image = tk.PhotoImage(file="right.png")
know_button = tk.Button(image=check_image, command=next_card)
know_button.grid(row=1, column=1)

# Call here the function next_card, to show at the start the first word!
next_card()





root.mainloop()

  ```
  
</details>

<details>
 <summary>Part 3 of solution</summary>

Add the back side of the card and keep switching the words each 3 seconds.
  
  ```python
# ------------ MODULES ------------ #
import tkinter as tk
import pandas as pd

# ------------ CONSTANTS ------------ #
BACKGROUND_COLOR = "#B1DDC6"
FRONT_1= ("Ariel", 40, "italic")
FRONT_2 = ("Ariel", 60, "bold")
import random

# ------------ DATA READ ------------ #
# Save the csv file inside a dataframe
df = pd.read_csv("data_flash_card.csv")
df_dict = df.to_dict(orient="records")  # Convert df to dictionary
current_card = {}  # We will store here a random dictionary with eng and ger word

# ------------ FUNCTIONS ------------ #
def next_card():
    global current_card, flip_timer
    root.after_cancel(flip_timer)  # Reset the timer
    current_card = random.choice(df_dict)  # This is still a dictionary
    random_word = current_card["English"]
    canvas.itemconfig(card_title, text="English", fill="black")
    canvas.itemconfig(card_word, text=random_word, fill="black")
    canvas.itemconfig(card_background, image=image_front)
    flip_timer = root.after(3000, func=flip_card)

def flip_card():
    canvas.itemconfig(card_title, text="German", fill="white")
    canvas.itemconfig(card_word, text=current_card["German"], fill="white")
    canvas.itemconfig(card_background, image=image_back)  # Change the image



# ------------ UI SETUP ------------ #
root = tk.Tk()
root.title("Flash Card")
root.config(padx=50, pady=50, background=BACKGROUND_COLOR)
# Call a function after delay in ms
flip_timer = root.after(3000, func=flip_card)  # If you go to a new card, card flips faster cuz 3 seconds counting down (bug)

# Canvas
image_front = tk.PhotoImage(file="card_front.png")
image_back = tk.PhotoImage(file="card_back.png")
canvas = tk.Canvas(height=526, width=800, background=BACKGROUND_COLOR, highlightthickness=0)
card_background = canvas.create_image(400, 263, image=image_front)
canvas.grid(row=0, column=0, columnspan=2)
# Text on Canvas
card_title = canvas.create_text(400, 150, text="Title", font=FRONT_1)
card_word = canvas.create_text(400, 263, text="word", font=FRONT_2)

# Buttons
cross_image = tk.PhotoImage(file="wrong.png")
unknown_button = tk.Button(image=cross_image, command=next_card)
unknown_button.grid(row=1, column=0)

check_image = tk.PhotoImage(file="right.png")
know_button = tk.Button(image=check_image, command=next_card)
know_button.grid(row=1, column=1)

# Call here the function next_card, to show at the start the first word!
next_card()


root.mainloop()

  ```
  
</details>

<details>
 <summary>FINAL solution</summary>

Reduce the amount of words to learn by creating an another csv file.
  
  ```python
# ------------ MODULES ------------ #
import tkinter as tk
import pandas as pd

# ------------ CONSTANTS ------------ #
BACKGROUND_COLOR = "#B1DDC6"
FRONT_1= ("Ariel", 40, "italic")
FRONT_2 = ("Ariel", 60, "bold")
import random

# ------------ DATA READ ------------ #
df_dict = {}
current_card = {}  # We will store here a random dictionary with eng and ger word

# Save the csv file inside a dataframe
try:
    df = pd.read_csv("Words_to_learn.csv")
except FileNotFoundError:
    original_data = pd.read_csv("data_flash_card.csv")
    df_dict = original_data.to_dict(orient="records")
else:
    df_dict = df.to_dict(orient="records")


# ------------ FUNCTIONS ------------ #
def next_card():
    global current_card, flip_timer
    root.after_cancel(flip_timer)  # Reset the timer
    current_card = random.choice(df_dict)  # This is still a dictionary
    random_word = current_card["English"]
    canvas.itemconfig(card_title, text="English", fill="black")
    canvas.itemconfig(card_word, text=random_word, fill="black")
    canvas.itemconfig(card_background, image=image_front)
    flip_timer = root.after(3000, func=flip_card)

def flip_card():
    canvas.itemconfig(card_title, text="German", fill="white")
    canvas.itemconfig(card_word, text=current_card["German"], fill="white")
    canvas.itemconfig(card_background, image=image_back)  # Change the image


def is_known():
    # Remove the known dictionary from main df_dict dictionary
    df_dict.remove(current_card)
    # For testing: print(len(df_dict))
    # Save the words which you have to learn in a csv
    data = pd.DataFrame(df_dict)
    data.to_csv("Words_to_learn.csv", index=False)  # Index set to false, to remove numbers in df
    next_card()

# ------------ UI SETUP ------------ #
root = tk.Tk()
root.title("Flash Card")
root.config(padx=50, pady=50, background=BACKGROUND_COLOR)
# Call a function after delay in ms
flip_timer = root.after(3000, func=flip_card)  # If you go to a new card, card flips faster cuz 3 seconds counting down (bug)

# Canvas
image_front = tk.PhotoImage(file="card_front.png")
image_back = tk.PhotoImage(file="card_back.png")
canvas = tk.Canvas(height=526, width=800, background=BACKGROUND_COLOR, highlightthickness=0)
card_background = canvas.create_image(400, 263, image=image_front)
canvas.grid(row=0, column=0, columnspan=2)
# Text on Canvas
card_title = canvas.create_text(400, 150, text="Title", font=FRONT_1)
card_word = canvas.create_text(400, 263, text="word", font=FRONT_2)

# Buttons
cross_image = tk.PhotoImage(file="wrong.png")
unknown_button = tk.Button(image=cross_image, command=next_card)
unknown_button.grid(row=1, column=0)

check_image = tk.PhotoImage(file="right.png")
know_button = tk.Button(image=check_image, command=is_known)
know_button.grid(row=1, column=1)

# Call here the function next_card, to show at the start the first word!
next_card()

root.mainloop()

  ```
  
</details>
