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
