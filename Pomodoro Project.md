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

<details>
 <summary>Part 2 of solution</summary>

<p align="left">
<img src="https://github.com/Olexandr-Andriyenko/Python-learning-path/blob/main/illustrations/img54.PNG" width="300">
<p>

Lets correct the blue marked area of the image! You have just to change the x value of the canvas image from `100` to `103`!

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
root.config(padx=100, pady=50, bg=YELLOW) # Change the window background color with bg


# Create a canvas widget to place an image on the top of the canvas
canvas = tk.Canvas(width=200, height=224, bg=YELLOW, highlightthickness=0)  # highlightthickness will remove the border! Them you can change x from 103 to 100
# Add image to the canvas
tomato_img = tk.PhotoImage(file="tomato.png")
canvas.create_image(100, 112, image=tomato_img)  # Image in the center of the canvas, that's why x and y is half of width and height
# Note: You can't add to the image="tomato.png"!!! Firstly create PhotoImage !!!
# Now we have to position our canvas inside the window with pack or grid

# Display some text
canvas.create_text(103, 130, text="00:00", fill="white", font=(FONT_NAME, 35, "bold"))  # With a little experimentation I figured the values 103 and 130 out
canvas.pack()  # The image is taking the entire space of the window, resize window with config



# ------------------------------------------------ #
root.mainloop()

```
 
Now the program should looks like this:

<p align="left">
<img src="https://github.com/Olexandr-Andriyenko/Python-learning-path/blob/main/illustrations/img55.PNG" width="300">
<p>
 
</details>

<details>
 <summary>Part 3 of solution</summary>


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
root.config(padx=100, pady=50, bg=YELLOW) # Change the window background color with bg


# Create a canvas widget to place an image on the top of the canvas
canvas = tk.Canvas(width=200, height=224, bg=YELLOW, highlightthickness=0)  # highlightthickness will remove the border!
# Add image to the canvas
tomato_img = tk.PhotoImage(file="tomato.png")
canvas.create_image(100, 112, image=tomato_img)  # Image in the center of the canvas, that's why x and y is half of width and height
# Note: You can't add to the image="tomato.png"!!! Firstly create PhotoImage !!!
# Now we have to position our canvas inside the window with pack or grid

# Display some text
canvas.create_text(103, 130, text="00:00", fill="white", font=(FONT_NAME, 35, "bold"))  # With a little experimentation I figured the values 103 and 130 out
# Now we will use only grid not pack
canvas.grid(column=1, row=1)
# canvas.pack()  # The image is taking the entire space of the window, resize window with config

# Add a title label
title_label = tk.Label(text="Timer", fg=GREEN, font=(FONT_NAME, 50), bg=YELLOW)
title_label.grid(column=1, row=0)

# Add the start button
start_button = tk.Button(text="Start")
start_button.grid(column=0, row=2)

# Add the reset button
reset_button = tk.Button(text="Reset")
reset_button.grid(column=2, row=2)

# Add the checkmark
check_marks = tk.Label(text="✔", fg=GREEN, bg=YELLOW)
check_marks.grid(column=1, row=3)


# ------------------------------------------------ #
root.mainloop()

```
 
Now the program should looks like this:

<p align="left">
<img src="https://github.com/Olexandr-Andriyenko/Python-learning-path/blob/main/illustrations/img56.PNG" width="300">
<p>
 
</details>


<details>
 <summary>Part 4 of solution</summary>

Lets creaate a countdown mechanism!
<br>
First we will learn the `after()` method.


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
# This GUI is event-driven, event-driven programming focuses on the events (messages) and their flow between different software components.
# So we can not use a while loop because "mainloop()" is already looping and checking if something happened


# ---------------------------- COUNTDOWN MECHANISM ------------------------------- #



# ---------------------------- UI SETUP ------------------------------- #
# Create a new window
root = tk.Tk()
# Set title of the window
root.title("Pomodoro")
# Configer the window
root.config(padx=100, pady=50, bg=YELLOW) # Change the window background color with bg
# We have to use "after()", this method takes an amount of time that it should wait and then after that amount of time
# it calls a function that you tell it to call
def say_something(thing):
    print(thing)

root.after(1000, say_something, "Hello" )  # After 1 sec it call the funct. "say_something" and passes "Hello" as the input to the funct.


