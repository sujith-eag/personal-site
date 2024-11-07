---
title: "switch-case"
description: ""
summary: ""
date: 2024-11-07T20:47:19+05:30
lastmod: 2024-11-07T20:47:19+05:30
draft: false
weight: 702
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---


## **`switch` Statements**

The `switch` statement is a more concise and readable way to handle multiple conditional checks based on a single value. It is often used as an alternative to multiple `if...else if` statements, particularly when you have many conditions to check against a single expression.

```js
switch (expression) {
    case value1:
        // code to execute if expression === value1
        break;
    case value2:
        // code to execute if expression === value2
        break;
    default:
        // code to execute if no cases match
        break;
}
```

* Switch takes single ***expression*** or ***value*** as an input, and then compares with several ***case values*** until they find one that matches that value.
* When the equality is found `switch` starts executing, starting from the corresponding`case`.
* Execution continues till the nearest `break`, or end of `switch`.
* As many number of `case` can be put inside the block opened by `switch`
* if no case is matched, then `default` code is executed if exists.
* If there is no `break` ***then the execution continues with the next `case` without any checks***

> **Note**: `switch` statements use strict equality (`===`), meaning both value and type must match. `'3' !== 3`, so a string `'3'` would not match the number `3`.

---

### **Basic `switch` Statement**

```js
let a = 2 + 2;

switch (a) {
    case 3:
        alert('Too small');
        break;
    case 4:
        alert('Exactly');
        break;
    default:
        alert('I don’t know such values');
}
```
- **Explanation**: 
    - The variable `a` is evaluated as `4`.
    - The `switch` checks the cases:
      - It doesn’t match `case 3`, so it moves to the next case.
      - It matches `case 4`, so the corresponding code `alert('Exactly')` is executed.
    - The `break` statement prevents further case evaluation, exiting the `switch` block.

---

### **Weather Application**

```js
switch (prompt("What is the weather like?")) {
    case "rainy":
        console.log("Remember to bring an umbrella.");
        break;
    case "sunny":
        console.log("Dress lightly.");
        break;
    case "cloudy":
        console.log("Go outside.");
        break;
    default:
        console.log("Unknown weather type!");
        break;
}
```

---

### **Fall-through Behavior**

If a `break` statement is not included in a `case`, JavaScript will execute the code for that `case`, but then continue executing subsequent `case` blocks without further checks until a `break` or the end of the `switch` is reached. This is called **fall-through** behavior.

> **Note**: Fall-through can be useful when multiple `case` values should trigger the same block of code. However, it is generally considered good practice to be explicit with `break` statements to avoid unintended fall-through.

---

### **Grouping `case` Blocks**

You can group multiple `case` values that should run the same code. This allows you to combine cases that share identical behavior.

```js
let a = 3;

switch(a) {
    case 4:
        alert('Right!');
        break;

    case 3:
    case 5:
        alert('Wrong');
        alert("Why don't you take a math class?");
        break;

    default:
        alert('The result is strange.');
}
```

---

### **Key Points to Remember**

1. **`switch` uses strict equality (`===`)**: Ensure that both the value and type match. For example, `'3' !== 3`.
2. **`break` is optional**: Without it, execution will "fall through" to the next `case`.
3. **`default` is optional**: It provides a fallback when no cases match.
4. **Multiple `case` values can share the same block**: You can group cases that should execute the same code.
5. **`switch` is generally more readable**: When dealing with many conditions based on a single value, `switch` can improve readability compared to long chains of `if...else` statements.

---
