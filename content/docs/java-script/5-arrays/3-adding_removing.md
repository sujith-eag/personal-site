---
title: "03 - Adding and Removing Array Elements"
description: ""
summary: ""
date: 2024-11-09T17:09:14+05:30
lastmod: 2024-11-09T17:09:14+05:30
draft: false
weight: 424
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---



### Adding Elements with 'push()' and 'unshift()':

You can add elements to an array by simply assigning values to new indices or you can use methods like `push()` to add one or more elements to the end of an array and also returns the length of new array.

```js
let a = [];
// Start with an empty array

a.push("zero");
// Add a value at the end. a = ["zero"]

a.push("one", "two"); 
// Add two more values. a = ["zero", "one", "two"]
```

```js
let sequence = [1, 2, 3];
sequence.push(4);
sequence.push("Banana");

console.log(sequence);  
// [1, 2, 3, 4, Banana]

let length = sequence.push("Mango");  
// 6
```

You can use the `unshift()` method to insert an element at the **beginning** of an array, shifting existing elements to higher indexes.

```js
a.unshift("start"); // Adds "start" to the beginning of the array
```

____

### Removing Elements with 'pop()' and 'shift()':

The `pop()` method removes the last element of the array and returns it, reducing the length of the array by 1.

```js
let lastItem = a.pop(); // Removes and returns the last element
```

The `shift()` method removes the first element of the array and returns it, reducing the length by 1 and shifting all remaining elements down by one index.

```js
let firstItem = a.shift(); // Removes and returns the first element
```

```js
const fruits = ["Bannana", "Orange", "Mango", "Kiwi"];

fruits.shift();   // removes Banana
let fruit = fruits.shift();  // Orange

fruits.unshift("Lemon"); // adds lemon at front
let num = fruits.unshift("Lemon"); // 5
```

***A To do list***    Managing a queue of stack
```js
let todoList = [];

function remember(task) {
	todoList.push(task);
}
function getTask() {
	return todoList.shift();
}
function rememberUrgently(task) {
	todoList.unshift(task);
}
```


#### Function for Adding Entries to an Array

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

## Deleting Array Elements

Delete can be done with `delete` operator, similar to deleting object properties.

However, note that using `delete` on an array element **does not** affect the `length` property, and it does **not** shift the remaining elements to fill the gap. This results in a sparse array.

```js
let a = [1, 2, 3];

delete a[2];
// a now has no element at index 2

console.log(2 in a);  // => false: no element at index 2
console.log(a.length);  // => 3: Length is unaffected by delete
```

---


## 'splice()' Method

The `splice()` method is a general-purpose and very versatile method for inserting, deleting, or replacing array elements.

It alters the `length` property and shifts array elements to higher or lower indexes as needed.

```js
arr.splice(start[, deleteCount, elem1, ..., elemN])
```

It modifies `arr` starting from the index `start`, removes `deleteCount` elements, and then inserts `elem1, ..., elemN` at their place. It returns the array of removed elements.

---

#### **Using splice() for Deletion**:

```js
let arr = ["I", "study", "JS"];
// From index 1, remove 1 element
arr.splice(1, 1); 

console.log(arr); // ["I", "JS"]
```

**Returning Deleted Items**:
```js
let arr = ["I", "study", "JS", "right", "Now"];

// Remove 2 elements starting from index 0
let deletedItems = arr.splice(0, 2);

console.log(arr);  // ["JS", "right", "Now"]
console.log(deletedItems);  // ["I", "study"]
```

---

#### **Using splice() for Deletion and Insertion**:

```js
let a = [1, 2, 3, 4, 5];

a.splice(2, 2, "newElement"); 
// This removes 2 elements at index 2 and replaces them with "newElement"
// a becomes [1, 2, "newElement", 5]
```

**Using splice() for Deletion and Replacement**:
```js
let arr = ["I", "study", "JS", "right", "Now"];

// Remove 3 elements starting from index 0 and replace them with "Let's" and "Dance"
arr.splice(0, 3, "Let's", "Dance");

console.log(arr);  // ["Let's", "Dance", "right", "Now"]
```

---

#### **Inserting Without Removing Elements**:

```js
let arr = ["I", "study", "JS", "right", "Now"];

// Starting from index 2, delete nothing, and insert "right" and "Now"
arr.splice(2, 0, "right", "Now");

console.log(arr);  // ["I", "study", "JS", "right", "Now"]
```

---

#### **Negative Index for Counting from the End**:

```js
let arr = [1, 2, 5];

// From index -1 (one step from the end), delete nothing, and insert 3 and 4
arr.splice(-1, 0, 3, 4);   // [1, 2, 3, 4, 5]
```

The first parameter defines the index where the new element should be added (spliced). The second parameter defines how many elements should be removed. The rest of the parameters define the new elements to be added.

---

### Example with Fruits Array:

```js
const fruits = ["Banana", "Orange", "Apple", "Mango"];

// Starting from index 2, remove nothing, and add "Lemon" and "Kiwi"
fruits.splice(2, 0, "Lemon", "Kiwi");
// fruits becomes ["Banana", "Orange", "Lemon", "Kiwi", "Apple", "Mango"]
```

```js
const fruits = ["Banana", "Orange", "Apple", "Mango"];

// Starting from index 2, remove 2 elements, and add "Lemon" and "Kiwi"
fruits.splice(2, 2, "Lemon", "Kiwi");  
// fruits becomes ["Banana", "Orange", "Lemon", "Kiwi"]
// Removed items: ["Apple", "Mango"]
```

---

### Finding a Range In-Place Using splice()

To remove elements that do not fall within a specified range, you can use a `for` loop to iterate through the array. To avoid skipping an element after deletion, you can adjust the index.

```js
function findInRange(arr, a, b) {
  for (let i = 0; i < arr.length; i++) {
    if (arr[i] < a || arr[i] > b) {
      arr.splice(i, 1);
      i--;  // Adjust the index to avoid skipping elements
    }
  }
}

let arr = [5, 3, 8, 1];
findInRange(arr, 1, 4);
console.log(arr); // Output: [3, 1]
```

Reverse looping using a negative index:

```js
function findRangeInPlace(arr, a, b) {
  for (let i = arr.length - 1; i >= 0; i--) {
    if (arr[i] < a || arr[i] > b) {
      arr.splice(i, 1);
    }
  }
}

let arr = [5, 3, 8, 1];
findRangeInPlace(arr, 1, 4);
console.log(arr); // Output: [3, 1]
```

---

### **'arr.toSpliced()' Method**

The `toSpliced()` method is a safe way to splice an array without altering the original array. It creates a new array with the modifications, leaving the original array unchanged.

```js
arr.toSpliced(start[, deleteCount, elem1, ..., elemN])
```

```js
const fruits = ["Banana", "Orange", "Apple", "Mango"];

const spliced = fruits.toSpliced(2, 0, "Lemon", "Kiwi");
// spliced becomes ["Banana", "Orange", "Lemon", "Kiwi", "Apple", "Mango"]

console.log(fruits);  // Original array remains unchanged
```

---
