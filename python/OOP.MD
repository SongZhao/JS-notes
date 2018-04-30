isintance(instance, class)
issubclass(subclass, class)

Decorator is a function takes another function as arguement, adds some kind of functionality and returns another function without altering the original source code of function you passing in.  By adding functionality in wrapper function, we can alter the functionality of orig_functoin
```python
def decorator_function(orig_function)
  def wrapper_function():
    return orig_function()
  return wrapper_function

@decorator_function
def display():
  print('display function ran')

display()  #because display is tagged with @decorator_function, it will execute the decorator_function
```
To create decorator chain
```python
from functools import wraps

#change all wrapper function in decorator chain to @wraps
```
----------

regular method in class auto take instace as the first arguements.  
`@classmethod` class method will take class `cls` as first argument. Possible usage for class method would be change the class variable or create a constructor.

`@staticmethod` do not take the instance or the class as the first argument.  

-----------------

### Property Decorator - Getters, Setters, and Deleters  
`@peroperty` define attribute using method, and access the attribute as the method is an attribute(i.e. no '()' needed). This is Getter.  
`@method_name.setter` define the attribute(the attribute name = 'method_name') 
Use `@method_name.deleter` above the method, the usage would be `del object.method_name`.

---------
### Magic / Dunder method
![alt text][table]

Magic method
https://docs.python.org/3/reference/datamodel.html#special-method-names




[table]: http://ww1.sinaimg.cn/large/e5da91aaly1fquneof72zj20p20h0dh2.jpg "magic function table"