# Create a canvas widget to place an image on the top of the canvas
canvas = tk.Canvas(width=200, height=224, bg=YELLOW, highlightthickness=0)  # highlightthickness will remove the border!
# Add image to the canvas
tomato_img = tk.PhotoImage(file="tomato.png")
canvas.create_image(100, 112, image=tomato_img)  # Image in the center of the canvas, that's why x and y is half of width and height
# Note: You can't add to the image="tomato.png"!!! Firstly create PhotoImage !!!
# Now we have to position our canvas inside the window with pack or grid

# Display some text
canvas.create_text(103, 130, text="00:00", fill="white", font=(FONT_NAME, 35, "bold"))  # With a little experimentation I figured the values 103 and 130 out
# Now we will use only grid not pack
canvas.grid(column=1, row=1)
# canvas.pack()  # The image is taking the entire space of the window, resize window with config

# Add a title label
title_label = tk.Label(text="Timer", fg=GREEN, font=(FONT_NAME, 50), bg=YELLOW)
title_label.grid(column=1, row=0)

# Add the start button
start_button = tk.Button(text="Start")
start_button.grid(column=0, row=2)

# Add the reset button
reset_button = tk.Button(text="Reset")
reset_button.grid(column=2, row=2)

# Add the checkmark
check_marks = tk.Label(text="✔", fg=GREEN, bg=YELLOW)
check_marks.grid(column=1, row=3)




# ------------------------------------------------ #
root.mainloop()

```
 
</details>

<details>
 <summary>Part 5 of solution</summary>

Lets creaate a countdown mechanism!
<br>
First we will learn the `after()` method.
<br>
Now we create a time which counts from 5 to 0.


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
# This GUI is event-driven, event-driven programming focuses on the events (messages) and their flow between different software components.
# So we can not use a while loop because "mainloop()" is already looping and checking if something happened


# ---------------------------- COUNTDOWN MECHANISM ------------------------------- #
def count_down(count):
    canvas.itemconfig(timer_text, text=count)
    if count > 0:
        root.after(1000, count_down, count - 1)  # After 1 sec it call the funct. "say_something" and passes "Hello" as the input to the funct.


# ---------------------------- UI SETUP ------------------------------- #
# Create a new window
root = tk.Tk()
# Set title of the window
root.title("Pomodoro")
# Configer the window
root.config(padx=100, pady=50, bg=YELLOW) # Change the window background color with bg




# Create a canvas widget to place an image on the top of the canvas
canvas = tk.Canvas(width=200, height=224, bg=YELLOW, highlightthickness=0)  # highlightthickness will remove the border!
# Add image to the canvas
tomato_img = tk.PhotoImage(file="tomato.png")
canvas.create_image(100, 112, image=tomato_img)  # Image in the center of the canvas, that's why x and y is half of width and height
# Note: You can't add to the image="tomato.png"!!! Firstly create PhotoImage !!!
# Now we have to position our canvas inside the window with pack or grid

# Display some text
timer_text = canvas.create_text(103, 130, text="00:00", fill="white", font=(FONT_NAME, 35, "bold"))  # With a little experimentation I figured the values 103 and 130 out
# Now we will use only grid not pack
canvas.grid(column=1, row=1)
# canvas.pack()  # The image is taking the entire space of the window, resize window with config

# We have to use "after()", this method takes an amount of time that it should wait and then after that amount of time
# it calls a function that you tell it to call
count_down(5)


# Add a title label
title_label = tk.Label(text="Timer", fg=GREEN, font=(FONT_NAME, 50), bg=YELLOW)
title_label.grid(column=1, row=0)

# Add the start button
start_button = tk.Button(text="Start")
start_button.grid(column=0, row=2)

# Add the reset button
reset_button = tk.Button(text="Reset")
reset_button.grid(column=2, row=2)

# Add the checkmark
check_marks = tk.Label(text="✔", fg=GREEN, bg=YELLOW)
check_marks.grid(column=1, row=3)




# ------------------------------------------------ #
root.mainloop()

```
 
</details>

<details>
 <summary>Part 6 of solution</summary>

