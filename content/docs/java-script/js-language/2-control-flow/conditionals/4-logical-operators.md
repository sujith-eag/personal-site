---
title: "Logical Operators"
description: ""
summary: ""
date: 2024-11-07T20:48:21+05:30
lastmod: 2024-11-07T20:48:21+05:30
draft: false
weight: 704
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---


Logical operators are used to reason about **Boolean** values. They can be applied to values of any type, not just Boolean.
`||(OR)  &&(AND)  !(NOT)  ??(Nullish Coalescing)`

### **1. `||` (OR)**

The `||` (OR) operator evaluates to `true` if **any** of its operands are true.

Returns the first truthy value.
```js
result = a || b;  // a or b
```
- The operands are evaluated **left to right**. Each operand is converted to boolean.
- The operator returns the **first truthy value** it finds, or the last value if no truthy value is found.

```js
if (1 || 0) {  // Equivalent to true || false
    alert('truthy!');
}
```

```js
let hour = 9;
let isWeekend = true;

if (hour < 10 || hour > 18) {
    alert('The office is closed.');
}

if (hour < 10 || hour > 18 || isWeekend) {
    alert('The office is closed.');
}
```

```js
alert(1 || 0);  // 1 (truthy)
alert(null || 1);  // 1 (truthy)
alert(null || 0 || 1);  // 1 (truthy)
alert(undefined || null || 0);  // 0 (falsy)
alert(first || last || Nickname || "Anonymous");  // "Anonymous" (if all fail)
```

**Short-Circuit Evaluation:**
Once the first truthy value is found, the evaluation stops, and further operands aren't evaluated.
Used to execute the command only if the left is false/falsey.

```js
true || alert("not printed");  // alert won't run
false || alert("printed");     // alert will run
```

---

### **2. `&&` (AND)**

`&&` finds the first falsy value.
- The operator returns the **first falsy value** it encounters, or the last value if all operands are truthy.
- The `&&` (AND) operator evaluates to `true` only if **both** operands are true.

From left to right, converting each operand to Boolean. 
If the result is false, stops and returns the original value of that operand.
If all are truthy, then the last one is returned.

```js
if (hour == 12 && minute == 30) {
    alert("The time is 12:30");
}

if (1 && 0) {
    alert("Won't work as one of them is falsy");
}
```
  
```js
result = value1 && value2 && value3;

alert(1 && 0);  // 0 (falsy)
alert(1 && 5);  // 5 (truthy)
alert(null && 5);  // null (falsy)
alert(0 && "whatever");  // 0 (falsy)
alert(1 && 2 && null && 3);  // null (falsy)
alert(1 && 2 && 3);  // 3 (truthy)
```

#### **Operator Precedence:**

- The `&&` operator has **higher precedence** than `||`, so it is evaluated first in expressions.

```js
a && b || c && d 
// both are equal
(a && b) || (c && d)

alert(null || 2 && 3 || 4);
// 2 && 3 evaluates to 3
// null || 3 || 4 evaluates to 3
```

---

### **3. `!` (NOT)**

The `!` (NOT) operator negates the Boolean value of its operand. It flips `true` to `false` and `false` to `true`.
```js
result = !value;
alert(!true);  // false
alert(!0);     // true (0 is falsy)
```

```js
if (!(age >= 14 && age <= 90)) {
    // Age is not between 14 and 90
}
```
This is equivalent to:
```js
if (age < 14 || age > 90) {
    // Age is not between 14 and 90
}
```

#### **Operator Precedence:**

- The `!` operator has **higher precedence** than both `&&` and `||`, so it is evaluated first.

```js
if (-1 || 0) alert('first');
if (-1 && 0) alert('second');
if (null || -1 && 1) alert('third');

// "first" and "third" will execute as -1 is truthy
```

**Important Notes:** **Avoid Replacing `if` with `||` or `&&`:**
- Logical operators are often used for short-circuit evaluations, not for complex branching. It’s recommended to use `if...else` when the logic requires more than just a true/false check.

