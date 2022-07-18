# Integrated development environment


Now that Python is installed on the operating system, you could theoretically already start programming. Now the only question is where exactly is programming happening, in which software (environment) are the programs being written? In fact, it doesn't take much to get started creating a Python program. Under Windows, a simple text editor is already enough. To do this, you can for example, create a text document on the desktop using the right mouse button under "New".
<br>
<br>
Then you open the created text document and you have an area where you can write your own source code. To test this you can paste the following source code:
```python
import time
print("hello")
time.sleep(5)
```
The meaning of the individual "words" is not important for now, the explanations will come later. To run this program now, you need to go to "Save As" under "File". Afterwards a window appears where you have to select "All files" under "File type". At the "filename" you choose any name, but you have to take care that the ending of the name is ".py" (e.g. program.py). After saving, a Python file appears, which can be executed by double-clicking on it. The file is located under the location you selected. After running the file, the console will open automatically, saying "hello". After 5 seconds the console closes automatically and the program is finished.
<br>
<br>
If you have completed all the steps, you have just created your first Python program. The enthusiasm is probably not that great, because the program doesn't really do anything exciting except output the word "hello". Of course, in the future we will deal with much more complex programs, behind which there is also a meaning. But what I wanted to show is that a Python program can be created with simple tools like a text editor. However, such a text editor has its limitations and disadvantages, in the development of programs, so they are not actually used in practice. For example, in an ordinary editor the programmer is not informed if he made any mistakes, such as syntax errors. There is also no tool available that allows us to perform a detailed error analysis. The source code has constantly the same color and important program parts are not highlighted in color. Also a management of the current programming project is missing. Graphical elements (GUI) are also not supported.
<br>
<br>
In software development, programming is therefore done in a so-called IDE (Integrated Development Environment) instead of in the common text editors. An IDE is an integrated development environment that provides a collection of the most important tools for software development on a graphical interface. An IDE can be compared to a Swiss Army knife, which is equipped with many different tools. As a programmer, we should get familiar with an IDE, because it simply makes our everyday life easier and helps us to create programs.
<br>
<br>
The most important components of an IDE are:
- Source code editor with syntax highlighting, visual hints, bug checking 
- Debugger for effective error analysis to fix bugs
- Compiler, Interpreter
- Tools for the development of graphical user interfaces (GUI)
- Version control
- Many more tools and extensions