Lets assign the timer to the start button!


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
# This GUI is event-driven, event-driven programming focuses on the events (messages) and their flow between different software components.
# So we can not use a while loop because "mainloop()" is already looping and checking if something happened
def start_timer():
    count_down(5)

# ---------------------------- COUNTDOWN MECHANISM ------------------------------- #
def count_down(count):
    canvas.itemconfig(timer_text, text=count)
    if count > 0:
        root.after(1000, count_down, count - 1)  # After 1 sec it call the funct. "say_something" and passes "Hello" as the input to the funct.


# ---------------------------- UI SETUP ------------------------------- #
# Create a new window
root = tk.Tk()
# Set title of the window
root.title("Pomodoro")
# Configer the window
root.config(padx=100, pady=50, bg=YELLOW) # Change the window background color with bg




# Create a canvas widget to place an image on the top of the canvas
canvas = tk.Canvas(width=200, height=224, bg=YELLOW, highlightthickness=0)  # highlightthickness will remove the border!
# Add image to the canvas
tomato_img = tk.PhotoImage(file="tomato.png")
canvas.create_image(100, 112, image=tomato_img)  # Image in the center of the canvas, that's why x and y is half of width and height
# Note: You can't add to the image="tomato.png"!!! Firstly create PhotoImage !!!
# Now we have to position our canvas inside the window with pack or grid

# Display some text
timer_text = canvas.create_text(103, 130, text="00:00", fill="white", font=(FONT_NAME, 35, "bold"))  # With a little experimentation I figured the values 103 and 130 out
# Now we will use only grid not pack
canvas.grid(column=1, row=1)
# canvas.pack()  # The image is taking the entire space of the window, resize window with config

# We have to use "after()", this method takes an amount of time that it should wait and then after that amount of time
# it calls a function that you tell it to call



# Add a title label
title_label = tk.Label(text="Timer", fg=GREEN, font=(FONT_NAME, 50), bg=YELLOW)
title_label.grid(column=1, row=0)

# Add the start button
start_button = tk.Button(text="Start", command=start_timer)
start_button.grid(column=0, row=2)

# Add the reset button
reset_button = tk.Button(text="Reset")
reset_button.grid(column=2, row=2)

# Add the checkmark
check_marks = tk.Label(text="✔", fg=GREEN, bg=YELLOW)
check_marks.grid(column=1, row=3)




# ------------------------------------------------ #
root.mainloop()

```
 
</details>

<details>
 <summary>Part 7 of solution</summary>

Now we create a timer with 25 minutes!

```python
import tkinter as tk
import math

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
# This GUI is event-driven, event-driven programming focuses on the events (messages) and their flow between different software components.
# So we can not use a while loop because "mainloop()" is already looping and checking if something happened
def start_timer():
    count_down(25 * 60)  # 25 minutes

# ---------------------------- COUNTDOWN MECHANISM ------------------------------- #
def count_down(count):
    # Format time to 00:00
    count_min = math.floor(count / 60)  # Example 4.8 will be 4.0
    count_sec = count % 60

    canvas.itemconfig(timer_text, text=f"{count_min}:{count_sec}")
    if count > 0:
        root.after(1000, count_down, count - 1)  # After 1 sec it call the funct. "say_something" and passes "Hello" as the input to the funct.


# ---------------------------- UI SETUP ------------------------------- #
# Create a new window
root = tk.Tk()
# Set title of the window
root.title("Pomodoro")
# Configer the window
root.config(padx=100, pady=50, bg=YELLOW) # Change the window background color with bg




# Create a canvas widget to place an image on the top of the canvas
canvas = tk.Canvas(width=200, height=224, bg=YELLOW, highlightthickness=0)  # highlightthickness will remove the border!
# Add image to the canvas
tomato_img = tk.PhotoImage(file="tomato.png")
canvas.create_image(100, 112, image=tomato_img)  # Image in the center of the canvas, that's why x and y is half of width and height
# Note: You can't add to the image="tomato.png"!!! Firstly create PhotoImage !!!
# Now we have to position our canvas inside the window with pack or grid

# Display some text
timer_text = canvas.create_text(103, 130, text="00:00", fill="white", font=(FONT_NAME, 35, "bold"))  # With a little experimentation I figured the values 103 and 130 out
# Now we will use only grid not pack
canvas.grid(column=1, row=1)
# canvas.pack()  # The image is taking the entire space of the window, resize window with config

