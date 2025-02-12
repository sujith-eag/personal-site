---
title: "06 OOP - 01 OOP Concepts"
description: ""
summary: ""
date: 2025-02-11T23:53:03+05:30
lastmod: 2025-02-11T23:53:03+05:30
draft: false
weight: 55
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---


A **class** is a user-defined data type in Python. Classes allow you to construct new data types that go beyond Python's built-in types. 

Essentially, a class is a **template** from which you can create objects (instances). Each class defines the structure (attributes) and behavior (methods) that the objects created from it will have.

### Key Features:

- **Encapsulation**: A class can store data and also define functions (methods) that manipulate that data.
- **Interface vs Implementation**: A class defines an interface (a set of functions that interact with the object). However, the implementation details of these functions should be hidden (private) to prevent direct manipulation like a black box. This allows for optimizations in the implementation without affecting how the class is used.

### Example Data Structures Implemented Using Classes:

- **Stack** (Last-In, First-Out):
    - Operations: `push()` and `pop()`
    - Example: `(s.push(v)).pop() == v` — the value pushed onto the stack is the first to be popped out.

- **Queue** (First-In, First-Out):
    - Operations: `addq()` and `removeq()`
    - Example: `((q.addq(u)).addq(v)).removeq() == u` — the first item added will be the first to be removed.

- **Heap**:    
    - Operations: `insert()` and `delete_max()`

In these examples, the list may serve as the internal structure for storing the data, but the implementation details should be kept hidden, allowing the class to be used with a well-defined public interface.

___

### OOP (Object-Oriented Programming) Concepts

Object-Oriented Programming (OOP) allows you to define classes that represent real-world entities. Once you have a class, you can create objects (instances) based on that class, each of which can have unique attributes but share the same behavior as defined in the class.

1. **Class**: A blueprint for creating objects. It defines the common behavior (methods) and attributes for the objects created from it.
2. **Object (Instance)**: An individual, unique object created from a class.
3. **Instantiation**: The process of creating an object from a class (We will work with instances of a class).


## Class Definition in Python

In Python, a **class** is used as a blueprint to create objects, which are instances of that class.

### Basic Syntax and Naming Convention:

- **Class names** are written in **CamelCase** (starting with a capital letter) as per the Python naming convention.
- The class definition begins with the `class` keyword, followed by the class name and a colon (`:`).
- Inside the class, you define **attributes** (variables) and **methods** (functions) that belong to the class.
- The class does not require parentheses unless it inherits from a base class (this is a topic related to object inheritance).

```python
class Dog:
    def __init__(self, name, age):  # Initialize attributes for each instance.
        self.name = name
        self.age = age

    def sit(self):  # Method to make the dog sit.
        print(f"{self.name} is now sitting.")

    def roll_over(self):  # Method to make the dog roll over.
        print(f"{self.name} rolled over!")
```

- **`__init__()`**: This is the **constructor** method, which initializes each new instance of the `Dog` class.
- **Attributes (`self.name` and `self.age`)**: These store the state of the object. In this case, `name` and `age` are attributes of each individual dog.
- **Methods (`sit()` and `roll_over()`)**: These define behaviors or actions that the `Dog` class can perform.

### Class Instantiation:

To create an instance (or object) of the class, you call the class as if it were a function, passing the required arguments.

```python
my_dog = Dog('Willie', 6)  # Creates an instance of Dog named Willie, age 6.
your_dog = Dog('Lucy', 3)  # Creates another Dog named Lucy, age 3.
```

After creating the instances, you can access their attributes and methods like so:

```python
print(f"My dog's name is {my_dog.name}.")
print(f"My dog is {my_dog.age} years old.")
my_dog.sit()  # Calls the sit() method for my_dog.

print(f"\nYour dog's name is {your_dog.name}.")
print(f"Your dog is {your_dog.age} years old.")
your_dog.sit()  # Calls the sit() method for your_dog.
```

---
