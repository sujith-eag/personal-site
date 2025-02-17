---
title: "06 OOP - 04 Changing Attriute and Using Class"
description: ""
summary: ""
date: 2025-02-11T23:54:04+05:30
lastmod: 2025-02-11T23:54:04+05:30
draft: false
weight: 58
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---


### Creating and Using a Class

#### Example 1 : **Restaurant Class**

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

### Example 2: **Car Class**

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



**Setting a Default Value for an Attribute**

In Python, you can set default values for attributes in the `__init__()` method. This allows you to initialize an attribute without having to pass it as a parameter when creating an instance.

In the following example, we define an attribute `odometer_reading` that always starts at 0 by default. A method `read_odometer()` is provided to read the car’s odometer value.

```python
class Car:
    def __init__(self, make, model, year):
        """
        Initialize the car object with make, model, year, and a default odometer reading of 0.
        """
        self.make = make
        self.model = model
        self.year = year
        self.odometer_reading = 0  # Default value for odometer reading

    def descriptive_name(self):
        """
        Return a descriptive name for the car in the format 'year make model'.
        """
        long_name = f"{self.year} {self.make} {self.model}"
        return long_name

    def read_odometer(self):
        """
        Print the current odometer reading for the car.
        """
        print(f"This car has {self.odometer_reading} miles on it.")

# Create an instance of Car
new_car = Car('Audi', 'A4', '2024')

# Print descriptive name and odometer reading
print(new_car.descriptive_name())
new_car.read_odometer()
```

- `self.odometer_reading = 0`: This sets the default value of the `odometer_reading` attribute to 0 when a new instance of `Car` is created.
- The `read_odometer()` method prints the current odometer reading.

---

### **Modifying Attribute Values**

You can modify the attributes of an instance in multiple ways:

#### 1. **Modifying an Attribute's Value Directly**

You can change the value of an attribute directly using dot notation.

```python
new_car.odometer_reading = 23  # Direct modification of the odometer reading
```

#### 2. **Modifying an Attribute's Value Through a Method**

Instead of changing an attribute directly, you can use a method to update it. This approach allows you to add logic, such as validation, to ensure that values are correctly updated.

```python
class Car:
    def __init__(self, make, model, year):
        """
        Initialize the car with make, model, year, and default odometer reading.
        """
        self.make = make
        self.model = model
        self.year = year
        self.odometer_reading = 0

    def descriptive_name(self):
        """
        Return the descriptive name of the car.
        """
        long_name = f"{self.year} {self.make} {self.model}"
        return long_name

    def read_odometer(self):
        """
        Print the car's odometer reading.
        """
        print(f"This car has {self.odometer_reading} miles on it.")

    def update_odometer(self, mileage):
        """
        Update the odometer reading, ensuring it cannot be rolled back.
        """
        if mileage >= self.odometer_reading:
            self.odometer_reading = mileage
        else:
            print("You can't roll back the odometer.")

    def increment_odometer(self, miles):
        """
        Increment the odometer reading by a certain number of miles.
        Ensures that negative mileage is not added.
        """
        if miles >= 0:
            self.odometer_reading += miles
        else:
            print("Odometer value cannot be reduced.")

# Creating and modifying instances of the Car class
new_car = Car('Audi', 'A4', '2024')
new_car.odometer_reading = 23  # Direct modification
new_car.update_odometer(2345)  # Update odometer with a valid value
new_car.update_odometer(12)    # Invalid update, will print an error
new_car.increment_odometer(-12)  # Invalid increment, will print an error

print(new_car.descriptive_name())
new_car.read_odometer()

# Creating another car and updating its odometer
old_car = Car('Subaru', 'Outback', '2017')
old_car.update_odometer(20456)

print(old_car.descriptive_name())
old_car.read_odometer()
```

- **Direct modification**: `new_car.odometer_reading = 23` modifies the attribute directly.
- **`update_odometer()` method**: This method ensures the odometer cannot be rolled back (i.e., it checks if the new mileage is greater than or equal to the current value).
- **`increment_odometer()` method**: This method adds a specific number of miles to the odometer. It ensures the value cannot be negative.

---

### **Creating Points for 2D Representation**

Here, we create a `Point` class to represent points in a 2D space. This class has methods for translating the point and calculating its distance from the origin.

```python
import math

class Point:
    def __init__(self, a=0, b=0):
        """
        Initialize the point with coordinates (a, b).
        By default, the point is set to (0, 0).
        """
        self.x = a
        self.y = b

    def translate(self, deltax, deltay):
        """
        Translate the point by a certain amount in the x and y directions.
        """
        self.x += deltax
        self.y += deltay

    def distance(self):
        """
        Calculate the distance from the origin (0, 0) using the Pythagorean theorem.
        """
        return math.sqrt(self.x ** 2 + self.y ** 2)

    def __str__(self):
        """
        Return a string representation of the point in the format (x, y).
        """
        return f"({self.x}, {self.y})"

    def __add__(self, p):
        """
        Add another point to this point (i.e., point addition).
        """
        return Point(self.x + p.x, self.y + p.y)

# Example usage
p1 = Point(3, 4)  # Point at (3, 4)
p2 = Point(1, 2)  # Point at (1, 2)

# Translate p1 by (2, -3)
p1.translate(2, -3)

# Calculate the distance of p1 from the origin
print(p1.distance())  # Output: 5.0

# Add p1 and p2 to get a new point
p3 = p1 + p2
print(p3)  # Output: (6, 3)
```

- `__init__(self, a=0, b=0)`: Initializes a point with coordinates `(a, b)`, defaulting to `(0, 0)` if no values are provided.
- `translate(self, deltax, deltay)`: Shifts the point by the values `deltax` and `deltay`.
- `distance(self)`: Calculates the distance from the point to the origin `(0, 0)` using the Pythagorean theorem.
- `__str__(self)`: This special method provides a string representation of the point, making it easier to print.
- `__add__(self, p)`: This special method allows for adding two points together using the `+` operator.

---

### **Operator Overloading (Additional Methods)**

In Python, you can overload common operators for custom behavior. For example, you can overload the multiplication operator (`*`), comparison operators (`<`, `<=`, `>`, `>=`), and others.

```python
def __mul__(self, scalar):
    """Multiply the point by a scalar value."""
    return Point(self.x * scalar, self.y * scalar)
```

In this case, multiplying a point by a scalar value would scale both the `x` and `y` coordinates.

---
