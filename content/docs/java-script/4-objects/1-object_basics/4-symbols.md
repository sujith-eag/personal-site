---
title: "04 - Symbols for property name"
description: ""
summary: ""
date: 2024-11-09T17:07:07+05:30
lastmod: 2024-11-09T17:07:07+05:30
draft: false
weight: 388
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---


Symbols were introduced in **ES6** to serve as non-string property names.

Property names in objects are typically (and until ES6, exclusively) strings. However, in ES6 and later, **Symbols** can also be used as property names. Symbols are opaque values, meaning you can’t do anything with them other than use them as property names. Each Symbol is unique, which makes them useful for creating distinct property names.

```javascript
let strname = "string name";
typeof strname; 
// 'string'

let symbname = Symbol("Propane");
typeof(symbname); 
// 'symbol'

let o = {};  // Create a new object
o[strname] = 1;  // Property with string name
o[symbname] = 2;  // Property with symbol name

o[symbname];  // Accessing value
// 2

o;  // Object with string and symbol properties
// { 'string name': 1, [Symbol(Propane)]: 2 }
```

#### The 'Symbol()' Function

The `Symbol()` function takes an optional string argument and returns a unique Symbol value. If a string argument is provided, that string will appear in the output of the Symbol's `toString()` method. Note, however, that calling `Symbol()` twice with the same string produces two completely different Symbol values.

```javascript
let s = Symbol();
s.toString(); 
// 'Symbol()'

typeof(s); 
// 'symbol'

let p = Symbol("sym_x");
p.toString();
// 'Symbol(sym_x)'

let q = Symbol("sym_x");
q.toString();
// 'Symbol(sym_x)'
```

The point of Symbols is not to provide security but to define a safe extension mechanism for JavaScript objects. If you receive an object from third-party code that you don't control and need to add your own properties to it, using Symbols ensures that your properties won’t conflict with any existing properties on that object. Additionally, this guarantees that third-party code won’t accidentally modify your symbolically named properties.

By using `Symbol()`, you can safely add new properties to an object without worrying about overwriting an existing property with the same name. Similarly, when you use symbolic property names and keep your symbols private, you can be confident that other code modules in your program won’t accidentally overwrite your properties.

#### 'Symbol.iterator'

`Symbol.iterator` is a special Symbol value that can be used as a method name to make an object iterable.

---

### The Global Symbol Registry

JavaScript defines a global **Symbol registry**. The `Symbol.for()` function takes a string argument and returns a Symbol value associated with the string you pass. If a Symbol is already associated with that string, it is returned; otherwise, a new one is created.

This is different from the `Symbol()` function, which always returns a new, unique Symbol value. `Symbol.for()` ensures that the same Symbol is returned whenever called with the same string. The string passed to `Symbol.for()` appears in the output of the `toString()` method for the returned Symbol and can also be retrieved using the `Symbol.keyFor()` function.

```javascript
let s = Symbol.for("shared");
let t = Symbol.for("shared");

s === t;
// true

Symbol.keyFor(t);
// 'shared'
```

If you create two Symbols using the `Symbol()` function with the same string, they will still be different:

```javascript
let p = Symbol("notshared");
let q = Symbol("notshared");

p === q;
// false

Symbol.keyFor(p);
// undefined

Symbol.keyFor(q);
// undefined
```

---
