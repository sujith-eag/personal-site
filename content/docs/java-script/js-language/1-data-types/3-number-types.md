---
title: "Number Types"
description: ""
summary: ""
date: 2024-11-07T14:43:35+05:30
lastmod: 2024-11-07T14:43:35+05:30
draft: false
weight: 603
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---


In JavaScript, there are two types of numbers: **Regular Numbers** and **BigInt Numbers**.

## Types of Numbers

### Regular Numbers

**Regular Numbers** are stored in **64-bit** memory, with some bits representing the sign (positive or negative), and others representing the value of the number (including the decimal point for floating-point numbers).

### BigInt Numbers

A **BigInt** is a numeric type that can represent **integers of arbitrary length**, i.e., numbers larger than the limit of the regular `number` type (which is `2^53 - 1`). This makes **BigInt** useful for working with very large integers, such as cryptography or certain scientific calculations.

A **BigInt** value is created by appending an `n` to the end of an integer:
```js
const bigInt = 12345553213423423424241313322442324234342n;
// The 'n' at the end indicates it's a BigInt
```

### Converting to Number

You can convert a value to a regular `number` using the `Number()` function. It will convert the value to a number if it’s possible:
```js
const myString = '123';
const myNum = Number(myString);
console.log(typeof myNum);  // "number"
```

---

## Special Numeric Values

JavaScript has several special numeric values:

- **Infinity**: Represents an infinitely large number. It results from dividing a positive number by zero.
  ```js
  alert(1 / 0);  // Infinity
  ```

- **-Infinity**: Represents an infinitely large negative number.
  ```js
  alert(-1 / 0); // -Infinity
  ```

- **NaN** (Not a Number): Indicates an invalid or undefined result of a mathematical operation.
  ```js
  alert(0 / 0);  // NaN
  alert("hello" * 2);  // NaN
  ```
`NaN` is **not equal** to itself (`NaN !== NaN`), which is a unique property in JavaScript.
If `NaN` appears in an expression, the entire result will likely be `NaN`.

---

## Arithmetic Operators

JavaScript provides several operators for performing arithmetic operations on numbers:

```js
+   // Addition
-   // Subtraction
*   // Multiplication
/   // Division
%   // Modulo (Remainder) Operation
**  // Exponentiation (Power)
```

### Arithmetic Behavior

- **Division by Zero**: When dividing by zero, JavaScript returns **Infinity** or **-Infinity** depending on the sign.
  ```js
  alert(1 / 0);  // Infinity
  alert(-1 / 0); // -Infinity
  ```

- **NaN (Not a Number)**: If an operation results in a value that cannot be calculated, it returns `NaN` (Not a Number). This can happen in operations like division by zero, or invalid operations involving non-numeric values.
  ```js
  alert("not a number" / 2);  // NaN
  alert(NaN + 1);  // NaN
  ```

- **Special Cases Involving NaN**:
  - Any expression involving `NaN` will propagate `NaN` as the result:
    ```js
    0 / 0;           // NaN
    Infinity - Infinity;  // NaN
    ```

- **NaN Propagation**:
  If `NaN` is part of an expression, the result will also be `NaN`, unless the operation is **NaN raised to the power of 0**, which is **1**.
  ```js
  NaN ** 0;   // 1
  ```
  
---

## Ways to Write Numbers in JavaScript

JavaScript provides different ways to represent numbers in a readable and compact form:

### 1. Using Underscores (`_`) as Separators
You can use underscores to improve the readability of large numbers. These underscores are ignored during execution.

```js
let billion = 1_000_000_000; // 1 billion
```

### 2. Using Scientific Notation (`e`)
You can represent numbers using exponential (scientific) notation with the `e` character, where `e` represents "times 10 raised to the power of."

- Positive exponent:
  ```js
  let billion = 1e9;  // 1e9 is equal to 1,000,000,000 (1 billion)
  alert(7.3e9);       // 7.3e9 is 7.3 billion
  ```

- Negative exponent:
  ```js
  let mcs = 1e-6;  // 1e-6 is 0.000001
  alert(mcs);      // 0.000001
  // five zeroes to left from 1
  ```

### 3. Standard Notation (Without Exponent)
A number can be written in its standard form without any scientific notation.

```js
let billion = 1000000000;  // 1 billion
```

---
