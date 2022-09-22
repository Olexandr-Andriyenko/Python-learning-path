# Creating GUI with Tkinter

We will learn the module tkinter to create GUI (graphical user interface)

```python
# Import the pre-installed module
import tkinter as tk
# Creating a new window (a bit equivalent to the screen from turtle module)
window = tk.Tk()
# Keep the window open, check last like inside the program for information!
# -------------------------------------------------------------------------------------- #
# Change the title of the program
window.title("My First GUI Program")
# Change size of window
window.minsize(width=500, height=300)
# Create a label
# We can change this label like text...
my_label = tk.Label(text="I am a Label" ,font=("Arial", 24, "bold"))
# Specify how this label has to be layout on the window
my_label.pack()  # pack() method center the label and place it on the window
my_label.pack(side="left")  # You can use options of the pack method to change some properties
# -------------------------------------------------------------------------------------- #
# We need to keep the window on screen, This line of code has to by at the end of your prograam
window.mainloop()
```

## Buttons, Entry and Setting Component Options

Do noit forget to read the [documentation](http://tcl.tk/man/tcl8.6/TkCmd/contents.htm) !

```python
# Import the pre-installed module
import tkinter as tk
# Creating a new window (a bit equivalent to the screen from turtle module)
window = tk.Tk()
# Keep the window open, check last like inside the program for information!
# -------------------------------------------------------------------------------------- #
# Change the title of the program
window.title("My First GUI Program")
# Change size of window
window.minsize(width=500, height=300)
# Create a label
# We can change this label like text...
my_label = tk.Label(text="I am a Label", font=("Arial", 24, "bold"))
# Specify how this label has to be layout on the window
my_label.pack()  # pack() method center the label and place it on the window
my_label.pack(side="left")  # You can use options of the pack method to change some properties
# -------------------------------------------------------------------------------------- #
# Change the text from the initial text that it displays
my_label["text"] = "New Text"
# The other possible way ist to use the config method to change the text
my_label.config(text="Another New Text")
# Create a button

# This will be explained latter
def button_click():
     print("I got clicked")
# Create command at the button object

button = tk.Button(text="Click Me",command=button_click)
# Display the button
button.pack()
# Position the label
my_label.pack(side="bottom")
# Let's make the button "work" (add this function above the button object)
# def button_click():
#     print("I got clicked")


# -------------------------------------------------------------------------------------- #
# We need to keep the window on screen, This line of code has to by at the end of your prograam
window.mainloop()

```

The button should change the text of the labbel:

```python
# Import the pre-installed module
import tkinter as tk
# Creating a new window (a bit equivalent to the screen from turtle module)
window = tk.Tk()
# Keep the window open, check last like inside the program for information!
# -------------------------------------------------------------------------------------- #
# Change the title of the program
window.title("My First GUI Program")
# Change size of window
window.minsize(width=500, height=300)
# Create a label
# We can change this label like text...
my_label = tk.Label(text="I am a Label", font=("Arial", 24, "bold"))
# Specify how this label has to be layout on the window
my_label.pack()  # pack() method center the label and place it on the window
my_label.pack(side="left")  # You can use options of the pack method to change some properties
# -------------------------------------------------------------------------------------- #
# Change the text from the initial text that it displays
my_label["text"] = "New Text"
# The other possible way ist to use the config method to change the text
my_label.config(text="Another New Text")
# Create a button

# This will be explained latter
def button_click():
     my_label.config(text="I got clicked")
# Create command at the button object


button = tk.Button(text="Click Me",command=button_click)
# Display the button
button.pack()
# Position the label
my_label.pack(side="bottom")
# Let's make the button "work" (add this function above the button object)
# def button_click():
#     print("I got clicked")


# -------------------------------------------------------------------------------------- #
# We need to keep the window on screen, This line of code has to by at the end of your prograam
window.mainloop()

```

Create a input and shot the writen text inside the labbel:

```python
# Import the pre-installed module
import tkinter as tk
# Creating a new window (a bit equivalent to the screen from turtle module)
window = tk.Tk()
# Keep the window open, check last like inside the program for information!
# -------------------------------------------------------------------------------------- #
# Change the title of the program
window.title("My First GUI Program")
# Change size of window
window.minsize(width=500, height=300)
# Create a label
# We can change this label like text...
my_label = tk.Label(text="I am a Label", font=("Arial", 24, "bold"))
# Specify how this label has to be layout on the window
my_label.pack()  # pack() method center the label and place it on the window
my_label.pack(side="left")  # You can use options of the pack method to change some properties
# -------------------------------------------------------------------------------------- #
# Change the text from the initial text that it displays
my_label["text"] = "New Text"
# The other possible way ist to use the config method to change the text
my_label.config(text="Another New Text")
# Create a button

# This will be explained latter
def button_click():
     # my_label.config(text="I got clicked")
# Create command at the button object

     # Code for input
     entry = input.get()
     my_label.config(text=entry)


button = tk.Button(text="Click Me",command=button_click)
# Display the button
button.pack()
# Position the label
my_label.pack(side="bottom")
# Let's make the button "work" (add this function above the button object)
# def button_click():
#     print("I got clicked")

# Create entry
input = tk.Entry(width=10)
input.pack()
# Return the entry back

# -------------------------------------------------------------------------------------- #
# We need to keep the window on screen, This line of code has to by at the end of your prograam
window.mainloop()
```

## Radiobuttons, Scales, Checkbuttons and more
