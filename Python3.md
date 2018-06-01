# Python 3000 quick reference

### Quick look at contents of module

```python
dir(module)
```

### Quick look at documentation of function

```python
help(module.function())
help(os.getcwd())
```

### generate random integers

```python
import random
random.randint(1, 60)
# This will generate a random integer in range 1 to 59
```

### NOTE

* Primitive data types like integers/strings/float/etc get passed to functions by value
* Other data types gets passed in as reference and not by value (list, set, dictionary)

### Find first occurance of substring in string

```python
my_string = "Hello !"
print my_string.find('l')
# This finds first occurance of 'l' in string 'hello' 

>>> 2
```

### find multiple occurance of substring in a string

second argument we pass the place where is starts its search from  
that index is included in search.  

```python
my_string = 'hi hello hi !!'
print my_stirng.find('h', 0)

>>> 0

print my_string.find('hi', 4)

>>> 9

print my_string.find('h', 1)

>>> 3
```

### String formatting

```python
my_string = "{}___{}".format('hello', 292)

>>> hello____292

# We can also specify the index of argument before hand
my_string = "{1}----{0}----{1}".format(23,'world')

>>> world----23----world
```

### Count occurance of substring in a string

```python
my_string = 'helloollooll'
print my_String.find("ll")

>>> 3
```

### Convert string to all upper case

```python
my_string = 'hello'
print my_string.upper()

>>> HELLO
```

### Convert string to all lower case 

```python
my_string = 'HELLO'
print my_string.lower()

>>> hello
```

### Capitalize 1st letter in string

```python
my_string = 'happy birthday!!'
my_string.capitalize()

>>> Happy birthday!!
```

### Capitalize 1st letter of each word

```python
my_string = 'happy birthday!!'
my_string.title();

>>> Happy Birthday!!
```

### String validation methods

```python
x = "string"

x.istitle()
x.iscapitalize()
x.isupper()
x.islower()

x.isalpha() # only alphabets
x.isdigit() # only numbers
x.isalnum() # alphabets and numbers
```

### Remove pattern from string

```python
my_string = '00000happyBirthday0000'
my_string.strip('0')

>>> happyBirthday
```

### Make single string from list

```python
a = ['a', 'b', 'c']
':'.join(a)

>>> 'a:b:c'
```

### List Slicing

```
[start:end:step]
```

### Add a pause to program

```python
import time
time.sleep(5)
# adds a pause of 5 seconds
```

### Add element at particular location in the list

```python
users = ['alice', 'bob']
users.insert('roma', 1)

>>> ['alice', 'roma', 'bob']
```

### delete 1st occurance in list

```python
a = [1, 2, 3, 1, 1, 2, 3]
a.remove(1)
>> [2, 3, 1, 1, 2, 3]
#1st occurance of 1 is removed
```

### pop element from last index in list

```python
a = [1, 2, 3, 1, 1, 2, 3]
a.pop()
>>[1, 2, 3, 1, 1, 2]
#last element is removed from the list
```


### pop element from particular index in list

```python
a = [1, 2, 3, 1, 1, 2, 3]
a.pop(2)
>>[1, 2, 1, 1, 2, 3]
#3rd element is removed from the list
```

### concatenate 2 lists

```python
a = [1, 2, 3, 1, 1, 2, 3]
a + [1, 2, 3]
>>[1, 2, 3, 1, 1, 2, 3, 1, 2, 3]
#both the lists are now concatenated

# method 2
a.extend([1, 2, 3])
>>[1, 2, 3, 1, 1, 2, 3, 1, 2, 3]
```

### insert element at a particular position in list

```python
a = [1, 2, 3]
a.insert(1, 7)
>>[1, 7, 2, 3]
```

### make a copy of list and not a reference

```python
a = [1, 2, 3]
# make a reference
b = a
# make a actual copy
c = a.copy()
```

### Convert list into a tuple

```python
a = [1, 2, 4]
b = tuple(a)

>>> (1, 2, 4)
```

### List Comprehension

```python
even_numbers = [for i in range(0,20) if i%2 == 0]
```

### Get all keys in dictionary

```python
dict = {'a':1, 'b':2, 'c': 3, 'd': 4}
dict.keys()

>>> ['a', 'b', 'c', 'd']
```

### Get all item pairs in dictionary
Returns a list of tuples

```python
dict = {'a':1, 'b':2, 'c': 3, 'd': 4}
dict.items()

>>> [('a', 1), ('c', 3), ('b', 2), ('d', 4)]
```

### if key not found then set it to some default value

```python
a = {'a': 1}
a.setdefault('e', 0)
>>{'a': 1, 'e': 0}
# if 'e' is found in dict then it wont be touched, if not found then it will be set to the default value of 0
```

### Avoid key errors

`.get(key)` returns the corresponding value if found  
else returns `None`  

```python
a = {'a': 1}
a['e']

>>> KeyError

a.get('e')

>>> None
```

### creating sets

```python
vowels = { 'a', 'e', 'e', 'i', 'o', 'u', 'u' }
>>> vowels
{'e', 'u', 'a', 'i', 'o'}
```

