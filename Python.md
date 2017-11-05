# Python quick reference

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

