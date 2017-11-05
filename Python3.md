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

### Add a pause to program

```python
import time
time.sleep(5)
# adds a pause of 5 seconds
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

### if key not found then set it to some default value

```python
a = {'a': 1}
a.setdefault('e', 0)
>>{'a': 1, 'e': 0}
# if 'e' is found in dict then it wont be touched, if not found then it will be set to the default value of 0
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
```

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
