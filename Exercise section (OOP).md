# Exercise section (OOP)

## 1. Assignment

Build a quiz game with the OOP paradigma.<br>
The user is asked a question and he chooses between "true" or "false".<br>
If the question is correct we give him one point.<br>
If the question was wrong, ask him the next question<br>
You need a `main`, `question_model`, `quiz_brain` and a `data` file!<br>

<details>
 <summary>data.py</summary>
```python
question_data = [
{"text": "A slug's blood is green.", "answer": "True"},
{"text": "The loudest animal is the African Elephant.", "answer": "False"},
{"text": "Approximately one quarter of human bones are in the feet.", "answer": "True"},
{"text": "The total surface area of a human lungs is the size of a football pitch.", "answer": "True"},
{"text": "In West Virginia, USA, if you accidentally hit an animal with your car, you are free to take it home to eat.", "answer": "True"},
{"text": "In London, UK, if you happen to die in the House of Parliament, you are entitled to a state funeral.", "answer": "False"},
{"text": "It is illegal to pee in the Ocean in Portugal.", "answer": "True"},
{"text": "You can lead a cow down stairs but not up stairs.", "answer": "False"},
{"text": "Google was originally called 'Backrub'.", "answer": "True"},
{"text": "Buzz Aldrin's mother's maiden name was 'Moon'.", "answer": "True"},
{"text": "No piece of square dry paper can be folded in half more than 7 times.", "answer": "False"},
{"text": "A few ounces of chocolate can to kill a small dog.", "answer": "True"}
]  
```
</details>

The most logic should be inside the `quiz_brain` file.<br>
The output should look like this:
```
C:\Users\olexa\PycharmProjects\pythonProject\venv\Scripts\python.exe C:/Users/olexa/PycharmProjects/pythonProject/main.py
Q.1: A slug's blood is green. (True/False): true
You got it right!
The correct answer was: True.
Your current score is: 1/1


Q.2: The loudest animal is the African Elephant. (True/False): true
That's wrong!
The correct answer was: False.
Your current score is: 1/2
.
.
.
.
.
Q.11: No piece of square dry paper can be folded in half more than 7 times. (True/False): false
You got it right!
The correct answer was: False.
Your current score is: 1/11


Q.12: A few ounces of chocolate can to kill a small dog. (True/False): false
That's wrong!
The correct answer was: True.
Your current score is: 1/12


You have completed the quiz
Your final score was: 1/12

Process finished with exit code 0
```
