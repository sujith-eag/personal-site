---
title: "JS - 01.02 - Values and Types"
description: ""
summary: ""
date: 2024-11-07T14:43:05+05:30
lastmod: 2024-11-07T14:43:05+05:30
draft: false
weight: 302
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---


In JavaScript, **values** are chunks of information.  
Each value has a specific **type** that defines how it behaves and interacts with other values.  

There are eight basic types in JavaScript:

```js
number
bigint
string
boolean
null
undefined
object
symbol
```

---

## Types of Values

### Primitive Types

Primitive types can hold **only one value** at a time, and they are **immutable** (i.e., they can't be changed). These types include:

**String**: Represents a sequence of characters. 
`let name = "Eag";`

**Number**: Represents both integer and floating-point numbers. JavaScript doesn't distinguish between them — all numbers are of the same type.
`let age = 30;`

**Boolean**: Represents a true or false value. 
`let isApproved = false;`

**Undefined**: Indicates that a variable has been declared but not assigned a value. 
`let firstName = undefined; // Value not initialized`

**Null**: Represents an intentionally empty or non-existent value. 
`let lastName = null; // Value intentionally left blank`

**BigInt**: Used to represent very large integers that are beyond the limit of the standard `Number` type.
`let largeNumber = 1234567890123456789012345678901234567890n; // BigInt`

**Symbol**: Represents a unique and immutable value, often used to create unique identifiers.
`let sym = Symbol("id");`


### Reference Types

Reference types can store **collections of data** and **more complex entities**. These include:

- **Object**: Can hold collections of data, including properties and methods.
  ` let user = { name: "John", age: 30 };`

- **Array**: A special type of object for storing ordered collections of values.  
	 `let numbers = [1, 2, 3];`

- **Function**: A special type of object used to define callable blocks of code.
```js
function greet() {
console.log("Hello!");
}
```

- **`symbol`**: Used to create unique identifiers, ensuring no collisions in object properties.

---

### 'typeof' Operator

The `typeof` operator is used to determine the **type** of a value or variable. It returns a string indicating the type of the operand.  
The type can change based on the value it holds.

```js
typeof 0              // "number"
typeof 10n            // "bigint"
typeof 'foo'          // "string"
typeof Symbol("id")   // "symbol"

typeof Math           // "object"  (Math is an object)
typeof null           // "object"  (This is a known quirk in JavaScript)
typeof alert          // "function" (Functions are objects)
```

> **Note**: The behavior of `typeof` with `null` is incorrect — it returns `"object"`, which is a **known issue** in JavaScript, but it's kept for compatibility reasons. `null` is not an object; it is its own unique type.


---

## Methods of Primitives

Methods are part of objects.  While primitives (like strings, numbers, booleans) are not objects by themselves, JavaScript allows them to **behave like objects** in certain situations. This is done through **"wrapper objects"** that temporarily convert the primitive to an object for method access.

When you call a method on a primitive value, JavaScript **wraps** the primitive in an appropriate **object wrapper** (e.g., `String`, `Number`, `Boolean`, `Symbol`, or `BigInt`). After the method call, the wrapper is discarded.

```js
let str = "hello";
console.log(str.toUpperCase());  // "HELLO"
```
- `str` is a primitive string.
- JavaScript temporarily wraps it in a `String` object to call the `toUpperCase` method, and then the wrapper is discarded. So primitives can provide methods yet still remain lightweight.

### Wrappers for Each Primitive Type:
- **String** has methods like `.toUpperCase()`, `.toLowerCase()`, etc.
- **Number** has methods like `.toFixed()`, `.toPrecision()`, etc.
- **Boolean** has methods like `.toString()` to convert it into a string.

However, **`null`** and **`undefined`** do not have object wrappers, so they **cannot** be used with methods.

#### Converting primitive types:
```js
let num = Number("123"); // Converts the string "123" into a number
let booleanVal = Boolean(0); // Converts 0 to false
```

> **Note**: `null` and `undefined` do not have methods because they are **the most primitive types** and do not have associated object wrappers.

---

- **Primitive types**: Single values, immutable, include `string`, `number`, `boolean`, `null`, `undefined`, `symbol`, `bigint`.
- **Reference types**: Store collections of data and more complex entities, include `object`, `array`, `function`, etc.
- **`typeof` operator**: Used to check the type of a value.
- **Wrapper objects**: Allow primitives to behave like objects when methods are invoked on them (e.g., `String`, `Number`, `Boolean`).

---

### Empty values

`null` is used to assign an `empty`, `nothing` or `value unkown` value to a variable.

`undefined` means `value is not assigned` 
It as a default initial value when variable is declared but value is not assigned.
Many operations yield `undefined` when they have to yield some value if the operation don't produce a meaningful value. 


`null`  and  `undefined`  are used to denote the absence of meaningful value / value unknown.
These two are values but they do not carry no information. Both are mostly interchangeable.


---

#17sep24 
