# Methods for a string 
``` python
.capitalize() # returns a copy of the string with the first letter CAPITALIZED and the rest lowercase

.casefold() # a more aggressive lower() method which coverts string into casefolded string for caseless matching

.count(substring, start index, end index) # start index/end index(optional) within the string where search starts

.startswith(substring, start index, end index) # same as endswith but string starts with substring

.endswith(substring, start index, end index) # basically checks if the string ends with this substring, start index/end index(optional)

.upper() # returns a copy of the string UPPERCASED

.lower() #returns a copy of the string LOWERCASED

string[n] # indexing starts from 0

string[a:b:c] # a = start (inclusive), b = end (exclusive), c = step

.strip() # removes white spaces from both ends

.lstrip() # remove white spaces from left end

.rstrip() # removes white spaces from right end

.find(substring, start, end) # first subsequence found, searching left to right. Returns -1 if not found

.rfind(substring, start, end) #last subsequence found searching left to right. Returns -1 if not found

.index(substring, start, end) #finds the substring in the string and returns the index, if substring not found, ValueError is thrown

.rindex(substring, start, end) # same as .index but returns highest index

.split(separator) # Breaks up the string at the specified separator and returns a list of strings. If separator is not specified, it splits at spaces

.istitle() # returns True if all string is a titlecase string such as s = 'Python Is Good'; False otherwise

.isspace() # returns True if all char in string are spaces or tabs & at least one char; False otherwise

.isalnum() # returns True if all char in string are ALPHANUMERIC & at least one char; False otherwise

.isalpha() # returns True if all char in string are ALPHABETIC & at least one char; False otherwise

.isdigit() # returns True if all char in string are DIGITS & at least one char; False otherwise

.islower() # returns True if all char in string are LOWERCAED & at least one char; False otherwise

.isupper() # returns True if all char in string are UPPERCASED & at least one char; False otherwise
```
----------------------------------------------------------------------------------------------------
# Methods for list
``` python

list() # makes a variable a list type

temp_list[index] # returns item at the list index

temp_list[a:b:c] # a = start (inclusive), b = end (exclusive), c = step

sum(iterable(list/str), start(this is added to the sum)) # sums up the items in the list; only works if all the items within the list are numbers

.append(item) # adds a single item to a list, item can be any type. This modifies the list instead of making a new list

.extend(list) # adds the elements of the list to the original list. if its a tuple or a set just list(tuple/set)

.insert(index, element) # inserts an element at a particular index of a list

.remove(element) # removes a particular element from the list, if element not found, valueError is thrown

.index(element) # finds the element in the list and gives the index, if element not found, valueError is thrown.count

.count(element) # counts the number of elements

.pop(index) # returns the element at that index number and also removes it from the list

.reverse(list) # reverse the order of the list

from copy import deepcopy => list_1 = deepcopy(list_2)

deepcopy() # copies a list such that the original list will not be changed

max(list) # returns max value

min(list) # returns min value

.sort(reverse=True) # sorts the list, in a descending order if you put the reverse=True if not its ()

sorted(list, reverse=True) # returns the sorted list, in an ascending order unless you put reverse=True
```
----------------------------------------------------------------------------------------------------
# Methods for Dictionary 
``` python
.get(key, value_1(optional)) 
```
This searches the key in the dict and returns value of key. value_1 is returned if key is not found. The default value is None.
Difference between .get() and dict[key] is the latter will return a keyError exception if key is not found


----------------------------------------------------------------------------------------------------
# Methods for Set() 
``` python
values = set_1.intersection(set_2) # returns the intersection of values between set_1 and set_2

list_1 = set([1,2,3])
list_2 = set([3,4,5])

list_3 = list_1 | list_2 #union
list_4 = list_1 & list_2 #intersection
list_5 = list_2 - list_1 #difference

print('Union = ', list_3)
print('Intersection = ', list_4)
print('Difference = ', list_5)
```
----------------------------------------------------------------------------------------------------
