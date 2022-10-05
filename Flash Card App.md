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
