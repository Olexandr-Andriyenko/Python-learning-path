# Exercise section (functions)

1. Write two functions that calculates the area and perimeter of a rectangle. <br>
   The functions should return the area and the perimeter, to save the values. <br>
   Add up the area and perimeter using the return values of the functions. <br>
   Summarize the results "nicely" and output them to the console.
   
<details>
<summary>Solution</summary>

```python
# Create a function to calculate the area
def rectangle_area(width, length):
    area = width * length
    return area


# Create a function to calculate the perimeter
def rectangle_perimeter(width, length):
    perimeter = 2 * width + 2 * length
    return perimeter


# Now we ask the user to input the width and length
# Do not forget to convert the string input in a float data type
width = float(input("Enter the width of the rectangle: "))
length = float(input("Enter the length of the rectangle: "))
# We use the functions to calculate the area and perimeter
area = rectangle_area(width, length)
perimeter = rectangle_perimeter(width, length)
# We print the results in the console
print(f"A rectangle with a length of {length} units and width of {width} units has a\narea of {area} square units and a perimeter of {perimeter} square units!")
```

</details>

2. The body mass index (short: BMI) is a number that can be used to estimate whether you are underweight, normal or overweight. One calculates this number according to the following formula: 
<br>

![CodeCogsEqn](https://user-images.githubusercontent.com/92121260/181480006-dc4e3e8b-069c-4b19-83db-0def0bca2aef.png)

<br>
The weight has the unit "kg" and height the unit "m". <br>
Write a function which returns the BMI value after user input.
<details>
<summary>Solution</summary>

```python
# Create a function to calculate the BMI
def calc_bmi(weight, height):
    # Devide by 100 to convert centimeters in meters
    bmi = weight / (height/100) ** 2
    return bmi


# Here starts the actual program
# Calculating BMI by users input
user_bmi = calc_bmi(float(input("Enter your weight in kg: ")), float(input("Enter your height in cm: ")))
print(f"Your bmi is: {user_bmi}")
```

</details>
