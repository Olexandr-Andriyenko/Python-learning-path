# What is python

Python is one of the most successful programming languages of our time, because it can be used in basically all fields of knowledge: 
Mathematics, science, technology and even art. Besides, Python is a so-called higher programming language. To understand what exactly this means, we must first understand what a programming language is. 

In general, a language can be categorized into artificial and natural languages.
Natural language is a language "spoken" by humans, such as German and English.
The focus is on the expression of human thought and feeling.
It is therefore a means of communication between people, which is constantly evolving along with people.
Such a natural language is never developed by a single person, but by a totality of people sharing a common 
experience set with each other. Today, there are more than 6000 different natural languages known.
There are different theories how these natural languages had developed, but this is not relevant for us for now, 
because in computer science the artificial language plays a big role.
That is why we will take a closer look at artificial language to get deeper into the meaning of programming language.<br>
<br>
<br>

<p align="center">
<img src="https://github.com/Olexandr-Andriyenko/Python-learning-path/blob/main/illustrations/img01.png" width="450">
<p>
  
<br>
<br>
  
Artificial languages are also often called constructed languages because, unlike natural languages, they had not evolved in the progress of human history as a medium of communication between people, but were constructed for a specific purpose.
<br>
<br>
For example, secret languages have the purpose that only initiates understand the conversations among themselves.
For such a secret language, a "key" is designed that makes it possible to encode the messages between the initiates, for example, by shifting letters or replacing them with numbers. In the process of the programming exercises, we will learn about the so-called "Caesar cipher", which allows us to encode a message.
<br>
<br>
Another example of artificial languages are the fictional languages that are conceived as part of a fictional world.
They can be found mostly in movies, books or even computer games. If you've ever watched Star Trek, you're probably familiar with the fictional language Klingon.
Many other examples of artificial languages exist, but for us as programming enthusiasts, the formal language is of particular importance.
<br>
<br>
For the formal language there are many mathematical descriptions, which I will not go into for now, instead I will give you a simple description for the beginning, to get a basic overview. Formal languages have no meaning for interpersonal communication, their purpose is to enable an exact mathematical description or to describe the processing of data. Such a formal language is built from a certain set of symbol chains ("words" of a language), which can be composed from a character set ("alphabet" basic symbols). Perhaps in simpler terms: A formal language is composed of a set of words, which in turn is composed of characters of the alphabet of a language. The alphabet is the set of characters that is allowed to be used in a word. With such a formal language, a natural language can be modeled very well, because computers only work with formal languages. At some point you will come across the terms syntax and semantics in the context of languages. Syntax refers to the rules by which words of the language are constructed and semantics answers the question: What is the meaning of these words?
<br>
<br>
  
<p align="center">
<img src="https://github.com/Olexandr-Andriyenko/Python-learning-path/blob/main/illustrations/img02.png" width="450">
<p>  
  
<br>
<br>
Since we already know that Python is a programming language, we can already answer the following question with the previous knowledge: What actually is a programming language?<br> 

***A programming language is a formal language that is used to formulate algorithms and data structures that can be executed by the computer.***

<br>
An algorithm is the set of all steps which are necessary to solve a given problem. So an algorithm is a solution plan, according to which data are processed in such a way, that they lead to the desired result. Algorithms are the basis of programming and can be formulated independently of a chosen programming language. In order to formulate an algorithm, first of all you have to describe the problem which you want to solve.
<br>
As an example of an algorithm, let's take the following example as a problem statement:
<br>
How much wallpaper is needed, to completely cover a rectangular wall?
<br>
In order to solve this problem, we will now define separate steps, which will be executed step by step in order to master this issue:
<br>
<br>
  
<p align="center">
<img src="https://github.com/Olexandr-Andriyenko/Python-learning-path/blob/main/illustrations/img03.png" width="400">
<p> 

<br>
<br>  
These four individual steps are necessary to solve the problem. The four individual steps combined as a whole are called an algorithm.
Such an algorithm can then be implemented in any programming language. In very general terms, an algorithm is a systematic, logical procedure of steps that leads to the solution of a problem. Such an algorithm can also be seen as a function, because input variables (width and length) are transformed into output variables (area), which represent the solution of the problem. Now it is left to explain what exactly a data structure is.
<br>
<br>
In computer science, data refers to certain information that has been translated into a particular format so that a computer can understand and process it.
Data such as videos, images, sounds or texts are represented as binary values with patterns of two numbers (0 and 1) inside the computer.
<br>
<br>
But these data must have some order in the computer. For this purpose the so-called data structures are available, this is understood as the organization of data in the memory of a computer. Data structures are important for organizing, processing, accessing and storing data. Over time, you will learn about different data structures and understand how to use them.
<br>
<br>
The two terms "algorithms" and "data structures" are of central importance in computer science. Already in 1976 Niklaus Wirth published a book with the title "Algorithms + Data Structures = Programs". This statement is of great importance and illustrates the
term "program". A program is a sequence of instructions and definitions, written in machine language or a higher programming language so that the computer understands the instructions. The program's task is to make the computer understand and execute an algorithm and process the necessary input data to solve a given problem. Programs are also very often called software. The person who creates a program is called a programmer and his activity is called programming (don't worry about this activity, we will deal with it long enough).
<br>
<br>
At the beginning of the chapter was written: "Python is a higher programming language". Slowly we are getting closer to the answer, what is Python. Now it only remains to find out why Python is not only a programming language, but a "higher" programming language. It was already mentioned that a computer understands only zeros and ones, a pattern from these two numbers is also called machine code, machine language or binary code. The reason for this lies in the construction of a computer from certain building blocks, which are controlled by electric current. Electric current can either flow through these components, represented by a one, or not, represented by a zero. However, for a programmer it is very complicated to develop a program by using a machine language. This is because a human being is not used to thinking in ones and zeros, because it does not correspond to its everydays communication medium (natural language).
<br>
<br>
  
