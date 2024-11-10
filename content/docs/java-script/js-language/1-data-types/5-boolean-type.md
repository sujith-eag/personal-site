---
title: "Boolean Type"
description: ""
summary: ""
date: 2024-11-07T14:46:45+05:30
lastmod: 2024-11-07T14:46:45+05:30
draft: false
weight: 308
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---



Booleans are a primitive data type with only two possible values: `true` and `false`. They are commonly used to represent binary states such as "yes/no" or "on/off".

```js
let nameFieldChecked = true;
let ageFieldChecked = false;
```

### Comparisons (`==`, `!=`, `>=`, `<=`)

Boolean values often come as the result of comparison operations.

```js
console.log(3 > 2);   // true
console.log(2 > 3);   // false
```

#### String Comparison

When comparing strings, JavaScript compares their Unicode values from left to right, one character at a time. This means that **uppercase letters** are considered "less than" **lowercase letters** (because their Unicode values are smaller), and **non-alphabetical characters** are also considered.

```js
alert('z' > 'A');  // true (uppercase 'A' < lowercase 'z')
alert('Glow' > 'Glee');  // true ('Glow' is greater than 'Glee' because 'o' > 'e')
alert('Bee' > 'Be');  // true ('Bee' is longer than 'Be', and longer strings are greater)
alert("Aardvark" < "Zoroaster"); // true ('A' < 'Z' because of Unicode comparison)
```

JavaScript compares strings character by character based on their **Unicode values**. Here's the step-by-step process:

1. Compare the first character.
2. If they are the same, move to the next character and repeat.
3. The first difference found determines the result.

---
[[7_type_conversions]]


### Strict Comparison (`===`, `!==`)

Regular check `==` cannot differentiate `0` from `fasle`.
For strict equality comparisons, JavaScript offers the `===` (strict equality) and `!==` (strict inequality) operators. These operators **do not perform type conversion**.


```js
// Regular equality comparison (performs type conversion)
alert(0 == false); // true (0 is falsy, so it converts to false)
alert("" == false); // true (empty string is falsy, so it converts to false)

// Strict equality comparison (does not perform type conversion)
alert("" === false); // false ("" is a string, false is a boolean)
alert(0 === false); // false (0 is a number, false is a boolean)
```

When we use `===` or `!==`, JavaScript checks both the **value and the type**, so there's no unexpected type conversion.

---

### Comparison with `null` & `undefined`

- **`null`** and **`undefined`** are special values in JavaScript. They behave differently when used with comparison operators.
- **Equality (`==`)**: `null` and `undefined` are considered equal to each other, but not equal to any other values.
- **Strict Equality (`===`)**: `null` is not equal to `undefined`, because they are different types.

```js
alert(null == undefined);    // true (only null == undefined is true)
alert(null === undefined);   // false (strict comparison)

alert(null == 0);            // false (null is not equal to 0)
alert(null == false);        // false (null is not equal to false)
```

#### Testing for a valid value:

To check if a variable is not `null` or `undefined`, use the `==` or `!=` operators. This can be useful to determine if a value has been set.

```js
let value = null;

if (value == null) {
    alert("Value is null or undefined");
}
```

---

### Math Comparisons (`>`, `<`, `<=`, `>=`)

When performing mathematical comparisons involving `null` or `undefined`, JavaScript performs type coercion:

- **`null` becomes `0`** when compared mathematically.
- **`undefined` becomes `NaN`** (Not-a-Number), which is **never equal to any number**.

```js
alert(null < 0);    // false (null is treated as 0)
alert(null == 0);   // false (null is not equal to 0)
alert(null >= 0);   // true (null is treated as 0)

alert(undefined == 0);  // false (undefined is not equal to 0)
alert(undefined < 0);   // false (undefined becomes NaN, which is not less than 0)
alert(undefined >= 0);  // false (undefined becomes NaN, which is not greater than or equal to 0)
```

### Summary:

| Comparison          | `==` Behavior                      | `===` Behavior                         |
|---------------------|------------------------------------|----------------------------------------|
| **`null == undefined`** | true                               | false                                  |
| **`null == 0`**         | false                              | false                                  |
| **`undefined == 0`**    | false                              | false                                  |
| **`null < 0`**          | false                              | -                                      |
| **`null >= 0`**         | true                               | -                                      |
| **`undefined < 0`**     | false                              | -                                      |
| **`undefined >= 0`**    | false                              | -                                      |
