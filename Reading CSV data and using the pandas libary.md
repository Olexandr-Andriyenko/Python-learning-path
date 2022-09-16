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
    
## Pandas libary
    
This is an python data analysis libary which is super helpful to perform data analysis on tabula data like the csv file above.
<br>
Before you can work with the pandas libary, you have to import it. Because it is not a built in libary, you have to install it firstly.
<br>
<br>
Do not forget to read the [pandas documentation](https://pandas.pydata.org/docs/)!
<br>
<br>
First steps:

```python
import pandas
# Lets read a csv
data = pandas.read_csv("weather_data.csv")
# Display the data inside the csv
print(data)
# Just get the column called temp
temperatures = data["temp"]
print("# ------------------------------------ #")
# Display only temperatures
print(temperatures)

# Output is:
#           day  temp condition
# 0     Monday    12     Sunny
# 1    Tuesday    14      Rain
# 2  Wednesday    15      Rain
# 3   Thursday    14    Cloudy
# 4     Friday    21     Sunny
# 5   Saturday    22     Sunny
# 6     Sunday    24     Sunny
# ------------------------------------ #
# 0    12
# 1    14
# 2    15
# 3    14
# 4    21
# 5    22
# 6    24
# Name: temp, dtype: int64
```

In pandas we have two importan datatypes:
- dataframe, it is equivalent to the table like in the first example. 
- series, it is a column like a list

If you understand this two data types then you are on a good way understanding this libary!<br>
At the start of learning pandas you should take a closer look to the twi classes ["DataFrame"](https://pandas.pydata.org/docs/reference/frame.html) and ["Series"](https://pandas.pydata.org/docs/reference/series.html).
    
 Lets calculate the average temperature:
    
 ```python
import pandas
# Lets read a csv
data = pandas.read_csv("weather_data.csv")
# Just get the column called temp
temperatures = data["temp"]
# Convert the temperatures series to a list
temperature_list = temperatures.to_list()
# Calculate the average temperature
temperature_sum = 0
for temperature in temperature_list:
    temperature_sum += temperature
average_temperature = temperature_sum / len(temperature_list)
print(average_temperature)
# Alternative and faster:
# average_temperature = sum(temperature_list) / len(temperature_list)
# With a pandas library even faster:
# data["temp"].mean()

# Output is:
# 17.428571428571427
```
    
We can get quick the maximum value of the temperature column:
    
```python
 import pandas
# Lets read a csv
data = pandas.read_csv("weather_data.csv")
# Just get the column called temp
temperatures = data["temp"]
# Get te max temperature of the series
max_temp = temperatures.max()
print(max_temp)

# Output is:
# 24
```

Sometimes you just like to get only one row of your table:
 
```python
import pandas
# Lets read a csv
data = pandas.read_csv("weather_data.csv")
# Get data in row
row_day = data[data["day"] == "Monday"]
print(row_day)

# Output is:
#       day  temp condition
# 0  Monday    12     Sunny
```

Try to find the row with the highest temperature:
 
```python
import pandas
# Lets read a csv
data = pandas.read_csv("weather_data.csv")
# Find the max temperature
max_temp = data["temp"].max()
# Find the row with max temperature
row_max_temp = data[data["temp"] == max_temp]
print(row_max_temp)

# Output is:
#       day  temp condition
# 6  Sunday    24     Sunny
    
```

Lets get the temperatures of monday and convert them in Fahrenheit:
 
```python
import pandas
# Lets read a csv
data = pandas.read_csv("weather_data.csv")
# Find the row with monday
monday = data[data["day"] == "Monday"]
# Find the temperature of monday
monday_temp = int(monday["temp"])
# Convert in Fahrenheit
monday_temp_fahrenheit = (monday_temp * (9/5)) + 32
print(monday_temp_fahrenheit)

# Output is:
# 53.6
```
    
    
You can even create a dataframe from scratch:
    
```python
import pandas
# You have given data:
data_dict = {
    "students": ["Amy", "James", "Angela"],
    "scores": [76, 56, 65]
}
# We have to create a data frame from this dictionary
data = pandas.DataFrame(data_dict)
print(data)
# We can even convert our data frame to a csv
data.to_csv("new_data.csv")
    
```
