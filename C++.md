# C++ Quick Reference For Myself

### Max Heap STL

```c++
priority_queue <int> pq;
    
pq.push(5)
pq.push(1)
   
pq.empty()
        
pq.top()
       
pq.pop()
```
### Min Heap STL

Generic Template

```c++
priority_queue <Type, vector<Type>, ComparisonType > min_heap;
```

Example

```c++
priority_queue <int, vector<int>, greater<int> > pq;

pq.push(5);
pq.push(1);

pq.empty();

pq.top();

pq.pop();
```

### Why is “using namespace std” considered bad practice?

This is not related to performance at all. But consider this: you are  
using two libraries called Foo and Bar:
```c++
using namespace foo;
using namespace bar;
```
Everything works fine, you can call `Blah()` from Foo and `Quux()` from Bar without problems.  
But one day you upgrade to a new version of Foo 2.0, which now offers a function called `Quux()`.  
Now you've got a conflict: Both Foo 2.0 and Bar import `Quux()` into your global namespace.  
This is going to take some effort to fix, especially if the function parameters happen to match.  
If you had used `foo::Blah()` and `bar::Quux()`, then the introduction of `foo::Quux()` would have been a non-event.  

### Difference between class and struct

Class is binding of data and methods, Struct is a binding of data and methods.  
So what is the difference?  
**1. Inheritance  
2. Access Modifiers (public, private, default, protected)**  

### What is the Diamond problem? How can we get around it?  

![Image](../master/assets/diamond.png?raw=true)

When I create object of D, I get object A twice, from B and C  
so when I access the content of object A, I get an error because  
the compiler is confused as to which path to choose to get to object A  
as there exists 2, one through B and the other through C.  
```c++
#include <bits/stdc++.h>
using namespace std;

class Mammal {
public:
    int a = 10;
};

class Tiger : public Mammal {
public:
    int b = 20;
    void groom();
};

class Lion : public Mammal {
public:
    int c = 30;
    void groom();
};

class Liger : public Tiger, public Lion {
public:
    void nap();
};

int main()
{
    Liger a;
    cout << a.a;
    return 0;
}
```
The following code will give an error, as the compiler is confused.  

**How to solve?**  
1. Tell the compiler which path to take.  
```c++
int main()
{
    Liger a;
    cout << a.Lion::a;
    return 0;
}
```
In the above example I told compiler to take the path through `Lion`.  

**But is it a good idea to have 2 copies of the same thing?**  
In order to avoid this we use `virtual inheritance`  

```c++
#include <bits/stdc++.h>
using namespace std;

class Mammal {
public:
    int a = 10;
};

class Tiger : public virtual Mammal {
public:
    int b = 20;
    void groom();
};

class Lion : public virtual Mammal {
public:
    int c = 30;
    void groom();
};

class Liger : public Tiger, public Lion {
public:
    void nap();
};

int main()
{
    Liger a;
    cout << a.a;
    return 0;
}
```
Now Tiger and Lion inherit Mammal virtually so only 1 copy of Mammal would be created  
this time which is the right thing to do as we want to save redundant memory.  

### Logarithms

**What logarithm even means?**  

Example: log<sub>10</sub>100  

base = 10  
what should be the power to 10 to get the answer as 100  

10<sup>x</sup> = 100  

so x = 2  

**what are logarithm used for?**  
It is used to solve x when x is an exponent  

**Logs and Algorithms**  
**How many times must we double 1 before we get to n?**  
or  
**How many times must we divide nn in half in order to get back down to 1?**  

```
For both the correct answer is log (n)  -- log base 2 n
```
