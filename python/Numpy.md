python note Numpy



```python
array = np.array([1,2,3,4], dtype = np.float64)
array1 = np.array([1,2,3,4], dtype = np.int32) 
```
using as type will create a deep copy of the original array
```python
array2 = array1.astype(np.float64)
```


`array = np.arrange(5)` the array will be [0 1 2 3 4]
Another way to generate unit data array
`array = np.arrange(1,11,2, dtype=float64)` [  0.   2.   4.   6.   8.  10.]
`array = np.linspace(0,10,6)` [  0.   2.   4.   6.   8.  10.]

```python
array = np.ones((3, ))
```
will create a rank 1 array.
`array = np.ones((3,1))` will create a rank 2 array, in most case we wanna create array like this
so we can use operation like transpose.


`array.flatten()` will transform the array to a one dimensonal array.
`array.transpose()` will get the transpose of the matrix

math operation will cast on each element in the matrix
```array + 1
array ** 2
1/array 
```
Some operations, such as += and *=, act in place to modify an existing array rather than create a new one.

math operation between matrix that has the same dimension will cast on each 
correspond element pair in both matrix
```
arr + arr
arr * arr
```

##slice the matrix
Its much like the list, first index is inclusive and second is exclusive.
The only difference between this and the list is that it does not make a 
new deep copy of the data, thus any assignment will reflect on the original 
array.
if we dont wanna do that we can copy the slice and modify it.
`temp = array[5:8].copy()`


#bool indexing
when we do compare on a matrix we can get a bool matrix that has the same dimension
```
names = np.array(['tom','bob','bill','jack','tom']) 
arr_bool = names == 'tom' #arr_bool = [True False False False True]
```
This kind of bool array can use as indexing, but the lengh of this array must be as 
the same as the highest dimension of the matrix to be casted on. It will return the 
elments/sub array corresponding to the truth.
Following selecting by index are all making copies thus the change will not reflect on
the original matrix.
```python
names = np.array(['tom','bob','bill','jack','tom']) 
data = np.random.rand(5,3) 
print(data) 
print(data[names == 'tom',1:])  
```
[[ 0.16915065  0.15038684  0.34028728]  
 [ 0.32732646  0.69241855  0.65203056]  
 [ 0.84402175  0.77184234  0.48730057]  
 [ 0.94376757  0.33876278  0.77287885]  
 [ 0.58535219  0.50321862  0.28196336]]  

[[ 0.15038684  0.34028728]  
 [ 0.50321862  0.28196336]]


#directly assign value using bool indexing
```
names = np.array(['tom','bob','bill','jack','tom']) 
data = np.random.rand(5,3) 
print(data) 
data[data<0.5]=0 
print(data)  
```
[[ 0.11395235  0.30461958  0.02896975]  
 [ 0.54829738  0.25386957  0.71327458]  
 [ 0.95840718  0.01013043  0.75231583]  
 [ 0.1600976   0.09872024  0.96804632]  
 [ 0.16516135  0.44308404  0.90036341]]  

[[ 0.          0.          0.        ]  
 [ 0.54829738  0.          0.71327458]  
 [ 0.95840718  0.          0.75231583]  
 [ 0.          0.          0.96804632]  
 [ 0.          0.          0.90036341]]

#To assign the whoole row or col
```python
names = np.array(['tom','bob','bill','jack','tom']) 
data = np.random.rand(5,3) 
print(data) 
data[names == 'tom']=0 
print(data)  
```
[[ 0.45025316  0.63122953  0.92612377]  
 [ 0.02918047  0.72361626  0.50190505]  
 [ 0.97611338  0.92807698  0.60883423]  
 [ 0.40124052  0.81103418  0.05447573]  
 [ 0.07352045  0.16173038  0.28114157]]  

[[ 0.          0.          0.        ]  
 [ 0.02918047  0.72361626  0.50190505]  
 [ 0.97611338  0.92807698  0.60883423]  
 [ 0.40124052  0.81103418  0.05447573]  
 [ 0.          0.          0.        ]]



#Choose row in a specific order
```python
arr = np.random((8,4))
print(arr[[4,3,0,6]])  #this will choose the 4, 3, 0 and 6 indexed row.
```
this will choose the first element of the row indexed 1
the index 3 element of the index 5 row, etc.. 
```python
print(arr[[1,5,7,2],[0,3,1,2]]) 
```
#The following operation will take each row on given order first
and rearange each row by the order of 0,3,1,2. Those kind of operation 
are all making a copy of the matrix, thus the change will not reflect 
on the original matrix.
`print(arr[[4,3,0,6]][:,[0,3,1,2]])`



#Calculation
```python
arr = np.arange(6).reshape(3,2) 
print(arr) 
'''
[[0 1]  
 [2 3]  
 [4 5]] 
'''
print(arr.T) 
'''
[[0 2 4]  
 [1 3 5]]  
'''
print(np.dot(arr.T,arr)) 
'''
[[20 26]  
 [26 35]]
'''
```
#broadcasting, operation that casts on each element individually
arr1 = np.array([1,3,5,4,5]) 
arr2 = np.array([4,6,1,3,4])  
print(np.sqrt(arr1)) 
print(np.square(arr2)) 
print(np.multiply(arr1,arr2)) 
print(np.subtract(arr1,arr2))

[ 1.          1.73205081  2.23606798  2.          2.23606798] 
[16 36  1  9 16] 
[ 4 18  5 12 20] 
[-3 -3  4  1  1]


#np.where
arr = np.random.randn(4,4) 
#if element is larger than 0, assign it to 2, otherwise assign it to -2
print(np.where(arr>0,2,-2)) 
#if element is larger than 0, assign it to 2, otherwise stay the same.
print(np.where(arr>0,2,arr))  


arr = np.array([[0,1,2],[3,4,5],[6,7,8]]) 
#mean of the whole matrix
print(arr.mean()) 
#mean of each col
print(arr.mean(axis=0))
#mean of each row 
print(arr.mean(axis=1))

#same can apply to the sum(), std(), var(), min(), max(), argmin(), argmax() operation
print((arr>0).sum())  #sum all elements that are larger than 0


#cumsun abd cumprod
arr = np.array([[0,1,2],[3,4,5],[6,7,8]]) 
print(arr.cumsum(axis=0)) 
print(arr.cumprod(axis=1))  

[[ 0  1  2]  
 [ 3  5  7]  
 [ 9 12 15]] 

[[  0   0   0] 
 [  3  12  60]  
 [  6  42 336]]


#bool array
```python
bools = np.array([False,False,True,False]) 
print(bools.any())   #or
print(bools.all())   #and

#True 
#False
```

#Sorting
```python
arr.sort() #sort all elments
arr.sort(axis = 1) #sorting horizontally
```




https://docs.scipy.org/doc/numpy-dev/user/quickstart.html
