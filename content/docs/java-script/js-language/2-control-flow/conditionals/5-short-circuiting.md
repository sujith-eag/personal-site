---
title: "Short Circuiting"
description: ""
summary: ""
date: 2024-11-07T20:48:55+05:30
lastmod: 2024-11-07T20:48:55+05:30
draft: false
weight: 705
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---


Logical operators like `&&`, `??`, and `||` handle values of different types in a unique way. They **convert** the left-hand value to a Boolean to decide how to proceed. These operators might **return** either the original left-hand value or the right-hand value, based on the evaluation.

### **1. `||` (OR) Operator**

The `||` (OR) operator will return the **left-hand value** if it **can be converted to `true`**. If not, it returns the **right-hand value**.

- Values that are considered **falsy** in JavaScript (like `0`, `NaN`, `""`, `null`, `undefined`) will cause `||` to return the **right-hand value**.
- Otherwise, it returns the **left-hand value**.

```js
console.log(null || "user");   // "user" (null is falsy)
console.log("Agnes" || "user"); // "Agnes" (non-empty string is truthy)
```

### **Fallback to Default Values**

The `||` operator is often used to provide **default values** when a variable might be empty or falsy.
```js
let username = "";
let defaultName = "Guest";

let name = username || defaultName;
console.log(name);  // "Guest" (since username is falsy, defaultName is returned)
```

In this example, if `username` is falsy (empty string, `null`, etc.), `"Guest"` is used as a fallback value.

---

### **2. `&&` (AND) Operator**

The `&&` (AND) operator works **oppositely** to `||` and `??`:
- If the value on the **left** side is **falsy** (like `0`, `null`, `undefined`), `&&` immediately returns the **left-hand value**.
- If the value on the **left** side is **truthy**, it returns the **right-hand value**.

```js
console.log(0 && "user");    // 0 (0 is falsy)
console.log("Agnes" && "user"); // "user" (both are truthy)
```

This can be useful for **chaining conditions** or using a default value if the left operand is truthy:

```js
let user = "John";
let role = "admin";

let userRole = user && role;  // "admin"
```

If `user` is falsy (e.g., `null`, `undefined`, `""`), `userRole` would be assigned the falsy value of `user`.

---

### **3. `??` (Nullish Coalescing) Operator**

The `??` operator behaves similarly to `||`, but with a key difference: it **only considers `null` and `undefined` as falsy** values. Other falsy values like `0`, `false`, or `""` are treated as valid values.

```js
console.log(null ?? "default");  // "default" (null is considered "undefined" here)
console.log(0 ?? "default");     // 0 (0 is not null or undefined)
console.log(undefined ?? "default");  // "default" (undefined is treated as "missing")
```

This allows for a more **predictable behavior** when you need a fallback only for missing or undefined values, rather than for all falsy values.

---

### **Short-Circuit Evaluation**

All three logical operators (`&&`, `||`, and `??`) support **short-circuit evaluation**. This means that the right-hand operand is only evaluated if necessary.

- For `true || x`, `x` is **not evaluated** because the left-hand operand is already truthy (the result is `true`).
- For `false && x`, `x` is **not evaluated** because the left-hand operand is falsy (the result is `false`).

```js
console.log(true || alert("This will not be evaluated"));  // The alert is not triggered.
console.log(false && alert("This will not be evaluated either"));  // The alert is not triggered.

let x = null;
console.log(x ?? "default");  // "default" (null is treated as missing, so the right side is used)
```

---

### **Conditional Operator (Ternary) and Short-Circuiting**

The conditional operator (`? :`) also behaves similarly in terms of **short-circuiting**. Only the second or third values are evaluated depending on the condition:

```js
console.log(true ? 1 : 2);  // 1 (the second value is not evaluated)
console.log(false ? 1 : 2); // 2 (the first value is not evaluated)
```

- If the condition is `true`, the first value is returned and the second value is ignored.
- If the condition is `false`, the second value is returned and the first value is ignored.

---

### **Summary of Short-Circuiting Behavior:**

- **`||` (OR):** Returns the first truthy value, or the second operand if the first is falsy.
- **`&&` (AND):** Returns the first falsy value, or the second operand if the first is truthy.
- **`??` (Nullish Coalescing):** Returns the right operand only if the left operand is `null` or `undefined`.
- **Short-Circuiting:** The right operand is only evaluated when necessary, allowing for efficient evaluations and conditional operations.