### creating sets method 2

```python
vowels2 = set('aeeiouu')
>>> vowels2
{'e', 'u', 'a', 'i', 'o'}
```

### take union of set

```python
vowels = set('aeiou')
word = 'hello'
u = vowels.union(set(word))
>> {'a', 'e', 'i', 'o', 'u', 'h', 'l'}
```

### whats not shared (difference)

```python
vowels = set('aeiou')
word = 'hello'
d = vowels.difference(set(word))
>>> d
{'u', 'i', 'a'}
```

### find intersection of sets

```python
vowels = set('aeiou')
word = 'hello'
i = vowels.intersection(set(word))
>>> i
{'e', 'o'}
```

### create a tuple

```python
a = ('a', 'e', 'i')
```

### create a tuple of single object

```python
a = ('a',)
# Make sure there is a comma at the end inside a tuple if you want to create a tuple of single object
```

### create empty data structure

```python
l = list()
s = set()
d = dict()
t = tuple()
```

### specify accepted data type and return type in a function

```python
def search4vowels(word:str) -> set:
  """Return any vowels found in a supplied word."""
  vowels = set('aeiou')
  return vowels.intersection(set(word))
```

### default arguments in functions

```python
def search4letters(phrase:str, letters:str='aeiou') -> set:
```

### Flask write logs to a file

```python
def log_request(req:'flask_request', res:str) -> None:
  with open('vsearch.log', 'a') as log:
    print(req.form, file=log, end='|')
    print(req.remote_addr, file=log, end='|')
    print(req.user_agent, file=log, end='|')
    print(res, file=log)

@app.route('/', methods=['POST', 'GET'])
def do_search() -> 'html':
  log_request(request, results)
  # do stuff
  return jsonify(res)
```

### MYSQL Driver python

```python
import mysql.connector

dbconfig = { 'host': '127.0.0.1',
             'user': 'vsearch',
             'password': 'vsearchpasswd',
             'database': 'vsearchlogDB', }

conn = mysql.connector.connect(**dbconfig)

cursor = conn.cursor()

_SQL = """show tables"""

cursor.execute(_SQL)

# result don't appear immmidiately, we have to request them explicitly

"""
You can ask for results using one of three cursor methods:
•	 cursor.fetchone retrieves a single row of results.
•	 cursor.fetchmany retrieves the number of rows you specify.
•	 cursor.fetchall retrieves all the rows that make up the results.
"""

res = cursor.fetchall()
>>> res
[('log',)]

# fetchAll returns list of tuples
# fetchone returns single tuple

"""
Any insert operation doesn't directly insert into the database, 
it first goes to the database cache and later this cache is executed to the actual server disk,
so if there is any select query before cache is committed then select query will not return the data,
so it is advised to commit the cached data
"""

conn.commit()

# close the cursor

cursor.close()

# close the connection

conn.close()
```

### Classes in Python

```python
class CountFromBy:
  def __init__(self, v: int=0, i: int=1) -> None:
    self.val = v
    self.incr = i
  
  def increase(self) -> None:
    self.val += self.incr
  
  def __repr__(self) -> str:
    return str(self.val)
  
  # when you print the object, this method will be called
  def __str__(self):
    print(self.val)
  
  # Destructor
  def __del__(self):
    print("Clean up code ! deleting object")
```

### Static Methods

These methods don't have any `cls` param or `self` param.  
They are simple utility functions that can be called without  
the object as well.  

```python
class A():
  @staticmethod
  def go():
    print "Go to the school !!"

A.go()

>>> "Go to the school !!"
```

### Class Methods

* A class method is a method which is bound to the class and not the object of the class.  
* They have the access to the state of the class as it takes a class parameter that points to the class and not the object instance.  
* It can modify a class state that would apply across all the instances of the class. For example it can modify a class variable that will be applicable to all the instances.  

```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age
     
    # a class method to create a Person object by birth year.
    @classmethod
    def fromBirthYear(cls, name, year):
        return cls(name, date.today().year - year)

person1 = Person('Roshi', 22)
person2 = Person.fromBirthYear('Master', 1996)
```
Class methods are mostly used for creating factory methods.

### 'with' statement and context management protocol

```python
"""
What's needed in context manager?
•	an __init__ method to perform initialization (if needed);
•	an __enter__ method to do any setup; and
•	an __exit__ method to do any teardown (a.k.a. tidying-up)
"""

class UseDatabase:
   def __init__(self):
      pass
    
   def __enter__(self):
      pass
    
   def __exit__(self):
      pass
```

### Example of context manager (self explainatory)

```python
import mysql.connector

class UseDatabase:
  
  def __init__(self, config: dict) -> None:
    self.configuration = config

  def __enter__(self) -> 'cursor':
    self.conn = mysql.connector.connect(**self.configuration)
    self.cursor = self.conn.cursor()
    return self.cursor
  
  def __exit__(self, exc_type, exc_value, exc_trace) -> None:
    self.conn.commit()
    self.cursor.close()
    self.conn.close()
    
# how to use this context manager?

dbconfig = { 'host': '127.0.0.1',
             'user': 'vsearch',
             'password': 'vsearchpasswd',
             'database': 'vsearchlogDB', }

with UseDatabase(dbconfig) as cursor:
  _SQL = 'show tables'
  cursor.execute(_SQL)
  data = cursor.fetchall()
```

