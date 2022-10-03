# Passwort Manager

Use this image:

<p align="left">
<img src="https://github.com/Olexandr-Andriyenko/Python-learning-path/blob/main/illustrations/img57.png" width="250">
<p>

Starting code:

```python
# ---------------------------- PASSWORD GENERATOR ------------------------------- #


# ---------------------------- SAVE PASSWORD ------------------------------- #


# ---------------------------- UI SETUP ------------------------------- #
```

<details>
 <summary>Part 1 of solution</summary>

Creating the UI

```python
import tkinter as tk


# ---------------------------- PASSWORD GENERATOR ------------------------------- #

# ---------------------------- SAVE PASSWORD ------------------------------- #

# ---------------------------- UI SETUP ------------------------------- #
root = tk.Tk()
root.title("Passwort Manager")
root.config(padx=50, pady=50)
# Create the canvas to place the logo
image_logo = tk.PhotoImage(file="img57.png")
canvas = tk.Canvas(height=200, width=200)
canvas.create_image(100, 100, image=image_logo)
canvas.grid(row=0, column=1)
# Create all labels
website_label = tk.Label(text="Website:")
website_label.grid(row=1, column=0)
email_label = tk.Label(text="Email/Username:")
email_label.grid(row=2, column=0)
passwort_label = tk.Label(text="Passwort:")
passwort_label.grid(row=3, column=0)
# Create the input fields
website_entry = tk.Entry(width=50)
website_entry.grid(row=1, column=1, columnspan=2)
email_entry = tk.Entry(width=50)
email_entry.grid(row=2, column=1, columnspan=2)
passwort_entry = tk.Entry(width=32)
passwort_entry.grid(row=3, column=1)
# Create buttons
generate_passwort_button = tk.Button(text="Generate Passwort")
generate_passwort_button.grid(row=3, column=2)
add_button = tk.Button(text="Add")
add_button.grid(row=4, column=1, columnspan=2)
# ------------------------ MAINLOOP ------------------------------- #
root.mainloop()


```
  
</details>

<details>
 <summary>Part 2 of solution</summary>

Save the data inside a txt file

```python
import tkinter as tk


# ---------------------------- PASSWORD GENERATOR ------------------------------- #

# ---------------------------- SAVE PASSWORD ------------------------------- #
def save():
    # Get the data from the entrys
    website = website_entry.get()
    email = email_entry.get()
    passwort = passwort_entry.get()
    # Open/Create a txt to save data
    with open("data.txt", "a") as data_file:
        data_file.write((f"{website} | {email} | {passwort}\n"))

    # Clear the enetered data
    website_entry.delete(0, tk.END)
    passwort_entry.delete(0, tk.END)
# ---------------------------- UI SETUP ------------------------------- #
root = tk.Tk()
root.title("Passwort Manager")
root.config(padx=50, pady=50)
# Create the canvas to place the logo
image_logo = tk.PhotoImage(file="img57.png")
canvas = tk.Canvas(height=200, width=200)
canvas.create_image(100, 100, image=image_logo)
canvas.grid(row=0, column=1)
# Create all labels
website_label = tk.Label(text="Website:")
website_label.grid(row=1, column=0)
email_label = tk.Label(text="Email/Username:")
email_label.grid(row=2, column=0)
passwort_label = tk.Label(text="Passwort:")
passwort_label.grid(row=3, column=0)
# Create the input fields
website_entry = tk.Entry(width=50)
website_entry.grid(row=1, column=1, columnspan=2)
website_entry.focus()  # Place the courser inside this entry at the start
email_entry = tk.Entry(width=50)
email_entry.grid(row=2, column=1, columnspan=2)
email_entry.insert(0, "olexandr@e_mail.com")  # Insert pre-written text inside the entry
passwort_entry = tk.Entry(width=32)
passwort_entry.grid(row=3, column=1)
# Create buttons
generate_passwort_button = tk.Button(text="Generate Passwort")
generate_passwort_button.grid(row=3, column=2)
add_button = tk.Button(text="Add", command=save)
add_button.grid(row=4, column=1, columnspan=2)
# ------------------------ MAINLOOP ------------------------------- #
root.mainloop()


```
  
</details>

<details>
 <summary>Part 3 of solution</summary>

Add messageboxes and check whether the entry field is empty

