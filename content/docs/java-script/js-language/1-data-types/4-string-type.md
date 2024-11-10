---
title: "String Type"
description: ""
summary: ""
date: 2024-11-07T14:44:54+05:30
lastmod: 2024-11-07T14:44:54+05:30
draft: false
weight: 305
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---


A **string** is a sequence of text characters enclosed in either single quotes (`' '`), double quotes (`" "`), or backticks (`` ` ``). Strings are one of the most commonly used data types in JavaScript.

### Basic String Declaration
```js
let str = "Hello";               // Double quotes
let str1 = 'Single quotes are ok too'; // Single quotes

let phrase = `Backticks allow embedding expressions like ${str}`; // Template literal (backticks)

let combined = `${str} ${phrase}`;  // String concatenation using template literals

alert(`1 + 2 = ${sum(1, 2)}.`);  // Using template literals to embed function results
```

### Template Literals

Template literals are enclosed by backticks (`` ` ``) and allow embedding of expressions inside `${}`. These expressions are evaluated, converted to strings, and inserted into the string.

```js
let name = "John";
console.log(`Hello, ${name}`); // Hello, John

console.log(`The result of 1 + 2 is ${1 + 2}`); // The result of 1 + 2 is 3
```

Template literals can do much more:
- **Multiline strings**: Unlike regular strings enclosed in quotes, template literals can span multiple lines without the need for escape characters.
  
  ```js
  let multiline = `This is a string
  that spans multiple lines.`;
  ```

- **Embedded expressions**: As shown above, you can embed variables, calculations, and even function calls inside `${}`.

  ```js
  let a = 5, b = 10;
  let result = `${a} + ${b} = ${a + b}`; // "5 + 10 = 15"
  ```

### Escaping Characters

Escaping characters allows you to treat characters as literal text when needed. This is useful for special characters such as quotes, newlines, or backslashes that might otherwise have special meaning in JavaScript.

- **Escape sequences**:
  - `\n`: Newline character
  - `\t`: Tab character
  - `\\`: Backslash
  - `\'`: Single quote
  - `\"`: Double quote

  ```js
  First line and\nThis is second line
  A newline character is "\n"
  A newline character is \"\\n\"

  let message = "First line\nSecond line";
  console.log(message);  // First line (new line) Second line
  
  const quote = "I\'ve got no right to take my place";  // Escape single quote
  console.log(quote);  // I've got no right to take my place
  ```

### Concatenation

Concatenation is the process of combining two or more strings into one string. You can use the `+` operator to concatenate strings.

```js
let first = "Hello";
let second = "World";
let combined = first + " " + second;  // "Hello World"

let name = "con" + "cat" + "e" + "nate"
```

If any of the operands is a string, the other will be converted to a string and concatenated.
```js
alert('1' + 2);    // "12" (number 2 converted to string)
alert(2 + "1");    // "21" (number 2 converted to string)
```

JavaScript concatenates strings from **left to right**:
```js
alert(2 + 1 + "1");    // "31" (2 + 1 = 3, then "3" + "1" = "31")
alert("2" + 1 + 1);    // "211" ("2" + 1 = "21", then "21" + 1 = "211")
```

All other math operators try to convert string to number and do the operation but not `+`

The `String()` function can explicitly convert other data types to strings.
```js
let number = 123;
let str = String(number);   // Converts the number to a string
console.log(str);           // "123"
```
