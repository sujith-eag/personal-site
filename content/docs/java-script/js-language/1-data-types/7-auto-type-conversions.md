---
title: "Auto Type Conversions"
description: ""
summary: ""
date: 2024-11-07T14:47:36+05:30
lastmod: 2024-11-07T14:47:36+05:30
draft: false
weight: 310
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---


JavaScript automatically converts values between different types when necessary. This is commonly known as **type coercion**. It happens in a variety of scenarios, such as when performing mathematical operations or comparisons.

#### Automatic Type Conversion:

1. **Comparison with Different Types**:
   JavaScript will convert values to the same type when doing comparisons, which can sometimes produce unexpected results.

   ```js
   alert('2' > 1);  // true, because '2' is automatically converted to a number
   alert('01' == 1);  // true, because '01' is automatically converted to 1 (string to number)
   
   alert(true == 1);  // true, because 'true' is converted to 1
   alert(false == 0);  // true, because 'false' is converted to 0
   ```

2. **Boolean Conversion**:
   When converting values to `Boolean`, JavaScript considers certain values as **falsy** (which become `false`) and others as **truthy** (which become `true`).

   **Falsy values**:
   - `0`
   - `""` (empty string)
   - `null`
   - `undefined`
   - `NaN`

   **Truthy values**:
   - Non-zero numbers
   - Non-empty strings
   - Objects, arrays, functions, etc.

   ```js
   alert(Boolean(1));     // true
   alert(Boolean(0));     // false
   alert(Boolean("0"));     // true
   alert(Boolean(""));    // false
   alert(Boolean("Hello"));// true
   alert(Boolean(null));  // false
   alert(Boolean([]));    // true (empty array is truthy)
   ```

---

### Explicit Type Conversion

There are situations where you might need to explicitly convert values between types, which can be done using functions like `String()`, `Number()`, and `Boolean()`.

#### String Conversion

To convert a value to a string explicitly, you can use the `String()` function.

```js
let value = true;
value = String(value);  // "true"
alert(typeof value);  // "string"
```

Alternatively, you can use string concatenation to convert any value to a string:

```js
let number = 123;
let str = number + ""; // converts 123 to "123"
```

#### Numeric Conversion

When performing mathematical operations, JavaScript automatically converts strings to numbers if they represent valid numeric values. For explicit conversion, you can use the `Number()` function.

```js
let str = "123";
let num = Number(str);
alert(num);  // 123
alert(typeof num);  // "number"
```

If the value is not a valid number, `Number()` will return `NaN`.

```js
let str = "Hello";
let num = Number(str);
alert(num);  // NaN
```

Common automatic conversions:
- `undefined` becomes `NaN`
- `null` becomes `0`
- Strings containing a valid numeric value are converted to numbers (e.g., `"123"` becomes `123`).
- Non-numeric strings become `NaN`.

#### Numeric Conversion with Unary `+`

The unary `+` operator is a shorthand for converting a value to a number, similar to `Number()`. 

```js
alert(+true);   // 1
alert(+false);  // 0
alert(+"");     // 0
alert(+undefined); // NaN
```

In the case of strings that are numbers, it works like `Number()`:

```js
let apple = "2";
let orange = "3";

alert(apple + orange);    // "23" (concatenation, as both are strings)
alert(+apple + +orange);  // 5 (conversion to number, then addition)
```

---

### Summary of Common Type Conversions

- **String Conversion**: 
  - `String(value)` or concatenating with an empty string (`value + ""`) will convert any value to a string.

- **Numeric Conversion**: 
  - `Number(value)` or unary `+` will convert values to numbers. If the value is not a valid number, it will return `NaN`.
  
- **Boolean Conversion**: 
  - `Boolean(value)` converts any value to `true` or `false`, based on its truthiness.

#### Common Conversion Examples:

```js
let num = "100";      // string
let bool = "false";   // string

alert(Number(num));   // 100 (string to number)
alert(Boolean(num));  // true (non-empty string is truthy)
alert(String(num));   // "100" (number to string)

alert(Number(bool));  // NaN (string "false" is not a valid number)
alert(Boolean(bool)); // true (non-empty string is truthy)
```

