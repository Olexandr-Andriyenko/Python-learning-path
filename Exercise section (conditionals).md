# Exercise section (conditionals)
1. Assignment
<br>
<br>
Create a program for tax calculation. The user should be requested to enter his monthly gross salary. If the salary is over 3000 €, 22% tax is payable otherwise 18%.
The program should tell the user how much euro tax he has to pay.
<br>
<br>

<details open>
<summary>Solution</summary>

```python
# Ask the user for his salary
salary = float(input("Please input your salary: "))
# Differentiation of the income and calculation of tax
if salary > 3000:
    print("You have to pay a tax of 22%")
    tax = salary * 22 / 100
    print(f"You have to pay {tax}€ tax!")
else:
    print("You have to pay a tax of 18%")
    tax = salary * 18 / 100
    print(f"You have to pay {tax}€ tax!")
```  
  
</details>

2. Assignment
<br>
<br>
Create a program for tax calculation. The user should be requested to enter his monthly gross salary. Use the following table to calculate the tax:
<br>
<br>

| Salary                                            | Tax      |
| ------------------------------------------------- | -------- | 
| Over 4000€                                        | 26%      | 
| 2500€ until 4000€                                 | 22%      |  
| Less than 2500€                                   | 18%      |  

<details open>
<summary>Solution</summary>

```python
# Ask the user for his salary
salary = float(input("Please input your salary: "))
# Differentiation of the income and calculation of tax
if salary > 4000:
    print("you have to pay 26% tax!")
elif 2500 < salary < 4000:
    print("you have to pay 22% tax!")
else:
    print("you have to pay 18% tax!")
```  
  
</details>

3. Assignment
<br>
<br>
Create a program for tax calculation. The user should be requested to enter his monthly gross salary and his marital status. Use the following table to calculate the tax:

| Salary                                            | Tax      | Marital status |
| ------------------------------------------------- | -------- | -------------- |
| Over 4000€                                        | 26%      | Single         |
| Over 4000€                                        | 22%      |  Married       |
| Less than 4000€ or equal 4000€                    | 22%      | Single         |
| Less than 4000€ or equal 4000€                    | 18%      | Married        |


<details open>
<summary>Solution</summary>

```python
# Ask the user for his salary
salary = float(input("Please input your salary: "))
# Ask the user for his marital status
status = input("Enter your marital status: ")
# Differentiation of the income and calculation of tax
if salary > 4000 and status == "Single":
    print("you have to pay 26% tax!")
    tax = 4000 * 26 / 100
    print(f"You have to pay {tax}€ tax!")
elif salary > 4000 and status == "Married":
    print("you have to pay 22% tax!")
    tax = 4000 * 22 / 100
    print(f"You have to pay {tax}€ tax!")
elif salary <= 4000 and status == "Single":
    print("you have to pay 22% tax!")
    tax = 4000 * 22 / 100
    print(f"You have to pay {tax}€ tax!")
else:
    print("you have to pay 18% tax!")
    tax = 4000 * 18 / 100
    print(f"You have to pay {tax}€ tax!")
```  
  
</details>

4. Assignment
<br>
<br>
Write a function that calculates the BMI value of the user and gives an output based on the following table.  
<br>
<br>

| BMI                                               | Rating            |
| ------------------------------------------------- | ----------------- | 
| Less than 18.5                                    | Under weight      | 
| 18.5 until 24.9                                   | Normal weight     |  
| 25 until 29.9                                     | Overweight        |  
| 30 until 39.9                                     | Severe overweight (obesity)        |  
| Over 40                                           |  	Extreme obesity        |  
    
  
 Use the following formula to calculate the BMI value:
 <br>
 <br>
    
