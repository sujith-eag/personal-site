---
title: "JS - 05.01 - Array"
description: ""
summary: ""
date: 2024-11-09T17:08:28+05:30
lastmod: 2024-11-09T17:08:28+05:30
draft: false
weight: 390
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---


JavaScript arrays are a special type of object used to store ordered sequences of values.   Unlike regular objects, which use named keys (like strings), arrays use numeric indexes.

---

### Creating Arrays

#### 1. **Empty Arrays**

You can create an empty array using either of these two methods:

```js
let arr = new Array();  // Using the Array constructor
let arr = [];           // Using array literal (preferred)
```

#### 2. **Array with Values**

An array can be initialized with values inside square brackets (`[]`):

```js
let listOfNumbers = [2, 3, 4, 5];
console.log(listOfNumbers[2]);  // 4 (indexing starts from 0)

console.log(listOfNumbers[2 - 1]);  // 3 (same as listOfNumbers[1])
```

Array elements can be accessed using their index values. Arrays are **zero-indexed**.
You can also use arithmetic expressions as indices.

```js
const cars = ["Volvo", "BMW", "Tata"];
let car = cars[0];  // "Volvo"
```

```js
const cars = [];
cars[0] = "Volvo";
cars[1] = 'BMW';
```

---

### **Associative Arrays in JavaScript**

Although arrays in JavaScript are **indexed by numbers**, you can technically assign a value to a string index.

Arrays with named indexes are called associative arrays or hashes, but
JavaScript **does not support** arrays with named indexes, it always uses Numbered Index.

If named indexes are used, `js` converts array to an object. Then array methods and properties will produce incorrect result.

Example of incorrect usage (for associative arrays):
```js
const person = [];
person["first"] = "John";
person["last"] = "Doe";

console.log(person.length);  // 0 (wrong, since it's an object now)
console.log(person["first"]);  // "John"
console.log(person[0]);  // undefined
```

If you need associative arrays, consider using an **object** instead.

---

### **Arrays of Objects, Arrays in Arrays, and Functions in Arrays**

Arrays in JavaScript can contain any type of data, including objects, functions, and even other arrays.

#### 1. **Array of Objects**

You can store objects inside an array, which is a common pattern for structured data.

```js
let journal = [
  {event: ["work", "touched tree", "pizza", "running"], squirrel: false},
  {event: ["work", "ice cream", "lasagna"], squirrel: false},
  {event: ["weekend", "cycling", "peanuts"], squirrel: true}
];
```

#### 2. **Array of Functions**

You can also store functions within an array:

```js
let functionsArray = [
  function() { console.log("Function 1"); },
  function() { console.log("Function 2"); },
  function() { console.log("Function 3"); }
];
```

#### 3. **Arrays within Arrays**

Arrays can even contain other arrays, creating nested structures:

```js
let arrayOfArrays = [
  [1, 2, 3],
  [4, 5, 6],
  [7, 8, 9]
];
```

---

#### **`length` Property**

The `length` property of an array returns the number of elements in the array. It’s important to note that `length` is **not** zero-based.
When using `[]` the expression between the brackets are evaluated to get the property name.

```js
const fruits = ["Banana", "Orange", "Mango"];
console.log(fruits.length);  // 3
```

You can also use `length` to access the last element of an array:

```js
let fruit = fruits[fruits.length - 1];  // "Mango"
```

---

### **Looping Through Arrays**

#### 1. **`for` Loop**

A traditional `for` loop is a common way to iterate through an array:

```js
for (let i = 0; i < journal.length; i++) {
  let entry = journal[i];
  console.log(entry);  // Do something with each entry
}
```

#### 2. **`for..of` Loop**

The `for..of` loop is a simpler way to iterate over array elements. It gives you the value directly without needing the index.

```js
for (let entry of journal) {
  console.log(`${entry.event.length} events.`);  // logs the number of events
}
```

#### 3. **`forEach()` Method**

The `forEach()` method allows you to run a function for each item in the array:

```js
arr.forEach(function(item, index, array) {
	// do something with item
});
```

```js
["Banana", "Orange", "Mango"].forEach(alert);
// This will alert each fruit in the array

const fruits = ["Bannana", "Orange", "Mango"];
fruits.forEach(alert);
```

```js
// making a list html item for each item
const fruits = ["Bannana", "Orange", "Mango"];

function myFunction(value) {
	text += "<li>" + value + "</li>";
}

fruits.forEach(myFunction);
```

You can also access the current index and the full array within the callback function:

```js
fruits.forEach((item, index, array) => {
  alert(`${item} is at index ${index} in ${array}`);
});
```

---

### **Using Functions to Manipulate Array Data**

JavaScript provides several ways to work with arrays and manipulate their data.

#### 1. **Function for Adding Entries to an Array**

If you want to simplify adding entries to an array of objects, you can use a function:

```js
let journal = [];

function addEntry(events, squirrel) {
  journal.push({events, squirrel});
}

addEntry(["work", "touched tree", "pizza", "running"], false);
addEntry(["work", "ice cream", "lasagna"], false);
addEntry(["weekend", "cycling", "peanuts"], true);
```

This is a shorthand for creating an object with properties named `events` and `squirrel`. Since the property names match the argument names, JavaScript will automatically assign them.

---

### **Summary of Key Points**

- **Arrays in JavaScript** are ordered lists of values, indexed by numbers.
- Arrays are **not associative arrays** (i.e., they cannot use string keys without being converted into objects).
- You can create arrays using both the array literal (`[]`) and the `Array` constructor (`new Array()`).
- **Array properties and methods** like `length`, `forEach()`, and `push()` are essential for manipulating data.
- JavaScript arrays can store **different data types**, including objects, functions, and even other arrays.
- **Iterating through arrays** can be done with `for` loops, `for..of`, and `forEach()` methods, each offering different levels of control and readability.


