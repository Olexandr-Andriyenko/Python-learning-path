# Modules

In simple words, a Python module is simply a file that contains pre-written Python code. In principle, each Python script can be seen as a Python module in its own way.
In practice, modules are primarily used to make it easier to organize the source code of a larger software project and to keep it clear. A general rule is that a module should only be so large that its contents and purpose can be summarized in one or two sentences. Each module represents a separate namespace for variables, so that functions with the same name defined in different modules do not cause conflicts. Module names are generally written in lowercase in Python.
<br>
<br>
With the installation of python many modules are already included. If you want to list all available modules, you have to open the PYTHON CONSOLE and type: 

```
help("modules") 
```

The console will show you all intealled modules, of course you can add latter new modules.

<p align="center">
<img src="https://github.com/Olexandr-Andriyenko/Python-learning-path/blob/main/illustrations/img27.JPG" width="700">
<p> 
  
## Import keyword
  
To integrate an external module or another .py file, into the current program, the following syntax is common:  
```python
  
# import modulname
# Exampels:

import random
import sys
  
```
  
The module "sys"  provides access to some variables used or maintained by the interpreter and to functions that interact strongly with the interpreter. It is always available.<br>
<br>
The module "random"  implements pseudo-random number generators for various distributions.
<br>
<br>
The module to be imported must be located in the Python path. So either installed globally or contained in the current directory. Otherwise an adjustment of the variable "sys.path" is necessary.
  
## Use of modules
  
After importing a module, the functions, variables, methods and classes defined in the module can be used. For this, the dot notation from the concept of object-oriented programming is often used, which you will get to know later in detail.
<br>
<br>
Let's take a closer look at the "random" module and use some functionalities of it. For each module you can find documentation, which you should definitely read!
Here is do documentantion to the ["random" module](https://docs.python.org/3/library/random.html).
<br>
<br>
In this example we use the "random" module:
  
```python
# Import the random module
import random
# Return a random integer between 0 and 10 where 0 and 10 is included
rand_num = random.randint(0, 10)
print(rand_num)
# Return a randomly selected element between 10 and 20 of two steps
rand_num_range = random.randrange(10, 20, 2)
print(rand_num_range)
# Return a random element from the non-empty sequence
companys = ["Apple", "Google", "Microsoft", "Meta", "Paypal"]
rand_company = random.choice(companys)
print(rand_company)

# Output is:
# 8
# 10
# Apple

```
  
So after importing a module, the classes, functions and variables defined in the module can be used with the following syntax:
 
```
modulname.Classname
modulname.Variablename
modulname.funcionname() 
```
  
To be able to save typing work with longer module names, an shortcut syntax is also possible when importing a module:
 
```python
# import modul_name as own_name
import random as r
# Return a random integer between 0 and 10 where 0 and 10 is included
rand_num = rd.randint(0, 10)
print(rand_num)
```

A further simplification is possible if you only want to import individual classes or functions of a module.
Multiple class or function names can also be specified, each separated by a comma. The classes or functions imported in this way can then be called directly as if they were defined in the current file.
  
The following syntax is possible for this:

```python
# from modulname import Class_name   
# from modulname import funkcion_name

from random import randint
# Return a random integer between 0 and 10 where 0 and 10 is included
rand_num = randint(0, 10)
print(rand_num)

  
```
  
During the learning process you will get to know different modules over time. You should only learn modules if you need them for a project. Otherwise you try to learn different modules, don't apply them to projects and forget them. It is important that you always work with the documentation of the modules because you can never know all the functionalities by memory.
<br>
<br>
A module is a file containing Python definitions and statements. The file name is the module name with the suffix .py appended.
