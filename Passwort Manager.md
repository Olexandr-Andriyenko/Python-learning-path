# Passwort Manager

Use this image:

<p align="left">
<img src="https://github.com/Olexandr-Andriyenko/Python-learning-path/blob/main/illustrations/img57.png" width="250">
<p>

Layout should look like this:

<p align="left">
<img src="https://github.com/Olexandr-Andriyenko/Python-learning-path/blob/main/illustrations/img58.PNG" width="350">
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

## Improve the program by using  exception handling

We already know different types of errors:

```python
# Examples for different errors

# FileNotFound
with open ("a_file.txt") as file:
    file.read()

# KeyError
a_dictionary = {"key": "value"}
value = a_dictionary["non_existent_key"]

# IndexError
fruit_list = ["Apple", "Banana", "Pear"]
fruit = fruit_list[3]

# TypeError
text = "abc"
print(text + 5)
```

[Murphy's law:](https://en.wikipedia.org/wiki/Murphy%27s_law) “Anything that can go wrong will go wrong.”
<br>
That is why we have to take a closer look at critical points in our code and try to catch the errors.
<br>
<br>
Lets take a look at some examples of catchning errors the right way:

```python

# FileNotFound error could happen
try:
    file = open("a_file.txt")
    a_dictionary = {"key": "value"}
    value = a_dictionary["key_nonExisting"]  # Change the key for success try run
except FileNotFoundError:  # A specific error!!!
    print("There was an error!")
    file = open("a_file.txt", "w")
    file.write("Text...")
except KeyError as error_message:
    print(f"The key {error_message} does not exist!")
else:
    content = file.read()
    print(content)  # Will only be executed if the try-block was error free
finally:
    file.close()

```

It is even possible to generate own exceptions, for this we will use the `raise` keyword:

```python

# FileNotFound error could happen
try:
    file = open("a_file.txt")
    a_dictionary = {"key": "value"}
    value = a_dictionary["key_nonExisting"]  # Change the key for success try run
except FileNotFoundError:  # A specific error!!!
    print("There was an error!")
    file = open("a_file.txt", "w")
    file.write("Text...")
except KeyError as error_message:
    print(f"The key {error_message} does not exist!")
else:
    content = file.read()
    print(content)  # Will only be executed if the try-block was error free
finally:
    file.close()
    # Raise an exception by my own, even if there is no error
    raise KeyError("This is an error that I made up!")

```

One more example catching error inside out BMI calculator:

```python
# BMI calculation

height = float(input("Height: "))  # Unit is m
weight = int(input("Weight: "))  # Unit is kg

# Raise our own exception if the inputs are unrealistic
if height > 3:
    raise ValueError("Human height should not be over 3 meters!")

bmi = weight / height ** 2
print(bmi)
```

### Exercises
 
1. Exercise: Catch the exceptions and make sure the code runs without crashing! If the user enters something that is out of range just print a default output of "Fruit pie".

```python
fruits = ["Apple", "Pear", "Orange"]


def make_pie(index):
    fruit = fruits[index]
    print(fruit + "pie")


make_pie(4)
```

<details>
 <summary>Solution</summary>


```python
# Catch the exceptions and make sure the code runs without crashing!
fruits = ["Apple", "Pear", "Orange"]


def make_pie(index):
    try:
        fruit = fruits[index]
        print(fruit + "pie")
    except IndexError as error_message:
        print("Fruit pie")
    else:
        print(fruit + "pie")


make_pie(4)

```
  
</details>

2. Exercise: We have got some buggy code, try running the code. The code will crash and give you a KeyError. This is because some of the posts in the facebook_posts do not have any "Likes".
<br>
 
```python
facebook_posts = [
    {'Likes': 21, 'Comments': 2}, 
    {'Likes': 13, 'Comments': 2, 'Shares': 1}, 
    {'Likes': 33, 'Comments': 8, 'Shares': 3}, 
    {'Comments': 4, 'Shares': 2}, 
    {'Comments': 1, 'Shares': 1}, 
    {'Likes': 19, 'Comments': 3}
]

total_likes = 0

for post in facebook_posts:
    total_likes = total_likes + post['Likes']


print(total_likes)
```
 
<br>
Catch the exceptions and make sure the code runs without crashing!

<details>
 <summary>Solution</summary>


```python
facebook_posts = [
    {'Likes': 21, 'Comments': 2}, 
    {'Likes': 13, 'Comments': 2, 'Shares': 1}, 
    {'Likes': 33, 'Comments': 8, 'Shares': 3}, 
    {'Comments': 4, 'Shares': 2}, 
    {'Comments': 1, 'Shares': 1}, 
    {'Likes': 19, 'Comments': 3}
]

total_likes = 0

for post in facebook_posts:
    try:
        total_likes = total_likes + post['Likes']
    except KeyError:
        pass
    # Instead of pass you can use this code:
    # total_likes += 0


print(total_likes)
```
  
</details>

### Lets start improving the passwort manager program
 
- We will add a search functionality (add more widgets)
- Switch from saving data to a text file, to a JSON(JavaScriptObjectNotation) file

To work with JSON data we can use the inbuild JSON libary. Then we can write, read and update out data inside the JSON file.

<details>
 <summary>Add JSON file and exception handling</summary>


```python
import tkinter as tk
from tkinter import messagebox
import random
# Modul to copy automatically without press buttons
import pyperclip
import json


# ---------------------------- PASSWORD GENERATOR ------------------------------- #
def generate_pass():
    letters = ['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j', 'k', 'l', 'm', 'n', 'o', 'p', 'q', 'r', 's', 't', 'u',
               'v', 'w', 'x', 'y', 'z', 'A', 'B', 'C', 'D', 'E', 'F', 'G', 'H', 'I', 'J', 'K', 'L', 'M', 'N', 'O', 'P',
               'Q', 'R', 'S', 'T', 'U', 'V', 'W', 'X', 'Y', 'Z']
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
    # Dictionary with data
    new_data = {
        website: {
            "email": email,
            "passwort": passwort,
        }}

    # Check whether the entry empty
    if len(website) == 0 or len(passwort) == 0:
        messagebox.showinfo(title="Oops", message="Empty fields not allowed!")
    else:
        # JSON file have to be filled and created before
        try:
            with open("data.json", "r") as data_file:  # Change the format and open mode
            # Read old data
                data = json.load(data_file)
        except FileNotFoundError:
            with open("data.json", "w") as data_file:
                json.dump(new_data, data_file, indent=4)
        else:
            # Update json file with new data
            data.update(new_data)
            with open("data.json", "w") as data_file:
                # Saving updated data
                json.dump(data, data_file, indent=4)  # indent for easier read, dump for write in file
        finally:
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

<details>
 <summary>Add search button</summary>


```python
import tkinter as tk
from tkinter import messagebox
import random
# Modul to copy automatically without press buttons
import pyperclip
import json


# ---------------------------- PASSWORD GENERATOR ------------------------------- #
def generate_pass():
    letters = ['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j', 'k', 'l', 'm', 'n', 'o', 'p', 'q', 'r', 's', 't', 'u',
               'v', 'w', 'x', 'y', 'z', 'A', 'B', 'C', 'D', 'E', 'F', 'G', 'H', 'I', 'J', 'K', 'L', 'M', 'N', 'O', 'P',
               'Q', 'R', 'S', 'T', 'U', 'V', 'W', 'X', 'Y', 'Z']
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
    # Dictionary with data
    new_data = {
        website: {
            "email": email,
            "passwort": passwort,
        }}

    # Check whether the entry empty
    if len(website) == 0 or len(passwort) == 0:
        messagebox.showinfo(title="Oops", message="Empty fields not allowed!")
    else:
        # JSON file have to be filled and created before
        try:
            with open("data.json", "r") as data_file:  # Change the format and open mode
            # Read old data
                data = json.load(data_file)
        except FileNotFoundError:
            with open("data.json", "w") as data_file:
                json.dump(new_data, data_file, indent=4)
        else:
            # Update json file with new data
            data.update(new_data)
            with open("data.json", "w") as data_file:
                # Saving updated data
                json.dump(data, data_file, indent=4)  # indent for easier read, dump for write in file
        finally:
            # Clear the enetered data
            website_entry.delete(0, tk.END)
            passwort_entry.delete(0, tk.END)
# ---------------------------- FIND PASSWORT ------------------------------- #
def find_passwort():
    website = website_entry.get()  # Get the value from the entry
    try:
        with open("data.json") as data_file:
            data = json.load(data_file)  # This is a dictionary
    except FileNotFoundError:
        messagebox.showinfo(title="Error", message="No Data File Found")
    else:
        # Check if searched website is inside dictionary
        if website in data:
            email = data[website]["email"]
            passwort = data[website]["passwort"]
            messagebox.showinfo(title=website, message=f"Email: {email}\nPasswort: {passwort}")
        else:
            messagebox.showinfo(title="Error", message=f"No details for {website} exists.")

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
website_entry = tk.Entry(width=32)
website_entry.grid(row=1, column=1)
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
# Add elements for search functionality
search_button = tk.Button(text="Search", width=13, command=find_passwort)
search_button.grid(row=1, column=2)
# ------------------------ MAINLOOP ------------------------------- #
root.mainloop()

```
  
</details>