### Pass function to a function

```python
def apply(func: object, value: object) -> object:
  return func(value)
  
# using this apply function

apply(print, "hello")
>>> hello

apply(len, 'abc')
>>> 3
```

### Nested functions

```python
def outer():
  
  def inner():
    print('This is inner.')
  
  print('This is outer, invoking inner.')
  inner()
  
# Output ->
This is outer, invoking inner.
This is inner.
```
When would you ever use this?
Looking at this simple example, you might find it hard to think of a situation
where creating a function inside another function would be useful. However,
when a function is complex and contains many lines of code, abstracting some of
the function’s code into a nested function often makes sense (and can make the
enclosing function’s code easier to read).

### Return a function from function

```python
def outer():
  
  def inner():
    print('This is inner.')
  
  print('This is outer, returning inner.')
  return inner

i = outer()
>>> This is outer, returning inner.
type(i)
>>> <class 'function'>
i()
>>> This is inner
```

### Use * to accept an arbitrar y list of arguments

```python
def myfunc(*args):
  for a in args:
     print(a, end=' ')
  if args:
    print()
 
myfunc(10)
>>> 10
myfunc(10, 20, 30, 40, 50)
>>> 10, 20, 30, 40, 50
```

### * works on the way in, too

If you provide a list to myfunc as an argument, the list (despite potentially
containing many values) is treated as one item (i.e., it’s one list). To instruct the
interpreter to expand the list to behave as if each of the list’s items were an
individual argument, prefix the list’s name with the * character when invoking the
function.

```python
values = [1, 2, 3, 4, 5]
myfunc(values)
>>> [1, 2, 3, 4, 5]

# myfunc treats this list as 1 item
# what if I want the function to treat it as list of args

myfunc(*values)
>>> 1 2 3 4 5
```

### Accepting a Dictionary of keyword Arguments

```python
def myfunc2(**kwargs):
  for k,v in kwargs.items():
    print(k, v, sep='->', end=' ')
  if kwargs:
    print()

myfunc(a=2, b=3)
>>> a->2 b->3
```

### ** works on the way in, too

You probably guessed this was coming, didn’t you? As with *args, when you
use **kwargs it’s also possible to use ** when invoking the myfunc2 function.

```python
dbconfig = { 'host': '127.0.0.1',
            'user': 'vsearch',
            'password': 'vsearchpasswd',
            'database': 'vsearchlogDB', }
            
conn = mysql.connector.connect(**dbconfig)
```

## Fuction Decorators

### simplest decorator

```python
def decorator_func(original_func):
    def wrapper_func():
        print "some code before the {} function".format(original_func.__name__)
        return original_func()
    return wrapper_func()

@decorator_func
def original():
    print "This is original"
    return

decorate = decorator_func(original)
```

**Motivation** : Lets say I want to allow access to a route function only  
if the user is logged in  
I can copy paste the login code in each function and that would do our job  
But Why would I copy paste the login code if I can create a simple function and call from  
wherever I want. That way code would be more elegant.  
But can I do even better, I don't want to disturb the functionality of the function  
I only want to add the extra feature of login to the current state, and I want to reuse the  
logic inside the function the next time I call it.  
So that we dont have to disturn the funtionality of a funtion, we have decorators in python.  


Example - flask: add login to routes 
```python
from flask import session

from functools import wraps

def check_logged_in(func):
  @wraps(func)
  def wrapper(*args, **kwargs):
    if 'logged_in' in session:
      return func(*args, **kwargs)
    return 'You are NOT logged in.'
  return wrapper
  
# Finally using this decorator in the actual routing code
@app.route('/page1')
@check_logged_in
def page1() -> str:
  return 'This is page 1.'
  
@app.route('/page3')
@check_logged_in
def page3() -> str:
  return 'This is page 3.'
```

### Skeleton for function decorators

```python
from functools import wraps

def decorator_name(func):
  @wraps(func)
  def wrapper(*args, **kwargs):
    # 1. Code to execute BEFORE calling the decorated function.
    
    # 2. Call the decorated function as required, returning its
    # results if needed.
    
    return func(*args, **kwargs)
    
    # 3. Code to execute INSTEAD of calling the decorated function.
  return wrapper
```

### Exception Handling Done Right

If exceptions are handled this way then we can know the exact error that was caused  
and we can know the class of error and the most important info of all i.e LINE NUM of place where error took place

```python
def fuction_to_call():
    try:
        # critical code
    except Exception, e:
        print e.message
        exc_type, exc_obj, exc_tb = sys.exc_info()
        fname = os.path.split(exc_tb.tb_frame.f_code.co_filename)[1]
        print(exc_type, fname, exc_tb.tb_lineno, exc_tb.tb_frame.f_code.co_filename)
```

## Singleton Class 

