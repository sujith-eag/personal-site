---
title: "if, else"
description: ""
summary: ""
date: 2024-11-07T20:46:23+05:30
lastmod: 2024-11-07T20:46:23+05:30
draft: false
weight: 321
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---


## **Conditional Execution / Branching**

### **`if()` Statement**

The `if` statement allows you to execute a block of code only if a specified condition is true. The condition is typically a Boolean expression that evaluates to either `true` or `false`.

```js
if (condition) {
    // Code to execute if condition is true
}
```

```js
let hour = 14; // Example hour value
let greeting;

if (hour < 18) {
    greeting = "Good Day";
}

console.log(greeting); // Output: Good Day
```

```js
let theNumber = Number(prompt("Pick a number"));

if (!Number.isNaN(theNumber)) {
    console.log("Your number is the square root of " + (theNumber * theNumber));
}
```
- `Number()` converts the user input to a number. If the input is not a valid number (i.e., `NaN`).
- `Number.isNaN()` is a standard function that returns true only if the argument is `NaN`. 
- The condition `!Number.isNaN(theNumber)` ensures that the block is executed only if the value is a valid number. So 'unless `theNumber` is not-a-number, do this'

> **Note**: `Number.isNaN()` is more reliable than `isNaN()` because it specifically checks for `NaN` values, whereas `isNaN()` can produce unexpected results for non-numeric strings.

#### Block vs Single Statement
When there’s only one statement to execute after `if`, curly braces `{}` can be omitted:
```js
if (1 + 1 === 2) console.log("It's true");
```
However, it's considered good practice to always use curly braces for clarity and to avoid errors when adding additional statements.

---

### **`else` Clause**

The `else` clause is used to specify what should happen if the `if` condition evaluates to `false`.

```js
if (condition) {
    // Code if condition is true
} else {
    // Code if condition is false
}
```

```js
let theNumber = Number(prompt("Pick a number"));

if (!Number.isNaN(theNumber)) {
    console.log("Your number is the square root of " + (theNumber * theNumber));
} else {
    console.log("Why didn't you give me a number?");
}
```

---

### **`else if` Statement**

The `else if` statement is used when you have multiple conditions to check. It allows you to chain multiple conditions together.

```js
if (condition1) {
    // Code for condition1
} else if (condition2) {
    // Code for condition2
} else {
    // Code if none of the above conditions are true
}
```

```js
let num = Number(prompt("Pick a number"));

if (num < 10) {
    console.log("Small");
} else if (num < 100) {
    console.log("Medium");
} else {
    console.log("Large");
}
```

> **Note**: If `num` is less than 10, it prints `"Small"` and does not check further conditions. The evaluation stops after the first `true` condition.

---

## **Common Pitfalls**

**String and Number Conversion**

It’s important to handle type conversion carefully, especially when working with user inputs. 
For example, the `Number()` function can produce unexpected results if the user enters something that isn’t a valid number.


> **Tip**: Always ensure to check that the input is valid before performing mathematical operations.

---

#### **FizzBuzz**

```js
for (let number = 1; number <= 100; number++) {
    if ((number % 3) === 0 && (number % 5) === 0) {
        console.log("fizzbuzz");
    } else if (number % 5 === 0) {
        console.log("buzz");
    } else if (number % 3 === 0) {
        console.log("fizz");
    } else {
        console.log(number);
    }
}
```


---
