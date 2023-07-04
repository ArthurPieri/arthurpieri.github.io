---
title: "Python - Mutable and Immutable types"
author: "Arthur Pieri"
tags: 
- python
---
#python #coding 

While programming in Python, have you ever found a variable that changed its value seemly out of the blue? 
Perhaps you found someone else's code that passes a variable to a function but returns nothing, and still, the variable was changed outside that function? 
Or have you just heard about that concept and want to learn more? 

Here is a brief explanation and a bit more detailed further below.

## Python variables and types
If you have ever programmed in Python, you are probably familiar with variables and data types like:
- int
- str
- list
- dict
- Etc...

> Those are the foundations of any program, but these data types can also be grouped into two different types.

## Mutable vs. Immutable a straightforward explanation
As the name implies, mutable types are types that can be changed, and immutable types are those that cannot.

However, it is more complex because we can think that if I can change the content of a variable, then variables are mutable. Or I know that tuples cannot be changed after they are assigned. Thus, it is immutable. And even tho the latter is immutable; it is not for that reason. 

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
One big problem it may cause is that they are mutable for all their existence, so when you pass a variable as a parameter to a function, every change made inside that function will also reflect back to the variable. 
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

## Real-World Applications

Understanding mutable and immutable types becomes essential in many real-world applications. For example, when working with large data sets in data science, understanding immutability can be critical for memory management. If you're using a mutable object when an immutable one would suffice, you could end up using significantly more memory than necessary.

Similarly, when building web applications with frameworks like Django or Flask, understanding the difference between mutable and immutable types can help you avoid bugs that could occur due to unexpected variable mutation.

## A more detailed explanation

### Variables, memory, and scope
When working with variables, we are actually working with memory blocks. And so when I initiate a variable 'x', what happens under the hood is that we get a memory block, save the value there and keep a reference to that block. Something like:
```python
x = 3
```
What Python and your OS do is:
1. Search for a free memory address, something like 0x9c001f *
2. Assign the value '3' to that memory address
3. Return the address and assign it to the variable x
4. And python does this every time you assign value to a variable (old or new)
> [!info]+  \* about memory address
> 
> \* Python is a bit more clever than this, so if you want to save the same value into different variables, it will point to the same memory address, but when you change one of those variables if it is immutable, it will point to a different address

> - The big difference is that the variable will receive the memory address for an object(the value itself) for immutable types.
> - While for mutable types, it receives just the reference to that memory block. And changes are made to that single object stored in that address and referenced by one or more variables.

> [!attention]
> Sometimes mutable variables will extrapolate the scope on which they are defined without using the keyword 'Global.' 
> Meaning: changes made to a variable inside the scope of a function will reflect on the variable outside said function
> 


## FAQ

> [!info]+ Can a mutable object be a member of an immutable object? 
Yes, but it can lead to some unexpected behavior. For example, tuples are immutable, but if a tuple contains a list (which is mutable), the list can be modified.

> [!info]+ How can I create a copy of a mutable object? 
You can use the copy module in Python to create a shallow or deep copy of a mutable object.

## Further Reading

If you want to dive deeper into the topic, here are some resources:

- [Python official documentation: Data Model]([Title](https://docs.python.org/3/reference/datamodel.html))
- [Article: Python's Mutable vs Immutable Types: What's the Difference?]((https://realpython.com/python-mutable-vs-immutable-types/))

Remember, the more you practice, the more these concepts will become second nature. Keep exploring and happy coding!