```python
class singleton(object):
    _instance = None

    def __new__(self):
        if not self._instance:
            self._instance = super(singleton, self).__new__(self)
            self.q = 12
        return self._instance
```

### First Class functions 

**Languages that give the capability to treat functions as regular variables and objects**  
These functions can be stored in a variable, passed to a function, returned from another function  
Lets see all these with the help of examples  

### Store Function in a variable  

```python
def square(x:int)->int:
  return x*x
  
executed_answer = square(4)
stored_function = square

print(executed_answer) # 16
print(stored_function) # function<0x1f23f4f2a2>
print(stored_function(5)) # 25
```
This way we can store function in a variable, and execute function from this variable  

### Pass function to another function

We can create a function that executes that passed function repeatedly on some array for example  
```python
def square(x:int)->int:
  return x*x

def iterator(func, array):
  result = []
  for i in array:
    result.append(func(i))
  return result

array = [1, 2, 3, 4, 5]

iterator(square, array)
```

### Return function from another function  

```python
def html_tag(tag):

    def wrap_text(msg):
        print('<{0}>{1}</{0}>'.format(tag, msg))

    return wrap_text

print_h1 = html_tag('h1')
print_h1('Test Headline!')
print_h1('Another Headline!')

print_p = html_tag('p')
print_p('Test Paragraph!')
```
**Note:** When we return the inner function, the inner function **remembers**  
the lacal variables of the outer functions. This is called a **CLOSURE**  

### Anonymous functions or Lambda Expressions

Lambda expressions are used to create anonymous functions  
Syntax:  
```
lambda [arguments] : [return expression]
```

example:  
```python
# No args
 fun = lambda : "hello world"
 
 # 1 arg
 fun = lambda x : 3x + 1
 
 # 2 args
 fun = lambda x,y : 3x + 4y
 
 lis.sort(key=lambda x: x.lower())
```

### Creating python modules

```python
def foo():
  pass

def main():
  foo()

if __name__ == "__main__":
  main()
```

## Operator Overloading

```python
class Point:
    def __init__(self, x = 0, y = 0):
        self.x = x
        self.y = y
    
    def __str__(self):
        return "({0},{1})".format(self.x,self.y)
    
    # predefined function to overload for add operator (+)
    def __add__(self,other):
        x = self.x + other.x
        y = self.y + other.y
        return Point(x,y)
```
![Image](../master/assets/overload.png?raw=true)

![Image](../master/assets/overload_1.png?raw=true)

## Virtual Environment

First install virtual-environment  
```
# go in to the project directory

cd project-dir/
```

```
# Create virtual environment in that project directory

virtualenv env
```

```
# activate that virtual-environment

source env/bin/activate
```

```
# deactivate this virtual directory

deactivate
```

## Some insights

### Single leading underscore variables and functions `_hello`

It is a convention to declare private variables and functions for internal use only  
so `from module import *` ignores these variables and methods.  

```python
_private_variable = 'This is a prvate variable'
```

### Single trailing underscore `hello_`

To avoid conflicts with built-ins. Not used very often.  

```python
list_ = List.new_type_of_list()
```

### Double Leading underscores `__hello`

Used for truely private data or methods, although they are not completely private but they still can be  
used as a convention.  

```python
__private_member = "You need to do special things to be able to access me outside my package.."
```

### Double leading and trailing underscores `__magic__`

Called magic mthods or variables.  
`__file__` indicates the location of Python file, `__eq__` is executed when a == b expression is excuted.  

## Threading in Python

Threads are defined by a class, you just override the run method of Thread and it is good to go.  

```python
import time
import threading

class CountdownThread(threading.Thread):
 def __init__(self,count):
  threading.Thread.__init__(self)
  self.count = count
 
 def run(self):
  while self.count > 0:
    print "Counting down", self.count
    self.count -= 1
    time.sleep(5)
 return
 
 thread1 = CountdownThread(10)
 thread1.start()
```

### Launch a function as Thread

```python
import threading

def print_hello():
  for i in range(5):
    print 'hello '
    
def print_world():
  for i in range(5):
    print "world !"

t1 = threading.Thread(target=print_hello, args=())
t2 = threading.Thread(target=print_world, args=())

t1.start()
t2.start()
```

### Wait for 1 thread before you start another using `join()`

Lets say we have dependancy of other threads on the one of the threads, so this thread must complete  
before anyone else dependant on it starts executing. For this we make the main thread wait before it  
executes other threads.  

```python
import threading

def print_hello():
  for i in range(5):
    print 'hello '
    
def print_world():
  for i in range(5):
    print "world !"

t1 = threading.Thread(target=print_hello, args=())
t2 = threading.Thread(target=print_world, args=())

t1.start()
t1.join()
t2.start()
```
Now thread 1 completes execution so all 'hello' are printed before 'world'  

### Daemon Threads

Right now, main thread waits for other threads to complete and then exits.  
If I want to exit the main thread and execute other threads in background  
then I can use daemon threads.  

