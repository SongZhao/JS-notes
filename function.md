## Function in JS:
JS treats function as a value just like string value or number value. Thus you can pass function into another function as an input.
```
function print(x){
	return x;
}
function add(x, y)
{
	return x + y;
}
print(add)(1,1);  //get 2.
```

#### Properties of function:
- name : function name.
- length : # of input of the function.
- toString() : return the code of the function include comments inside it.

#### Passing by value vs. passing by refrence:
- JS passes primitive variable(string, number, boolean) by value. 
- JS passes object, list by reference. 

However, if we changed the whole object using '=' instead of changing property of the object inside a function; the object will remain unchanged outside of the scope(acting like pass by value). This is because '='on the whole object cuts down the connection between the reference object(x) and the actual object(obj).
```
var obj = [1,2,3]
function f(x){
    x = [2,3,4];
}
f(obj); 
console.log(obj) //[1,2,3]
```
The way pass primitive type by reference is to use 'this.' to make it a property of current window.

#### JS treat arguements of a function as an 'arguements' object, like argv in C. 'arguments.length' will return the # of arguments.
arguments is an object instead of list, to convert it to a list we will want to use
				`var args = Array.prototype.slice.call(arguements);`


#### IIFE(immediately-Invoked-Function-Expression)
Surround a function definition with parenthesis will call this function immediately after its been defined.
Add parenthesis after the function definition to pass arguements.
```
(functionA(a, b){
	var c;
	c = a + b;
}(1,2));
```

#### Closure:
closure is the bridge between global scope and function scope. It enables reading local variable from outer scope, it also keeps local variable in memory(will not be collect by garbage collecting).
closure can be used to read/write private variable.

3 ways to avoid the reference problem in async function:
1. Add an anonymous wrapper to get copy of the variable. (function(copied vairable){ original function here })(variable wants to be copied).
2. Return a function inside the anonymous wrapper. 
3. add additional arguement as call back.


#### Scope in JS:
- Global scope: variable declared in this scope can be accessed from anywhere.
- Local(function) scope: variable declared inside a function can not be accessed from outside. 

A commen error would be that when function A calls function B and function B is defined in global scope; then function B will take input from global scope rather than from function A's local scope. 


###### Declaration Hoisting: both var statements and function declarations will be moved to the top of their enclosing scope.
