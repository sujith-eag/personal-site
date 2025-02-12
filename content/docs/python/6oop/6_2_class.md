---
title: "06 OOP - 02 Classes"
description: ""
summary: ""
date: 2025-02-11T23:53:16+05:30
lastmod: 2025-02-11T23:53:16+05:30
draft: false
weight: 56
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---



## The '__init__()' Method (Constructor)

The `__init__()` method is a special method in Python that is automatically called when a new object of the class is created. It's used to initialize the instance's attributes and set up its initial state.

- **Purpose**: The `__init__()` method is a **constructor**, meaning it sets up the initial state of a new object.
- **Self**: The first parameter of `__init__()` (and any method within a class) is always `self`.
    - `self` refers to the **instance** itself, allowing you to access the instance's attributes and methods.
    - Every object (or instance) of the class will have its own copy of these attributes and methods.

#### Why is `self` needed?

- **`self`** is required because each instance of the class needs a way to refer to itself.
- When an object is created, Python automatically passes the instance as the first argument to the method (`self`), so you don't have to manually pass it when calling methods on the object.


```python
class Dog:
    def __init__(self, name, age):  
		    # Constructor with self, name, and age
        self.name = name  # Assign the value of name to the instance's name attribute.
        self.age = age    # Assign the value of age to the instance's age attribute.

my_dog = Dog('Willie', 6)  # Here, self refers to the new instance, 'Willie' and 6 are passed as arguments.
```

- In this example, `self.name = name` means that the **`name`** attribute of the instance (`self`) is set to the value passed during instantiation (`'Willie'`).
- The `__init__()` method does **not return** anything. Its purpose is simply to set up the initial state of the object.

---

## Instance Attributes

Instance attributes are variables that are tied to a specific instance of a class. Each object (instance) has its own unique set of attributes, even if they share the same class.

- **Defining Instance Attributes**: Instance attributes are defined inside the `__init__()` method using the `self` keyword.
- **Accessing Instance Attributes**: Once an instance is created, you can access its attributes using the dot (`.`) notation.


```python
class Dog:
    def __init__(self, name, age):  # Initialize instance attributes
        self.name = name
        self.age = age

my_dog = Dog('Willie', 6)  # Creates an instance of Dog with name 'Willie' and age 6.

# Accessing attributes
print(f"My dog's name is {my_dog.name}.")  # Accesses the name attribute of my_dog
print(f"My dog is {my_dog.age} years old.")  # Accesses the age attribute of my_dog
```

- In this case, `my_dog.name` refers to the `name` attribute of the `my_dog` instance, and `my_dog.age` refers to its `age` attribute.

---

## Class Methods

Methods within a class define the behavior or actions that objects of that class can perform. A method is simply a function defined inside a class.

- **`self`** is always the first parameter of a method, which refers to the instance calling the method.
- Class methods generally operate on instance attributes and can modify or interact with the object's state.
- Methods can **return values**, perform actions, or manipulate the object's attributes.

```python
class Dog:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def sit(self):  # Method to make the dog sit.
        print(f"{self.name} is now sitting.")

    def roll_over(self):  # Method to make the dog roll over.
        print(f"{self.name} rolled over!")

# Create instances of the Dog class
my_dog = Dog('Willie', 6)
your_dog = Dog('Lucy', 3)

# Calling methods on the instances
my_dog.sit()        # Calls the sit method on my_dog
your_dog.roll_over()  # Calls the roll_over method on your_dog
```

- **Methods like `sit()` and `roll_over()`** don't require extra arguments because they only need to operate on the specific instance (i.e., the dog that called the method).

---

## Key Concepts to Remember

1. **`self`**:
    - The `self` parameter is used in methods to refer to the instance itself.
    - Each object has its own `self`, which is why it can hold its own attributes and perform actions independently of other objects.
    
2. **Instantiation**:
    - When you create an object from a class, Python automatically calls the `__init__()` method to set up the object's initial state.
    - You do not pass `self` manually; Python handles that for you.
    
