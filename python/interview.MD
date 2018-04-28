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





https://www.interviewcake.com/python-interview-questions

https://www.tutorialspoint.com/python/python_interview_questions.html

https://www.edureka.co/blog/interview-questions/python-interview-questions/

regex lib https://docs.python.org/2/library/re.html
