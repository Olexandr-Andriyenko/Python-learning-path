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
