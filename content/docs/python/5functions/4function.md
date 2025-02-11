---
title: "05 Functions - 04 Arguments & Parameters (2)"
description: ""
summary: ""
date: 2025-02-11T19:58:41+05:30
lastmod: 2025-02-11T19:58:41+05:30
draft: false
weight: 49
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---



The optional parameter `age` has a special value `None` as a placeholder. In conditional tests, `None` evaluates to `False`.

Returning a dictionary:
```python
def build_person(first_n, last_n, age=None):
    person = {"first": first_n, "last": last_n}
    if age:
        person["age"] = age  
    return person

name = build_person("jimi", "hendrix", 27)
print(name)
```


---

## Using Functions with a While Loop

```python
def get_formatted_name(first_name, last_name):
    full_name = f"{first_name} {last_name}"
    return full_name.title()

while True:
    print("\nPlease tell me your name: ")
    print("(Enter 'q' at any time to exit)")

    f_name = input("First Name: ")
    if f_name == "q":
        break

    l_name = input("Last Name: ")
    if l_name == "q":
        break

    name = get_formatted_name(f_name, l_name)
    print(f"\n{name.title()}")
```


---

## Passing a List

```python
def greeting(names):
    for name in names:
        print(f"Hello, {name.title()}.")

usernames = ['hannah', 'ty', 'margot']
greeting(usernames)
```

---

#### Moving Elements to a New List and Printing Without a Function

```python
unprinted_designs = ['phone case', 'robot pendant', 'dodecahedron']
completed_models = []

while unprinted_designs:
    one = unprinted_designs.pop()
    print(f"The following model is done: {one}")
    completed_models.append(one)

print("\nThese have been printed:")
for model in completed_models:
    print(model)
```

---

#### Performing the Same Action with Functions

```python
def making_print(unprinted_designs, completed_models):
    """Simulates printing each design until none are left."""
    while unprinted_designs:
        one = unprinted_designs.pop()
        print(f"The following model is done: {one}")
        completed_models.append(one)

def last_check(completed_models):
    """Displays all completed models."""
    print("\nThese have been printed:")
    for model in completed_models:
        print(model)

# Lists to store designs
unprinted_designs = ['phone case', 'robot pendant', 'dodecahedron']
completed_models = []

# Call functions
making_print(unprinted_designs, completed_models)
last_check(completed_models)
```

---

## Using Slice Notation to Pass a Copy of a List

The slice notation `[:]` creates a copy of the list when passed to a function. This ensures that the original list remains unchanged.

```python
print_models(unprinted_designs[:], completed_models)
```

This prevents `unprinted_designs` from being modified inside the function.


---

## Passing an Arbitrary Number of Arguments

When you don't know ahead of time how many arguments a function needs to accept, python allows function to collect an arbitrary no of arguments, from the calling statement. by using `*` in parameters, it accepts as many as it is given.

```python
def make_pizza(*toppings):
    print("\nMaking pizza with the following toppings:")
    for topping in toppings:
        print(f"-{topping}")

make_pizza('pepperoni')
make_pizza('mushroom', 'pepper', 'extra cheese')
```

Using both positional and arbitrary arguments:        
arbitrary must be in the end, python matches with first and passes rest to the end.

```python
def make_pizza(size, *toppings):
    print(f"\nMaking a {size}-inch pizza with the following toppings:")
    for topping in toppings:
        print(f"-{topping}")

make_pizza(16, 'pepperoni')
make_pizza(12, 'mushroom', 'green pepper', 'cheese')
```

___

## Using Arbitrary keyword Arguments:

Sometimes you'll want to accept an arbitrary number of arguments, but you won't know ahead of time, what kind of information will be passed to the function.

In this case, you can write functions that accept as many key-value pairs as the calling statement provides.

```python
def build_profile(first, last, **user_info):        
#**kwargs, used to collect non-specific keyword arguments
    user_info['first_name'] = first    # Being placed into dictionary with keys
    user_info['last_name'] = last
    return user_info

user_profile = build_profile('albert', 'einstein', location ='princeton', field = 'physics')

print(user_profile)

# Output : {'location': 'princeton', 'field': 'physics', 'first_name': 'albert', 'last_name': 'einstein'}
```

