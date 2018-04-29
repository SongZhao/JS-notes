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

16. range returns a list, xrange returns an iterable object,. In python 3, range is implemented using xrange.

17. difference between python 2 and 3:
* print function, python 3 need ().
* divide operator, in python 3 **/** will no longer cut the decimal part off. If you want to cut the decimal part you should use **//**.
* Unicode: in python 2, unicode and str type can be concatinated together and the new type is bytearray. In python 3, we can not add str type to byte/bytearray type.
* range in python 3 has a new ``__contain__`` magic method implemented.
* Python2 exception: ```except NameError, err```. Python3 exception: ```except NameError as err```
* Python3 no longer u cant use ``` iterableObject,.next()```, funtion ```next(iterableObject)``` is the way to do it.
* input() in Python3 only returns type str.
* In Python3 if we want to return a list instead of an iterable object, we can use list(iterable object) to get the list.


18. What is generator? Why do we want to use generator? Q: use on demand.

19. Why function is first class object? Describe some use of it. 
Q: properties of first class function is:
* a function is an instance of the Object type
* you can store the function in a variable
* you can pass the function as a parameter to another function
* you can return the function from a function
* you can store them in data structures such as hash tables, lists


Functions are objects, therefore function can be assigned to a variable, can be defined in another function.

20. Describe memory management in python.  
Q: 
* Python memory is managed by Python private heap space. All Python objects and data structures are located in a private heap. The programmer does not have an access to this private heap and interpreter takes care of this Python private heap. 
* The allocation of Python heap space for Python objects is done by Python memory manager. The core API gives access to some tools for the programmer to code.
* Python also have an inbuilt garbage collector, which recycle all the unused memory and frees the memory and makes it available to the heap space.
21. Describe GC in python, if there is an object with non-zero reference, should you do GC?
Q: We might want to GC that if two instance is pointed to each other, thus formed a deadlock.

22. What is closure?
Q:A closure is a function object that remembers calues in enclosing scopes even if they are not present in memory. A closure allows the function to access those captured variables through the closure's copies of their values or references, even when the function is invoked outside their scope.
```python
import logging
logging.basicConfig(filename='example.log', level=logging.INFO)
def logger(func):
    def log_func(*args):
        logging.info(
            'Running "{}" with arguments {}'.format(func.__name__, args))
        print(func(*args))
    # Necessary for closure to work (returning WITHOUT parenthesis)
    return log_func              
 
def add(x, y):
    return x+y
 
def sub(x, y):
    return x-y
 
add_logger = logger(add)
sub_logger = logger(sub)
add_logger(3, 3)
sub_logger(20, 10)
#6
#5
```
23. When and why to use closures?  
Q: As closures are used as callback functions, they provide some sort of data hiding. This helps us to reduce the use of global variables. When we have few functions in our code, closures prove to be efficient way. But if we need to have many functions, then go for class(OOP).


24. remove repeat elements in list
Q:
 * 1. `list(set(l))`
   2. `l = {}.fromkeys(l1).keys()`
   3. `l2 = list(set(l1))` `l2.sort(key=l1.index)` keep the order in the original list.
   4. `l2.append(i) for i in l1 if not i in l2` sort the order then insert.

25. list comprehension
Q: list comprehension provide a concise way to create list. a list comprehension consists of brackets containing an expression followed by a for clause, then zero or more for or if clauses. The result will be a new list resulting from evaluating the expression in the context of the for and if clause which follow it.

26.  
```python
list = [ [ ] ] * 5
list 
list[0].append(10)
list 
list[1].append(20)
list
list.append(30)
list 
# [[], [], [], [], []]
# [[10], [10], [10], [10], [10]]
# [[10, 20], [10, 20], [10, 20], [10, 20], [10, 20], 30]
```
Keep in mind in python everything is an object.

27. Deep copy and shallow copy  
Shallow copy is used when a new instance type gets created and it leeps the values that are copied in the new instance. Shallow copy is used to copy the reference pointers just like it copies the values. These references point to the original objects and the changes made in any member of the class will also affect the original copy of it. Shallow copy allows faster execution of the program and it depends on the size of the data that is used.  
Deep copy is used to store the calues that are already copied, deep copy doesn't copy the reference pointers to the objects. It makes the refrence to an object and the new object that is pointed by some other object gets stored. The changes made in the original copy won't affect any other copy that uses the object. Deep copy makes execution of the program slower due to making certain copies for each object that is been called.

The difference between shallow and deep copying is only relevant for compound objects(objects that contain other objects, like list or class instances) 
* a shallow copy constructs a new compund object and then inserts regerences into it to the objects found in the original.
* a deep copy constructs a new compund object and then, recursively, inserts copies into it of the objects found in the original.
Two problems often exist with deep copy operations that don’t exist with shallow copy operations:  
* Recursive objects (compound objects that, directly or indirectly, contain a reference to themselves) may cause a recursive loop.
* Because deep copy copies everything it may copy too much, such as data which is intended to be shared between copies.

28. What is monkey patching in Python?  
Q: In Python, the term monkey patch only refers to dynamic modifications of a class or module at run-time.
https://www.interviewcake.com/python-interview-questions

https://www.tutorialspoint.com/python/python_interview_questions.html

https://www.edureka.co/blog/interview-questions/python-interview-questions/

regex lib https://docs.python.org/2/library/re.html

http://codingpy.com/article/essential-python-interview-questions/

https://www.jianshu.com/p/92b56fa62c37

https://zhuanlan.zhihu.com/p/23582996

https://blog.csdn.net/yjk13703623757/article/details/79364637