<p align="center">
<img src="https://github.com/Olexandr-Andriyenko/Python-learning-path/blob/main/illustrations/img04.png" width="400">
<p> 
  
<br>
<br>
To prevent programming directly with the machine language, different programming languages were invented, which abstract and simplify the communication between computer and human. To illustrate how impractical machine language programming is, consider the following command, whose meaning is not relevant to us for now:
  
```ruby
  int a = 2;  
```
  
This is an excerpt of a programming code from the language "C" language. If the same code were formulated in machine language, it would look like this:
  
```ruby
  11000111010001011111110000000010
```

The reason why one does not program directly in a machine language nowadays is the same reason, that nowadays people prefer to drive from Germany to France in a car, rather than in a horse carriage. The use of a machine language is confusing for humans, error-prone, non-compliant, and very complex compared to a 
abstract programming language that is similar to a natural language.
<br>
<br>
It is important to mention that such a machine language is dependent on the processor architecture (structure of the processors). Each processor architecture has its own instruction set, which represents the set of machine instructions that a particular processor can execute.
<br>
<br>
Programming languages allow the interaction between programmer and computer to be abstracted and significantly simplified. And exactly depending on this level of abstraction, programming languages can be divided into machine languages, assembly languages and higher programming languages. Python is a higher-level programming language, which means that it is very far abstracted from zeros and ones and is closer to natural language.
<br>
<br>
Assembly languages are much less abstracted from zeros and ones compared to higher programming languages. Although you don't program in binary code, the commands are still very cryptic and confusing. A higher level programming language like Python has a very high level of abstraction, which makes the language more understandable and easy to remember.
<br>
<br>
  
<p align="center">
<img src="https://github.com/Olexandr-Andriyenko/Python-learning-path/blob/main/illustrations/img05.png" width="600">
<p> 
  
<br>
<br>
It was already mentioned that a computer understands only machine language. This means that the programming language that we use to create a program must firstly be translated into machine language, before the computer executes the program. Without translation, the computer would not understand the program and would not be able to execute it. To convert a programming language into machine language, you need a translator. Depending on what kind of translator is used for a programming language, it is either a compiled programming language, an interpreted programming language or an intermediate language. Python is an interpreted programming language, what exactly this means will be understood in the next lines. 
<br>
<br>
When a program is created by using a programming language, it creates a file with the programming code, which is also called source code. This source code must now be translated into machine language. This can be done either with a compiler or interpreter. For compiled programming languages like C or C++, a compiler must be used for the conversion into machine language. A corresponding compiler for the respective programming language must be available on each operating system. For compiling the C programming language, a different compiler with the appropriate version is required on Windows, Linux or macOS. A program that has been compiled for a specific operating system is also called a native program. When using compilers, the following points should be considered:

- Program must be translated into machine language before execution
- The entire source text is translated at once
- Errors are collected and displayed after complete compilation 
- The translation speed is low
- The development effort is high
- Program requires less execution time and memory

  
In an interpreted programming language such as Python, there is an interpreter used to translate it into machine language. The source code is translated into machine language line by line during the runtime of the program. The interpreter does not finish his work until the end of the program is reached or an error is detected in the source code. Programming languages which interpret source code are often called scripting languages. When using interpreters, the following points should be considered:
- Source code translation is performed during the runtime of the program
- It is translated line by line
- Better error analysis because translation stops immediately when an error appears
- Interpreted code is about 20 times slower than compiled code
- Can be executed on any operating system as long as suitable interpreter is available
- Development effort very low
  
Often a clear assignment of a programming language to the compiler language or interpreter language is not possible, because for most programming languages both compilers and interpreters are available. At this point it must be mentioned that the description of compiler and interpreter is kept simple, but offers a good introduction to the topic. In reality, a compiler and interpreter is not a pure translator, because they have many more tasks than converting the source code into machine language.
<br>
<br>
Some programming languages, such as Java, cannot be clearly assigned to a compiled or interpreted programming language. In Java, both an interpreter and compiler are used. In this process, the source code is translated into an intermediate language (bytecode) by a compiler and then converted into machine language by an interpreter.
This can have some advantages such as platform independence of a programming language.
<br>
<br>
After all the terms and explanations, you should now be able to successfully answer the question **"What is Python?"**:
- It is a higher level programming language because Python is very far abstracted from the machine language and is similar to the natural language
- Python is a scripting language because it is usually executed with an interpreter
