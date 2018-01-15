# Javascript  

### Declare variables with `var` and without `var`

when you declare variable with `var` that will define that variable for that  
particular scope.  
But if you declare variable without `var` then that variable will  
be defined for the global scope.  
```javascript
//Global Scope
var global_variable = 'Hello';

var get_something = function(){
  var local_var = 34; //this variable is limited to the scope of this function
  new_variable = 'World'; //forgot var, but this variable goes in the global scope and not limited to the scope of this function
}

console.log(global_variable + ' ' + new_variable);
//we should get Hello World as output !!
```

**Best Practice**  
Always write var before the variable declaration !!  

### Javascript and Functions

**1. Normal Function Declaration**  
This is a pretty straight forward method of declaring functions,  
just like the way we do in other languages like C++ etc.  

```javascript
function square(number) {
  return number * number;
}
```

**2. Anonymous Function Declaration**  
This was made so that we could write functions the way we write  
normal expressions. It gets clear with examples.  

```javascript
var square = function(number) { return number * number; }; 
//By now the function is stored in the variable sqaure but not executed yet.

//how to execute this function?
console.log(square(4));
```
With this we can programmatically store functions in variables  

**Note** We notice that in anonymous functions we don't specify the  
function name when we are writing the function, but if I want to do  
recursion in the anonymous function then how will I achieve that?  

```javascript
var factorial = function fac(n) { return n < 2 ? 1 : n * fac(n - 1); };
```

We can specify the function name as well when we write the anonymous functions.  
Infact it is a good practice to always write the function name while writing the anonymous  
functions.  

**3. One Time Anonymous Function, Executes immediately**  

```javascript
(function(){
  alert("Hello World !!");
})();
```
We didn't assign function to a variable, and this function gets executed  
the moment it is seen.  

### First Class functions 

**Languages that give the capability to treat functions as regular variables and objects**  
These functions can be **stored in a variable, passed to a function, returned from another function**  
Lets see all these with the help of examples  

### Store Function in a variable  

```javascript
function square(x){
  return x*x;
}

// function stored in variable
var f = square  

console.log(square);
console.lof(f);
console.log(square(5));
console.log(f(5));
```
This way we can store function in a variable, and execute function from this variable  

### Pass function to another function

We can create a function that executes that passed function repeatedly on some array for example  
```javascript
function square(x){
  return x*x;
}

function iterator(func, arr){
  var result = [];
  for(var i = 0; i < arr.length; i++){
    result.push(func(arr[i]));
  }
  return result;
}

var array = [1, 2, 3, 4, 5];

var res = iterator(square, array);
```

### Return function from another function  

```javascript
function html_tag(tag){
  function wrap_text(msg){
    console.log('<' + tag +'>' + msg + '</' + tag + '>')
  }
  return wrap_text
}

print_h1 = html_tag('h1')

print_h1('Test Headline!')
print_h1('Another Headline!')


print_p = html_tag('p')
print_p('Test Paragraph!')
```
**Note:** When we return the inner function, the inner function **remembers**  
the lacal variables of the outer functions. This is called a **CLOSURE**  
**Closures are inner functions that remember the state, or the local variables of outer function**

### `this` in JS

lets pass data to function, create object of that data in function and return it.  
```javascript
function make_object(name, age){
  var obj = {};
  obj.name = name;
  obj.age = age;
  return obj;
}

var magic_mike = make_object("Mike", 26);
console.log(magic_mike);
console.log(magic_mike.name);
console.log(magic_mike.age);
```

This is pretty easy to understand, what's going on..  
But to avoid declaring an object and returning it, JS itself  
makes an object called `this` and automatically returns this object  
so it saves us 2 lines of code every time.. eg:  
```javascript
function make_object(name, age){
  //this object will be declared automatically by js
  this.name = name;
  this.age = age;
  //this object will automatically be returned
}

var magic_mike = new make_object("Mike", 26);
console.log(magic_mike);
console.log(magic_mike.name);
console.log(magic_mike.age);
```
By using `this` and `new` we were able to mock the behaviour of constructors in objects.

### `this` in more detail

```javascript
var fn = function(one, two){
  console.log(this, one, two);
};

var r = {'color': 'red'};
var g = {'color': 'green'};
var b = {'color': 'blue'};

r.method = fn;
r.method(g, b);
```

**What do you think will be `this` bound to in the above example?**  
Since `r` is the focal object which is invoking the function,  
`this` will be bound to `r` and so when we log `this` it will  
print the object `r`.  

**If there is no object invoking the method then what do you think will `this` be bound to?**  
```javascript
var fn = function(one, two){
  console.log(this, one, two);
};

var r = {'color': 'red'};
var g = {'color': 'green'};
var b = {'color': 'blue'};

fn(r,g);
```
**Since global object is calling the function this time and we don't have a `.` to tell us  
object invoking the function, the `global object` will be logged when we log `this`**


### So what happens when I write `new` in front of method invocation?  

**Very Important:** When you invoke method with new in front, a brand new object is  
created and `this` gets bound to the newly created object.  