```python
import tkinter as tk
from tkinter import messagebox



# ---------------------------- PASSWORD GENERATOR ------------------------------- #

# ---------------------------- SAVE PASSWORD ------------------------------- #
def save():
    # Get the data from the entrys
    website = website_entry.get()
    email = email_entry.get()
    passwort = passwort_entry.get()

    # Check whether the entry empty
    if len(website) == 0 or len(passwort) == 0:
        messagebox.showinfo(title="Oops", message="Empty fields not allowed!")
    else:

        # Ask the user if he is sure to save
        is_ok = messagebox.askokcancel(title=website, message=f"These are the details entered: \nEmail: {email} \nPasswort: {passwort} \nIs it ok to save?")
        if is_ok:
            # Open/Create a txt to save data
            with open("data.txt", "a") as data_file:
                data_file.write((f"{website} | {email} | {passwort}\n"))
            # Clear the enetered data
            website_entry.delete(0, tk.END)
            passwort_entry.delete(0, tk.END)
# ---------------------------- UI SETUP ------------------------------- #
root = tk.Tk()
root.title("Passwort Manager")
root.config(padx=50, pady=50)
# Create the canvas to place the logo
image_logo = tk.PhotoImage(file="img57.png")
canvas = tk.Canvas(height=200, width=200)
canvas.create_image(100, 100, image=image_logo)
canvas.grid(row=0, column=1)
# Create all labels
website_label = tk.Label(text="Website:")
website_label.grid(row=1, column=0)
email_label = tk.Label(text="Email/Username:")
email_label.grid(row=2, column=0)
passwort_label = tk.Label(text="Passwort:")
passwort_label.grid(row=3, column=0)
# Create the input fields
website_entry = tk.Entry(width=50)
website_entry.grid(row=1, column=1, columnspan=2)
website_entry.focus()  # Place the courser inside this entry at the start
email_entry = tk.Entry(width=50)
email_entry.grid(row=2, column=1, columnspan=2)
email_entry.insert(0, "olexandr@e_mail.com")  # Insert pre-written text inside the entry
passwort_entry = tk.Entry(width=32)
passwort_entry.grid(row=3, column=1)
# Create buttons
generate_passwort_button = tk.Button(text="Generate Passwort")
generate_passwort_button.grid(row=3, column=2)
add_button = tk.Button(text="Add", command=save)
add_button.grid(row=4, column=1, columnspan=2)
# ------------------------ MAINLOOP ------------------------------- #
root.mainloop()


```
  
</details>

<details>
 <summary>FINAL solution</summary>

Generate paswort and copy it without shortcuts!

```python
import tkinter as tk
from tkinter import messagebox
import random
# Modul to copy automatically without press buttons
import pyperclip


# ---------------------------- PASSWORD GENERATOR ------------------------------- #
def generate_pass():
    letters = ['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j', 'k', 'l', 'm', 'n', 'o', 'p', 'q', 'r', 's', 't', 'u', 'v', 'w', 'x', 'y', 'z', 'A', 'B', 'C', 'D', 'E', 'F', 'G', 'H', 'I', 'J', 'K', 'L', 'M', 'N', 'O', 'P', 'Q', 'R', 'S', 'T', 'U', 'V', 'W', 'X', 'Y', 'Z']
    numbers = ['0', '1', '2', '3', '4', '5', '6', '7', '8', '9']
    symbols = ['!', '#', '$', '%', '&', '(', ')', '*', '+']

    nr_letters = random.randint(8, 10)
    nr_symbols = random.randint(2, 4)
    nr_numbers = random.randint(2, 4)

    password_list = []

    for char in range(nr_letters):
      password_list.append(random.choice(letters))

    for char in range(nr_symbols):
      password_list += random.choice(symbols)

    for char in range(nr_numbers):
      password_list += random.choice(numbers)

    random.shuffle(password_list)

    password = ""
    for char in password_list:
      password += char
    # Add passwort to the entry
    passwort_entry.insert(0, password)
    # Copy passwort
    pyperclip.copy(password)

# ---------------------------- SAVE PASSWORD ------------------------------- #
def save():
    # Get the data from the entrys
    website = website_entry.get()
    email = email_entry.get()
    passwort = passwort_entry.get()

    # Check whether the entry empty
    if len(website) == 0 or len(passwort) == 0:
        messagebox.showinfo(title="Oops", message="Empty fields not allowed!")
    else:

        # Ask the user if he is sure to save
        is_ok = messagebox.askokcancel(title=website, message=f"These are the details entered: \nEmail: {email} \nPasswort: {passwort} \nIs it ok to save?")
        if is_ok:
            # Open/Create a txt to save data
            with open("data.txt", "a") as data_file:
                data_file.write(f"{website} | {email} | {passwort}\n")
            # Clear the enetered data
            website_entry.delete(0, tk.END)
            passwort_entry.delete(0, tk.END)
# ---------------------------- UI SETUP ------------------------------- #
root = tk.Tk()
root.title("Passwort Manager")
root.config(padx=50, pady=50)
# Create the canvas to place the logo
image_logo = tk.PhotoImage(file="img57.png")
canvas = tk.Canvas(height=200, width=200)
canvas.create_image(100, 100, image=image_logo)
canvas.grid(row=0, column=1)
# Create all labels
website_label = tk.Label(text="Website:")
website_label.grid(row=1, column=0)
email_label = tk.Label(text="Email/Username:")
email_label.grid(row=2, column=0)
passwort_label = tk.Label(text="Passwort:")
passwort_label.grid(row=3, column=0)
# Create the input fields
website_entry = tk.Entry(width=50)
website_entry.grid(row=1, column=1, columnspan=2)
website_entry.focus()  # Place the courser inside this entry at the start
email_entry = tk.Entry(width=50)
email_entry.grid(row=2, column=1, columnspan=2)
email_entry.insert(0, "olexandr@e_mail.com")  # Insert pre-written text inside the entry
passwort_entry = tk.Entry(width=32)
passwort_entry.grid(row=3, column=1)
# Create buttons
generate_passwort_button = tk.Button(text="Generate Passwort", command=generate_pass)
generate_passwort_button.grid(row=3, column=2)
add_button = tk.Button(text="Add", command=save)
add_button.grid(row=4, column=1, columnspan=2)
# ------------------------ MAINLOOP ------------------------------- #
root.mainloop()


```
  
</details>