```python
import threading
import time

def print_hello():
  for i in range(5):
    print 'hello '

def print_world():
  for i in range(10):
    print "world !"

t1 = threading.Thread(target=print_hello, args=())
t2 = threading.Thread(target=print_world, args=())
t2.setDaemon(True)

t1.start()
t1.join()
t2.start()
print 'exiting !!'
```
We will observe that before thread 2 completes the main program will stop execution

### Synchronisation Mechanisms  

When there is a common resource on which 2 threads are working, then  
we must synchronise both threads, as they will produce different result everytime.  

Example: 

```python
x = 0 # A shared value

def foo():
 global x
 for i in xrange(100000000): x += 1

def bar():
 global x
 for i in xrange(100000000): x -= 1

t1 = threading.Thread(target=foo)
t2 = threading.Thread(target=bar)

t1.start(); t2.start()
t1.join(); t2.join() # Wait for completion

print x # Expected result is 0
```
Everytime you run this, it will produce a different result.  

### 1. Mutex Locks

```python
import threading

m = threading.Lock()
m.acquire()    # Acquire the lock
m.release()    # Release the lock
```

Always follow this prototype:  

```python
x = 0
x_lock = threading.Lock()

# Example critical section
x_lock.acquire()

try:
 statements using x
finally:
 x_lock.release()
```

Improved syntax to deal with mutex locks:  

```python
x = 0
x_lock = threading.Lock()

# Critical section
with x_lock:
 statements using x
```

## Python Thread Performance Testing

```python
def count(n):
 while n > 0:
 n -= 1
 
# Case 1
count(100000000)
count(100000000)

# Case 2
t1 = Thread(target=count,args=(100000000,))
t1.start()
t2 = Thread(target=count,args=(100000000,))
t2.start()
```
We might expect the 2nd to run twice as fast.  

Results:  
```
2 CORE CPU: 
Sequential : 24.6s
Threaded : 45.5s (1.8X slower!)

1 CORE CPU:
Threaded : 38.0s
```
Bwaaahhhh !!!! Makes no sense !  
Threaded runs 1.8x slower and runs slightly faster on reducing cores.  

### Deep Dive into python internals

**Only one Python thread can execute in the interpreter at once**  

**The GIL ensures that sure each thread gets exclusive access to the entire interpreter  
internals when it's running**  

### GIL (Global Interpreter Lock)  

It controls thread execution.  

**Why do we need GIL?**

The GIL makes it easy to integrate with external libraries that are not thread-safe,  
and it makes non-parallel code faster.  


# David P3 TuT

## Get command line args

**python3 try.py 234 6545**  

```python
import sys

args_list = sys.argv # ['try.py', '234', '6545']
```

## Don't always write python3 to execute that script

Add a shebang/poundbang to the top of the script.  

```python
#!/usr/bin/env python3
```

Now make the script an executable file.  

```cmd
chmod +x try.py
```

## Debugging

### 1. Run script in 'Interactive' mode

If you executed a program and it gave you an error. Then launch the program in interactive mode  
to see all memory variables etc. We do it simply using :  

```cmd
python3 -i try.py 234 6456
```

If we ran this program without the flag -i then this program gives an error.  
Now in interactive mode, we can check if everything data in the program is the way  
we expect it to be or not.  


### 2. Run the pdb in interactive mode  

While in the interactive mode import pdb  

```python
import pdb
```
 after importing we can run post mortem to get to the point where it failed and do stuff after.  
 
 ```python
 pdb.pm()
 ```
 
 ### 3. Set manual breakpoint in the code (preffered !)  
 
 We set manual breakpoint in the code using pdb  
 
 ```python
 import pdb
 pdb.set_trace() # BREAKPOINT
 ```
 The code stops execution when this line hits, and we are taken to the interactive pdb console.  
 We can use several commands inside the pdb console:  
 
 * n -> execute next line
 * c -> complete execution
 * l -> list 3 lines before and after current line
 * s -> step into function call
 * b -> list of all breakpoints
 * b[int] -> set breakpoint at that line number
 * b[funct] -> set breakpoint at that function  
 * p -> print variables  
 
 ## print output to file   
 
 ```python
 out = open('output.txt', 'w')
 print('hello world !', file=out)
 out.close()
 ```

## Read CSV  

Takes care of a lot of things, that you don't have to manually.  
Always make a habbit of using this library when workingwith csv.  

```python
import csv

file = open('output.csv', 'r')
lines = csv.reader(file)

for line in lines:
  print(line)

file.close()
```

## Get counter in the special for loop of python `Enumerate`

If I want index of iterable in the list, I had to maintain a counter outside of loop,  
and then update the counter inside the loop. This is bad.  
To get iterated item and index we use the enumerate in the special for loop.  
It retuens a tuple of (index, element)  

```python
for i, val in enumerate(items):
  print 'index:', i, 'val:', val
```

## Modules

when we write a script in a file, we can import that file as a module.  
This allows us to reuse the code inside that module.  

**When we import a module then all of its code is executed before its code gets copied**  

### `import mod` vs `from mod import submod`

We sometimes think that latter way of import is more efficient that than the former.  
But that is not true. In both cases, complete modules are imported and put in the memory.  
But when we import sub mod, it only exposes a small part.  

