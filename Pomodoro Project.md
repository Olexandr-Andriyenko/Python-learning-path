# Pomodoro Project

We will create a Pomodoro GUI. You can read [here](https://en.wikipedia.org/wiki/Pomodoro_Technique) about the Pomodoro Technique!
<br>
You have to use this [image](https://github.com/Olexandr-Andriyenko/Python-learning-path/blob/main/illustrations/tomato.png) for the project!
<br>
You can start with this code:

```python

# ---------------------------- CONSTANTS ------------------------------- #
PINK = "#e2979c"
RED = "#e7305b"
GREEN = "#9bdeac"
YELLOW = "#f7f5dd"
FONT_NAME = "Courier"
WORK_MIN = 25
SHORT_BREAK_MIN = 5
LONG_BREAK_MIN = 20

# ---------------------------- TIMER RESET ------------------------------- # 

# ---------------------------- TIMER MECHANISM ------------------------------- # 

# ---------------------------- COUNTDOWN MECHANISM ------------------------------- # 

# ---------------------------- UI SETUP ------------------------------- #
```

## Solution

<details>
 <summary>Part 1 of solution</summary>

```python
import tkinter as tk

# ---------------------------- CONSTANTS ------------------------------- #
PINK = "#e2979c"
RED = "#e7305b"
GREEN = "#9bdeac"
YELLOW = "#f7f5dd"
FONT_NAME = "Courier"
WORK_MIN = 25
SHORT_BREAK_MIN = 5
LONG_BREAK_MIN = 20


# ---------------------------- TIMER RESET ------------------------------- #

# ---------------------------- TIMER MECHANISM ------------------------------- #



# ---------------------------- COUNTDOWN MECHANISM ------------------------------- #



# ---------------------------- UI SETUP ------------------------------- #
# Create a new window
root = tk.Tk()
# Set title of the window
root.title("Pomodoro")
# Configer the window
root.config(padx=100, pady=50)
# Create a canvas widget to place an image on the top of the canvas
canvas = tk.Canvas(width=200, height=224)
# Add image to the canvas
tomato_img = tk.PhotoImage(file="tomato.png")
canvas.create_image(100, 112, image=tomato_img)  # Image in the center of the canvas, that's why x and y is half of width and height
# Note: You can't add to the image="tomato.png"!!! Firstly create PhotoImage !!!
# Now we have to position our canvas inside the window with pack or grid
canvas.pack()  # The image is taking the entire space of the window, resize window with config

# ------------------------------------------------ #
root.mainloop()

```
  
</details>
