
# Table of Contents
[Concepts to note:](#concepts-to-note)
  - [Lists](#lists)
    - [List.extend VS List.append VS List += VS List = List +](#listextend-vs-listappend-vs-list--vs-list--list-)
    - [List Referencing](#list-referencing)
    - [List Infinite Recursion](#list-infinite-recursion)
    - [To Get list of all items except current index](#to-get-list-of-all-items-except-current-index)
    - [For list splitting, specified end index can be out of range](#for-list-splitting-specified-end-index-can-be-out-of-range)
    - [Shadow Variables and variable scoping](#shadow-variables-and-variable-scoping)
    - [Joining List items in a string.](#joining-list-items-in-a-string)
- [Short circuit evaluation](#short-circuit-evaluation)
- [Demorgan's Theorem](#demorgans-theorem)
  - [Examples](#examples)
- [Others](#others)
    - [To get max value from a dictionary](#to-get-max-value-from-a-dictionary)
    - [Exit a for loop using break](#exit-a-for-loop-using-break)
    - [Continue in a for loop](#continue-in-a-for-loop)
    - [Take note of execution of elif and if statements in for loop](#take-note-of-execution-of-elif-and-if-statements-in-for-loop)
    - [.pop vs .remove](#pop-vs-remove)
    - [Division Operator](#Division-Operator)


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
``` python 
a = []
b = [a for i in range(5)]
b[0] += ([1,2])
for i in range(len(b)):
    print(id(b[i]))
'''
This is the output

1832473327424
1832473327424
1832473327424
1832473327424
1832473327424
'''
```
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


### For list splitting, specified end index can be out of range
```python
mylist = [0, 1, 2, 3, 4, 5]
print(mylist[2:10])

# [2, 3, 4, 5]
```


### Shadow Variables and variable scoping
```python

a = 3 
def fn():
  a = 5 
  print(a) # prints 5
fn()
print(a) # prints 3

```
- local variables inside function will take precedence over those (of the same name) in global namespace

- if identifier is mot found in the local namespace, it will look in global namespace

- however if an assignment is done anywhere within function, any call to that variable (before the assignment) will result in unboundlocal exception even if the variable exists in the global namespace

```python
def a(f):
    n = [2]
    for i in f:
        if i not in n:
            n.append(i)
    f = n
f = [1,4]    
print(f)
a(f)
print(f)

''' Output '''
# [1,4]
# [1,4]
```
This happens because the local var 'f' is assigned the to var 'n' and not the original input var. Below are some alternative apporaches.

```python

def a(f):
    n = [2]
    for i in f:
        if i not in n:
            n.append(i)
    return n
f = [1,4]    
print(b)
f = a(f)
print(f)

''' Output '''
# [1,4]
# [2,1,4]
```


```python

def a(f):
    n = [2]
    for i in f:
        if i not in n:
            n.append(i)
    f.clear
    f.extend(n)
f = [1,4]    
print(b)
f = a(f)
print(f)

''' Output '''
# [1,4]
# [2,1,4]
```

Or just be verbose with your variable names to avoid name conflict. 


### Joining List items in a string.

```python
x = ['a','b','c']
y = " " #take not of the space
z = y.join(x)
print(z)
#a b c

```
 
# Short circuit evaluation 
| Operation   | Notes |
| ------------- | ------------- |
| `if A or B`  | B is evaluated only if A if false. If A is true, the if condition is satisfied and B is not evaluated  |
| `if A and B`  | B is evaluated only if A is true, If A is false, B is not evaluated  |

# Demorgan's Theorem

``not(A or B) = not(A) and not(B)``  

``not(A and B) = not(A) or not(B)``

## Examples
### Simplify the negation of the following
```python 
x >= 22 or y < 3
''' Negation '''

```

```python 
ch1 == ch2 and num %2 != 0
''' Negation '''

```

```python 
not(a) or is_odd(y)
''' Negation '''

```

```python 
x < 1 and isHappy(y) or a %2 == 0
''' Negation '''

```




# Others
### To get max value from a dictionary
`` max(dict, key=dict.get()) ``

### Exit a for loop using break
```python
for nums in arr:
    for i in nums:
        if i <255:
            break
            .....
            
```
### Continue in a for loop
```python
for i in range(10):
    if i % 2 == 0:
        continue
        print(i)
    elif i % 3 == 0:
        i += 10
    elif i % 6 == 0:
        break       
    print(i)
```

The continue statement continues to the next iteration in the for loop. The code below it is not executed at all. 

### Take note of execution of elif and if statements in for loop

```python
s = 0
for i in range(10):
    if i % 2 == 0:
        i = i+1
     if i % 3 == 0:
        i = i-1
     else:
        i = 0
     s+=1
print(s)
        
```
Take note that both if statements will be executed unlike an if - elif block


### .pop vs .remove
Take this function for example that removes odd numbers from a list
```python
def remove_odd(x):
    for i in x:
        if i%2 == 0:
            x.pop(i)
    return x
print(remove_odd([1,5,10,3,2,2]))
#[1, 10, 2, 2]
```
This prints the wrong answer as .pop() method expects an index. However, in the above code, the value is provided.
As such, using .remove method can solve the problem as it expects a value instead of the index.

```python
def remove_odd(x):
    for i in x:
        if i%2 == 0:
            x.remove(i) # or x.pop(x.index(i))
    return x
print(remove_odd([1,5,10,3,2,2]))
#[5, 10, 2, 2]
```
However, this still does not print the correct result.

This happens because the list is being modified on the spot. Which can cause weird behaviours.

|Iteration|Index|List|
| ------------- | ------------- |------------- |
|0|0|[5,10,3,2,2]|
|1|1|[5,10,3,2,2]|
|2|2|[5,10,3,2,2]|
|3|3|[5,10,2,2]|
|4|4|[5,10,2,2]|

As seen from the above example, once the element is removed, the list shape changes and the value that was previously was at index 0 was changed. However, the iteration moved on to the next index which caused the value 5 to remain inside the final list. 

In order to prevent this, we can use .copy() method to create a shallow copy of the list. That way the original list is not modified.

```python
def remove_odd(x):
    for i in x.copy():
        if i%2 == 0:
            x.remove(i) # or x.pop(x.index(i))
    return x
print(remove_odd([1,5,10,3,2,2]))
#[10, 2, 2]
```
There is a caveat. If the original list was a list of list. Using copy method will still modify the original list as it is a shallow copy.

### range() params
range(start,stop,step)
start is inclusive
stop is **exclusive**

### Division Operator
for division, no matter what the types of the operands are, the result is always represented as a float
```python 
print(4/2) # 2.0
```
