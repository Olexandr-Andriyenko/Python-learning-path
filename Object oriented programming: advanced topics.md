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

    # Special method which will be called if using print() function to an object
    def __str__(self):
        return f'First name: {self.first_name}, Last name: {self.last_name}, Age: {self.age}'


# Create an object
teacher = Person("Max", "Musterman", 20)
# print this object
print(teacher)

# Output is:
# First name: Max, Last name: Musterman, Age: 20

# Without the implementation of the __str()__ method inside the class.
# We will get by using print(str(teacher)) the memory location of this object!
```

You can get information about an object using the built-in function `__repr()__`. You can specify the layout of this information by yourself if you define the special method `__repr()__` within the class definition. However, this is rarely used in practice and will not be discussed for the time being. It works exactly like the `__strt()__` method!
