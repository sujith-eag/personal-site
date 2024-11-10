---
title: "do-while Loop"
description: ""
summary: ""
date: 2024-11-07T20:50:37+05:30
lastmod: 2024-11-07T20:50:37+05:30
draft: false
weight: 330
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---


## **`while` and `do...while` Loops**

### **1. `while` Loop**

The `while` loop executes the code inside its body **as long as** the condition evaluates to **truthy**. The condition is checked **before** each iteration.

```js
initializer / counter variable;
while (condition) {
    // code to run in the loop body
    final-expression;  // increment or other operation
}
```

A single execution of the loop body is called an **iteration**.

```js
let number = 0;

while (number <= 12) {
    console.log(number);
    number = number + 2;  // Increment by 2
}
// Output: 0, 2, 4, 6, 8, 10, 12
```

```js
let result = 1;
let counter = 0;

while (counter < 10) {
    result = 2 * result;  // Multiply result by 2 each time
    counter = counter + 1;  // Increment counter
}
console.log(result);  // Output: 1024 (2^10)
```

#### **Shortened `while` condition:**

shorter way to write `while (i != 0)`   is  `while(i)`
If the condition is just a variable (e.g., `i`), it can be simplified:

```js
let i = 3;
while (i) {
    alert(i);  // Alert the current value of i
    i--;  // Decrement i
}
// Output: Alerts 3, 2, 1, then stops as i becomes 0
```

```js
let hash = "";  // Start with an empty string

while (hash.length < 7) {
    hash += "#";  // Append one "#" to the string
    console.log(hash);  // Output the current string
}
// Output:
// "#"
// "##"
// "###"
// "####"
// "#####"
// "######"
// "#######"
```

---

### **2. `do...while` Loop**

The `do...while` loop guarantees **at least one execution** of its body. It first executes the code block, then checks the condition. If the condition is truthy, it continues; otherwise, it stops.

```js
initializer / counter variable;
do {
    // code to run in the loop body
    final-expression;  // increment or other operation
} while (condition);
```

```js
let i = 0;
do {
    alert(i);  // Alert the current value of i
    i++;  // Increment i
} while (i < 3);
// Output: Alerts 0, 1, 2
```

**Ensuring user input:**
```js
let yourName;

do {
    yourName = prompt("Who are you?");  // Prompt the user for their name
} while (!yourName);  // Continue if the input is falsy (e.g., empty string)
console.log("Hello " + yourName);  // Output: "Hello <user's name>"
```

In this example, the program will **force** the user to enter a name that isn’t an empty string or `null`. The `!` operator converts the value to a Boolean, and **any non-empty string** is considered **truthy**.

---

### **Indenting Code**

Although indentation is not required in JavaScript, **proper indentation** makes the code more **readable** for humans. Even though JavaScript can run code in a single line, using proper indentation is a **best practice** to maintain clarity.

**Without indentation:**
```js
if (true != false) {console.log("That makes sense."); if (1 < 2) {console.log("No surprise there.");}}
```

**With proper indentation:**
```js
if (true != false) {
    console.log("That makes sense.");
    if (1 < 2) {
        console.log("No surprise there.");
    }
}
```

This structure makes the logic clearer and helps other developers (or your future self) easily understand your code.

---

### **Summary**

- **`while` loop**: Checks the condition before executing the code block. It runs as long as the condition is **truthy**.
- **`do...while` loop**: Executes the code block **at least once** and checks the condition **after** execution.
- **Indentation**: While optional, proper indentation makes code more readable and maintainable.

