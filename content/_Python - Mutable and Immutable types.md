---
title: "Python - Mutable and Immutable types"
author: "Arthur Pieri"
tags: 
- python
---
#python

## Python variables and types
If you have ever programmed in Python, you are probably familiar with variables and data types like:
- int
- str
- list
- dict
- etc...

Those are the foundations of any program, but these data types can also be grouped into two different types

## Mutable vs. Immutable a straightforward explanation
As the name implies, mutable types are types that can be changed, and immutable types are those that cannot.

However, it is not so simple because we can think that, well, if I can change the content of a variable, then variables are mutable. Or I know that tuples cannot be changed after they are assigned. Thus, it is immutable. And even tho the latter is immutable; it is not for that reason. 

### Immutable types
Here is a list of data types that are immutable in Python:
- str
- int
- float
- bool
- bytes
- tuple

Meaning that when I define it, it cannot change, so when I try to do something like:

```python
x = 3
y = x
```

The variable 'y' receives a copy of the information stored in 'x'. So if I change the value in y, x remains the same.

```python
x = 3
y = x
y = 4
print(x, y)
# outputs
3, 4
```

### Mutable types
- list
- set
- dict
- other library-specific structures like pandas.DataFrame

Mutable types can change after their definition, and so when I try to execute something like:
```python
x = [1,5,4,3,2]
y = x
```
The variable 'y' does not receive a copy of the list, but only a reference to the original object, which means that changes made in 'y' affect 'x'.
```python
x = [1,5,4,3,2]
y = x

y.sort()

print(x)
print(y)
# outputs
[1,2,3,4,5]
[1,2,3,4,5]
```
Because both variables reference the same object in memory.

## Why does it matter?
One big problem that it may cause is that, they are mutable for all their existence, so when you pass a variable as a parameter to a function, every change made inside that function, will also reflect back to the variable. 
```python
x = [1,5,4,2,3]

def sort_list(unordered:list):
	unordered.sort()

	return unordered

ordered = sort_list(x)
print(ordered)
print(x)
# outputs
[1,2,3,4,5]
[1,2,3,4,5]
```
And this can lead to a myriad of problems during the execution of your code. So be mindful of this when working with mutable types.

With this in mind, you can return to your code and avoid some problems.

But if you want a little more detailed explanation, keep reading.

## A more detailed explanation

### Variables, memory, and scope
When working with variables, we are actually working with memory blocks. And so when I initiate a variable 'x' what happens under the hood is that we get a memory block, save the value there and keep a reference to that block. Something like:
```python
x = 3
```
What Python and your OS do is:
1. Search for a free memory address, something like 0x9c001f
2. Assign the value '3' to that memory address
3. Return the address and assign it to the variable x