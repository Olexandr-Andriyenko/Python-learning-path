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
