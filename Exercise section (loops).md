# Exercise section (loops)

1. Assignment
<br>

Write a program that produces the following output:

```python
# 15 inch = 38.1 cm
# 20 inch = 50.8 cm
# 25 inch = 63.5 cm
# 30 inch = 76.2 cm
# 35 inch = 88.9 cm
# 40 inch = 101.6 cm
```

The inch value was calculated by conversion with the factor of 2.54. No input by the user is required.

<details open>
<summary>Solution</summary>

  ```python
  # Create the inch numbers with a for loop
for inch in range(15, 45, 5):
    # Calculate the cm value
    cm = inch * 2.54
    # Print the values every loop run
    print(f"{inch} inch = {cm} cm")
 ``` 
  
</details>

2. Assignment
<br>
Write a program that repeatedly requests the user to enter a value in inches. The entered value should then be converted into centimeters and displayed. The program should be terminated after entering the value 0.

<details open>
<summary>Solution</summary>

  ```python
# Variable for the loop condition
stop_program = False
# Loop to calculate the cm value until user exits
while not stop_program:
    inch_value = float(input("Enter a value in Inch: "))
    cm_value = inch_value * 2.54
    print(f"{inch_value} Inch are {cm_value} cm!")
    # Variable to enter the if statement
    continue_loop = int(input("Enter a 0 to exit the program or other key to continue: "))
    if continue_loop == 0:
        # Set condition variable of the while loop to exit the loop
        stop_program = True

 ``` 
  
</details>