# We have to use "after()", this method takes an amount of time that it should wait and then after that amount of time
# it calls a function that you tell it to call



# Add a title label
title_label = tk.Label(text="Timer", fg=GREEN, font=(FONT_NAME, 50), bg=YELLOW)
title_label.grid(column=1, row=0)

# Add the start button
start_button = tk.Button(text="Start", command=start_timer)
start_button.grid(column=0, row=2)

# Add the reset button
reset_button = tk.Button(text="Reset")
reset_button.grid(column=2, row=2)

# Add the checkmark
check_marks = tk.Label(text="✔", fg=GREEN, bg=YELLOW)
check_marks.grid(column=1, row=3)




# ------------------------------------------------ #
root.mainloop()

```
 
</details>

<details>
 <summary>Part 8 of solution</summary>

Add reps and change the label from Timer to Work or Break!

```python
import tkinter as tk
import math
reps = 0

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
# This GUI is event-driven, event-driven programming focuses on the events (messages) and their flow between different software components.
# So we can not use a while loop because "mainloop()" is already looping and checking if something happened
def start_timer():
    # ------------ REPS ----------- #
    global reps
    reps += 1

    work_sec = WORK_MIN * 60
    short_break_sec = SHORT_BREAK_MIN * 60
    long_break_sec = LONG_BREAK_MIN * 60

    count_down(work_sec)  # 25 minutes

    if reps % 8 == 0:
        count_down(long_break_sec)
        title_label.config(text="Break", fg=RED)
    elif reps % 2 == 0:
        count_down(short_break_sec)
        title_label.config(text="Break", fg=PINK)
    else:
        count_down(work_sec)
        title_label.config(text="Work", fg=GREEN)

# ---------------------------- COUNTDOWN MECHANISM ------------------------------- #
def count_down(count):
    # Format time to 00:00
    count_min = math.floor(count / 60)  # Example 4.8 will be 4.0
    count_sec = count % 60
    # Display the first 0 in the time
    if count < 10:
        count_sec = f"0{count_sec}"

    canvas.itemconfig(timer_text, text=f"{count_min}:{count_sec}")
    if count > 0:
        root.after(1000, count_down, count - 1)  # After 1 sec it call the funct. "say_something" and passes "Hello" as the input to the funct.
    else:
        start_timer()

# ---------------------------- UI SETUP ------------------------------- #
# Create a new window
root = tk.Tk()
# Set title of the window
root.title("Pomodoro")
# Configer the window
root.config(padx=100, pady=50, bg=YELLOW) # Change the window background color with bg




# Create a canvas widget to place an image on the top of the canvas
canvas = tk.Canvas(width=200, height=224, bg=YELLOW, highlightthickness=0)  # highlightthickness will remove the border!
# Add image to the canvas
tomato_img = tk.PhotoImage(file="tomato.png")
canvas.create_image(100, 112, image=tomato_img)  # Image in the center of the canvas, that's why x and y is half of width and height
# Note: You can't add to the image="tomato.png"!!! Firstly create PhotoImage !!!
# Now we have to position our canvas inside the window with pack or grid

# Display some text
timer_text = canvas.create_text(103, 130, text="00:00", fill="white", font=(FONT_NAME, 35, "bold"))  # With a little experimentation I figured the values 103 and 130 out
# Now we will use only grid not pack
canvas.grid(column=1, row=1)
# canvas.pack()  # The image is taking the entire space of the window, resize window with config

# We have to use "after()", this method takes an amount of time that it should wait and then after that amount of time
# it calls a function that you tell it to call



# Add a title label
title_label = tk.Label(text="Timer", fg=GREEN, font=(FONT_NAME, 50), bg=YELLOW)
title_label.grid(column=1, row=0)

# Add the start button
start_button = tk.Button(text="Start", command=start_timer)
start_button.grid(column=0, row=2)

# Add the reset button
reset_button = tk.Button(text="Reset")
reset_button.grid(column=2, row=2)

# Add the checkmark
check_marks = tk.Label(text="✔", fg=GREEN, bg=YELLOW)
check_marks.grid(column=1, row=3)




# ------------------------------------------------ #
root.mainloop()