**Both methods of import are same.**  

POINTS TO PONDER:  

* when an import is made then it caches that import statement and doesn't execute the same code again if same import is made again.
```python
import sys

sys.modules # returns a dictionary of cached or already imported modules.

# If I were to delete a module from this dictionary and then try import 
# that module again, then codeof that modile will be executed again.
```

* It is possible that module that we are trying to import is not in the directory that we currently are in. Modules are looked up in the list of paths available in the `sys.path`. We can add a new path in this `sys.path` list so that python can look for modules in that directory.  
```python
import sys

paths = sys.path # list of paths known to python interpretor.

sys.path.append('..') # puts the directory one level up in that list of paths known to python
```

## Packages

We can pack the modules in a package. 

**How?**
* Create a folder and add all the modules in that folder.  
* Create a new empty file in that folder `__init__.py`
* Now we can import this package and modules inside of this package.  
```python
import package
# since we are just importing package and not the modules inside of it. Nothing will happen.
# We have an empty `__init__.py` which is why nothing will happen on importing just the package

import package.module
This will actually import the module inside of that package
```
* If we have modules importing each other in the package then always do **relative package import**  
```python
from . import module # always follow this, never gives error
```

### `__init__.py` in packages

We usually do all the initialisations in this file. So when we import this package, this is the  
file that is run. Acts like a constructor to the package import.  

```python
# __init__.py

print("You imported this package !!")
```

Important Takeaways :  

* If I have a package, I basically don't know the location of a particular function or a class.  
  So that as a user of a package, I dont have to find a particular variable, function or a class,  
  one must import those functions and classes inside `__init__.py`, so that as soon package is imported  
  I have all those functions available to me
  
```python
# __init__.py

from .module1 import function1
from .module1 import function2
from .module2 import function1
from .module2 import function2
```
Now I import the package and these literals are available to me.  

```python
import package

res = package.function1() # these functions are directly available to me from package.
```

## Classes

Classes are collection of variables and functions.  
**NOTE : Inherit class from object**  

```python
class MyClass(object):
  def __init__(self, arg):
    self.arg = arg
  
  def print_hello_and_arg(self):
    print('hello world ! and ', self.arg)
```

### Only 3 operations understood by python object model

### 1. Access variables inside object

```python
obj = MyClass(123)
print(obj.arg)

# We can use method to access attribute
print(getattr(obj, 'arg'))

```

### 2. Change attributes or Add attributes (Set)

```python
obj = MyClass(123)
obj.arg = 234

# we can add new attribute
obj.newarg = 999
print(obj.newarg)


# We can use method to set attribute
print(setattr(obj, 'arg', 98989))
```

### 3. Delete existing attribute from the object

```python
obj = MyClass(123)

# delete attribute
del obj.arg
```

## Multiple constructors and rise of `classmethods`

We can have only one `__init__` method in a class. But if I want to initialise in  
a different way, then  I'll have to use `classmethods`  

```python
class Date(object):
  def __init__(self, day, month, year):
    self.day = day
    self.month = month
    self.year = year
    
  @classmethod
  def from_string(cls, date_string # 'dd-mm-yyyy'):
    lis = date_string.split("-")
    return cls(lis[0], lis[1], lis[2])
  
  @classmethod
  def todays_date(cls):
    import time
    t = time.localtime()
    return cls(t.tm_year, t.tm_mon, t.tm_mday)
    
    
a = Date(21, 3, 2018)
b = Date.from_string('21-03-2018')
c = Date.todays_date()
```

### Classmethods

class methods allow us to  create multiple constructor to a class.  
Use the previous code example to understand what is happening.  

**WHEN WE INVOKE CLASSMETHODS, THEN THE CLASS INVOKING THAT METHOD GETS PASSED TO `cls`**  
So whatever is to the left of `dot` gets captured in the `cls`.  

## Inheritance

We can inherit from base class. This way we can borrow all the code from that of base class. 

```python

class Child(Parent):
  def new_method(self):
    print("This is a brand new method !!")
```

**Why Inheritance ?**  

* We can add extra funtionality to the new class, while keeping all the other from base class.  
* Change the functionality of some function of base class, that you want different in child class.  
* add extra functionality to a method of base class without disturbing the logic of function in base.  

```python
class Parent(object):
  def __init__(self, value):
    value = value
  
  def spam():
    print('Parent Class ', self.value)
  

class Child(Parent):
  def spam():
    print("this is child class !")
    super().spam()


if __name__ == "__main__":
  a = Child(23)
  a.spam()
  
# OUTPUT:
this is child class !
Parent Class 23
```
We were able to wrap the functionality of base class function in the child class.  
**Somewhat like how decorators work !!**  

* Add extra attributes to the child class. after handling extra parameter, we must call the constructor  
of the base class explicitly.  

```python
class Parent(object):
  def __init__(self, value):
    value = value
  
  def spam():
    print('Parent Class ', self.value)
  
class Child(Parent):
  def __init__(self, value, extra):
    self.extra = extra
    super().__init__(value)

a = Child(12, 32)
```

