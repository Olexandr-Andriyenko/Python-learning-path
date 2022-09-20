# Nato Alphabet Project

We want to create a tool that takes the NATO phonetic alphabet which was generated because it's often really importan
for the other side to know exactly what it is that you said and which letters you are spelling out so that they
don't mistake your E for a B.

<p align="left">
<img src="https://github.com/Olexandr-Andriyenko/Python-learning-path/blob/main/illustrations/img49.png" width="300">
<p>

For this project you have to use this [csv data](https://github.com/Olexandr-Andriyenko/Python-learning-path/blob/main/Files/nato_phonetic_alphabet.csv).
<br>
<br>
TODO 1. Create a dictionary from the csv in this format:

```
{"A": "Alfa", "B": "Bravo"}`
```

TODO 2. Create a list of the phonetic code words from a word that the user inputs.

Example program:

```python
# User input: Enter a word: Thomas
# Output is:
# ["Tango", "Hotel", "Oscar", "Mike", "Alfa", "Sierra"]
```

This is an example how you can Iterate through a pandas data frame:

```python
# Sometimes you have to loop a pandas data frame
import pandas as pd
student_dict = {
    "student": ["Angela", "James", "Lily"],
    "score": [56, 76, 98]
}
# Create a data frame from an dictionary
student_data = pd.DataFrame(student_dict)
# Loop through a data frame with pandas inbuilt loop
for (index, row) in student_data.iterrows():
    # Filter the student james
    if row.student == "James":
        print(row.student)
        print(row.score)

# Output is:
# James
# 76

```

<details>
 <summary>Solution</summary>

```python
import pandas as pd

# Load the csv file in a data frame
data = pd.read_csv("nato_phonetic_alphabet.csv")
# Create the dictionary
data_dict = {row.letter: row.code for (index, row) in data.iterrows()}
# Ask the user for a word
word = input("Enter a word: ").upper()
# Check each letter in the word for the key
try:
    data_list = [data_dict[letter] for letter in word]
    print(data_list)
except:
    print("Wrong input. Only letters allowed!")

```
    
</details>
