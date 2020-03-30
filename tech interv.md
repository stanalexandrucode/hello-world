# Programming Basics questions

## Computer science

### Data structures

#### What is the purpose of a list (array in some programming languages) data structure? Name some methods of it!
* The purpose of a list is to collect objects in an orderly manner. 
* Some list methods are: _append()_, _extend()_, _insert()_, _remove()_, or _pop()_.
#### What is the difference between a list/array and a set?
* A list is ordered, can be accessed using an index, can have duplicate elements and are mutable (elements can be added,deleted, or moved around). 
* A set is unordered, its elements are unique and are immutable (they can't be changed once they have been assigned).
#### What is the purpose and methods of a dictionary/map data structure* The purpose of a dictionary is to map keys to values and store them in an array or collection. 
* The methods of a dictionary are: _items()_, _keys()_, _values()_, _get()_ and _popitem()_.



### Algorithms

#### Fibonacci sequences. Write a method (or pseudo code), that generates the Fibonacci sequences.
def fibonacci(n):
    terms = [0, 1]
    i = 2
    while i <= n:
        terms.append(terms[i - 1] + terms[i - 2])
        i += 1
    return terms

#### How do you find a max value in a list/array if you can’t use any built-in functions?
def max_in_list(listOfNr):
    maxi = 0
    for number in listOfNr:
        if maxi < number:
            maxi = number
    return maxi

#### How do you find the average of values in a list/array if you can’t use any built-in functions?
def find_avg(array):
    suma = 0
    count = 0
    for i in array:
        count +=1
        suma +=i
    return suma / count

#### What do we call an *in-place* sort?
* We call _sort()_ an in-place method because it modifies a given list in-place (it modifies the actual list on the spot without returning a new one) by using _<_ comparisons between items.

#### Explain an algorithm which sorts a list!
* Example of *Bubble Sort* algorithm:
```
finished = False                    # declare a boolean variable to check if we finished sorting the list
list_length = len(a_list)           # get the number of items in a list so that we don't call len() for each iteration
while not finished:                 # we keep looping until we finished sorting (finished == True)
    finished = True                 # we assume it's finished (the condition to break out of the while loop)
    for i in range(list_length - 1):               # iterate through the list without the last item
        if a_list[i] > a_list[i + 1]:              # if the current item is bigger than the next..
            a_list[i], a_list[i + 1] = a_list[i + 1], a_list[i]         # we swap them
            finished = False        # keep looping until we have nothing left to swap
```

### Programming paradigms - procedural

#### What is the call stack?
* The _call stack_ is a frame where Python stores information about functions which have been called. 
* Whenever a function is called, a new stack frame is added to the stack – all of the function’s parameters are added to it, and as the body of the function is executed, local variables will be created there.
* When the function finishes executing, its stack frame is discarded, and the flow of control returns to wherever you were before you called the function, at the previous level of the stack.

#### What is “Stack overflow”?
* A tool where we can find answer
#### What are the main parts of a function?
* The main parts of a function are: _parameters_, _function body_, _variables_, _statements_, _expressions_, _function call_ and _arguments (input parameters)_.


### Programming languages - Python  
#### How do you use a dictionary in Python?
* We can use a dictionary to store key-value pairs. To define a dictionary literal, we put a comma-separated list of key-value pairs between curly brackets. We use a colon to separate each key from its value. We access values in the dictionary by using keys instead of indices.

#### What does it mean that an object is immutable in Python?
* _Immutable_ means we cannot alter the existing value in any way. Some values in Python can be modified, and some cannot. 
* Integers, floating-point numbers and strings are all immutable types. Tuples are immutable data types

#### What is conditional expression in Python?
* A _conditional expression_ is a selection control statement that allows programmers to change the flow of control.
* Conditionals (the _if/elif/else_ family) can be used to pick a code block based upon the truth value of the conditions in them.

#### What are different types of arguments in Python?
* There are 3 types of arguments:
    1. _optional_ => To make a parameter optional, we need to supply a default value for it. Optional parameters must come after all the required parameters in the function definition:
    ```
    def make_greeting(title, name, surname, formal=True):
        if formal:
            return "Hello, %s %s!" % (title, surname)
        return "Hello, %s!" % name
    make_greeting("Mr", "John", "Smith")
    make_greeting("Mr", "John", "Smith", False)
    ```
    2. _positional_ => a tuple of values which are matched up with parameters in the function signature based on their positions:
    ```
    def make_greeting(title, name, surname, formal=True, time=None):
        if formal:
            fullname =  "%s %s" % (title, surname)
        else:
            fullname = name
        if time is None:
            greeting = "Hello"
        else:
            greeting = "Good %s" % time
        return "%s, %s!" % (greeting, fullname)
    make_greeting("Mr", "John", "Smith", False, "evening")
    ```
    3. _keyword_: => explicitly specify the parameter names along with the values:
    ```
    make_greeting(title="Mr", name="John", surname="Smith", formal=False, time="evening")
    ```

#### What is variable shadowing? (context: variable scope)
```
x = 0
def outer():
    x = 1
    def inner():
        x = 2
        print("inner:", x)
    inner()                # prints //inner: 2
    print("outer:", x) 
outer()                    # prints //outer: 1
print("global:", x)        # prints //global: 0
```

#### What can happen if you try to delete/drop/add an item from a List, while you are iterating over it in Python?
* You may encounter an IndexError: list index out of range.

#### What is the "golden rule" of variable scoping in Python (context: LEGB)? What is the lifetime of variables?
* The "golden rule" of variable scoping in Python (context: LEGB, L = Local, E = Enclosed (function is wrapped inside another function), G = Global, B =Built-in): when local as well as global variable is present, *preference is given to the local variable*. 
* The lifetime of a variable: it exists for as long as the function is executing. 

#### If you need to access the iterator variable after a for loop, how would you do it in Python?
* The built-in Python function _iter()_, which returns something called an iterator. The built-in function _next()_ is used to obtain the next value from an iterator:
```
a = ['foo', 'bar', 'baz']
itr = iter(a)
next(itr)
next(itr)
next(itr)
```
* If all the values from an iterator have been returned already, a subsequent next() call raises a StopIteration exception. 

#### What type of elements can a list contain in Python?
* A list can contain basically any type of elements.

#### What is slice operator in Python and how to use?
* The slice operator is a method that extracts a subset of a list, which will itself be a list.
* In order to use it, you need to specify an upper and lower bound. Note that our sublist will include the element at the lower bound, but _exclude_ the element at the upper bound:
```
animals = ['cat', 'dog', 'fish', 'bison']
print(animals[1:3]) # ['dog', 'fish']
print(animals[1:-1]) # ['dog', 'fish']
```

#### What arithmetic operators (+,*,-,/) can be used on lists in Python? What do they do?
* The arithmetic operators that can be used on lists are:
    - **+** addition
    - **-** subtraction
    - __*__ multiplication
    - **/** division
    - **%** modulo (the remainder of division)
    - __**__ exponentiation

#### What is the purpose of the in and not in membership operators in Python?
* Membership operators like _in_ and _not in_ are operators used to validate the membership of a value. It test for membership in a sequence, such as strings, lists, or tuples.

#### What does the + operator mean when used with strings in Python?
* When used with strings, the __+__ operator means concatenation: a method to add multiple strings together.

#### Explain f strings in Python?
* Python 3.6 added a new string formatting approach called formatted string literals or “f-strings”. This new way of formatting strings lets you use embedded Python expressions inside string constants:
```
>>> f'Hello, {name}!'
'Hello, Bob!'
```

#### Name 4 iterable types in Python!
* Lists, tuples, dictionaries and sets are all iterable types in Python.

#### What is the difference between list/set/dictionary comprehension and a generator expression in Python?
* List Comprehension allows us to create a list using for loop with lesser code.
* The Generator Expression allows us to create a generator without the yield keyword. Instead of creating a list/set/dictionary and keeping the whole sequence in the memory, the generator generates the next element in demand.
```
list_comprehension = [i for i in range(11) if i % 2 == 0]
generator_expression = (i for i in range(11) if i % 2 == 0)
```
* The generator yields one item at a time and generates item only when in demand. Whereas, in a list/set/dictionary  comprehension, Python reserves memory for the whole list. Thus we can say that the generator expressions are memory efficient than the lists/set/dictionary comprehensions. Also generator expressions are faster than list/set/dictionary comprehensions and hence time efficient.

#### Does the order of the function definitions matter in Python? Why?
 * Yes, the order of the function definitions does matter in Python, because any call to a function must come after that function definition.

#### What does unpacking mean in Python?
* We can use * or ** when we are calling a function to _unpack_ a sequence or a dictionary into a series of individual parameters:
```
my_list = ["one", "two", "three"]
print_args(*my_list)
my_dict = {"name": "Jane", "surname": "Doe"}
print_kwargs(**my_dict)
```

#### What happens when you try to assign the result of a function which has no return statement to a variable in Python?
* A function without an explicit return statement returns _None_. The variable will have the value of _None_.

## Software engineering

### Debugging

#### What techniques can you use while debugging a program in Python?
* We can use the following techniques for debugging:
    + insert a _print()_ statement after every line which outputs the intermediate results which were calculated on that line.
    + an IDE debugger tool or the _pdb_, a built-in Python module which we can use to debug a program while it’s running.
    + some automated tools which can help us to debug errors: 
        - _Pyflakes_ parses code instead of importing it, which means that it can’t detect as many errors as other tools (but it is also safer to use, since there is no risk that it will execute broken code which does permanent damage to our system).
        - _Pylint_ and _PyChecker_ do import the code that they check, and they produce more extensive lists of errors and warnings.
        - _Pep8_ specifically targets bad coding style – it checks whether our code conforms to Pep 8, a specification document for good coding style.

#### What does step over, step into and step out mean while using the debugger?
* __*step into*__ A function is about to be invoked and you want to debug into the code of that function, so the next step is to go into that function and continue debugging step-by-step.
* __*step over*__ A function is about to be invoked, but you're not interested in debugging this particular invocation, so you want the debugger to execute that function completely as one entire step.
* __*step out*__ You're done debugging this function step-by-step and you just want the debugger to run the entire function until it returns as one entire step.

#### How can you start to debug a program from a certain line using the debugger?
* __*line breakpoint*__ You don't care how it got there, but if execution reaches a particular line of code, you want the debugger to temporarily pause execution there so you can decide what to do.

### Version control

#### What are the advantages of using a version control system?
- The primary benefits you should expect from version control are as follows:
    1. A complete long-term change history of every file (enables going back to previous versions to help in root cause analysis for bugs and it is crucial when needing to fix problems in older versions of software).
    2. Branching and merging. Individuals working on their own can benefit from the ability to work on independent streams of changes. There are many different workflows that teams can choose from when they decide how to make use of branching and merging facilities.
    3. Traceability. Version control software keeps track of every modification to the code in a special kind of database. If a mistake is made, developers can turn back the clock and compare earlier versions of the code to help fix the mistake while minimizing disruption to all team members.

#### What is the difference between the working directory, the staging area and the repository in git?
- Git has 3 areas:
    + The _working directory_ = contains the latest downloaded version from the repository together with any changes that have yet to be committed. As you're working on a project, all changes are made in this working directory.
    + The _staging area_  = helps to maintain this workflow by allowing you to only promote certain files at a time instead of all the changes in your working directory. Users move, otherwise referred to as promote, changes from the working directory, to a staging area before committing them into the repository.
    + The _repository_ = a virtual storage of your project. It allows you to save versions of your code, which you can access when needed.

#### What are remote repositories in git?
- Remote repositories are versions of your project that are hosted on the Internet or network somewhere. Collaborating with others involves managing these remote repositories and pushing and pulling data to and from them when you need to share work.

#### Why does a merge conflict occur?
- Merge conflicts happen when you merge branches that have competing commits, and Git needs your help to decide which changes to incorporate in the final merge.

#### Through what series of commands could you put a new file into a remote repository connected to your existing local repository?
- In Terminal, add the URL for the remote repository where your local repository will be pushed:
    + $ git remote add origin remote repository URL # Sets the new remote
    + $ git remote -v # Verifies the new remote URL
- Push the changes in your local repository to GitHub:
    + $ git push origin master # Pushes the changes in your local repository up to the remote repository you specified as the origin

#### What does it mean atomic commits and descriptive commit messages?
- When making code changes, you want to make commits that are generally smaller and that encompass only one irreducible feature, fix, or improvement.

#### What’s the difference between git and GitHub?
- Git is a version control system that lets you manage and keep track of your source code history.
- GitHub is a web-based hosting service that lets you manage Git repositories.  If you have open-source projects that use Git, then GitHub is designed to help you better manage them.

## Software design

### Clean code

#### What does clean code mean?
- Code is clean if it can be understood easily – by everyone on the team. Clean code can be read and enhanced by a developer other than its original author. With understandability comes readability, changeability, extensibility and maintainability.

#### What steps do we usually do during a clean code refactoring?
- Read through the whole code.
- Summarize what is the purpose of the script in one sentence.
- Run the code to see what is the end result.
- The code should keep runnable and show the same content when you finish the refactor.
- Run the code frequently to check you are on the right track.
- Actual refactoring:
    + Remove clutter: Clutter is anything in your code that does not add value
        * Format your code
        * Delete comments
    + Remove complexity:
        * bad names
        * long methods
        * deep conditionals
        * improper variable scopes (global, local)
    + Remove cleverness: If it's simple and elegant you wouldn't refer to it as 'clever'
    + Remove the 3 D's: duplication, duplication, duplication
        * his can be applied by extracting the duplicated code parts into functions

### Error handling

#### What is exception handling?
- _Exception handling_ is a method that handles unexpected errors in a Python program. Instead of letting the error crash our program we can intercept it, do something about it, and allow the program to continue.
- Errors are called exceptions in Python and all exceptions are subclasses of the Exception class.

#### What are the basics of exception handling in Python?
- The basics of _exception handling_ consist of _try-except_ blocks. Python will try to process all the statements inside the _try_ block. 
- If an error occurs at any point as it is executing them, the flow of control will immediately pass to the except block, and any remaining statements in the try block will be skipped.
- It is good practice if the only code inside the try block is the single line that is the potential source of the error that we want to handle.

#### In which case should we catch an exception? Why?
- We should catch an exception when we want to protect small blocks of code against specific errors (better than to wrap large blocks of code and write vague, generic error recovery code).
- We catch exceptions because:
    + Exception handling separates normal code from code that handles errors.
    + Exceptions can easily be passed along functions in the stack until they reach a function which knows how to handle them. 
    + Exceptions come with lots of useful error information built in – for example, they can print a traceback which helps us to see exactly where the error occurred.

#### What can/should we do with an exception in the ‘except’ block?
- In the ‘except’ block we should write code that the program will execute when there is an exception.
- We can raise exceptions ourselves using the _raise_ statement - perhaps we may want to handle it partially in the current function, but also want to respond to it in the code which called the function.
- We can also write our own custom exception classes which are based on existing exception classes.

#### What does the else and finally statement do in a try-except block in Python?
- The _else_ statement will be executed only if the try clause doesn’t raise an exception.
- The _finally_ clause will be executed at the end of the try-except block no matter what – if there is no exception, if an exception is raised and handled, if an exception is raised and not handled, and even if we exit the block using *break*, *continue* or *return*. We can use the *finally* clause for cleanup code that we always want to be executed.

## Software Development Methodologies

#### What is the main goal of a retrospective meeting?
According to Agile software development:
>- A retrospective meeting is a meeting that's held at the end of a single development cycle, usually measured as one week or two. 
>- The main goal of the retrospective is to reflect on what happened in the development and identify actions for improvement and going forward.
>- Each member of the team members answers the following questions:
>    + What worked well for us?
>    + What did not work well for us?
>    + What actions can we take to improve our process going forward?

## Programming environment- _wget file_

### Unix

#### What is UNIX and what is Linux?
- UNIX is an operating system that was born in the late 1960s, when AT&T Bell Labs released an operating system called Unix written in C, which allows quicker modification, acceptance, and portability. It began as a one-man project under the leadership of Ken Thompson of Bell Labs. It went on to become most widely used operating systems. Unix is a proprietary operating system. Unix is a proprietary operating system.
- Linux is a replica of UNIX that does not use its code built by Linus Torvalds at the University of Helsinki in 1991. The name "Linux" comes from the Linux kernel. It is free and open source software.

#### What do we call the shell in Linux?
- Shell = command line interpreter

#### What does root means in a Linux environment?
- Root is the user name or account that by default has access to all commands and files on a Linux or other UNIX-like operating systems. It is also referred to as the root account, root user and the superuser.

#### How do you access your personal files in Linux?
- In Linux, personal data is stored in /home/username folder.

#### How can you install an application in Linux?
- Run the command in the Terminal (text input/output environment):
```
sudo apt install <name_of_application>
```

#### What is package management in Linux, what are repositories?
- Package management system allows users to install, update, remove and get information about software installed.
- Repositories are storage locations where the packages are downloaded from.
- Users can use _apt_ and _dpkg_ commands to query and update the database of software available in repositories and installed on the system, to install or remove software and upgrade installed packages, and clean up obsolete programs.
#### How do you navigate in the filesystem with the command line?
- _cd_ Change directory. Used to navigate between folders.
- _pwd_ Display current directory.
- _ls_ Display a list of files in the current directory.
- _stat_ Display when a file was last accessed, modified, or changed.

#### What does the following commands do: mkdir, rm, cat, cp, touch?
- _mkdir_ Create a directory.
- _rm_ Remove a file or set of files.
- _cat_ Display the contents of a text file.
- _cp_ Makes a copy of a file.
- _touch_ Create a file.

#### How can you look up what does a command do in Linux if you have no internet connection?
- _command --help_ or _man command_

#### What does the following commands do: head, tail, more, less?
- _head_ Output the first 10 lines of file.
- _tail_ Output the last 10 lines of file.
- _more_ Output the contents of file.
- _less_ View and paginate file.

#### How do you download a file from internet using the terminal?
- _wget file_
