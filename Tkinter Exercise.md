# Tkinter Exercise

1. Exercise:
<br>
Create a GUI which converts km in miles.
<br>
The user can input in a text box the km which have to be converted!
<br>
1 km is 0,621371 miles!

<details>
 <summary>Solution</summary>

```python
import tkinter as tk

root = tk.Tk()
root.title("Length Converter")
root.config(padx=20, pady=20)


# ---------------------------------------------------- #


# Functions
def convert():
    km = float(km_input.get())  # Returns a string, we have to convert it with float
    miles = km * 0.621
    miles_result_label.config(text=f"{miles}")  # Here we have to add a string to the text parameter


# ---------------------------------------------------- #
# 1. Create all widgets
# 2. Use grid to lay out the widgets
# 3. Change the input size
# 4. Add padding
# 5. Create function to convert km to miles
# 6 Add to the button the command parameter
# In future you can try to catch errors in this program, what happens when you enter letters?
# Input box
km_input = tk.Entry(width=7)
km_input.grid(column=1, row=0)
# Show km
km_label = tk.Label(text="km")
km_label.grid(column=2, row=0)
# Label for information
is_equal_label = tk.Label(text="is equal to")
is_equal_label.grid(column=0, row=1)
# Output label
miles_result_label = tk.Label(text="0")
miles_result_label.grid(column=1, row=1)
# Show miles
miles_label = tk.Label(text="miles")
miles_label.grid(column=2, row=1)
# Button for calculation
calc_button = tk.Button(text="Calculate", command=convert)
calc_button.grid(column=1, row=2)
# ---------------------------------------------------- #
root.mainloop()
  
```
  
</details>

2. Exercise:
<br>
Create a graphical application in Python Tkinter that asks the user to enter two integers and displays their sum as shown in the figure below:

<details>
 <summary>Solution</summary>

```python
import tkinter as tk

root = tk.Tk()
root.title("Calculation")
root.config(padx=20, pady=20)
# Prevent the user to resize the window
root.resizable(False, False)

# ---------------------------------------------------- #


# Functions
def calc():
    m_value = float(input_m.get())
    n_value = float(input_n.get())
    sum_value = n_value + m_value
    result.config(text=f"{sum_value}")


# ---------------------------------------------------- #
# Label for description (columnspan: Set the number of adjacent columns that the widget can span.)
description_label = tk.Label(text="Enter a value for M and N for addition.")
description_label.grid(column=0, row=4, columnspan=2, pady=20)
# Label for value M
label_m = tk.Label(text="Enter the value of M:")
label_m.grid(column=0, row=0)
# Label for value N
label_n = tk.Label(text="Enter the value of N:")
label_n.grid(column=0, row=1)
# Input box for M
input_m = tk.Entry()
input_m.grid(column=1, row=0)
# Input box for N
input_n = tk.Entry()
input_n.grid(column=1, row=1)
# Label to display the result
result = tk.Label(text="")
result.grid(column=1, row=2)
# Button for calculation
calc_button = tk.Button(text="Calculate", command=calc)
calc_button.grid(column=1, row=3)
# ---------------------------------------------------- #
root.mainloop()


```
  
</details>

3. Exercise:
<br>
Write a program in Python that lists all divisors of a given integer N.
Create a program in Python that which a Tkinter window asking the user to enter an integer N and returns all the divisors of N.

<details>
 <summary>Solution</summary>

```python
import tkinter as tk

root = tk.Tk()
root.title("Calculation")
root.config(padx=20, pady=20)
# Prevent the user to resize the window
root.resizable(False, False)


# ---------------------------------------------------- #
# Functions
def calc_divisor():
    divisors = []
    number = int(input_N.get())
    for divisor in range(1, number):
        if number % divisor == 0:
            divisors.append(str(divisor))
    # Take each element of the list and separate them by a comma
    divisor_output_label.config(text=f"{', '.join(divisors)}")


# ---------------------------------------------------- #
# Label for the input
input_n_label = tk.Label(text="Enter the value of N")
input_n_label.grid(column=0, row=0)
# Label for the divisor information
divisor_label = tk.Label(text="The divisor of N:")
divisor_label.grid(column=0, row=1)
# Label to show the divisors
divisor_output_label = tk.Label(text="")
divisor_output_label.grid(column=1, row=1)
# Button for calculation
cal_button = tk.Button(text="Calculate", command=calc_divisor)
cal_button.grid(column=1, row=2)
# Input box
input_N = tk.Entry()
input_N.grid(column=1, row=0)
# ---------------------------------------------------- #
root.mainloop()

```
  
</details>