```
 
</details>


<details>
 <summary>FINAL solution</summary>


```python
import tkinter as tk
import math


# ---------------------------- CONSTANTS ------------------------------- #
PINK = "#e2979c"
RED = "#e7305b"
GREEN = "#9bdeac"
YELLOW = "#f7f5dd"
FONT_NAME = "Courier"
WORK_MIN = 1
SHORT_BREAK_MIN = 5
LONG_BREAK_MIN = 20
reps = 0
timer = None


# ---------------------------- TIMER RESET ------------------------------- #
def reset_timer():
    root.after_cancel(timer)
    canvas.itemconfig(timer_text, text="00:00")
    title_label.config(text="Timer")
    check_marks.config(text="")
    global reps
    reps = 0



# ---------------------------- TIMER MECHANISM ------------------------------- #
# This GUI is event-driven, event-driven programming focuses on the events (messages) and their flow between different software components.
# So we can not use a while loop because "mainloop()" is already looping and checking if something happened
def start_timer():
    # ------------ REPS ----------- #
    global reps
    reps += 1

    work_sec = WORK_MIN * 60
    short_break_sec = SHORT_BREAK_MIN * 60
    long_break_sec = LONG_BREAK_MIN * 60



    if reps % 8 == 0:
        count_down(long_break_sec)
        title_label.config(text="Break", fg=RED)
    elif reps % 2 == 0:
        count_down(short_break_sec)
        title_label.config(text="Break", fg=PINK)
    else:
        count_down(work_sec)
        title_label.config(text="Work", fg=GREEN)

# ---------------------------- COUNTDOWN MECHANISM ------------------------------- #
def count_down(count):
    # Format time to 00:00
    count_min = math.floor(count / 60)  # Example 4.8 will be 4.0
    count_sec = count % 60
    # Display the first 0 in the time
    if count < 10:
        count_sec = f"0{count_sec}"

    canvas.itemconfig(timer_text, text=f"{count_min}:{count_sec}")
    if count > 0:
        global timer
        timer = root.after(1000, count_down, count - 1)  # After 1 sec it call the funct. "say_something" and passes "Hello" as the input to the funct.

    else:
        start_timer()
        mark = ""
        work_seassions = math.floor(reps / 2)
        for _ in range(work_seassions):
            mark += "✓"
        check_marks.config(text="✓")


# ---------------------------- UI SETUP ------------------------------- #
# Create a new window
root = tk.Tk()
# Set title of the window
root.title("Pomodoro")
# Configer the window
root.config(padx=100, pady=50, bg=YELLOW) # Change the window background color with bg




# Create a canvas widget to place an image on the top of the canvas
canvas = tk.Canvas(width=200, height=224, bg=YELLOW, highlightthickness=0)  # highlightthickness will remove the border!
# Add image to the canvas
tomato_img = tk.PhotoImage(file="tomato.png")
canvas.create_image(100, 112, image=tomato_img)  # Image in the center of the canvas, that's why x and y is half of width and height
# Note: You can't add to the image="tomato.png"!!! Firstly create PhotoImage !!!
# Now we have to position our canvas inside the window with pack or grid

# Display some text
timer_text = canvas.create_text(103, 130, text="00:00", fill="white", font=(FONT_NAME, 35, "bold"))  # With a little experimentation I figured the values 103 and 130 out
# Now we will use only grid not pack
canvas.grid(column=1, row=1)
# canvas.pack()  # The image is taking the entire space of the window, resize window with config

# We have to use "after()", this method takes an amount of time that it should wait and then after that amount of time
# it calls a function that you tell it to call



# Add a title label
title_label = tk.Label(text="Timer", fg=GREEN, font=(FONT_NAME, 50), bg=YELLOW)
title_label.grid(column=1, row=0)

# Add the start button
start_button = tk.Button(text="Start", command=start_timer)
start_button.grid(column=0, row=2)

# Add the reset button
reset_button = tk.Button(text="Reset", command=reset_timer)
reset_button.grid(column=2, row=2)

# Add the checkmark
check_marks = tk.Label(fg=GREEN, bg=YELLOW)
check_marks.grid(column=1, row=3)




# ------------------------------------------------ #
root.mainloop()

```
 
</details>
