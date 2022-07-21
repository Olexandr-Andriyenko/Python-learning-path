# Type conversion/casting

Type conversion in computer science is the conversion of one data type into another data type. A distinction is made between explicit and implicit type conversion.

## Implicit type conversion

In implicit type conversion, Python automatically converts one data type to another data type. This process does not require the participation of the programmer. With the "type()" function you can display the data type of a variable, to be more precise of an object.
<br>
<br>
Example:
```python
num_int = 20
num_float = 3.141
new_num = num_int * num_float
# Which datatype has the variable "new_num"?
print(f"Datatype of num_int ist: {type(num_int)}")
print(f"Datatype of num_float ist: {type(num_float)}")
print(f"Datatype of new_num ist: {type(new_num)}")

# Gives the output:
# Datatype of num_int ist: <class 'int'>
# Datatype of num_float ist: <class 'float'>
# Datatype of new_num ist: <class 'float'>

# The datatype of "new_num" is determined automaticlly(implicit type conversion)
```

## Explicit type conversion

In explicit type conversion, the programmer converts the data type of an variable/object to the required data type. For this purpose we use the functions which are already included in Python.

| Function      |  Description                                                    |
| ------------- | --------------------------------------------------------------- |
| int()         | Converts the specified value into an integer number.            |
| float()       | Converts the specified value into a floating point number.      |
| str()         | Converts the specified value into a string.                     | 
