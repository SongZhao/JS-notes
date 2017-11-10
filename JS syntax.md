### JS basic syntax:
JS supports label to enable location jumping.
```
label:
	statement
```
One of the usages of label is use with 'break' or 'continue' to break all the loops start from the label or jump to next iteration of the loop start from the label.

JS is not restricted on variable type, variable(var) can be assigned with any value without type cast 
JS does have primitive type(Boolean, Number, String, undefined, null).
#### typecasting in JS:
##### Number(): this function can convert arguement into number if the arguement is convertable.
```Number('123') //123
Number('a123') //NaN  (NaN is a value)
Number('') // 0
Number(true) //1
Number(undefined) //NaN
Number(null) // 0
```
Note: another way to get the number value of a string is use the function parseInt().

##### String(): this function can convert any value to string. it's basiclly the same as calling the function toString().
```
String(123) //"123"
String(true) //"true"
String(null) //"null"
string([1,2,3]) //"1,2,3"
```
##### Boolean(): only undefined, null, 0, -0, +0, NaN, ''(empty string) will convert to false, all other value will convert to true.

##### Auto-casting: system issued cast, invisible to user.

1. calculation of different types    // number + string will act like two string concatinate togather.
2. asking for boolean value of a non-boolean variable //the auto-cast process is the same as Boolean()
3. use '+' or '-' on non-number var or object(like list)  //will produce Nan most likely




#### Error handling:
- Error() this function is used to create a new Error object.
```
var err = new Error("something is wrong")
console.log(err.message) // something is wrong
Error object must have three properties(message, name, stack).
```
- customize error handling:
```
function userError(message)
{
	this.message = message || "default message";
	this.name = "errorName";
}
userError.prototype = new Error();
userError.prototype.constructor = userError;
userError.prototype.toString = function(){
	return this.name + ': ' + this.message + '.'; 
}

throw new userError("some error message");
```
- assert():
```
funtion assert(expression, message){
	if(!expression)
		throw {name: "Assertion exception", message: message};
}
```
we can also display assert in console by using `console.assert(expression, 'message')`;


