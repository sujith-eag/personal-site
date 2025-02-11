---
title: "05 Functions - 02 Scope"
description: ""
summary: ""
date: 2025-02-11T17:08:40+05:30
lastmod: 2025-02-11T17:08:40+05:30
draft: false
weight: 47
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---

### Assigning Functions to Different Names

A function can be assigned to another name, allowing it to be referenced differently.

```python
# Assigning a function to a new name
def f(a, b, c):
    ...

g = f  # g is now another name for f
```

This technique is useful for passing functions as arguments to other functions.

```python
# Applying a function repeatedly
def apply(f, x, n):
    res = x
    for i in range(n):
        res = f(res)
    return res

def square(x):
    return x * x

print(apply(square, 5, 2))  # Output: 625
```

Here, `square` is passed as `f` to `apply()`.

---

Function definitions can be conditionally assigned.

```python
if condition:
    def f(a, b, c):
        ...
else:
    def f(a, b, c):
        ...
```

---

### Customizing Function Behavior

Functions can be customized based on parameters, such as sorting based on a comparison function.

```python
def sort_function(l, cmp_fn=default_cmp_fn):
    ...
```

---

## Function Calls and Scope Issues

The `main()` function prompts for a name and calls another function to process it.

```python
# Defining and calling functions
def main():
    name = input("What's your name? ")    
    hello(name)

def hello(to="world"):
    print("Hello,", to)

main()
```

### Scope Issue Example

If a variable is defined inside a function, it cannot be accessed outside its scope.

```python
# Scope issue example
def main():
    name = input("What's your name? ")    
    hello()

def hello():  # No parameter defined
    print("Hello,", name)  # Error: name is not defined in this function

main()
```

Since `name` is local to `main()`, `hello()` cannot access it directly.

Issue of "Scope" which refers to a variable only existing in the context it was defined in. `name` was defined in `main()` so it cannot be used directly in `hello()`.
When the value is handed to `hello()` within the `main()`, it can be used.
Its for each function to name its own variable so the "name" variable in main can be passed to "hello" which becomes "to"

---

## Returning Values and Scope Management

Returning values allows functions to pass data back.

```python
# Returning values between functions
def main():
    x = int(input("What's x? "))
    print("Value of x squared is:", square(x))

def square(n):
    return n * n  # Returns the squared value

main()
```

---

## Scope in Functions

### Local vs. Global Scope

Variables inside a function are separate from those outside.

```python
# Scope demonstration
def f():
    y = x
    print(y)

x = 7  # Global variable
f()  # Runs fine
```

If a variable is defined inside the function, it does not check the external definition:

```python
# Local scope overriding global
def f():
    y = x  # Error: x is referenced before assignment
    print(y)
    x = 22  # Local x is defined after usage

x = 7
f()
```
in first case, there is no x inside the function so it checks outside.
this applies only to immutable values.

___

### Global Variables and Mutability

Lists and dictionaries are mutable and can be updated globally.

```python
# Modifying a global mutable variable

def f():
    y = x[0]
    print(y)
    x[0] = 22  # Modifies global list

x = [7]  # x is a list
f()  # Prints 7 and updates x
```

### Modifying Global Immutable Variables

To modify global immutable variables, `global` must be declared.

```python
# Using global to modify immutable variables
def f():
    global x  # Declare global usage
    y = x
    print(y)
    x = 22  # Modifies global x

x = 7
f()  # Prints 7, updates x to 22
print(x)  # Output: 22
```

---

## Nested Functions

A function can be defined inside another function called "helper" function. 

```python
# Nested functions example
def f():
    def g(a):
        return a + 1
    
    def h(b):
        return 2 * b
    
    global x
    y = g(x) + h(x)
    print(y)
    x = 22

x = 7
f()
```

Here, `g()` and `h()` are only accessible within `f()`. Nested functions are useful for encapsulating helper logic within a function.

---

