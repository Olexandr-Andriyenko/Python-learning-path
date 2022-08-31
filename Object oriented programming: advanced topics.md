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
