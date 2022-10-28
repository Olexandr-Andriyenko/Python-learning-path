# Quizz app with API

Build a tkinter app with an API to [Open Trivia DB](https://opentdb.com/api_config.php).
<br>
<br>
Use OOP concepts to structure your code and the following images for the UI:

<p align="left">
<img src="https://github.com/Olexandr-Andriyenko/Python-learning-path/blob/main/illustrations/false.png" width="100">
<p>


<p align="left">
<img src="https://github.com/Olexandr-Andriyenko/Python-learning-path/blob/main/illustrations/true.png" width="100">
<p>

We will use the code from the [1 Assignment](https://github.com/Olexandr-Andriyenko/Python-learning-path/blob/main/Exercise%20section%20(OOP).md) of the chapter Exercise section (OOP):

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
 <summary>question_model.py </summary>
 
```python
# 1. Create a "Question" class with an constructor with two attributes "text" and "answer"
class Question:
    def __init__(self, q_text, q_answer):
        self.text = q_text
        self.answer = q_answer
 
```
 
</details>


<details>
 <summary>quiz_brain</summary>
 
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
            self.score += 1
            print("You got it right!")
        else:
            print("That's wrong!")
        # 15. Tell the user after each question the correct answer and the current score
        print(f"The correct answer was: {correct_answer}.")
        print(f"Your current score is: {self.score}/{self.question_number}")
        print("\n")

```
 
</details>

So you have just to build the UI with `tkinter` and implement the API to get the data.
<br>
<br>
Create additional files called: `data.py` and `ui.py`

## Solution

<details>
 <summary>main.py</summary>
 
```python
from question_model import Question
from data import question_data
from quiz_brain import QuizBrain
from ui import QuizInterface

question_bank = []
for question in question_data:
    question_text = question["question"]
    question_answer = question["correct_answer"]
    new_question = Question(question_text, question_answer)
    question_bank.append(new_question)


quiz = QuizBrain(question_bank)
quiz_ui = QuizInterface(quiz)

# while quiz.still_has_questions():
#     quiz.next_question()

print("You've completed the quiz")
print(f"Your final score was: {quiz.score}/{quiz.question_number}")

```
 
</details>

<details>
 <summary>question_model.py</summary>
 
```python
class Question:

    def __init__(self, q_text, q_answer):
        self.text = q_text
        self.answer = q_answer

```
 
</details>

<details>
 <summary>quiz_brain.py</summary>
 
```python
import html

class QuizBrain:

    def __init__(self, q_list):
        self.question_number = 0
        self.score = 0
        self.question_list = q_list
        self.current_question = None

    def still_has_questions(self):
        return self.question_number < len(self.question_list)

    def next_question(self):
        self.current_question = self.question_list[self.question_number]
        self.question_number += 1
        # Unescape HTML entities
        q_text = html.unescape(self.current_question.text)
        return f"Q.{self.question_number}: {q_text} (True/False): "
        # user_answer = input(f"Q.{self.question_number}: {q_text} (True/False): ")
        # self.check_answer(user_answer)

    def check_answer(self, user_answer):
        correct_answer = self.current_question.answer
        if user_answer.lower() == correct_answer.lower():
            self.score += 1
            return True
        else:
            return  False


```
 
</details>

<details>
 <summary>data.py</summary>
 
```python
import requests

parameters = {
    "amount": 10,
    "type": "boolean"
}

response = requests.get("https://opentdb.com/api.php?amount=10&type=boolean", params=parameters)
response.raise_for_status()
data = response.json()
question_data = data["results"]
# If you get strange symbols inside the questions (like: &quot;), read about the HTML character entities!
# Use this tool: https://www.freeformatter.com/html-escape.html#before-output

# question_data = [
#     {
#         "category": "Science: Computers",
#         "type": "boolean",
#         "difficulty": "medium",
#         "question": "The HTML5 standard was published in 2014.",
#         "correct_answer": "True",
#         "incorrect_answers": [
#             "False"
#         ]
#     },
#     {
#         "category": "Science: Computers",
#         "type": "boolean",
#         "difficulty": "medium",
#         "question": "The first computer bug was formed by faulty wires.",
#         "correct_answer": "False",
#         "incorrect_answers": [
#             "True"
#         ]
#     },
#     {
#         "category": "Science: Computers",
#         "type": "boolean",
#         "difficulty": "medium",
#         "question": "FLAC stands for 'Free Lossless Audio Condenser'.",
#         "correct_answer": "False",
#         "incorrect_answers": [
#             "True"
#         ]
#     },
#     {
#         "category": "Science: Computers",
#         "type": "boolean",
#         "difficulty": "medium",
#         "question": "All program codes have to be compiled into an executable file in order to be run. This file can then be executed on any machine.",
#         "correct_answer": "False",
#         "incorrect_answers": [
#             "True"
#         ]
#     },
#     {
#         "category": "Science: Computers",
#         "type": "boolean",
#         "difficulty": "easy",
#         "question": "Linus Torvalds created Linux and Git.",
#         "correct_answer": "True",
#         "incorrect_answers": [
#             "False"
#         ]
#     },
#     {
#         "category": "Science: Computers",
#         "type": "boolean",
#         "difficulty": "easy",
#         "question": "The programming language 'Python' is based off a modified version of 'JavaScript'",
#         "correct_answer": "False",
#         "incorrect_answers": [
#             "True"
#         ]
#     },
#     {
#         "category": "Science: Computers",
#         "type": "boolean",
#         "difficulty": "medium",
#         "question": "AMD created the first consumer 64-bit processor.",
#         "correct_answer": "True",
#         "incorrect_answers": [
#             "False"
#         ]
#     },
#     {
#         "category": "Science: Computers",
#         "type": "boolean",
#         "difficulty": "easy",
#         "question": "'HTML' stands for Hypertext Markup Language.",
#         "correct_answer": "True",
#         "incorrect_answers": [
#             "False"
#         ]
#     },
#     {
#         "category": "Science: Computers",
#         "type": "boolean",
#         "difficulty": "easy",
#         "question": "In most programming languages, the operator ++ is equivalent to the statement '+= 1'.",
#         "correct_answer": "True",
#         "incorrect_answers": [
#             "False"
#         ]
#     },
#     {
#         "category": "Science: Computers",
#         "type": "boolean",
#         "difficulty": "hard",
#         "question": "The IBM PC used an Intel 8008 microprocessor clocked at 4.77 MHz and 8 kilobytes of memory.",
#         "correct_answer": "False",
#         "incorrect_answers": [
#             "True"
#         ]
#     }
# ]

```
 
</details>

<details>
 <summary>ui.py</summary>
 
```python
import tkinter
from quiz_brain import QuizBrain
THEME_COLOR = "#375362"
FONT = ("Arial", 20, "italic")

class QuizInterface:
    def __init__(self, quiz_brain: QuizBrain):  # variable "quiz_brain" is a datatype "QuizBrain"
        self.quiz = quiz_brain
        self.window = tkinter.Tk()
        self.window.title("Quizzler")
        self.window.config(padx=20, pady=20, bg=THEME_COLOR)

        self.score_label = tkinter.Label(text="Score: 0", fg="white", bg=THEME_COLOR)
        self.score_label.grid(row=0, column=1)

        self.canvas = tkinter.Canvas(width=300, height=250, bg="white")
        self.canvas.grid(row=1, column=0, columnspan=2, pady=50)
        self.question_text = self.canvas.create_text(
            150,
            125,
            width=280,
            text="Some Question Text",
            fill=THEME_COLOR,
            font=FONT
        )
        true_image = tkinter.PhotoImage(file="true.png")
        self.true_button = tkinter.Button(image=true_image, highlightthickness=0, command=self.true_pressed)
        self.true_button.grid(row=2, column=0)

        false_image = tkinter.PhotoImage(file="false.png")
        self.false_button = tkinter.Button(image=false_image, highlightthickness=0, command=self.false_pressed)
        self.false_button.grid(row=2, column=1)

        self.get_next_question()


        self.window.mainloop()

    def get_next_question(self):
        self.canvas.config(bg="white")
        if self.quiz.still_has_questions():
            self.score_label.config(text=f"Score: {self.quiz.score}")
            q_text = self.quiz.next_question()
            self.canvas.itemconfig(self.question_text, text=q_text)
        else:
            self.canvas.itemconfig(self.question_text, text="You have reached the end of the quiz.")
            self.true_button.config(state="disabled")
            self.false_button.config(state="disabled")

    def true_pressed(self):
        is_right = self.quiz.check_answer("True")
        self.give_feedback(is_right)

    def false_pressed(self):
        is_right = self.quiz.check_answer("False")
        self.give_feedback(is_right)

    def give_feedback(self, is_right):
        if is_right:
            self.canvas.config(bg="green")
        else:
            self.canvas.config(bg="red")
        self.window.after(1000, self.get_next_question)
```
 
</details>

