---
title: "Variables"
description: ""
summary: ""
date: 2024-11-07T14:42:23+05:30
lastmod: 2024-11-07T14:42:23+05:30
draft: false
weight: 301
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---


In JavaScript, *bindings* (also known as *variables*) are used to maintain the internal state and store values.

## Rules for naming variables:

- **No keywords or reserved words** (e.g., `if`, `for`, `function`, etc.).
- **Cannot start with a number** (e.g., `123variable` is invalid).
- **No spaces or hyphens (`-`)**.
- **No special characters**, except for `$` and `_`.

---

## Naming Variables Properly

A good variable name should be **descriptive** and **easy to understand**. It should clearly represent the value or data that it holds.

- **Use `camelCase`** for variable names (e.g., `userName`, `squareRoot`).
- Choose **human-readable names** that describe the purpose of the variable (e.g., `currentUser`, `shoppingCart`).
- **Avoid abbreviations or short names** like `a`, `b`, and `c`, unless it's clear what they represent.
- **Be descriptive** but also **concise**. For example, avoid overly generic names like `data` or `value`.
- If referring to a user in your application, use names like `currentUser` or `newUser` instead of vague terms like `currentVisitor` or `newManInTown`.
- lazy programmers who, instead of declaring new variables, tend to reuse existing ones. like boxes into which people throw different things without changing their stickers. What’s inside the box now? Who knows?. Such programmers save a little bit on variable declaration but lose ten times more on debugging.

```js
// Descriptive variable names
let userName = 'Jane Doe';
let totalPrice = 100.50;
```

---

## Comments in JavaScript

- **Single-line comment** `//`
- **Multi-line comment** `/* ... */`
  ```js
  // This is a single-line comment
  let x = 5; // Inline comment
  
  /* This is a multi-line comment
     that spans across multiple lines */
  let y = 10;
  ```

---

## `var` (Old Way of Declaring Variables)

The `var` keyword was previously used to declare variables in JavaScript, but it is now considered outdated due to some issues with variable scoping. As such, its usage is discouraged in favor of `let` and `const`.

---

## `let` for Declaring Variables

The `let` keyword is used to declare variables that can be **reassigned** later.

```js
let message; // Declaring a variable
message = 'Hello'; // Assigning a value

let caught = 5 * 5; // Declaring and assigning a value in one line
```

- The `let` keyword indicates that a new variable is being defined.
- A variable declared with `let` can be reassigned to a different value after its initial assignment.

### Reassigning Variables:
The binding is not tied to that value, it can be disconnected from current value and have them point to a new one;
```js
let mood = 'light';  // Initial assignment
mood = 'dark';       // Reassigning the value
```

- **Important**: Once a variable is declared with `let`, it can be reassigned, but it does **not** need `let` for the reassignment. You only use `let` when declaring the variable for the first time.

### Defining Multiple Variables:
You can define multiple variables in a single `let` declaration, separating them with commas.

```js
let one = 1, two = 2;  // Multiple variables in one line

let user = 'John', age = 25, message = 'Hello';  // Another example

// Alternatively, you can split the declarations across multiple lines:
let user = 'John'
    , age = 25
    , message = 'Hello';
```

---

## `const` for Constants

The `const` keyword is used to declare **constants**. Once a value is assigned to a `const` variable, it **cannot be reassigned**. Attempting to change the value of a constant results in an error.

```js
const pi = 3.142;          // Constant value
const myBirthday = '18.04.1999';  // Another constant
```
A constant binding points to the same value as long as it lives. **Constants cannot be reassigned** once their initial value is set.

### Constants and Runtime Values:
Some constants may be known beforehand (e.g., `pi`), while others are calculated at runtime but remain unchanged after their initial assignment.

```js
const pageLoadTime = /* Time taken for a webpage to load */;

const age = calculateAge(myBirthday); // Value computed at runtime
```

---

## Uppercase Constants

A common convention for constants that represent values known before execution is to use **uppercase letters** with underscores (`_`) to separate words. This makes them easier to identify in your code.

```js
const COLOR_RED = "#F00";
const COLOR_GREEN = "#0F0";
const COLOR_BLUE = "#00F";
const COLOR_ORANGE = "#FF7F00";

// Using the constant to set a variable
let color = COLOR_ORANGE;
alert(color);  // Outputs the color value
```

Redone on #07oct24 

---
