---
title: "05 Functions - 05 Storing and Importing Functions"
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




## Storing Functions in Modules

With descriptive names, functions can be stored in a separate file (a module) and then imported into a program.

Storing functions separately allows better code organization, re-usability, and easier sharing of code among different programs without having to share the entire program.

### Importing an Entire Module

A module is a `.py` file that contains functions to be imported.

```python
# pizza.py - Summarize the pizza we are about to make.

def make_pizza(size, *toppings):
    print(f"\nMaking a {size}-inch pizza with the following toppings:")
    for topping in toppings:
        print(f"- {topping}")
```

```python
# making_pizzas.py

import pizza

pizza.make_pizza(16, 'pepperoni')
pizza.make_pizza(12, 'mushrooms', 'green peppers', 'extra cheese')
# (module_name).(function_name)(parameters)
```

---

### Importing Specific Functions

Instead of importing the entire module, specific functions can be imported.

```python
from module_name import function_name
from module_name import function_0, function_1, function_2
```

This allows calling the function directly without using the module name:

```python
from pizza import make_pizza

make_pizza(16, 'pepperoni')
make_pizza(12, 'mushrooms', 'green peppers', 'extra cheese')
```

---

### Using "as" to Give a Function an Alias

If a function's name is too long or conflicts with another function, it can be given an alias.

```python
from pizza import make_pizza as mp

mp(16, 'pepperoni')
mp(12, 'mushrooms', 'green peppers', 'extra cheese')
```

General syntax for aliasing:

```python
from module_name import function_name as fn
```

---

### Using "as" to Give a Module an Alias

A module itself can be assigned a shorter alias for convenience:

```python
import module_name as mn
import pizza as p
```

---

### Importing All Functions from a Module

Using `*`, all functions from a module can be imported:

```python
from pizza import *

make_pizza(16, 'pepperoni')
make_pizza(12, 'mushrooms', 'green peppers', 'extra cheese')
```
Because every function is imported, you can call each function by name without using the dot notation. 

While convenient, this approach is not recommended for larger modules as it can lead to function name conflicts.

---

