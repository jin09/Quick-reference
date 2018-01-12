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
Always write var before the variable !!
