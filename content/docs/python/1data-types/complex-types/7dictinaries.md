---
title: "02 CDT - 07 Dictinaries"
description: ""
summary: ""
date: 2024-12-17T22:47:04+05:30
lastmod: 2024-12-17T22:47:04+05:30
draft: false
weight: 26
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---



Dictionary is a collection of key-value pairs. each key is connected to a value, and key can be used to access a value.
It is wrapped in `{}` ,  key connected to value by colon `:` , and each key-value pair is separated by `,`
`a = {"colour" : "green", "points" : 5 }`

## Dictionary

```python NPTL
A list l = [13, 24, 54, 77, 33]
```
Values are associated to positions `{0,1,2,3,4}`, so `0,1,2,3,4` are keys which can be used to access corresponding values. But no specific key can be defined other than these, which are auto assigned.

```python
test1 = {}
test1 ["dhawan"] = 84
test1 ["Pujara"] = 16
```
Dictionaries, allows keys other than `range(0,n)`,	Key could be any immutable values (int, float, bool, string, tuple),  it cannot be (list, dict), they can be updated in place like lists.
(called dictionaries in python,  associative array in other languages)

Empty dictionary is `{}`, not `[]` which is a list,  `test1 = ()` is empty tuple

Adding new key-value pairs.
To add a new key-value pair,  give the name of the dict folowed by new key in [] along with new value.
```python
a["x"] = 0
a["y"] = 25        
a = {"colour":"green", "points":5, "x":0, "y":25}
# starting with an empty dictionary and then adding each new item to it   a = {}
```

Nested dictionaries
```python
# there can be multiple keys for a given value

score = {}
score["Test1"] = {}
score["Test2"] = {}
score["Test1"]["Dhawan"] = 84
score["Test1"]["Kohli"] = 200
score["Test2"]["Dhawan"] = 50
print(score)

# simplified
score = { "Test1": { "Dhawan":84, "Kohli":200},  "Test2":{ "Dhawan": 50 } }
```

Using `get()` to Access Value

`get()` method can be used to set a default value if the requested key doesn't exist.
It requires a key as first argument, a second optional argument if key doesn't exist.

If there is a chance that the value you might be asking doesn't exist, use get()
Even if second value is left blank, "None" will be returned, indicating absence of value
```python
point = a.get('points', 'No point value assigned')      
```

## Looping through a Dictionary

#### `items()` Looping through all key-value pairs

We can loop through all the dict key-value pairs through its keys or values.
using `for` loop for dict, create two variables to store keys and values. with dict name followed by method `items()`
```python ccp
user = { k:v, k1:v1  }  
for key, value in user.items()              
```

```python
user_0 = { "username": "efron", "first": "enric", "Last": "fermi" }
for key, value in user_0.items():
    print(f"\nKey: {key}")
    print(f"Value: {value}")
```

```python
fav_lang = { "jen": "Python", "sarah": "C", "edward":"rust", "phil": "python"}
for name, lang in fav_lang.items():
    print(f"{name}'s favorite language is {lang}.")
```

### `keys()` Looping through all keys

`for name in fav_lang.keys():` is same as `for name in fav_lang:` because looping through keys is default when for is applied to a dict.
```python
fav_lang = { "jen": "Python", "sarah": "C", "edward":"rust", "phil": "python"}
for name in fav_lang:   # for name in fav_lang.keys():  does same
    print(f"{name} took our survey.")
```

```python
fav_lang = { "jen": "Python", "sarah": "C", "edward":"rust", "phil": "python"}
friends = ["phil", "jen"]
for name in fav_lang:
    print(f"Hi, {name}")
    if name in friends:
        lang = fav_lang[name]   # print(f"{name}, I see you love {fav_lang[name]}")
        print(f"{name}, I see you love {lang}" )
```

### Looping through keys in a particular order

Getting all the keys sorted by passing list to sorted.
```python
for name in sorted(fav_lang.keys()):  
```
Looping through values in dict >>> `for lang in fav_lang.values():`

```python
fav_lang = { "jen": "python", "sarah": "C", "edward":"rust", "phil": "python"}
print("The following languages have been mentioned")

for lang in fav_lang.values():
    print(lang)
```

`set()` is a collection in which each item must be unique,
wrapping `set()` around a collection of values, python takes the unique items and forms a set.
```python
fav_lang = { "jen": "python", "sarah": "C", "edward": "rust", "phil": "python"}
print("The following languages have been mentioned")

for lang in set(fav_lang.values()):
    print(lang)
# wrapping set() around fav_lang.values() to get only uniqu values
```

___

```python
E = { 'apple' : 10, "banana" : 5, "orange":15, "grapes":20 }

# Find the fruit with the maximum key based on alphabetical order
max_key = ""
for fruit in E:
    if fruit > max_key:
        max_key = fruit
        max_value = E[fruit]

print("Max key:", max_key)  # Output: grapes
print("Max value:", max_value)  # Output: 20

# Check if 12 is a value in the dictionary
print(12 in E.values())  # Output: False

# Convert the dictionary values to a list and sort in descending order
value_list = list(E.values())
value_list.sort(reverse=True)  # Corrected reverse argument
print("Second largest value:", value_list[1])  # Output: 15

```

___

## Nesting

Nesting is storing multiple dictionaries in a list, or list of items in dictionary, or dicts in dict.
```python
ali_0 = {}
ali_1 = {}
ali_2 = {}
alie = [ali_0, ali_1, ali_2]  
for ali in alie:
    print(ali)     # will print each dictionary 
```

## Making a empty list and populating it

Using `range()` to create a fleet of 30 aliens
```python
aliens = []
for ali in range(30):
    new_alien = {"colour":"green", "points": "5", "speed":"slow" }
    aliens.append(new_alien)
```