---

### **4. Nullish Coalescing (`??`)**

The `??` (Nullish Coalescing) operator returns the **right-hand operand** if the left-hand operand is **null** or **undefined**.
A value is considered “**defined**” when it’s **neither `null` nor `undefined`**.
```js
result = a ?? b;  // returns b if a is null or undefined
```

```js
console.log(0 ?? 100);    // 0  (0 is defined, so it returns 0)
console.log(null ?? 100); // 100 (null is not defined, so it returns 100)
console.log(undefined ?? 100); // 100 (undefined is not defined, so it returns 100)
```

If the left operand is **not null** or **undefined**, the `??` operator will return it:

```js
let user = null;
alert(user ?? "Anonymous");  // "Anonymous" (user is null)
```

```js
let username = null;
let defaultName = "Guest";

let name = username ?? defaultName;
alert(name);  // "Guest" (because username is null)
```

```js
let username = "John";
let defaultName = "Guest";

let name = username ?? defaultName;
alert(name);  // "John" (because username is not null/undefined)
```

---

### **Difference between `??` and `||` (OR Operator)**

While both the nullish coalescing operator (`??`) and the logical OR operator (`||`) check for **falsy** values, there is an important difference:

- `??` only returns the **right operand** if the left operand is either `null` or `undefined`.
- `||` returns the **right operand** for any **falsy** value (including `0`, `false`, `""`, `NaN`, etc.).
- `??` is more preferable than `||` as it is more predictable.

```js
console.log(0 || 100);   // 100  (0 is falsy, so returns 100)
console.log(0 ?? 100);   // 0  (0 is defined, so returns 0)
console.log(null ?? 100); // 100 (null is not defined, so returns 100)
console.log('' ?? 100);  // ''  (empty string is defined, so returns '')
```

### **Using `??` with `&&` or `||`**

For safety reasons, JavaScript **forbids** combining `??` with `&&` or `||` **without explicitly specifying precedence** using parentheses. This is because the behavior of the combined operators can be ambiguous.

```js
let x = 1 && 2 ?? 3;  // Syntax Error: Invalid use of ?? with &&
```

To avoid the error, use **parentheses** to clarify the precedence:

```js
let x = (1 && 2) ?? 3;  // Correct! The AND operation happens first
```

---

```js
if (-1 || 0) alert ('first');
if (-1 && 0) alert ('second'):
if (null || -1 && 1) alert ('third');

// first and third will become true and execute
// -1 is truthy
```

```js
if ( (iceCreamVanOutside || houseStatus === "on fire")) {
	console.log("you should leave the house quickly");
} else {
	console.log("you should just stay in then")
}


if ( !(iceCreamVanOutside || houseStatus === "on fire")) {
	console.log("you should just stay in then");
} else {
	console.log("you should leave the house quickly")
}
```

**Password Verification (using logical operators)**
```js
let userName = prompt("Who's there?", '');

if (userName === "Admin") {
    let pass = prompt('Password?', '');

    if (pass === 'TheMaster') {
        alert("Welcome!");
    } else if (pass === '' || pass === null) {
        alert('Canceled');
    } else {
        alert('Wrong password');
    }
} else if (userName === '' || userName === null) {
    alert('Cancelled');
} else {
    alert("I don't know you");
}
```

---

### **Summary of Logical Operators:**

- **`||` (OR):** Returns the right operand if the left operand is any **falsy** value (including `0`, `false`, `""`, etc.).
- **`&&` (AND):** Returns the first falsy value, or the last operand if all are truthy.
- **`!` (NOT):** Flips the Boolean value of its operand.
- **`??` (Nullish Coalescing):** Returns the right operand if the left operand is `null` or `undefined`.
- **Safety with `??`:** Don’t combine `??` with `&&` or `||` without parentheses. Ensure proper precedence to avoid syntax errors.