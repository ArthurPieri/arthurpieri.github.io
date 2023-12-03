---
title: "Exploring Data Structures in C Programming: A Beginner's Guide"
author: Arthur Pieri
tags:
  - coding
  - clang
  - data-engineering
  - python
keywords:
  - data structures
  - clang
  - python
  - data engineering
---
### Exploring Data Structures in C Programming: A Beginner's Guide

**Introduction to Data Structures in C**
- **Why It Matters**: As you delve deeper into programming and data, understanding what happens "under the roof" is crucial. Before tackling complex data structures, it's essential to grasp the basics, starting with [[_Pointers in C_]].

### Understanding Basic Data Types in C
- **The Foundation**: In C, basic data types are the building blocks for more complex structures. Unlike Python, which abstracts many details, C offers a closer look at how data is stored and managed.
- **Examples of Basic Data Types**:
    1. **int**: Stores whole numbers.
    2. **float**: Handles decimal numbers.
    3. **double**: Similar to `float` but with more precision.
    4. **char**: Holds a single character.
    5. **_Bool**: Represents true (1) or false (0).
    6. **void**: Indicates no specific type.
- **Remember**: The size and range of these types can vary depending on the compiler, but there are standard minimum sizes.

### Diving into Complex Data Types
- **Beyond the Basics**: Complex data types allow for more sophisticated data handling in C. They include:
    1. **Structures (`struct`)**: Combine different types under one name. Useful for organizing complex data.
        ```c
        struct student {
            char name[50];
            int age;
        };
        ```
    2. **Unions (`union`)**: Store different types in the exact memory location, but only one at a time.
        ```c
        union Data {
            int i;
            float f;
            char str[20];
        };
        ```
    3. **Arrays**: A collection of items of the same type.
        ```c
        int numbers[10];
        ```
    4. **Pointers**: Variables that store the address of another variable.
        ```c
        int *p;
        ```
    5. **Enumerations (`enum`)**: Define a set of named integral constants.
        ```c
        enum day {
            monday, tuesday, wednesday, thursday, friday, saturday, sunday  
        };
        ```
    6. **Functions**: Can be treated as data types based on their return value.
        ```c
        int add(int a, int b) {
            return a + b;
        }
        ```

### Abstract Data Types (ADT) in C
- **Encapsulating Data and Operations**: ADTs define a set of operations for data, hiding the implementation details. In C, ADTs are typically implemented using `struct` and functions.
- **Example - Implementing a Stack**:
    ```c
    typedef struct {
        int top;
        int capacity;
        int *array;
    } Stack;

    Stack* createStack(int capacity){
       // function to create a stack
    }

    void push(Stack* stack, int item){
       // function to push items in the stack
    }

    int pop(Stack* stack){
       // function to pop item from the stack
    }
    ...
    ```
    In this example, `Stack` is an ADT that encapsulates data (array, capacity, top) and provides specific operations (`createStack`, `push`, `pop`).

### Expanding Your Knowledge
- **Next Steps**: To further explore data structures in C, consider learning about:
    - [[_Clang - linked lists]]
    - [[_Clang - queues]]
    - [[_Clang - stacks]]
    - [[_Clang - trees]]
    - [[_Clang - Graphs]]
    - [[_Clang - Hash Tables]]
    - [[_HyperLogLog]]
    - [[_Bloom filter]]

Understanding these fundamental concepts in C will give you a solid foundation for exploring more advanced data structures and algorithms. This knowledge is not just academic; it's a practical tool to enhance your programming skills and problem-solving abilities.