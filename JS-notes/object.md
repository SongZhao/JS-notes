JS
	JS object : 
		everything in JS except 'null' and 'undefined' are acting like an object. Number literals can also used as objects with parenthesis around it.


		Objects in JS can also be used as Hashmaps; consist of named properties mapping to values.
			var foo = {name : 'kitten'} //new object with a name property with value 12
			foo.name;  //display kitten
			foo['name'] //display kitten. this won't rise syntax error even if name property does not exist.


		To delete a property from an objet is to use the delete operator. delete foo.name
		Setting the property to null or undefined will remove the value associated with the property, but not the key.



	The prototype:
		
