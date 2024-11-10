---
title: "Object"
description: ""
summary: ""
date: 2024-11-09T17:05:46+05:30
lastmod: 2024-11-09T17:05:46+05:30
draft: false
weight: 370
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---


## **Objects in JavaScript**

- **Primitive types**: These can only hold a single value (e.g., numbers, strings, booleans).
- **Object types**: These are collections of key-value pairs and can store multiple values.

An object is a collection of key-value pairs, where:
- **Key** is a string.
- **Value** can be any data type.

**Syntax** for defining an object:
```js
let user = { key: value };
```

### **Braces `{}` in JavaScript**
- `{}` can denote:
  1. **A block of statements** in control structures like loops or conditionals.
  2. **An object literal** when defining an object.

**Creating an empty object**:
```js
let user = new Object();  // "object constructor" syntax
let user = {};            // "object literal" syntax
```

---

## **References and Copies of Objects**

When defining objects, they hold **references** to the data, not copies. This means multiple variables can reference the same object.
When a primitive variable is defined, it will contain a copy of the information provided to it.

```js
const obj = { data: 42 };
const objCopy = obj;  // objCopy points to the same object as obj

objCopy.data = 43;

console.log(obj);      // { data: 43 }
console.log(objCopy);  // { data: 43 }
```

This is how the DOM object gets edited using storing its references in `js` variables.

```js
const element = document.querySelector("#container");
element.style.backgroundColor = 'red';  // Changes the actual DOM element
```

---

## **Literals and Properties**

An **object literal** is a shorthand for creating objects by directly defining key-value pairs inside `{}`.
Each `property` has a `key`or `name` before the colon`:`   
Each property seperated by a `,` comma.

Each property in an object consists of:
- A **key** (or property name).
- A **value** associated with that key.

```js
let user = {
  name: "John",
  age: 30,
  "likes birds": true,  // property name with spaces must be in quotes
};

alert(user.name);  // "John"
user.isAdmin = true;  // Assigning a new property
delete user.age;  // Deletes the 'age' property
```

**Note**: Property names can be any string, number, or symbol, including reserved words or multi-word names.
Properties whose name are not valid bindings and multi word has to be in `""`quotes.
`"touch wood": "touched"`

---

## **Object Literals with Functions**

Objects can also have **methods** (functions). These are functions stored as properties of an object.

```js
const person = {
  name: ["Bob", "Smith"],
  age: 32,
  bio: function () {
    console.log(`${this.name[0]} ${this.name[1]} is ${this.age} years old.`);
  },
  introduceSelf: function () {
    console.log(`Hi! I'm ${this.name[0]}.`);
  },
};

// Calling the methods
person.bio();  // "Bob Smith is 32 years old."
```
An object like this is called an object literal - we have written out the object contents as we've come to create it.


**simplified syntax** for functions inside an object:
```js
bio: function () {...},
introduceSelf: function() {...},

// simpler is omitting the function
bio() { ... },
introduceSelf() { ... },
```

---

## **Accessing Properties of Objects**

### **Dot Notation**

The **dot notation** is the most common way to access properties of an object:

```js
person.age;         // Accessing a property
person.bio();       // Calling a method
```
The object name acts as the namespace - entered first to access anything inside the object. Next is a dot `.` , then what needs to be accessed.


**Nested Objects**: Objects can contain other objects, and to access nested properties, you chain dot notations:

```js
const person = {
  name: {
    first: "Bob",
    last: "Smith",
  },
};

console.log(person.name.first);  // "Bob"

// using bracket notation
person["name"]["first"];
```

---

## **Square Bracket Notation**

**Square bracket notation** is similar to array indexing but is used for object properties. 
Instead of index numbers to select an item, name associated with each member's value is used.
This allows:
- Dynamic property names.
- Accessing multi-word properties (those with spaces or special characters).

Objects are also called as ***associative arrays***

Dot notation is preferred as it is more easy to read but,
if an object property name is held in a variable, then dot notation cannot be used to access the value.

```js
const person = {
  name: ["Bob", "Smith"],
  age: 32,
};

function logProperty(propertyName) {
  console.log(person[propertyName]);  // Access using a variable
}

logProperty("name");  // ["Bob", "Smith"]
logProperty("age");   // 32
```

### **Multi-word Property Names**

When property names are multi-word or contain special characters (like spaces), you must use square bracket notation:

```js
let user = {};
user["likes birds"] = true;  // valid

alert(user["likes birds"]);  // true
delete user["likes birds"];  // deletes the property
```

### **Using Variables to Access Properties**

Square bracket notation allows properties to be accessed dynamically using variables:

```js
let key = "likes birds";
user[key] = true;  // Same as user["likes birds"] = true;
```

```js
let user = {
	name: "John",
	age: 30
};

let key = prompt("What do you know about user?", "name");
// access by variable
alert( user[key] );  // John ???
```

---

# for..in loop
[[4_for...in_loop|Details here]]

---

## **Property Value Shorthand**

When creating objects, if the property name matches the variable name, you can use shorthand syntax:

```js
function makeUser(name, age) {
  return {
    name,  // shorthand for name: name
    age,   // shorthand for age: age
  };
}

let user = makeUser("John", 30);
alert(user.name);  // "John"
```

### **Shorthand Example**:
```js
let user = {
  name,  // same as name: name
  age: 30,
};
```

---

## **Summary**

- **Objects** are collections of key-value pairs, often used to store structured data.
- **Keys** (or property names) are strings, and **values** can be any data type.
- Access properties using:
  - **Dot notation**: `obj.property`
  - **Square bracket notation**: `obj["property"]` (use when key is dynamic or contains spaces)
- **For-in loop** can be used to iterate over object properties.
- Objects can have methods, and shorthand notation can simplify property definition.

Additional operators:
- To delete a property: `delete obj.prop`.
- To check if a property with the given key exists: `"key" in obj`.
- To iterate over an object: `for (let key in obj)` loop.

What we’ve studied in this chapter is called a “plain object”, or just `Object`.