3. **Attributes**:
    - **Instance attributes** are data tied to an individual object.
    - They are defined in the `__init__()` method and accessed via `self`.
    
4. **Methods**:
    - Methods are functions that define the behavior of a class. They can access and modify instance attributes.
    - They usually operate on the instance itself (hence they take `self` as the first argument).

---

### Creating and Using a Class

#### Example 1 : Dog Class
 
Here's a complete example where a `Dog` class is defined, instantiate two `Dog` objects, and interact with them:

```python
# Define the Dog class
class Dog:
    def __init__(self, name, age):  # Constructor to initialize attributes
        self.name = name
        self.age = age

    def sit(self):  # Method for the dog to sit
        print(f"{self.name} is now sitting.")

    def roll_over(self):  # Method for the dog to roll over
        print(f"{self.name} rolled over!")

# Creating instances of Dog
my_dog = Dog('Willie', 6)  # Create an object of the Dog class
your_dog = Dog('Lucy', 3)

# Accessing attributes and calling methods on the instances
print(f"My dog's name is {my_dog.name}.")
print(f"My dog is {my_dog.age} years old.")
my_dog.sit()

print(f"\nYour dog's name is {your_dog.name}.")
print(f"Your dog is {your_dog.age} years old.")
your_dog.sit()
```

### Output:

```
My dog's name is Willie.
My dog is 6 years old.
Willie is now sitting.

Your dog's name is Lucy.
Your dog is 3 years old.
Lucy is now sitting.
```

---

#### Example 2 : **Restaurant Class**

A class called `Restaurant`, which stores the name and type of cuisine of a restaurant, and has methods to describe and open the restaurant.

```python
# Defining the Restaurant class
class Restaurant:
    def __init__(self, restaurant_name, cuisine_type):
        """
        Initializing attributes for the restaurant.
        """
        self.restaurant_name = restaurant_name
        self.cuisine_type = cuisine_type

    def describe_restaurant(self):
        """
        Print a description of the restaurant.
        """
        print(f"{self.restaurant_name} has {self.cuisine_type} as its special cuisine.")

    def open_restaurant(self):
        """
        Print a message indicating the restaurant is open.
        """
        print(f"\nThe {self.restaurant_name} is open now.")

# Creating an instance of the Restaurant class
restaurant = Restaurant("ACDC", "Chinese")

# Calling methods on the instance
restaurant.describe_restaurant()
restaurant.open_restaurant()

# Accessing attributes directly
print(f"Where is {restaurant.restaurant_name} with its {restaurant.cuisine_type.title()} cuisine?")
```

- `__init__()` initializes the attributes `restaurant_name` and `cuisine_type`.
- `describe_restaurant()` prints the description of the restaurant.
- `open_restaurant()` prints a message indicating the restaurant is open.
- The instance `restaurant` is created with `"ACDC"` as the name and `"Chinese"` as the cuisine type.
- Methods are called to describe the restaurant and indicate it's open.

---

### Example 3: **Car Class**

A `Car` class where each car has attributes for the make, model, and year, and includes a method to return a descriptive name for the car.

```python
# Defining the Car class
class Car:
    def __init__(self, make, model, year):
        """
        Initialize attributes for the car.
        """
        self.make = make
        self.model = model
        self.year = year

    def descriptive_name(self):
        """
        Return a descriptive name for the car.
        """
        long_name = f"{self.year} {self.make} {self.model}"
        return long_name  # Return the descriptive name

# Creating an instance of the Car class
new_car = Car('Audi', 'A4', '2024')

# Calling the descriptive_name() method and printing car attributes
print(new_car.descriptive_name())  # Prints: 2024 Audi A4
print(new_car.make)                # Prints: Audi
```

- The `__init__()` method initializes the attributes `make`, `model`, and `year`.
- The `descriptive_name()` method returns a string that combines the `year`, `make`, and `model` of the car.
- `new_car` is an instance of `Car` with the make `'Audi'`, model `'A4'`, and year `'2024'`.
- The descriptive name of the car is printed by calling `new_car.descriptive_name()`, and the `make` attribute is printed directly.

---

