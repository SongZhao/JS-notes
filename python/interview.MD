1. The **==** operator compares the values of both the operands and checks for value equality. **is** operator checks whether both the operands refer to the same object or not

2. In Python the precedence order is first **NOT** then **AND** and in last **OR**.  

3. **del** is used to delte a reference to an object, any variable or list value can be deleted using del.  

4. **//** is called truncating division where the remainder is truncated or dropped.

5. **filter** creates a list of elements for which a function returns true. filter(function_name, para_for_the_function).  

6. **Map** applies a function to all the items in an input_list. map(function_to_apply, list_of_inputs).  

7. **Reduce** performs computation on a list and returning the result. It applies a rolling computation to sequential pairs of values in a list.  
```python
from functools import reduce
product = reduce((lambda x, y : x*y), [1,2,3,4]
#output is 24
```
8.  `object.__dict__['key'] = value` add key value pair directly to the dictionary of this object. called by object.key = value

9.  use **extend** instead of **append** to append a list to another list.

10. There is a docstring defined for method, by putting a string on the first line after the start of the function definition. The docstring can be referenced using the `__doc__` attribute of the function.  

11. `*args` and `**kwargs` allow you to pass a variable number of arguments to a function. `*args` is used to send a non-keyworeded variable length argument list to the function. `**kawargs**` can handle named arguments in a function(ex. a dict).  

12. Whenever you assign a variable to another variable of mutable datatype, any changes to the data are reflected by both variables. The new variable is just an alias for the old variable.
```python
foo = ['hi']
print(foo)
# Output: ['hi']

bar = foo
bar += ['bye']
print(foo)
# Output: ['hi', 'bye']
```
This is also the reason we we dont want to define default arguments of mutable type.
```python
def add_to(num, target=[]):                   def add_to(element, target=None):     
    target.append(num)                            if target is None:
    return target                                     target = []
                                                  target.append(element)
add_to(1)                                         return target
# Output: [1]                                 
                                              add_to(1)                     
add_to(2)                                     #Output: [1]
# Output: [1,2]
                                              add_to(1)
add_to(3)                                     #Output: [2]
# Output: [1,2,3]
```

13. If you pass immutable arguments like integers, strings or tuples to a function, the passing acts like call by value. The object reference is passed to the function parameters. They can't be changed within the function, because they can't be changed at all. A mutable object exhibits time-varying behavior. Changes to a mutable object are visible through all names bound to it. The value of immutable objects can not be modified after they are created. However immutable object can contain mutable object which can be changed(ie. list in a tuple).

14. immutable: strings, tuples, numbers. Mutable: list, dict.  

15. 
* list: can contain elements of different types and repeatable.
* tuple: like a list but immutable.
* dict: list of key-value pair.
* set: elements in set are not repeatable.

16. range returns a list, xrange returns a generator. In python 3, range is implemented using xrange.

17. difference between python 2 and 3:
* print function, python 3 need ().
* divide operator, in python 3 **/** will no longer cut the decimal part off. If you want to cut the decimal part you should use **//**.
* Unicode: in python 2, unicode and str type can be concatinated together and the new type is bytearray. In python 3, we can not add str type to byte/bytearray type.
* range in python 3 has a new ``__contain__`` magic method implemented.
* Python2 exception: ```except NameError, err```. Python3 exception: ```except NameError as err```
* Python3 no longer u cant use ```generator.next()```, funtion ```next(generator)``` is the way to do it.
* input() in Python3 only returns type str.
* In Python3 if we want to return a list instead of a generator, we can use list(generator) to get the list.


https://www.interviewcake.com/python-interview-questions

https://www.tutorialspoint.com/python/python_interview_questions.html

https://www.edureka.co/blog/interview-questions/python-interview-questions/

regex lib https://docs.python.org/2/library/re.html

http://codingpy.com/article/essential-python-interview-questions/

https://www.jianshu.com/p/92b56fa62c37

https://zhuanlan.zhihu.com/p/23582996

https://blog.csdn.net/yjk13703623757/article/details/79364637
