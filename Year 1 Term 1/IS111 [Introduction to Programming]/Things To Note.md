
# Concepts to note:


## Lists
```python
lst += [5]  - > List id() remains the same
list = list + [5]   -> List is copied and a new id() is created
```

### List.extend VS List.append VS List += VS List = List +
```python
x = ['a','b','c']
y = ['d','e','f']
x.append(y) # ['a','b','c','['d','e','f']']
x.extend(y) # ['a','b','c','d','e','f']
x += y # ['a','b','c','d','e','f']
x = x + y # ['a','b','c','d','e','f']
```
### List Referencing
```python
a = []
b = [a for i in range(5)]
# b will print [[],[],[],[],[]]
b[0] += [1,2] # or using b[0].extend([1,2])
# b will print [[1,2],[1,2],[1,2],[1,2],[1,2]]

# Take note that when using 
# b[0].append([1,2])
# it will yield [[[1,2]],[[1,2]],[[1,2]],[[1,2]],[[1,2]]]

```
This happens because for the above code, reference to var a is created 5 times in the list comprehension. As such every list within list b is a reference to var a which gets updated upon append or +=.
In order to prevent it, avoid using global variables to create lists of lists inside comprehension, instead do this.

```python

b = [[] for i in range(5)]
b[0] += [1,2]
# b will print [[1,2],[],[],[],[]]

```
### List Infinite Recursion
```python
c = [1, 2, 3]
#c = [1, 2, 3]
c += c
# c = [1, 2, 3, 1, 2, 3]
c = [1, 2, 3]
c.append(c)
# c = [1, 2, 3, [...]]
```

The += operation adds the array elements to the original list. The list.append operation inserts the list (or any object) into the end of the original list, which results in a reference to self in that spot (hence the "..." infinite recursion).
 
 
### To Get list of all items except current index
```python
mylist = [0, 1, 2, 3, 4, 5]
x = 3
mylist[:x] + mylist[x+1:]
```

or

```python
mylist = [0, 1, 2, 3, 4, 5]
x = 3
newlist = [a for i,a in enumerate(mylist) if a!=x]
```
 
 
 
 
# Short circuit evaluation 
| Operation   | Notes |
| ------------- | ------------- |
| `if A or B`  | B is evaluated only if A if false. If A is true, the if condition is satisfied and B is not evaluated  |
| `if A and B`  | B is evaluated only if A is true, If A is false, B is not evaluated  |




# Others
## To get max value from a dictionary
`` max(dict, key=dict.get()) ``

