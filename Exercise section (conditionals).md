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
