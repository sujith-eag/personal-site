---
title: "05 Functions - 01 Defining a Function"
description: ""
summary: ""
date: 2025-02-11T17:08:10+05:30
lastmod: 2025-02-11T17:08:10+05:30
draft: false
weight: 46
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---




Functions are named blocks of code designed to perform a specific task. When you want to execute a task defined in a function, you call the function responsible for it.

### Why Use Functions?

- Avoid repetition by defining reusable code blocks which can be called when needed.
- Improve readability and maintainability.
- Allow abstraction by breaking down complex logic into smaller parts.

---

## Defining a Function

To define a function, use the `def` keyword, followed by the function name and parameters in parentheses `()` and `:` for the defining to begin. 
The function body is indented (Whatever gets indented is the functions body).

Defining and Calling a Function
```python CS50
def hello(to):
    print("hello,", to)
    
name = input ("whats your name? ")
hello(name)
```

```python
def greet(username):  # Function with a parameter
    """Prints a greeting message."""
    print(f"Hello, {username.title()}!")

greet("jess")  
# Function call with an argument
```

### Function Components:

1. **Function Name**: Identifier for the function.
2. **Parameters (Arguments)**: Input values the function can accept.
3. **Body**: Indented block of statements.
4. **Return Statement**: Optionally returns a value.
5. **Function Call**: Executes the function with given arguments.

---

## Function Parameters and Arguments

Functions can accept multiple arguments.

```python
# Function with Multiple Parameters
def add(a, b, c):
    """Returns the sum of three numbers."""
    return a + b + c

result = add(2, 3, 5)
print(result)  # Output: 10
```

---

## Default Parameter Values

Functions can have default parameter values. If an argument is not provided during the function call, the default value is used.

```python
# Function with Default Argument
def hello(to="world"):
    """Prints a greeting with a default name."""
    print("Hello,", to)

hello()  # Output: Hello, world
name = input("What's your name? ")
hello(name)  # Uses the user-provided name
```


Giving default value to the function like print had `sep=' '` and `end='\n'`.
If no value is provided default can run, if defined it gets replaced.

---

## Return Values

A function can return a value using the `return` statement. The returned value can be stored in a variable or used in expressions.

```python
# Function Returning a Value
def format_name(first, last):
    """Returns a formatted full name."""
    full_name = f"{first.title()} {last.title()}"
    return full_name

person = format_name("michal", "jackson")
print(person)  # Output: Michael Jackson
```

---

