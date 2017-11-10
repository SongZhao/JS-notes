JS basic syntax:

	JS supports label to enable location jumping.
		label:
			statement
	One of the usages of label is use with 'break' or 'continue' to break all the loops start from the label or jump to next iteration of the loop start from the label.

	JS is not restricted on variable type, variable(var) can be assigned with any value without type cast 
	JS does have primitive type(Boolean, Number, String, undefined, null).
		typecasting in JS:
			Number(): this function can convert arguement into number if the arguement is convertable.
				Number('123') //123
				Number('a123') //NaN  (NaN is a value)
				Number('')	// 0
				Number(true) //1
				Number(undefined)	//Nan
				Number(null)	// 0

			Note: another way to get the number value of a string is use the function parseInt().

			String(): this function can convert any value to string. it's basiclly the same as calling the function toString()
				String(123) //"123"
				String(true) //"true"
				String(null) //"null"
				string([1,2,3]) //"1,2,3"

			Boolean(): only undefined, null, 0, -0, +0, NaN, ''(empty string) will convert to false, all other value will convert to true.

			auto-casting: system issued cast, invisible to user
				1)	calculation of different types    // number + string will act like two string concatinate togather.
				2)	asking for boolean value of a non-boolean variable //the auto-cast process is the same as Boolean()
				3)	use '+' or '-' on non-number var or object(like list)  //will produce Nan most likely




	Error handling:
		Error() this function is used to create a new Error object.
		var err = new Error("something is wrong")
		console.log(err.message) // something is wrong
		Error object must have three properties(message, name, stack).

		customize error handling:
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

		assert()
			funtion assert(expression, message){
				if(!expression)
					throw {name: "Assertion exception", message: message};
			}
			we can also display assert in console by using console.assert(expression, 'message');





	Function in JS:
		JS treat function as a value just like string value or number value. Thus you can pass function into another function as an input.

		function print(x){
			return x;
		}
		function add(x, y)
		{
			return x + y;
		}
		print(add)(1,1);  //get 2.

		Properties of function:
			name : function name.
			length : # of input of the function.
			toString() : return the code of the function include comments inside it.

		Passing by value vs. passing by refrence:
			JS passes primitive variable(string, number, boolean) by value; passes object, list by reference. However if inside the function, instead change property of the object, it simply changed the whole object using '='; the object will remain unchanged outside of the scope(acting like pass by value).

			The way pass primitive type by reference is to use 'this.' to make it a property of current window.

			JS treat arguements of a function as an 'arguements' object, like argv in C. 'arguments.length' will return the # of arguments.
			arguments is an object instead of list, to convert it to a list we will want to use
				var args = Array.prototype.slice.call(arguements);


		Closure:
			closure is the bridge between global scope and function scope. It enables reading local variable from outer scope, it also keeps local variable in memory(will not be collect by garbage collecting).
			closure can be used to read/write private variable.

			3 ways to avoid the reference problem in async function:
				a) Add an anonymous wrapper to get copy of the variable. (function(copied vairable){ original function here })(variable wants to be copied)

				b) Return a function inside the anonymous wrapper. 

				c) add additional arguement as call back.



		IIFE(immediately-Invoked-Function-Expression)
			Surround a function definition with parenthesis will call this function immediately after its been defined.
			or add parenthesis after the function definition to pass arguements.
				(functionA(a, b){
					var c;
					c = a + b;
					}(1,2));


		Scope in JS:
			Global scope: variable declared in this scope can be accessed from anywhere.
			Local(function) scope: variable declared inside a function can not be accessed from outside. 

			A commen error would be that when function A calls function B and function B is defined in global scope; then function B will take input from global scope rather than from function A's local scope. 



		Declaration Hoisting: both var statements and function declarations will be moved to the top of their enclosing scope.


