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

### Solution

<details>
 <summary>main.py</summary>
 
```python
from question_model import Question
from data import question_data
from quiz_brain import QuizBrain

# 2. In this list we will save objects from the class "Question"
question_bank = []
# 2. Write a "for" loop to iterate over the "question_data".
for question in question_data:
    # 3. Create a "Question" object from each entry in "question_data"
    question_text = question["text"]
    question_answer = question["answer"]
    # 3. Now we create the object
    new_question = Question(question_text, question_answer)
    # 4. Append each "Question" object to the "question_bank"
    question_bank.append(new_question)

quiz = QuizBrain(question_bank)

# 11. Use a while loop to show the next question until the end
while quiz.still_has_questions():
    quiz.next_question()
# 16. Tell the user at the end that he completed the quiz and display the final score
print("You have completed the quiz")
print(f"Your final score was: {quiz.score}/{quiz.question_number}")
```
 
</details>


<details>
 <summary>question_model.py</summary>
 
```python
# 1. Create a "Question" class with an constructor with two attributes "text" and "answer"
class Question:
    def __init__(self, q_text, q_answer):
        self.text = q_text
        self.answer = q_answer
 
```
 
</details>


<details>
 <summary>question_model.py</summary>
 
```python
# 5. Use the "quiz_brain" file to asking the questions, checking of the answer was correct
#    and checking if it's the end of the quiz
# 6. Create a class "QuizBrain"
class QuizBrain:
    # 6. Write a constructor which initialise the question_number to 0 and
    # the question_list to an input
    def __init__(self, q_list):
        self.question_number = 0
        self.question_list = q_list
        # 14. Keep track of the user's score, add for this a new attribute "score"
        self.score = 0

    # 7. Create a method "next_question" inside the "QuizBrain" class.
    def next_question(self):
        # 7. The first question from the list begins at 0
        current_question = self.question_list[self.question_number]
        # 8. Rise the "question_number" by one each time if "next_question" is used
        self.question_number += 1
        # 7. Use the "input" function to show the user the question text and as for the user's answer.
        user_answer = input(f"Q.{self.question_number}: {current_question.text} (True/False): ")
        # 13. Inside "next_question" use "check_answer"
        self.check_answer(user_answer, current_question.answer)

    # 9. Create a new method inside the "quiz_brain" file called "still_has_questions".
    def still_has_questions(self):
        # 10. Return a boolean depending on the value of "question_number"
        if self.question_number < len(self.question_list):
            return True
        else:
            return False

    # 12. Create a new method called "check_answer" inside the "quiz_brain" file
    def check_answer(self, user_answer, correct_answer):
        # 12 It will check and display whether answer is correct or not
        if user_answer.lower() == correct_answer.lower():
            # 14. Keep track of the user's score, add for this a new attribute "score"
            self.score = 1
            print("You got it right!")
        else:
            print("That's wrong!")
        # 15. Tell the user after each question the correct answer and the current score
        print(f"The correct answer was: {correct_answer}.")
        print(f"Your current score is: {self.score}/{self.question_number}")
        print("\n")


 
```
 
</details>