Making 3 alien in the list change color, speed and points.
Looping through only 3 and then changing all values for the keys
```python
for a in aliens[:3]:
    if a["colour"] == "green":
        a["colour"] = "yellow"
        a["speed"] = "medium"
        a["points"] = 10

# to make any yellow aliens to red,
    elif a["colour"] == "yelow":
        a["colour"] = "red"
        a["speed"] = "fast"
        a["points"] = 15
for ali in aliens:
    print(ali)
```

___

## A list in a dictionary

Pizza order
```python
pizza = { "crust":"thick", "toppings": ["mushroom", "extra cheese"] }

print(f"You have ordered a {pizza['crust']} crust pizza. \nWith the following toppings " )

for top in pizza["toppings"]:
    print(f"\t{top}")           
    # print(top) would have worked but adding tab with \t needs f string
```

Favorite language
```python
fav_lang = {
'jen': ['python', 'rust'],
'sarah': ['c'],
'edward': ['rust', 'go'],
'phil': ['python', 'haskell'],
}

# i just divided getting the value

for name in fav_lang:
    print(f"{name}'s favorite languages are:")
    for lang in fav_lang[name]:        
    # i used fav_lang.values, but it is a list there are no values or keys
        print(f"\t{lang}")

# it could have been just at a time process
for name, lang in fav_lang.items():
    print(f"{name}'s favorite values are:")
    for l in lang:
        print(f"\t{l}")
```

## Refining the singular plural grammar issue

```python
fav_lang = {
'jen': ['python', 'rust'],
'sarah': ['c'],
'edward': ['rust', 'go'],
'phil': ['python', 'haskell'],
}

for name, lang in fav_lang.items():
    if len(lang) == 1:
        print( f"{name.title()}'s favorite language is:")
        print(f"\t{lang[0].title()}")
    else:
        print(f"{name.title()}'s favorite languages are:")
        for l in lang:
            print(f"\t{l.title()}")
```


## A dictionary in dictionary
```python
users = {
'aeinstein': {'first': 'albert',  'last': 'einstein', 'location': 'princeton',} ,
'mcurie': {'first': 'marie', 'last': 'curie', 'location': 'paris',} ,
}

for user, data in users.items():        
    print ( f"\nUsername: {user}")
    print ( f"\tFull Name: {data['first'].title()} {data['last'].title()}")
    print ( f"\tLocation: {data['location'].title()}")

# just another way
for user, data in users.items():        
    print ( f"\nUsername: {user}")
    full_name = f"{data["first"].title()} {data['last'].title()}"
    location = f"{data['location'].title()}"
    print(f"\tFull Name: {full_name}\n\tLocation: {location}")
```

____

## CS50

Associates a value with another value,  like words and meanings in a dictionary.
having multiple lists `[]` isn't practical.
```python
students = { }  
# empty dictionary

keys : values # : is the separator
```

`list[]` have numbers to index into them, but `dict{}` allows the actual words to be used as Indies to get their values. To get Draco values, we can use Draco as the key
```python
students = {
    "Harry" : "Gryffindor",
    "Hermione" : "gryffindor",
    "Draco" : "Slytherin" }
print(students["Hermione"])
print(students["Draco"])

for student in students:
    print(student)
 # by default the dic{} only the keys are read so only names are displayed

for student in students:
    print(student, students[student], sep=", ")
# students[student] is using the name as key to get the associated value
```

## List of Dict

Keyword "None" with capital N, which represents absence of value,
All `dict{}` are given same key words but different values, by design keys are standardized to find things easily.
```python
students = [
    {"name": "Hermione", "house": "Gryffindor", "patronus":"Otter" },
    {"name": "Harry", "house": "Gryffindor", "patronus": "Stag" },
    {"name": "Ron", "house": "Gryffindor", "patronus": "Terrier" },
    {"name": "Draco", "house": "Slytherin", "patronus": None}
]
for student in students:
    print(student["name"], student["house"], student["patronus"], sep=", ")

  
# using print(students["name"]) will give a str, but it must be int
# "for" will get first value which is dict{} 0, to student
# print(student["name"]) will get the value of key word "name"
```

## Processing a Dictionary

Extracting keys using `d.keys()`
It returns sequence of keys in dictionary d ( in random order). `d.key` is not a list, it is similar to range. To make a list of keys, `list(d.keys())` 
```python
for k in d.keys():
    # some process d[k]

# d.keys() will not be in any perticular order
for k in sorted(d.keys()):  # returns in predictible order
    # process d[k]

sorted(l)  # returns a sorted copy of l,  so doesnt modify l
l.sort()   # sorts l in place
```

Extracting Values from dictionary
```python
d.values()  
# is a sequence of values in d  

total = 0
for s in test1.values():
	total = total + s
```

Testing if value is in dict uising "in" function.
Assigning to an unknown key inserts an entry or updates if key already exists.
```python
d = {}
d[0] = 7  # then  d == {0:7}

l = []
l[0] = 7  # causes IndexError
```
    

# Course
## Implementing a dictionary

```python
A dictionary is implimented as a hash table
	an array plus a hash function

The underlying storage is an array
 given an offset i, find A[i] in constant time

keys have to be mapped to {0,1,. . ., n-1}
	given an key k, convert it to an offset i


Hash function

	h: S--> X maps a set of values S to a small range of integers X = {0,1,..,n-1}
	typically |X|<<|S|, so there will be collisions, h(s) = h(s'), s != s'
	
	a good hash function will minimize collisions
	SHA-256 is an industry standatd hashing function whose range is 256 bits
		use to hash large files 
```