## Abstract Base Classes

**How to make a abstract class ?**  

```python
from abc import ABC, abstractmethod

class MyAbstracClass(ABC):
  
  @abstractmethod
  def method1(self, argument):
    pass
  
  @abstractmethod
  def method2(self, argument):
    pass
```
Now we can inherit from this class and we now know what all methods are neccesary to override.  

## How inheritance works

```python
class Parent(object):
  def spam():
    print("Parent.spam")
  
class A(Parent):
  def spam():
    print("A.spam")
    super().spam()
  
class B(A):
  def spam():
    print(B.spam)
    super().spam()

a = A()
b = B()

a.spam()
""">>>  A.spam
        Parent.spam
"""
b.spam()
""">>>B.spam
      A.spam
      Parent.spam

"""
```

**How does the object know what to call when it sees a super?**  

Every class keeps a record of its parent in a attribute called `__mro__`  

```python
# In the previous code keep the code as it is.
B.__mro__
# out: [B, A, Parent, object]
```

If B inherits from multiple classes and super is called, then method is resolved order wise.  

```python
class B(A, C, D):
  def spam():
    super().spam()
```
A, C, D have `spam()` then, their spam will be called in the same order i.e.  

```
OUTPUT:  
A.spam
B.spam
C.spam
```

## Python Magic Methods

Any operation we do on python object is tied to some **Magic Method**.  
For example:  

```python
x = 42
x + 10

# >>> 52

# It is same as x.__add__(10)

# Mul: x.__mul__(5)

num = ['123', '321', '345']
num[1]

# >>> '321'
It is same as num.__getitem__(1)

num[1] = 999
# It is same as num.__setitem__(1, 999)

```

### Making use of magic methods in custom objects

Sometimes we create an object and try to print it then, we get some text printed out,  
that we dont understand. So to make it more human readable and debuggable, we define  
`__repr__` and `__str__`method.  

```python
class A(object):
  def __init__(self, a, b):
    self.a = a
    self.b = b
    
  def __repr__(self):
    return 'A({}, {})'.format(self.a, self.b)
  
  def __str__(self):
    return 'A has {}, {}'.format(self.a, self.b)
```

Difference between `__repr__` and `__str__` is that  
`__str__` is used when we perform a print  
`__repr__` otherwise  

## Classes and Objects deep down at memory level in python

Every object that we create in python is wrapper around the `python doctionary`  
When we initiate a object in `__init__` we basically are setting values in its dictionary.  
We can access that dictionary by `__dict__` on that object. See the example  

```python
class A(object):
  def __init__(self, a, ,b, c):
    self.a = a
    self.b = b
    self.c = c

obj = A(12, 34, 56)
obj.__dict__

# this will output the dictionary of object i.e {'a': 12, 'b': 34, 'c': 56}
``` 

So all objects in python are dictionary.  
But what about the methods? Where are they stored. They are not in the `__dict__`  
**Methods are stored in the class's dictionary**  

```python
class A(object):
  def __init__(self, a, ,b, c):
    self.a = a
    self.b = b
    self.c = c
  
  def print_values(self):
    print('{}, {}, {}'.format(self.a, self.b, self.c))

A.__dict__
# this will show the methods in the class A
```

## Owning the dot operator

Because python is very flexible it allows me to access the attributes using a dot.  
Example:  

```python
class A(object): 
  def __init__(self, a, b):
    self.a = a
    self.b = b

obj = A(12, 34)
obj.a = 'hello world'
```

We can access the attributes, set them.  
But lets say I don't want the user to set the value of an attribute as string.  
It must always be `int`. So how do I control the 'dot' operator  

### Approach 1 - make that variable private and use getter and setter 

```python
class A(object):
  def __init__(self, a, b):
    self._a = a
    self._b = b

  def get_a(self):
    return self.a
  
  def set_a(self, a):
    if not isinstance(a, float):
      raise TypeError('Can only set variable to float')
    self._a = a
```

Problem with this approach:  

* We have to make a lot of changes, add `_` to all the variables that we have to make private
* User can still access the private and set it because python is extremely flexible.  
* How will you enforce the user to use the getters and setters.  

### Approach 2 - add property decorator to get and set functions for that attribute

Rules to achieve this without errors:  

* getter and setter functions should be the same name as the attribute
* getter should have `@property` decorator
* setter should have `@att.setter` decorator, see example
* getter and setter should always access the attribute privately i.e. `_attribute`
* attribute in `__init__` should not have `_`, it should be used normally

```python
class A(obj):
  def __init__(self, a, b):
    self.a = a
    self.b = b
  
  @property
  def a(self):
    return self.a
  
  @a.setter
  def a(self, a):
    if not isinstance(a, int):
      raise TypeError('int expected !')
    self.a = a

x = A(12, 3)

x.a = '12'
# It will raise a type error since we are trying to set a to a string
```

Using the above example we saw how we can gain control over the `dot` operator.  
We can do all sorts of type checkin with this approach.  

**Turns out that for every attribute, I will have to crete these pair of getter and setter**  
**which is kind of repetetive and long and ugly**  


