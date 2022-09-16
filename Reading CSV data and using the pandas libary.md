# Reading CSV data and using the pandas libary


Firstly download [Download CSV data](https://github.com/Olexandr-Andriyenko/Python-learning-path/blob/main/Files/weather_data.csv) and copy this file to you pycharm project folder.
If you open the csv file inside pycharm it will look like this:

<p align="left">
<img src="https://github.com/Olexandr-Andriyenko/Python-learning-path/blob/main/illustrations/img45.png" width="250">
<p> 

CSV (Comma-separated values) is a common way representing tabula data.
<br>
<br>
Lets open the `weather_data.csv` file and read it. We will save each line of the file inside a list called "data".

```python
with open("weather_data.csv") as data_file:
    data = data_file.readlines()
    print(data)
  
# Output is:
# ['day,temp,condition\n', 'Monday,12,Sunny\n', 'Tuesday,14,Rain\n', 'Wednesday,15,Rain\n', 'Thursday,14,Cloudy\n', 'Friday,21,Sunny\n', 'Saturday,22,Sunny\n',
# 'Sunday,24,Sunny\n', '\n', '\n', '\n']
```
    
As you can imagine, it would be pretty painfull to work with the data, which is all in a string format! It would take a lot of cleaning to actually be able to extract each column und each row. So what can we do instead?
<br>
<br>
We can use the inbuilt libary which will help us with csv data:
    
```python
import csv
with open("weather_data.csv") as data_file:
    # Use the method reader()
    data = csv.reader(data_file)
    print(data)  # Output is an object
    # Now we can read each row by using this object
    for row in data:
        print(row)

# Output is:
# <_csv.reader object at 0x000001F31A649600>
# ['day', 'temp', 'condition']
# ['Monday', '12', 'Sunny']
# ['Tuesday', '14', 'Rain']
# ['Wednesday', '15', 'Rain']
# ['Thursday', '14', 'Cloudy']
# ['Friday', '21', 'Sunny']
# ['Saturday', '22', 'Sunny']
# ['Sunday', '24', 'Sunny']
```
    
As a exercise lets get only the temperature values inside a list. But they have to be integers inside the list and not strings!
    
```python
 import csv
with open("weather_data.csv") as data_file:
    # Use the method reader()
    data = csv.reader(data_file)
    # Now we can read each row by using this object
    temperatures = []
    for row in data:
        if row[1] != "temp":
            # Add the second position in the row to a list and convert it to and integer
            temperatures.append(int(row[1]))

print(temperatures)

# Output is:
# [12, 14, 15, 14, 21, 22, 24]
 ```
