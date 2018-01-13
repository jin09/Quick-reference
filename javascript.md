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

