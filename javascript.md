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


