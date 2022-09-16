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
