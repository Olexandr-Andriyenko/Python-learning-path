# Exercise section (functions)

1. Assignment <br>
<br>
Write two functions that calculates the area and perimeter of a rectangle. <br>
The functions should return the area and the perimeter, to save the values. <br>
Add up the area and perimeter using the return values of the functions. <br>
Summarize the results "nicely" and output them to the console.
<br>
<br>
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

2. Assignment <br>
<br> 
The body mass index (short: BMI) is a number that can be used to estimate whether you are underweight, normal or overweight. One calculates this number according to the following formula: 
<br>
<br>
    
![CodeCogsEqn](https://user-images.githubusercontent.com/92121260/181480006-dc4e3e8b-069c-4b19-83db-0def0bca2aef.png)


The weight has the unit "kg" and height the unit "m". <br>
Write a function which returns the BMI value after user input.
<br>
<br>
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

3. Assignment <br> 
<br>
The optimal pulse for endurance sports depends on age. It can be determined with the formula P = 165 - 0.75*A. <br>
Where "A" is tge age in years.<br>
Write a function which calculates the optimal pulse and returns it.
<br>
<br>
<details>
<summary>Solution</summary>

```python
# Create a function to calculate the optimal pulse
def calc_pulse(age):
    optimal_pulse = 165 - 0.75 * age
    return optimal_pulse


# Here starts the actual program
# Calculating the optimal pulse by entering the age by the user
user_pulse = calc_pulse(int(input("Enter your age in years: ")))
print(user_pulse)
```

</details>

4. Assignment <br> 
<br>
In driving school, you learn the following formulas for calculating stopping distances: 
<br>
<br>

![CodeCogsEqn(1)](https://user-images.githubusercontent.com/92121260/181553819-295779a9-8c87-44dc-b4b9-ea9c53e69575.png)

![CodeCogsEqn(2)](https://user-images.githubusercontent.com/92121260/181557431-decb196f-7d50-4faf-bc41-df5c3ce42930.png)

![CodeCogsEqn(3)](https://user-images.githubusercontent.com/92121260/181559063-175b3078-5f57-416c-b66a-61d2407ca575.png)

The unit of the distances is meters and the velocity in km/h.
<br>
<br>
Build a function to calculate the stop distance depending on the speed.


<details>
<summary>Solution</summary>

```python
# Create a function to calculate the stop distance
def stop_distance(velocity):
    response_path = (velocity / 10) * 3
    brake_distance = (velocity / 10) ** 2
    stop_distance = response_path + brake_distance
    return stop_distance

# Here start the actual program
# Calculate the stop distance and print it "nicely" on the console
velocity = float(input("Enter the velocity of the vehicle: "))
way = stop_distance(velocity)
print(f"If you drive with the velocity {velocity} km/h, then you have a stop distance of {way} meters!")
```

</details>
