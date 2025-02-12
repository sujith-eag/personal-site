---
title: "05 Functions - 05 Importing Functions"
description: ""
summary: ""
date: 2025-02-11T19:58:45+05:30
lastmod: 2025-02-11T19:58:45+05:30
draft: false
weight: 50
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---



**Storing Functions in Modules**

In Python, you can organize your code into separate modules for better structure, reusability, and easier sharing between different programs.

### **What is a Module?**

A module is a `.py` file containing Python code (usually functions or classes) that can be imported and used in other scripts.

---

### **Importing a Module**

To use functions from a module, you first need to import it:

```python
# pizza.py
def make_pizza(size, *toppings):
    print(f"\nMaking a {size}-inch pizza with the following toppings:")
    for topping in toppings:
        print(f"- {topping}")
```

You can then import and use the functions like so:

```python
# making_pizzas.py
import pizza

pizza.make_pizza(16, 'pepperoni')
pizza.make_pizza(12, 'mushrooms', 'green peppers', 'extra cheese')
```

---

### **Importing Specific Functions**

Instead of importing the entire module, you can import specific functions directly:

```python
from pizza import make_pizza

make_pizza(16, 'pepperoni')
make_pizza(12, 'mushrooms', 'green peppers', 'extra cheese')
```

This allows you to call the function directly without needing to reference the module. The Syntax will be
```python
from module_name import function_0, function_1, function_2
```

---

### **Using Aliases for Functions and Modules**

If a function name is too long or conflicts with another function, you can give it a shorter alias using `as` keyword:

```python
from pizza import make_pizza as mp

mp(16, 'pepperoni')
mp(12, 'mushrooms', 'green peppers', 'extra cheese')
```

You can also assign an alias to the entire module for convenience:

```python
import pizza as p

p.make_pizza(16, 'pepperoni')
```

General syntax for aliasing:

```python
from module_name import function_name as fn

import module_name as mn
```

---

### **Importing All Functions from a Module**

You can import all functions from a module using the `*` wildcard:

```python
from pizza import *

make_pizza(16, 'pepperoni')
```

However, this is not recommended for larger modules as it can lead to name conflicts, and it can make it harder to track where a function is coming from. 

Since every function is imported, you can call each function by name without using the dot notation. 

---
