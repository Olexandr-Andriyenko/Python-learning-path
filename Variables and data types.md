# Variables and data types

A variable can be understood as a container that is used to store data. In mathematics, variables are placeholders for numbers, but here not only numbers, but also strings, symbols and other data can be stored in a variable. In the process of a program, data of variables is being accessed and manipulated or replaced by new data.
<br>
<br>
A variable can be of a certain data type and have a value. There are different data types in python that are important to know. Depending on the data type of a variable, only certain values can be stored in a variable. 

| Datatype      | Abbreviation  | Meaning                 | Example for a value   |
| ------------- | ------------- | ------------------------| ----------------------|
| Integer       | int           | Whole number            | 42                    |
| Float         | float         | Real number             | 3.1415                |
| String        | str           | Sequence of characters  | "name, age, gender"   |
| Boolean       | bool          | Truth values            | True (1) or False (0) |


The variable name must be set for the definition of variables. For this purpose, some rules and conventions should be observed. Variable names should always be clearly specified so that the purpose of a variable is later understood. If a variable is used to store book titles, then it should logically be called "book_title" and not "b_t" or similar. If a variable name consists of different words, you should separate them with an underscore " _ ". The so-called "camel case notation" is also common, where each initial letter of a word is capitalized, such as "MaximumWidth". Don't forget, variable names start with lowercase letters! 
<br>
<br>
In many programming languages you have to specify the data type when defining the variables, in Python it is not the case, because it is a dynamically typed programming language. Depending on the variable value, Python itself decides which data type is involved.
<br>
<br>
Actually, in Python, the data is stored in objects and the variables simply reference those objects in memory. This is the actual reason why the specification of data types is not necessary for variables. However, this is only mentioned in passing, as it is not important for us for the time being.
<br>
<br>
Now we have to look at how to assign a value to variables. This is done with the so-called assignment operator "=", which should not be confused with the equals sign from mathematics. As an example, let's look at the following quel text (you should absolutely reproduce all examples on your own!):

```python
income = 4200
job = "programmer"
employee_vacation = False
# Increase employee salary
salary = 4700.97
```
