---
title: _Data_structures
author: Arthur Pieri
tags:
---

So you've started learning more about programming and data in general, and now you want to learn more about what is happening under the roof.
Before we can talk about some more "complex" data structures, you need to understand a little bit more about [[_Pointers in C_]]

Before we can start talking about data structures

## Data types 
Previously, in [[Python - Mutable and Immutable types]], we've talked a bit about data types applied to Python, which are at least one degree of abstraction higher, but now we are looking under the hood and see how it works in C.

### Basic data types
The basic data types in C are:
1. **int**: It is used to store integers.
2. **float**: It stores decimal numbers (floating-point numbers).
3. **double**: It's similar to `float` but has double precision.
4. **char**: It is used to store a single character.
5. **_Bool**: It stores boolean values, either true(1) or false(0).
6. **void**: It is a type specifier representing the absence of type.

Moreover, these data types' size and range can vary from compiler to compiler, but the standard does mention minimum size requirements.

### Complex data types
In C programming, most complex data types fall under user-defined types:

1. **Structures (`struct`)**: A `struct` in C is a collection of one or more variables, possibly of different types, grouped together under a single name for easy handling. Structures help in organizing complex data efficiently.
    ```c
    struct student 
    {
        char name[50];
        int age;
    };
    ```
2. **Unions (`union`)**: A `union` is a special data type that allows storing different data types in the same memory location. You can define a union with many members, but only one member can contain a value at any given time.
    ```c
    union Data
    {
        int i;
        float f;
        char str[20];
    };
    ```
3. **Arrays**: An array is a collection of data items, all of the same type, in which each item's position is uniquely designated by an integer.
    ```c
    int numbers[10];
    ```
4. **Pointers**: A pointer is a variable whose value is the address of another variable.
    ```c
    int *p;
    ```
5. **Enumerations (`enum`)**: An enumeration is a user-defined data type that consists of integral constants, and each integral constant is given a name.
    ```c
    enum day 
    {
        monday, 
        tuesday, 
        wednesday, 
        thursday, 
        friday, 
        saturday, 
        sunday  
    };
    ```
6. **Functions**: In C, functions are also treated as data types as they may return a value.
    ```c
    int add(int a, int b) 
    {
        return a + b;
    }
    ```

Note: Some complex types, such as strings, do not exist as a primitive type in C, but they can be achieved using an array of characters. Arrays, Structures, Unions, and Enums can contain elements and members of different types, while the pointer can point to any type of C data type. Also, functions can return any type of C data type.

### Abstract data types
In C programming, an abstract data type (ADT) is a type (or class) for objects whose behavior is defined by a set of value and a set of operations. 

The idea is to encapsulate the data and the operations that can be performed on the data. The encapsulation is done in such a way that the details of the data are hidden from the outside; only operations are allowed through a well-defined interface. 

Since C is not an object-oriented language, ADTs can be implemented using struct and functions that manipulate the struct data. For instance:

```c
typedef struct {
    int top;
    int capacity;
    int *array;
} Stack;

Stack* createStack(int capacity){
   // function to create stack
}

void push(Stack* stack, int item){
   // function to push item in stack
}

int pop(Stack* stack){
   // function to pop item from stack
}
...
```

In this example, `Stack` is the abstract data type. It encapsulates an array with its capacity and top pointer to maintain the stack. The operations `createStack`, `push`, and `pop` are the only ways to interact with `Stack` data type objects, and the implementation (how the data is stored and manipulated) is completely hidden.

- [[_Clang - linked lists]]
- [[_Clang - queues]]
- [[_Clang - stacks]]
- [[_Clang - trees]]
- [[_Clang - Graphs]]
- [[_Clang - Hash Tables]]
- [[_HyperLogLog]]
- [[_Bloom filter]]
- 