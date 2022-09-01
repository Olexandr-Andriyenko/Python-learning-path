# Object oriented programming: advanced topics

Be sure you understand the previous chapter!

## Constructor and destructor

There are two special methods that are defined in connection with a class.
- The constructor method is used to assign initial values to an object at the beginning of its lifetime.
- The destructor method is used to trigger actions at the end of an object's lifetime, for example, to close an open file.
<br>
<br>

The specified name `__init__()` specifies the constructor method<br>

The specified name `__del__()` specifies the destructor method<br>

Constructors are used often. They allow a more targeted creation of objects. Destructors are used less frequently.
<br>
<br>
Example:

```python
# Create a class
class Vehicle:
    # Create a constructor method
    def __init__(self, v_t, m_s, c):
        self.speed = None
        self.vehicle_type = v_t
        self.max_speed = m_s
        self.color = c

    # Create a destructor method
    def __del__(self):
        print("Vehicle has arrived! ")
        print(f"Object {self.vehicle_type} removed!")

    # Create a class method
    def drive_off(self, speed):
        self.speed = speed
        print(f"The vehicle is driving with {self.speed} km/h")


# Create an object of this class
car = Vehicle("Porsche", 350, "Red")
# Let's drive this car
car.drive_off(10)

# Output is:
# The vehicle is driving with 10 km/h
# Vehicle has arrived! 
# Object Porsche removed!
```

Exersice:<br>
Write a Program to create a class by name Students, and initialize attributes like name, age, and grade while creating an object.<br>
Write a method to display information about this student!<br>
Test your class!

<details>
 <summary>Solution</summary>
 
```python
# Class
class Student:
    # Constructor
    def __init__(self, name, age, grade):
        self.name = name
        self.age = age
        self.grade = grade

    # Method
    def information(self):
        print(f"{self.name} is {self.age} years old and the grade is {self.grade}")

    # This method checks if the student can drink and buy alcohol
    def alcohol_allowed(self):
        if self.age > 18:
            print(f"{self.name} can drink!")
            return True
        else:
            print(f"{self.name} can not drink!")
            return False


# Create some students
student_1 = Student("Alex", 17, 3)
student_2 = Student("Müller", 24, 6)
# Display information
student_1.information()
# Check if students can drink alcohol
student_1.alcohol_allowed()
student_2.alcohol_allowed()

# Output is:
# Alex is 17 years old and the grade is 3
# Alex can not drink!
# Müller can drink!
```
    
</details>


## Other special methods

Like the `__init()__` and `__del()__` methods there are other importan methods in connection with classes:
- `__str()__`
- `__repr()__`
<br>
When an object is printed using the `print()` function, the special `__str()__` method is called if it is defined. By default, this returns a string for outputting the properties.
<br>
<br>
Example:

```python
class Person:
    # Constructor
    def __init__(self, first_name, last_name, age):
        self.first_name = first_name
        self.last_name = last_name
        self.age = age

    # Special method which will be called if using print() or str() function to an object
    # This method must return a string value!
    # The output of the method" __str__()" is only used to display the output to the user.
    def __str__(self):
        return f'First name: {self.first_name}, Last name: {self.last_name}, Age: {self.age}'


# Create an object
teacher = Person("Max", "Musterman", 20)
# print this object
print(teacher)

```

You can get information about an object using the built-in function `__repr()__`. You can specify the layout of this information by yourself if you define the special method `__repr()__` within the class definition. However, this is rarely used in practice and will not be discussed for the time being. It works exactly like the `__strt()__` method! Both __str__ and __repr__ functions return string representation of the object. The __str__ string representation is supposed to be human-friendly and mostly used for logging purposes, whereas __repr__ representation is supposed to contain information about object so that it can be constructed again.

## Getter and Setter

Compared to other languages, Python uses the getter and setter method to add logic to get and set a value. To achieve the getters & setters property, when we define Normal `get()` and `set()` methods , no special implementation is considered.

```python
# Python program showing a use
# of get() and set() method
class Geek:
    def __init__(self, age=0):
        self.age = age

    # getter method
    def get_age(self):
        return self.age

    # setter method
    def set_age(self, x):
        self.age = x

# Create an object
raj = Geek()
# Use setter method
raj.set_age(25)
# Use getter method
raj_age = raj.get_age()
print(raj_age)

# Output is:
# 25
```

Basically, the main purpose of using getters and setters in object-oriented programs is to ensure data encapsulation (Hiding data or information from outside access).
In the above code, `get_age()` and `set_age()` acts as a normal function and does not play a role of getter and setter. 

## Inheritance

A class can inherit its attributes and methods to another class. This mechanism is often used. Inheritance creates a hierarchy of classes that allows the representation of objects that have partial matching characteristics.
<br>
<br>
Example of this "hierarchy": 

![Konto_Vererbung](https://user-images.githubusercontent.com/92121260/187907923-57023e5c-cc64-4fa6-84b5-3235b6eafc6f.png)

We implement the above example as code:

```python
# Create the class "Konto" (Superclass)
class Account:

    # Constructor
    def __init__(self, owner, account_number, account_balance):
        # Attributes
        self.owner = owner
        self.account_number = account_number
        self.account_balance = account_balance

    # Methods
    def do_deposit(self, amount):
        print(f"You deposit {amount} EUR!")
        self.account_balance += amount

    def do_payout(self, amount):
        print(f"You payout {amount} EUR!")
        self.account_balance -= amount

    def show_information(self):
        print(f"Owner: {self.owner}"
              f"Account number: {self.account_number}"
              f"Account balance: {self.account_balance}")


# Child class
class Checking_account(Account):
    def __init__(self, interest, owner, account_number, account_balance):
        # The super() function is used in the child class with
        # multiple inheritance to access the function of the next parent class or superclass.
        super().__init__(owner, account_number, account_balance)
        self.interest = interest

    def bank_transfer(self, amount):
        self.account_balance -= amount


# Child class
class Savings_account(Account):
    def __init__(self, interest_rate, owner, account_number, account_balance):
        # The super() function is used in the child class with
        # multiple inheritance to access the function of the next parent class or superclass.
        super().__init__(owner, account_number, account_balance)
        self.interest_rate = interest_rate


# ---------------------------------------------------------------------------------------- #
# Main program
# Create object
my_account = Account("Alex", 42, 25000)
# Show my balance
print(my_account.account_balance)
# Lets do a deposit
my_account.do_deposit(5000)
# Show my balance
print(my_account.account_balance)
# Lets do a payout
my_account.do_payout(10000)
# Show my balance
print(my_account.account_balance)
# Create a checking account
my_checking_account = Checking_account(2, "Alex", 42, 25000)
# Show balance of my checking account
print(my_checking_account.account_balance)
# Let's do a deposit to my checking account
my_checking_account.do_deposit(5000)
# Show balance of my checking account
print(my_checking_account.account_balance)
# Show balance of my account
print(my_account.account_balance)

```
