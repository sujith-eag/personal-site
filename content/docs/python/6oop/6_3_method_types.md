---
title: "06 OOP - 03 Types of Methods"
description: ""
summary: ""
date: 2025-02-11T23:53:35+05:30
lastmod: 2025-02-11T23:53:35+05:30
draft: false
weight: 57
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---



The purpose of a method is to process the variables provided in the class or in the method. Methods within a class define the behavior or actions that objects of that class can perform. A method is simply a function defined inside a class.

### Types of Methods

1. **Instance Methods**
    - Accessor Methods
    - Mutator Methods
2. **Class Methods**
3. **Static Methods**

---

### Instance Methods

Instance methods act upon the instance variables of the class. They are bound to instances (objects) and hence are called as `instancename.method()`.

The memory address of the instance variables in the object is provided to the instance method while defining, by passing `self` as the first parameter. When calling the instance method, there is no need to pass any value for `self` since it is automatically passed.

Instance methods are further divided into two types:

#### 1. Accessor Methods

Accessor methods simply access and read the data of the instance variables. They do not modify the data. Accessor methods are generally written as `getSomething()` and are also called **getter methods**.

```python
def getName(self):
    return self.name
```

#### 2. Mutator Methods

Mutator methods are responsible for modifying the instance variables. They are generally written in the form `setSomething()` and are also known as **setter methods**.

```python
def setName(self, name):
    self.name = name
```

When mutator methods define or set values for instance variables, the constructor is not needed to initialize the instance variables.

**Example:**

```python
>>> class Student:
...     # Setter methods
...     def setName(self, name):
...         self.name = name
...     def setMarks(self, marks):
...         self.marks = marks
...     # Getter methods
...     def getName(self):
...         return self.name
...     def getMarks(self):
...         return self.marks
... 
>>> n = int(input('How many students?: '))
How many students?: 2
>>> i = 0
>>> while(i < n):
...     name = input('Enter name: ')
...     s.setName(name)
...     marks = int(input('Enter marks: '))
...     s.setMarks(marks)
...     print("Hi", s.getName())
...     print("Your marks", s.getMarks())
...     i += 1
...     print("-"*25)
... 
Enter name: Krishna  # input
Your marks: 30

Hi Krishna           # output
Your marks 30
-------------------------
Enter name: Vimal
Your marks: 50

Hi Vimal
Your marks 50
-------------------------
```

---

### Class Methods

Class methods are used for processing that is commonly needed by all instances of a class. These methods act on class-level variables or static variables.

Class methods are written using the `@classmethod` decorator and have `cls` (which refers to the class itself) as the first parameter.

Class variables are referenced as `cls.variable`.

These methods are generally called as `classname.method()`.

```python
>>> class Bird:
...         # class variable
...     wings = 2
...         # class method
...     @classmethod
...     def fly(cls, name):
...         print(f"{name} flies with {cls.wings} wings.")
... 
>>> Bird.fly('Sparrow')
Sparrow flies with 2 wings.

>>> Bird.fly('Pigeon')
Pigeon flies with 2 wings.

>>> sparrow = Bird()
>>> sparrow.fly()
TypeError: Bird.fly() missing 1 required positional argument: 'name'
```

---

### Static Methods

Static methods are used when some processing is related to the class but doesn't require the class or its instances to perform the work.

These methods can accept values, process them, and return results without needing access to the class or its instance variables. Setting environmental variables, counting no of instances of class, changing attributes in another class are tasks related to a class, which can be handled by static methods.

Static methods are defined using the `@staticmethod` decorator.

Static methods are called as `classname.method()`.

**Example 1: Static method to track number of instances created**

```python
>>> class Myclass:
...     n = 0  # class variable
...     # constructor incrementing class variable
...     def __init__(self):
...         Myclass.n += 1
...
...     @staticmethod
...     def noObjects():
...         print(f"No. of instances created: {Myclass.n}")
... 

>>> obj1 = Myclass()
>>> obj2 = Myclass()
>>> obj3 = Myclass()

>>> Myclass.noObjects()
No. of instances created: 3
```

**Example 2: Static method to calculate the square root**

```python
>>> import math

>>> class Sample:
...
...     @staticmethod
...     def calculate(x):
...         result = math.sqrt(x)
...         return result
... 
>>> num = float(input('Enter a number: '))
Enter a number: 49

>>> result = Sample.calculate(num)
>>> print(f"The square root of {num} is {result:.2f}")
The square root of 49.0 is 7.00
```

---

### Example of Methods in Action

```python
>>> class Dog:
...     def __init__(self, name, age):
...             self.name = name
...             self.age = age
...     def sit(self):
...             print(f"{self.name} is now sitting.")
...     def roll_over(self):
...             print(f"{self.name} rolled over!")
... 
>>> my_dog = Dog( 'Will', 6 )
>>> your_dog = Dog( 'Lucy', 3 )
>>> 
>>> my_dog.sit()
Will is now sitting.
>>> your_dog.roll_over()
Lucy rolled over!
>>> print(f"Your dog name is {your_dog.name}.")
Your dog name is Lucy.
```

- Methods like `sit()` and `roll_over()` don't require extra arguments because they only need to operate on the specific instance (i.e., the dog that called the method).

---


- **Instance Methods** operate on instance variables and are tied to an object.
    - Accessor methods **(getter)**: Read data without modifying it.
    - Mutator methods **(setter)**: Modify instance data.
- **Class Methods** operate on class-level data and are used for tasks that are shared across all instances of a class.
- **Static Methods** are used for tasks that don't require class or instance data, but are logically related to the class.


____


