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
