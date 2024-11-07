---
title: "for-of Loop"
description: ""
summary: ""
date: 2024-11-07T20:51:24+05:30
lastmod: 2024-11-07T20:51:24+05:30
draft: false
weight: 723
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---



[for…of](https://javascript.info/array#loops) and [iterables](https://javascript.info/iterable) for looping over arrays and iterable objects.
[[6_Iterables|Iterable]]

## **`for...of` Loop**

The `for...of` loop is a convenient and modern syntax for iterating over **iterable objects** (e.g., arrays, strings, maps, sets). It's a simpler way to loop through elements in a collection, without needing to manually handle indices.

```js
for (const element of iterable) {
    // code to run for each element
}
```
- `iterable`: An object that can be iterated over (arrays, strings, etc.)
- `element`: The variable that will hold the value of each item in the iterable on each iteration.

---

### **Example 1: Looping Through an Array**

```js
const cats = ["Lepord", "Jaguar", "Tiger"];

for (const cat of cats) {
    console.log(cat);
}
// Output:
// Lepord
// Jaguar
// Tiger
```

In this example, the `for...of` loop iterates through the array `cats`, logging each cat name to the console.

---

### **Iterables**

An **iterable** is any object that can be used in a `for...of` loop. While arrays are commonly iterated with `for...of`, other iterable objects include:

- **Strings**: Each character can be iterated over.
- **Maps**: Iterate through key-value pairs.
- **Sets**: Iterate through values.

Looping through a string:
```js
let word = "Hello";

for (const char of word) {
    console.log(char);
}
// H  // e  // l  // l  // o
```

- **Maps**:
```js
const map = new Map([
    ['key1', 'value1'],
    ['key2', 'value2']
]);

for (const [key, value] of map) {
    console.log(`${key}: ${value}`);
}
// key1: value1   // key2: value2
```

- **Sets**:
```js
const set = new Set([1, 2, 3, 4, 5]);

for (const number of set) {
    console.log(number);
}
// 1  // 2  // 3  // 4  // 5
```

---

### **Create a Function `unique(arr)`**

The `for...of` loop can be helpful for tasks such as removing duplicates from an array. Here's an example of a function that returns an array of unique items from the input array:

```js
function unique(arr) {
    let result = [];

    for (let str of arr) {
        if (!result.includes(str)) {
            result.push(str);
        }
    }
    return result;
}

let strings = ['hare', 'krisna', 'hare', 'krishna', 'krishna', 'krishna', 'hare', 'hare', ':-0'];

alert(unique(strings)); // Output: hare, krisna, krishna, :-0
```

This function iterates through the `arr` using `for...of` and checks if each element is already in the `result` array using the `includes()` method. If the element is not present, it's added to the `result`.

**Note:** This approach has repeated comparisons (`includes()`), which is inefficient for large arrays because `includes()` has a time complexity of O(n). A more optimized solution might involve using a `Set` (which guarantees uniqueness and has O(1) lookup time) or leveraging other data structures.

---

### **Optimized Version Using `Set`**

Instead of using an array and `includes()`, you can use a `Set`, which automatically handles uniqueness for you:

```js
function unique(arr) {
    return [...new Set(arr)];
}

let strings = ['hare', 'krisna', 'hare', 'krishna', 'krishna', 'krishna', 'hare', 'hare', ':-0'];

alert(unique(strings)); // Output: hare, krisna, krishna, :-0
```

This version is much more efficient because the `Set` data structure automatically removes duplicates.

---

### **Summary**

- The `for...of` loop is a great way to iterate over **iterables** such as arrays, strings, maps, and sets.
- It's simpler and cleaner than using traditional `for` loops when you don't need the index.
- **Iterables** allow objects to be used in `for...of` loops, and they include more than just arrays.
- For handling **unique values**, using `Set` is a more optimized approach compared to manually checking with `includes()`.
