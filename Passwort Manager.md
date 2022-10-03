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