![181480006-dc4e3e8b-069c-4b19-83db-0def0bca2aef](https://user-images.githubusercontent.com/92121260/181736973-5d1c4c44-af79-42d3-b3a3-9ecf76181cb1.png)

 <details open>
<summary>Solution</summary>

```python
# Function for BMI calculation
def calc_bmi(weight, height):
    # Devide by 100 to convert cm in m
    bmi = weight / (height / 100) ** 2
    # Case differentiation
    if bmi < 18.5:
        print("You are under weight!")
    elif 18.5 <= bmi < 24.9:
        print("You have normal weight!")
    elif 25 <= bmi <29.9:
        print("You are oberweight!")
    elif 30 <= bmi < 39.9:
        print("You have severe overweight!")
    else:
        print("You have extreme obesity!")


# Use the function for bmi calculation by user input
calc_bmi(float(input("Enter your weight: ")), float(input("Enter your height: ")))


```  
  
</details>   

5. Assignment
<br>
<br>
Write a program that converts temperatures in different scale systems into each other. The program should offer a selection with the different possibilities at the beginning:
<br>
<br>
(1) Conversion from Celsius to Kelvin<br>
(2) Conversion from Celsius to Fahrenheit<br>
(3) Conversion from Kelvin to Celsius<br>
(4) Conversion from Kelvin to Fahrenheit<br>
(5) Conversion from Fahrenheit to Celsius<br>
(6) Conversion from Fahrenheit to Kelvin<br>
<br

This can certainly help you:

- Celsius = 5/9 * (Fahrenheit - 32).
- Celsius = Kelvin - 273.15.
- The lowest possible temperature is absolute zero 0K.

    
    <details open>
<summary>Solution</summary>

```python

# Function which concerts temperature in different scale systems
# This function just need the temperature as input
def temperature_converter(temperature):
    # Information for the user
    print("------------------------------------------------")
    print("(1) Conversion from Celsius to Kelvin")
    print("(2) Conversion from Celsius to Fahrenheit")
    print("(3) Conversion from Kelvin to Celsius")
    print("(4) Conversion from Kelvin to Fahrenheit")
    print("(5) Conversion from Fahrenheit to Celsius")
    print("(6) Conversion from Fahrenheit to Kelvin")
    print("------------------------------------------------")
    # Ask the user which system he likes to use
    system_temperature = int(input("Select a conversion: "))
    # The conversion starts here
    if system_temperature == 1:
        # Check whether the temperature is lower than -273.15 (absolute zero)
        if temperature < -273.15:
            print("Temperature can't be lower than -273.15 celsius!")
        else:
            converted_temperature = temperature + 273.15
            print(f"{temperature} celsius are {converted_temperature} kelvin!")
            return converted_temperature
    elif system_temperature == 2:
        # Check whether the temperature is lower than -273.15 (absolute zero)
        if temperature < -273.15:
            print("Temperature can't be lower than -273.15 celsius!")
        else:
            converted_temperature = (temperature * (9 / 5)) + 32
            print(f"{temperature} celsius are {converted_temperature} fahrenheit!")
            return converted_temperature
    elif system_temperature == 3:
        # Check whether the temperature is lower than 0 (absolute zero)
        if temperature < 0:
            print("Temperature can't be lower than 0 kelvin!")
        else:
            converted_temperature = temperature - 273.15
            print(f"{temperature} kelvin are {converted_temperature} celsius!")
            return converted_temperature
    elif system_temperature == 4:
        # Check whether the temperature is lower than 0 (absolute zero)
        if temperature < 0:
            print("Temperature can't be lower than 0 kelvin!")
        else:
            converted_temperature = ((temperature - 273.15) * 9 / 5) + 32
            print(f"{temperature} kelvin are {converted_temperature} fahrenheit!")
            return converted_temperature
    elif system_temperature == 5:
        # Check whether the temperature is lower than −459.67 (absolute zero)
        if temperature < (-459.67):
            print("Temperature can't be lower than -459.67 fahrenheit!")
        else:
            converted_temperature = 5 / 9 * (temperature - 32)
            print(f"{temperature} fahrenheit are {converted_temperature} celsius!")
            return converted_temperature
    elif system_temperature == 6:
        # Check whether the temperature is lower than −459.67 (absolute zero)
        if temperature < (-459.67):
            print("Temperature can't be lower than -459.67 fahrenheit!")
        else:
            converted_temperature = (5 / 9 * (temperature - 32)) + 273.15
            print(f"{temperature} fahrenheit are {converted_temperature} kelvin!")
            return converted_temperature


# Use the function to convert a temperature by user input
temperature_converter(float(input("Enter a temperature: ")))

```  
  
</details>
