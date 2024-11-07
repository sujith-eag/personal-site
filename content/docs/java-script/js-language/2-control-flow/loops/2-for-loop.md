---
title: "for Loop"
description: ""
summary: ""
date: 2024-11-07T20:50:52+05:30
lastmod: 2024-11-07T20:50:52+05:30
draft: false
weight: 722
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---


## **`for` Loop**

The `for` loop is typically used when you know in advance how many times you need to repeat an action. It provides a concise way to initialize, check the condition, and update the loop counter in one line.

```js
for (initializer; condition; final-expression) {
    // code to run on each iteration
}
```

- **Initializer**: Initializes the loop, typically setting a counter variable.
- **Condition**: Expression that is evaluated before each iteration. If it’s `false`, the loop stops.
- **Final-expression**: This is executed after every iteration, usually to update the loop counter (increment or decrement).

---

### **Example 1: Simple Loop with Counter**

```js
for (let number = 0; number <= 12; number = number + 2) {
    console.log(number);
}
// Output: 0, 2, 4, 6, 8, 10, 12
```

In this example, `number` starts at 0 and increments by 2 after each iteration, stopping when it exceeds 12.

---

### **Example 2: Loop with a Counter and Calculation**

```js
let result = 1;

for (let counter = 0; counter < 10; counter++) {
    result = result * 2;
}
console.log(result);  // Output: 1024 (2^10)
```

Here, we calculate `2^10` by doubling the result each time, using `counter` as the iteration variable.

---

### **Inline Variable Declaration**

You can declare the loop counter variable directly inside the `for` loop, making it **local** to the loop.

```js
for (let i = 1; i < 10; i++) {
    const newResult = `${i} x ${i} = ${i * i}`;
    console.log(newResult);  // Logs the square of each number
}
```

In this example, each iteration calculates and prints the square of `i`.

---

### **Example 3: Looping Over an Array (`for...of` vs `for`)**

#### **Using `for...of` Loop:**

```js
const cats = ["Lepord", "Jaguar", "Tiger", "Lion"];

for (const cat of cats) {
    console.log(cat);
}
// Output: Lepord, Jaguar, Tiger, Lion
```

The `for...of` loop is a simpler way to iterate over arrays (or other iterable objects).

#### **Using Traditional `for` Loop:**

```js
for (let i = 0; i < cats.length; i++) {
    console.log(cats[i]);
}
// Output: Lepord, Jaguar, Tiger, Lion
```

This is the traditional `for` loop, which uses an index to access array elements.

---

### **Example 4: Adding "and" Before the Last Item in an Array**

```js
const cats = ["Lepord", "Jaguar", "Tiger", "Lion"];
let myFavouriteCats = "My cats are called ";

for (let i = 0; i < cats.length; i++) {
    if (i === cats.length - 1) {
        myFavouriteCats += `and ${cats[i]}.`;  // Add "and" before last cat
    } else {
        myFavouriteCats += `${cats[i]}, `;
    }
}
console.log(myFavouriteCats);
// Output: "My cats are called Lepord, Jaguar, Tiger, and Lion."
```

This example demonstrates how to add "and" before the last item in a list.

---

### **Updating Counter Variables**

You can update the loop counter using shorthand operators:

```js
counter = counter + 1;    // equivalent to counter++;
counter -= 1;             // equivalent to counter--;
result *= 2;              // equivalent to result = result * 2;
```

These are more concise ways to update variables in loops.

---

### **Skipping Parts of the `for` Loop**

Any part of the `for` loop (initializer, condition, or final-expression) can be skipped:

**Skipping Initializer:**
```js
let i = 0;  // Initializer outside the loop
for (; i < 3; i++) {
    alert(i);  // Output: 0, 1, 2
}
```

**Skipping Final-Expression:**
```js
let i = 0;
for (; i < 3;) {
    alert(i);  // Output: 0, 1, 2
    i++;  // Incrementing inside the loop body
}
```

In these examples, you can omit parts of the loop declaration, but the loop still functions as expected.

---

### **Chessboard Pattern**

To print a chessboard pattern, you can use a nested loop:

```js
let size = 8;  // Chessboard size (8x8)
let board = "";  // Start with an empty string

for (let y = 0; y < size; y++) {
    for (let x = 0; x < size; x++) {
        if ((x + y) % 2 === 0) {
            board += " ";  // White square
        } else {
            board += "#";  // Black square
        }
    }
    board += "\n";  // Newline after each row
}

console.log(board);
```

This code generates an 8x8 chessboard pattern using a combination of two loops. Each square is determined by whether the sum of `x` and `y` is even or odd.

---

### **Summary**

- **`for` loop**: Ideal when you know the exact number of iterations or need to iterate over a collection.
- **Shorthand updates**: Use `++`, `--`, and `+=` for more concise code.
- **Skipping loop parts**: You can omit parts of the loop (initializer, condition, final-expression) if needed.
- **Nested loops**: Useful for tasks like printing patterns (e.g., chessboard).
