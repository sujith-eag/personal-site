---
title: "JS - 02.15 - break-continue-label"
description: ""
summary: ""
date: 2024-11-07T20:52:03+05:30
lastmod: 2024-11-07T20:52:03+05:30
draft: false
weight: 370
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---


## **`break` Statement**

The `break` statement is used to **immediately exit** from a loop, switch statement, or even a `try...catch` block. When encountered, the loop or block is terminated, and execution continues with the code after the loop.

**`break` in Loops:**
```js
for (let current = 20; current <= 30; current++) {
  if (current % 7 == 0) {
    console.log(current);  // Outputs 21
    break;  // Exit the loop
  }
}
```
- The loop starts from `current = 20` and increments by 1.
- It checks if the number is divisible by 7.
- When `21` is found (the first number greater than 20 and divisible by 7), it prints `21` and exits the loop with `break`.

```js
let sum = 0;

while(true) {
	let value = +prompt("Enter a number", '');
	if (!value) break;  // break if empty line
	sum += value;
} alert( 'sum: ' + sum );
```

---

## **`continue` Statement**

The `continue` statement is used to **skip the current iteration** of a loop and proceed with the next iteration. The rest of the code inside the loop body is skipped for that iteration.

**`continue` in Loops:**
```js
for (let i = 0; i < 10; i++) {
  if (i % 2 === 0) continue;  // Skip even numbers
  alert(i);  // Outputs: 1, 3, 5, 7, 9
}
```
- The loop runs from 0 to 9.
- The `continue` statement skips the even numbers (when `i % 2 === 0`), so the `alert(i)` is only executed for odd numbers.

> **Note:** `continue` cannot be used in ternary (`? :`) operators. It is only applicable within loops.

---

## **Labels for `break` and `continue`**

When we need to break or continue **multiple loops** at once, **labels** come in handy.

A label is an **identifier** followed by a colon (`:`) before a loop.   
A label is a way to name a specific loop in order to control the flow of execution in nested loops.  

```js
labelName: for (...){
	...
	}

labelName:
for (...){
	...
	}
```


### **Using `break` with Labels:**

To break out of a **nested loop** and jump directly to the code after the outer loop, you can use a label with `break`.

The `break labelName` breaks out of the named loop.
`break` directive must be inside the code block.

```js
label: {
	// ...
	break label; 
	// ...
}
```

```js
outer:  // Label for the outer loop
for (let i = 0; i < 3; i++) {
  for (let j = 0; j < 3; j++) {
    let input = prompt(`Value at coords (${i},${j})`, '');
    if (!input) break outer;  // Exit both loops if input is empty or canceled
  }
}
alert('Done!');
```

- In this example, if the user enters an empty string or cancels the prompt, the `break outer` will stop both the inner and outer loops, and the message `'Done!'` will be displayed.

### **Using `continue` with Labels:**

Similarly, you can use `continue` with labels to **skip to the next iteration** of a labeled loop.

```js
outer:  // Label for the outer loop
for (let i = 0; i < 3; i++) {
  for (let j = 0; j < 3; j++) {
    if (i === 1 && j === 1) continue outer;  // Skip the rest of the outer loop for i = 1, j = 1
    console.log(`i=${i}, j=${j}`);
  }
}
```

- This example uses `continue outer` to skip the remaining part of the outer loop when `i === 1 && j === 1`, causing the program to jump directly to the next iteration of the outer loop.

### **Using `break` and `continue` Inside Code Blocks:**

You can also use `break` and `continue` inside **blocks** of code by labeling the block itself. This is useful when you need to break out of specific code sections rather than the entire loop.

```js
label: {
  // Some code before
  console.log('Before break');
  break label;  // Exit the block
  console.log('After break');  // This won't run
}
```

- Here, the `break label` exits the block of code before the `console.log('After break')` line is executed.

---

## **Summary:**

- **`break`**: Exits a loop (or switch statement, etc.) immediately, regardless of the loop's condition.
- **`continue`**: Skips the current iteration of a loop and moves to the next iteration.
- **Labels**: Used to control the flow of execution in nested loops. Labels can be applied to both `break` and `continue` to exit or continue multiple loops at once.
  - `break label`: Breaks out of the labeled loop.
  - `continue label`: Skips to the next iteration of the labeled loop.
