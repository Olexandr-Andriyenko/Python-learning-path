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

```python
from tkinter import *

#Creating a new window and configurations
window = Tk()
window.title("Widget Examples")
window.minsize(width=500, height=500)

#Labels
label = Label(text="This is old text")
label.config(text="This is new text")
label.pack()

#Buttons
def action():
    print("Do something")

#calls action() when pressed
button = Button(text="Click Me", command=action)
button.pack()

#Entries
entry = Entry(width=30)
#Add some text to begin with
entry.insert(END, string="Some text to begin with.")
#Gets text in entry
print(entry.get())
entry.pack()

#Text
text = Text(height=5, width=30)
#Puts cursor in textbox.
text.focus()
#Adds some text to begin with.
text.insert(END, "Example of multi-line text entry.")
#Get's current value in textbox at line 1, character 0
print(text.get("1.0", END))
text.pack()

#Spinbox
def spinbox_used():
    #gets the current value in spinbox.
    print(spinbox.get())
spinbox = Spinbox(from_=0, to=10, width=5, command=spinbox_used)
spinbox.pack()

#Scale
#Called with current scale value.
def scale_used(value):
    print(value)
scale = Scale(from_=0, to=100, command=scale_used)
scale.pack()

#Checkbutton
def checkbutton_used():
    #Prints 1 if On button checked, otherwise 0.
    print(checked_state.get())
#variable to hold on to checked state, 0 is off, 1 is on.
checked_state = IntVar()
checkbutton = Checkbutton(text="Is On?", variable=checked_state, command=checkbutton_used)
checked_state.get()
checkbutton.pack()

#Radiobutton
def radio_used():
    print(radio_state.get())
#Variable to hold on to which radio button value is checked.
radio_state = IntVar()
radiobutton1 = Radiobutton(text="Option1", value=1, variable=radio_state, command=radio_used)
radiobutton2 = Radiobutton(text="Option2", value=2, variable=radio_state, command=radio_used)
radiobutton1.pack()
radiobutton2.pack()


#Listbox
def listbox_used(event):
    # Gets current selection from listbox
    print(listbox.get(listbox.curselection()))

listbox = Listbox(height=4)
fruits = ["Apple", "Pear", "Orange", "Banana"]
for item in fruits:
    listbox.insert(fruits.index(item), item)
listbox.bind("<<ListboxSelect>>", listbox_used)
listbox.pack()

window.mainloop()

```

## Layout: pack, place, grid

The `pack()` method will always start from the top and then pack every other widget just below the previous one. (You can use the side parameter!)
<br>
The `place()` method is all about precise positioning, you cana provide a x and y value. (x=0 and y=0 is the top left corner!)
<br>
The `grid` method is really simple and most used layout concept. It devides the program into any number of columns and rows.

![Tkinter-grid-Grid-Geometry](https://user-images.githubusercontent.com/92121260/191913991-a7d091d1-6d08-437a-87ae-42cc43b04740.png)

```python
from tkinter import *

# Creating a new window and configurations
window = Tk()
window.title("Widget Examples")
window.minsize(width=500, height=500)
# Add a bit padding
window.config(padx=100, pady=20)

# Label
my_label = Label(text="Random text...", font=("Arial", 24, "bold"))
my_label.grid(column=0, row=0)

# Button
my_button = Button(text="Click me", font=("Arial", 24, "bold"))
my_button.grid(column=1, row=1)

# Button
my_button_1 = Button(text="Click me", font=("Arial", 24, "bold"))
my_button_1.grid(column=2, row=0)

# Entry
input = Entry(width=10)
input.grid(column=3, row=2)

window.mainloop()
```