### #How `dot` operator works internally?  

We have 2 ways of using the `dot` i.e. `get` and `set`  

1. x = a.val , get 
2. a.val = x , set

when we use the `dot` to get value, then `__get__` magic method is looked for in the class dictionary.  

```python
x = a.val
# is equivalent to 
x = a.__class__.__dict__['val'].__get__(a)
```

Similarly when we use it to set value then `__set__` magic method is looked for.  

```python
x = 1000
a.val = x
# is equivalent to 
a.__class__.__dict__['val'].__set__(a, x)
```
**Note that how `__get__` and `__set__` are used**  

### Approach 3 - Descriptors

We can set the type of attribute at class level, it manages the getters and setters of that type.  

**Rules:**  
 
* Create a new descriptor class which will act as the manager for an attribute in actual class  
* Pass exact name of attribute to the descriptor while in `__init__`, because that is the key  
  of the dictionary which it will use to set or get
* Both `__set__` and `__get__` get `instance` as parameter, so use it to access the instance dictionary  
* All the typechecks happen in the `__set__`
* When you make use of the descriptor class make those attributes class variables and not instance variable.  

```python
class Integer(object):
  def __init__(self, name):
    self.name = name
  
  def __get__(self, instance, cls):
    return instance.__dict__[self.name]
  
  def __set__(self, instance, value):
    if not isinstance(value, int):
      raise TypeError("Expected int")
    instance.__dict__[self.name] = value

class Point(object):
  a = Integer('a')
  b = Integer('b')
  def __init__(self, a, b):
    self.a = a
    self.b = b
```

Look at just the `Point` class, see how clean and neat is its syntax. It clearly explains the  
intent behind those class attributes. This will enforce the user set the value to `int` even if  
`dot` operator is used.  

### Object Wrappers and Proxies

This is yet another way to own `get`, `set`, and `del` an attribute from object.  

```python
x.__getattr__('a')
# or
getattr(x, 'a')

x.__setattr__('a', 12)
# or 
setattr(x, 'a', 23)

x.__deleteattr__('a')
# or
delattr(x, 'a')
```

**Note:**  
`__getattribute__` gets called everytime we access any attribute.  
`__getattr__` gets called everytime we try to access some attribute that is not in the object.  

Same is the case with setting and deleting.  

#### Use Case 1: We are not allowed to add any new attribute to our class.  

```python
class A(object):
  def __init__(self, a, b, c):
    self.a = a
    self.b = b
    self.c = c
  
  def __setattr__(self, name, value):
    if not name in {'a', 'b', 'c'}:
      raise AttributeError('unexpected attribute')
    super().__setattr__(name, value)

x = A(1, 3, 4)
x.q = 23
# will raise attribute error
```

So what we have basically achieved here is that we dont allow user to set any value other than `a, b, or c`  
So user can not make mistake when setting value. We have allowed user not to add any other attribute to the object.  


#### Use Case 2: Make a read only class wrapper for object.  

```python
class ReadOnly(object):
  def __init__(self, obj):
    self.read_only_obj = obj
    
  def __getattr__(self, name):
    return getattr(self.read_only_obj, name)
    
  def __setattr__(self, name, value):
    if name == 'read_only_obj':
      super().__setattr__(name, value)
    else:
      raise AttributeError("Read Only !")

# Usage
x = A(1,2,4)
a = ReadOnly(x)
x.b = 12
# will raise read only error !
```


#### Use Case 3: extending class methods.  

In many cases we build our own class for example a class that has a list, our class will loose  
the properties of list.  
One way to give it all those methods of list is to add them manually.  

```python
class Holdings(object):
  def __init__(self): 
    self.holding = []
  
  def append(self, val):
    self.holding.append(val)
  
  def __len__(self):
    return len(self.holding)
```

We can already see that in order to give it all that functionality of list,  
we have to put in a lot of effort, basically re write all the methods of list again.  

To avoid this we can redirect the `get` calls on the objects to the list.  

```python
class Holdings(object):
  def __init__(self):  
    self.holding = []
  
  def __getattr__(self, name):
    # it catches only the attributes not found in the object
    return getattr(self.holding, name)

x = Holding()
x.append
x.insert
# We see that now this class automatically has these methods on it self.
```

## Functions as objects

We can store functions in variables and pass them along.  

```python
def func():
  print('Hello World !!')

a = func
a()
```

In this above example, what we have seen is we stored the function in another variable and called it later.  
We also call this Delayed Execution.  

We can pass functions to other functions as well.  

```python
import time 

def take_func(seconds, func):
  time.sleep(seconds)
  func()

def say_hello():
  print('Hello World !')

take_func(5, say_hello)
# will print hello winputorld after 5 seconds
```

### Return inner functions, Closures

```python
def add(x ,y):
  def inn():
    return x+y
  return inn

s = add(2,4)
s()
# Inner function remembers the variables of outer function
```

## Decorators

lets say I want to add extra functionality to a function.  

```python
def add(a,b):
  return a+b
```

Lets say I want to add logging to this. One way is to manually do it