```javascript
var fn = function(one, two){
  console.log(this, one, two);
};

var r = {'color': 'red'};
var g = {'color': 'green'};
var b = {'color': 'blue'};

r.method = fn;
new r.method(g, b);
```
In the above example, `this` is bound to the newly created object,  
and so the logged output would be  

```javascript
{} 
{color: "green"} 
{color: "blue"}
```
## Objects

```javascript
var obj = {};
obj.name = "Mike";
obj['age'] = 25;
```

### 1. Copy 1 instance of object (taking snapshot)

Simply run a for loop  
```javascript
var obj = {};
obj.name = "Mike";
obj['age'] = 25;

var new_obj = {};

for(var key in obj){
  new_obj[key] = obj[key];
}

new_obj.hobby = "Dancing";
```

### 2. Copy object through Prototype Chaining  

Earlier we copied object by taking snapshot so the data is not in sync  
in both the objects.  
If I want to lookup a property and I don't find it, I want to lookup  
that property in the parent object then this is what we use.  

```javascript
var obj = {};
obj.name = "Mike";
obj['age'] = 25;

var new_obj = Object.create(obj); // this parameter passed is the fallback function

new_obj.hobby = 'guitar';
console.log(new_obj.name);
```
We see that `name` property is not found in the `new_obj`  
so the parent or the fallback object is looked for that particular property.  

The image below gives us better understanding of what it means by `Prototype Chaining`  

![Image](../master/assets/prototype_chains.png?raw=true)

## Class Pattern in JS
```javascript
var Car = function(location){
  var obj = {loc: location};
  obj.move = function(){
    obj.loc++;
  }
  return obj;
};

var bob_car = Car(3);
var amy_car = Car(2);
bob_car.move();
amy_car.move();
```
Car variable is a constructor that returns the object with data and functions.  

### Reduce Redundancy  
We see that every time an object gets created the function move is created again and again  
this will consume a lot of memory and can easily be saved by creating 1 object and reusing it  
```javascript
var Car = function(location){
  var obj = {loc: location};
  var move = move;
  return obj;
};

var move = function(){
  this.loc++;
}

var bob_car = Car(3);
var amy_car = Car(2);
bob_car.move();
amy_car.move();
```

**Problem with this approach**  
Everytime I have to add a function, I'll have to make that function  
and add reference to it in the `Car` constructor, I might miss keeping code in sync  

What can be done?  
We should create object where we write all the functions and we iterate this method object  
to create references in the Car object.  
```javascript
var Car = function(location){
  var obj = {loc: location};
  extend(obj, methods); //this is equivalent to running a loop and copying
  return obj;
};

methods = {
  move : function(){
    this.loc++;
  }
};
```

**Slight Problem**  
methods object doesn't really tell me which object's methods are these  
**Solution**
```javascript
var Car = function(location){
  var obj = {loc: location};
  extend(obj, Car.methods); //this is equivalent to running a loop and copying
  return obj;
};

Car.methods = {
  move : function(){
    this.loc++;
  }
};
```
Simply make this `method` object, a part of Car object

### Improving Performance  

We see that each object has copied version of methods object  
We could simply make use of **Prototype Chaining** here  
```javascript
var Car = function(location){
  var obj = Object.create(Car.methods);
  obj.loc = location;
  return obj;
};

Car.methods = {
  move : function(){
    this.loc++;
  }
};
```
Now properties from method object won't have to be copied, they will stay at top level  
when lookup for a method fails, parent in chain will be looked up  

### Doing things the standard way, recommended by JS

We have been creating classes and objects using the functional prototyping  
Following is the recommended way of doing the same thing  
```javascript
var Car = function(location){
  var obj = Object.create(Car.prototype);
  obj.loc = location;
  return obj;
};

Car.prototype.move = function(){this.loc++;};
```
We have this `prototype` inbuilt by javascript for us  
So all the common data must be added to this prototype object.  
this prototype acts as shared common storage  

### Pseudoclassical Patterns

It is very close to the prototypical pattern that we have written example for above  
But pseudotypical is minor improvement as it reduces redundant code.  

**What do you think is redundant in prototypical pattern code below?**  
```javascript
1. var Car = function(location){
2.   var obj = Object.create(Car.prototype);
3.   obj.loc = location;
4.   return obj;
5. };
6. 
7. Car.prototype.move = function(){this.loc++;};
```
Line **2 and 4** are going to be common to all the constructors so we must avoid writing duplicate code.  

Pseudoclassical classes allow us to remove this redundancy by using the `new` operator  
When we use this `new` operator, the system undergoes a special constructor where we don't  
need to specifically create an object and return it, JS does that internally for us.  
```javascript
var Car = function(location){
  //this = Object.create(Car.prototype);
  this.loc = location;
  //return this;
};

Car.prototype.move = function(){this.loc++;};

var ben_car = new Car(2);
ben_car.move();
```
We had to use `new` to create object this time, so we were able to remove 2 extra lines of code this way  
