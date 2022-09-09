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
         
### Additional

It is a little boring when we have only one database in our quiz. You could now write your own questions and then add them to the directory. However, an alternative is to use a database. I chose to use the "OPEN TRIVIA DATABASE" which provides free "trivia questions". This database has over 3000 verified questions to choose from.
<br>
<br>
Go go the website of [open trivia database](https://opentdb.com/) and take a look to the API (Application Programming Interface). An API makes it possible to exchange data between software and program parts.
<br>
Setting which I selected:
         
<p align="center">
<img src="https://github.com/Olexandr-Andriyenko/Python-learning-path/blob/main/illustrations/img36.PNG" width="700">
<p> 
         
After a click on "GENERATE API URL" you will get at the top of the screen a URL! If you open this URL you will see generated data in the JSON-format (JavaScript Object Notation):
         
```    
 {"response_code":0,"results":[{"category":"History","type":"boolean","difficulty":"easy","question":"The Cold War ended with Joseph Stalin&#039;s death.","correct_answer":"False","incorrect_answers":["True"]},{"category":"Art","type":"boolean","difficulty":"medium","question":"Pablo Picasso is one of the founding fathers of &quot;Cubism.&quot;","correct_answer":"True","incorrect_answers":["False"]},{"category":"Politics","type":"boolean","difficulty":"easy","question":"Denmark has a monarch.","correct_answer":"True","incorrect_answers":["False"]},{"category":"History","type":"boolean","difficulty":"easy","question":"Former United States Presidents John Adams and Thomas Jefferson died within hours of each other.","correct_answer":"True","incorrect_answers":["False"]},{"category":"Science: Computers","type":"boolean","difficulty":"easy","question":"&quot;HTML&quot; stands for Hypertext Markup Language.","correct_answer":"True","incorrect_answers":["False"]},{"category":"General Knowledge","type":"boolean","difficulty":"medium","question":"The French word for &quot;glass&quot; is &quot;glace&quot;.","correct_answer":"False","incorrect_answers":["True"]},{"category":"Entertainment: Music","type":"boolean","difficulty":"hard","question":"The song &quot;Mystery Train&quot; was released by artist &quot;Little Junior&#039;s Blue Flames&quot; in 1953.","correct_answer":"True","incorrect_answers":["False"]},{"category":"History","type":"boolean","difficulty":"medium","question":"Martin Luther King Jr. and Anne Frank were born the same year. ","correct_answer":"True","incorrect_answers":["False"]},{"category":"Entertainment: Japanese Anime & Manga","type":"boolean","difficulty":"hard","question":"In the &quot;To Love-Ru&quot; series, Peke is considered a female robot.","correct_answer":"True","incorrect_answers":["False"]},{"category":"Art","type":"boolean","difficulty":"medium","question":"Venus of Willendorf is one of the earliest works of art, depicting the planets Mars and Venus embrace in the heavens at night.","correct_answer":"False","incorrect_answers":["True"]}]}        
```         
 
Lets copy the dat inside our `data.py` file and override the last data. After your paste the data is really hard to read, so go to `Code` and press `Reformat code` inside Pycharm IDE. Now it looks like this:
               
```python
 question_data = {"response_code": 0, "results": [{"category": "History", "type": "boolean", "difficulty": "easy",
                                                  "question": "The Cold War ended with Joseph Stalin&#039;s death.",
                                                  "correct_answer": "False", "incorrect_answers": ["True"]},
                                                 {"category": "Art", "type": "boolean", "difficulty": "medium",
                                                  "question": "Pablo Picasso is one of the founding fathers of &quot;Cubism.&quot;",
                                                  "correct_answer": "True", "incorrect_answers": ["False"]},
                                                 {"category": "Politics", "type": "boolean", "difficulty": "easy",
                                                  "question": "Denmark has a monarch.", "correct_answer": "True",
                                                  "incorrect_answers": ["False"]},
                                                 {"category": "History", "type": "boolean", "difficulty": "easy",
                                                  "question": "Former United States Presidents John Adams and Thomas Jefferson died within hours of each other.",
                                                  "correct_answer": "True", "incorrect_answers": ["False"]},
                                                 {"category": "Science: Computers", "type": "boolean",
                                                  "difficulty": "easy",
                                                  "question": "&quot;HTML&quot; stands for Hypertext Markup Language.",
                                                  "correct_answer": "True", "incorrect_answers": ["False"]},
                                                 {"category": "General Knowledge", "type": "boolean",
                                                  "difficulty": "medium",
                                                  "question": "The French word for &quot;glass&quot; is &quot;glace&quot;.",
                                                  "correct_answer": "False", "incorrect_answers": ["True"]},
                                                 {"category": "Entertainment: Music", "type": "boolean",
                                                  "difficulty": "hard",
                                                  "question": "The song &quot;Mystery Train&quot; was released by artist &quot;Little Junior&#039;s Blue Flames&quot; in 1953.",
                                                  "correct_answer": "True", "incorrect_answers": ["False"]},
                                                 {"category": "History", "type": "boolean", "difficulty": "medium",
                                                  "question": "Martin Luther King Jr. and Anne Frank were born the same year. ",
                                                  "correct_answer": "True", "incorrect_answers": ["False"]},
                                                 {"category": "Entertainment: Japanese Anime & Manga",
                                                  "type": "boolean", "difficulty": "hard",
                                                  "question": "In the &quot;To Love-Ru&quot; series, Peke is considered a female robot.",
                                                  "correct_answer": "True", "incorrect_answers": ["False"]},
                                                 {"category": "Art", "type": "boolean", "difficulty": "medium",
                                                  "question": "Venus of Willendorf is one of the earliest works of art, depicting the planets Mars and Venus embrace in the heavens at night.",
                                                  "correct_answer": "False", "incorrect_answers": ["True"]}]}
        
```    
         
This dictionary has two key value pairs (response_code and results). I fou `Reformat Code` again, you will see that `results` have 10 dictionarys:
         
```python
question_data = {"response_code": 0,
                 "results": [{"category": "History", "type": "boolean", "difficulty": "easy",
                              "question": "The Cold War ended with Joseph Stalin&#039;s death.",
                              "correct_answer": "False", "incorrect_answers": ["True"]},
                             {"category": "Art", "type": "boolean", "difficulty": "medium",
                              "question": "Pablo Picasso is one of the founding fathers of &quot;Cubism.&quot;",
                              "correct_answer": "True", "incorrect_answers": ["False"]},
                             {"category": "Politics", "type": "boolean", "difficulty": "easy",
                              "question": "Denmark has a monarch.", "correct_answer": "True",
                              "incorrect_answers": ["False"]},
                             {"category": "History", "type": "boolean", "difficulty": "easy",
                              "question": "Former United States Presidents John Adams and Thomas Jefferson died within hours of each other.",
                              "correct_answer": "True", "incorrect_answers": ["False"]},
                             {"category": "Science: Computers", "type": "boolean",
                              "difficulty": "easy",
                              "question": "&quot;HTML&quot; stands for Hypertext Markup Language.",
                              "correct_answer": "True", "incorrect_answers": ["False"]},
                             {"category": "General Knowledge", "type": "boolean",
                              "difficulty": "medium",
                              "question": "The French word for &quot;glass&quot; is &quot;glace&quot;.",
                              "correct_answer": "False", "incorrect_answers": ["True"]},
                             {"category": "Entertainment: Music", "type": "boolean",
                              "difficulty": "hard",
                              "question": "The song &quot;Mystery Train&quot; was released by artist &quot;Little Junior&#039;s Blue Flames&quot; in 1953.",
                              "correct_answer": "True", "incorrect_answers": ["False"]},
                             {"category": "History", "type": "boolean", "difficulty": "medium",
                              "question": "Martin Luther King Jr. and Anne Frank were born the same year. ",
                              "correct_answer": "True", "incorrect_answers": ["False"]},
                             {"category": "Entertainment: Japanese Anime & Manga",
                              "type": "boolean", "difficulty": "hard",
                              "question": "In the &quot;To Love-Ru&quot; series, Peke is considered a female robot.",
                              "correct_answer": "True", "incorrect_answers": ["False"]},
                             {"category": "Art", "type": "boolean", "difficulty": "medium",
                              "question": "Venus of Willendorf is one of the earliest works of art, depicting the planets Mars and Venus embrace in the heavens at night.",
                              "correct_answer": "False", "incorrect_answers": ["True"]}]}
```         

How you have to modify the quiz game, to get it work with this database? <br>
Firstly modify the `question_data`, just delete the `results` and `response_code`, then we have a list of dictionarys.<br>
The data have to lool like this:
         
```python
question_data = [
    {"category": "History", "type": "boolean", "difficulty": "easy",
     "question": "The Cold War ended with Joseph Stalin&#039;s death.",
     "correct_answer": "False", "incorrect_answers": ["True"]},
    {"category": "Art", "type": "boolean", "difficulty": "medium",
     "question": "Pablo Picasso is one of the founding fathers of &quot;Cubism.&quot;",
     "correct_answer": "True", "incorrect_answers": ["False"]},
    {"category": "Politics",
     "type": "boolean",
     "difficulty": "easy",
     "question": "Denmark has a monarch.",
     "correct_answer": "True",
     "incorrect_answers": ["False"]},
    {"category": "History", "type": "boolean", "difficulty": "easy",
     "question": "Former United States Presidents John Adams and Thomas Jefferson died within hours of each other.",
     "correct_answer": "True", "incorrect_answers": ["False"]},
    {"category": "Science: Computers", "type": "boolean",
     "difficulty": "easy",
     "question": "&quot;HTML&quot; stands for Hypertext Markup Language.",
     "correct_answer": "True", "incorrect_answers": ["False"]},
    {"category": "General Knowledge", "type": "boolean",
     "difficulty": "medium",
     "question": "The French word for &quot;glass&quot; is &quot;glace&quot;.",
     "correct_answer": "False", "incorrect_answers": ["True"]},
    {"category": "Entertainment: Music", "type": "boolean",
     "difficulty": "hard",
     "question": "The song &quot;Mystery Train&quot; was released by artist &quot;Little Junior&#039;s Blue Flames&quot; in 1953.",
     "correct_answer": "True", "incorrect_answers": ["False"]},
    {"category": "History", "type": "boolean", "difficulty": "medium",
     "question": "Martin Luther King Jr. and Anne Frank were born the same year. ",
     "correct_answer": "True", "incorrect_answers": ["False"]},
    {"category": "Entertainment: Japanese Anime & Manga",
     "type": "boolean", "difficulty": "hard",
     "question": "In the &quot;To Love-Ru&quot; series, Peke is considered a female robot.",
     "correct_answer": "True", "incorrect_answers": ["False"]},
    {"category": "Art", "type": "boolean", "difficulty": "medium",
     "question": "Venus of Willendorf is one of the earliest works of art, depicting the planets Mars and Venus embrace in the heavens at night.",
     "correct_answer": "False", "incorrect_answers": ["True"]}
]
```
         
The last step ist just to change in `main.py` file the keys inside `question_text` to "question" and inside `question_answer` to "correct_answer".         
         
## 2. Assignment
         
Rectangle class:<br>
         
1. Write a Rectangle class in Python language, allowing you to build a rectangle with length and width attributes.
2. Create a Perimeter() method to calculate the perimeter of the rectangle and a Area() method to calculate the area of ​​the rectangle.
3. Create a method display() that display the length, width, perimeter and area of an object created using an instantiation on rectangle class.
4. Create a Parallelepipede child class inheriting from the Rectangle class and with a height attribute and another Volume() method to calculate the volume of the Parallelepiped.         

         
<details>
 <summary>Solution</summary>
  

<br>
  
This is the `main.py` file:

```python
# 1. Create the class
class Rectangle:
    def __init__(self, width, length):
        self.width = width
        self.length = length

    # 2. Create perimeter method
    def perimeter(self):
        perimeter = 2 * self.width + 2 * self.length
        return perimeter

    # 2. Create an area method
    def area(self):
        area = self.width * self.length
        return area

    # 3. Create the method display
    def display(self):
        print(
            f"The length is {self.length} units, the width is {self.width} units, the perimeter is {self.perimeter()} units and the area is {self.area()} square units")


# 4. Create a Parallelepiped child class
class Parallelepiped(Rectangle):
    def __init__(self, length, width, height):
        self.height = height
        super().__init__(width, length)

    def volume(self):
        volume = self.area() * self.height
        return volume


# --------------------------------------------------------- #
# Main program
# --------------------------------------------------------- #
# Create the object
rectangle = Rectangle(7, 5)
rectangle.display()
# Create the object
my_parellepiped = Parallelepiped(7, 5, 2)
# Show the volume
print(f"The volume of the parellepiped is: {my_parellepiped.volume()}")

```
  
</details>         

## 3. Assignment
         
1. Create a Python class Person with attributes: name and age of type string.
2. Create a display() method that displays the name and age of an object created via the Person class.
3. Create a child class Student  which inherits from the Person class and which also has a section attribute.
4. Create a method displayStudent() that displays the name, age and section of an object created via the Student class.
5. Create a student object via an instantiation on the Student class and then test the displayStudent method.         
         
<details>
 <summary>Solution</summary>
  

<br>
  
This is the `main.py` file:

```python
# Super class
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def display(self):
        print(f"The name is: {self.name} and the age is: {self.age}.")


# Subclass
class Student(Person):
    def __init__(self, name, age, section):
        self.section = section
        super().__init__(name, age)

    def display(self):
        print(f"The name is: {self.name} and the age is: {self.age}.\nStudents section is: {self.section}.")


# -------------------------------- #
# Main program
# -------------------------------- #
person = Person("Alex", 12)
person.display()

student = Student("peter", 20, "engineering")
student.display()

```
  
</details>           

## 4. Assignment<br>
         
1. Create a Python class called BankAccount which represents a bank account, having as attributes: accountNumber (numeric type), name (name of the account owner as string type), balance.
2. Create a constructor with parameters: accountNumber, name, balance.
3. Create a Deposit() method which manages the deposit actions.
4. Create a Withdrawal() method  which manages withdrawals actions.
5. Create an bankFees() method to apply the bank fees with a percentage of 5% of the balance account.
6. Create a display() method to display account details.
Give the complete code for the  BankAccount class.         
         
<details>
 <summary>Solution</summary>
  

<br>
  
This is the `main.py` file:

```python
class BankAccount:
    def __init__(self, accountNumber, name, balance):
        self.accountNumber = accountNumber
        self.name = name
        self.balance = balance

    def deposit(self, deposit):
        self.balance += deposit

    def withdrawal(self, withdrawal):
        if self.balance > withdrawal:
            self.balance -= withdrawal
        else:
            print("Balance is to small!")

    def bankFees(self):
        self.balance = 95 / 100 * self.balance

    def display(self):
        print(f"Name: {self.name}, Account Number: {self.accountNumber}, Balance: {self.balance}")


# ---------------------
# Main program
# ---------------------

first_account = BankAccount(1, "Alex", 4000)
first_account.deposit(500)
first_account.display()
first_account.withdrawal(5000)
first_account.withdrawal(1000)
first_account.display()
first_account.bankFees()
first_account.display()

```
  
</details>         
