---
title: "JS - 02.16 - Iterables"
description: ""
summary: ""
date: 2024-11-07T20:52:20+05:30
lastmod: 2024-11-07T20:52:20+05:30
draft: false
weight: 335
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---


## [**Iterable**](https://javascript.info/iterable)

Objects that can be used in `for..of` are called _iterable_.
To be considered iterable, an object must implement the method `Symbol.iterator`, which returns an **iterator**. 

- **Example:** Arrays, Strings, Maps, Sets, and even custom objects that implement `Symbol.iterator`.

### **`Symbol.iterator` Method**

The `Symbol.iterator` method is a built-in symbol in JavaScript that returns an **iterator** object. This iterator object must have a method called `next()`, which provides the logic for iteration.

- The `next()` method returns an object with two properties:
  - **`done`**: A boolean that indicates whether the iteration has completed.
  - **`value`**: The current value of the iteration.

If `done` is `true`, the iterator has finished iterating, otherwise, `done` will be `false`, and `value` will hold the next item in the iteration.

```js
let range = {
  from: 1,
  to: 5,

  [Symbol.iterator]() {
    this.current = this.from;  // Start from "from"
    return this;
  },

  next() {
    if (this.current <= this.to) {
      return { done: false, value: this.current++ };  // Return value and increment
    } else {
      return { done: true };  // End of iteration
    }
  }
};

for (let num of range) {
  console.log(num);  // Outputs: 1, 2, 3, 4, 5
}
```

- In this example, `range` is an object that implements `Symbol.iterator`.
- The `next()` method returns each number from 1 to 5.
- Once the value exceeds `to`, `done: true` is returned to signal the end of the iteration.

---

## **String is Iterable**

Strings are iterable in JavaScript, meaning they can be used directly in a `for..of` loop. The loop iterates over each character of the string.

```js
for (let char of "test") {
  console.log(char);  // Outputs: t, e, s, t
}
```

- A string is considered **array-like**, as it has an index and a `length` property, but it is also iterable. Each character in the string is treated as an element that can be iterated over in a `for..of` loop.

### **Surrogate Pairs in Strings**
JavaScript strings are Unicode-compliant, meaning they support **surrogate pairs** (characters that require more than one code unit to represent in UTF-16). The `for..of` loop correctly handles these surrogate pairs, unlike traditional array-like indexing.

```js
let emoji = "😊";
for (let char of emoji) {
  console.log(char);  // Outputs: 😊
}
```

In this case, the `for..of` loop properly handles the emoji as a single character, even though it might require multiple code units internally.

---

## **Array-like Objects**

An **array-like object** is an object that has indexed properties (such as `0`, `1`, etc.) and a `length` property, but it lacks the built-in methods of arrays (like `.push()`, `.pop()`, etc.). These objects are **not** true arrays but are structured similarly.

```js
let arrayLike = {
  0: "Hello",
  1: "World",
  length: 2
};

console.log(arrayLike[0]);  // Outputs: Hello
console.log(arrayLike[1]);  // Outputs: World
```

Although `arrayLike` looks like an array (because it has a `length` and indexed properties), it’s not a real array, so you can't call array methods like `.pop()` or `.push()` on it directly.

---

## **`Array.from` Method**

[Array.from](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/from) is a **universal method** that allows you to convert an iterable or array-like object into a proper JavaScript `Array`. After conversion, the resulting array can use all the array methods like `.map()`, `.filter()`, `.reduce()`, etc.

**Converting an Array-like Object to an Array**
```js
let arrayLike = {
  0: "Hello",
  1: "World",
  length: 2
};

let arr = Array.from(arrayLike);
console.log(arr);  // Outputs: ['Hello', 'World']
console.log(arr.pop());  // Outputs: World
```

**Converting a String to an Array**
You can also use `Array.from` to convert a string into an array of its characters:

```js
let str = "hello";
let arr = Array.from(str);
console.log(arr);  // Outputs: ['h', 'e', 'l', 'l', 'o']
```

### **Using `mapFn` with `Array.from`**

`Array.from` accepts a **second argument** called `mapFn`, which is a mapping function applied to each element before adding it to the resulting array.

```js
let numbers = [1, 2, 3];
let squaredNumbers = Array.from(numbers, num => num * num);
console.log(squaredNumbers);  // Outputs: [1, 4, 9]
```

- In this example, `Array.from` creates an array from the `numbers` array and applies the `mapFn` to square each number before storing it in the new array.

### **Syntax of `Array.from`:**

```js
Array.from(obj[, mapFn, thisArg])
```

- `obj`: The iterable or array-like object.
- `mapFn` (Optional): A function to apply to each element in the array.
- `thisArg` (Optional): A value to use as `this` inside the `mapFn` function.

---

## **Summary**

- **Iterables** are objects that can be iterated over using a `for..of` loop. They must implement the `Symbol.iterator` method.
- **Strings** are iterable objects, meaning you can loop over them character by character using `for..of`.
- **Array-like objects** are objects that have indexed properties and a `length` property but are not true arrays.
- **`Array.from`** is a powerful method that converts iterable or array-like objects into actual arrays, enabling array methods like `.map()`, `.filter()`, and more.
