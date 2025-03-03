---
title: "05 - Basic Array Methods"
description: ""
summary: ""
date: 2024-11-09T17:09:41+05:30
lastmod: 2024-11-09T17:09:41+05:30
draft: false
weight: 428
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---




Arrays inherit properties from Array.prototype, which defines a rich set of array
manipulation methods, Most of these methods are generic, which means that they work correctly not only for true arrays, but for any “array-like object.”


# Basic Array Methods

Properties that contain functions are called methods of the value they belong to, 
as in `.toUpperCase` is a method of a string.

```js
// Covered in Previous note of Inserion

length  // gives length of array

// To Add and remove items at end
push()   pop()

// To Add and remove at beginning
shift()  unshift()	

delete()  // makes things undefined

splice() // used to insert, remove, replace elements
toSpliced()
```

```js
at()  // getting element with index

// String to array with delimeted
	split()  join()
	toString()  // array to a comma seperated string
	concat()  // new array including other arrays
	reverse()  // reverses order of array


// extracting parts of array
	slice()  // make new subarray

	
// searching in array
	indexOf()  lastIndexOf()   includes()
	find()  findIndex()  findLastIndex()


copyWithin()  // copy elements to other positions in array
flat()  flatMap()  // flaten multidimensional array
```

__________________________

### arr.at(pos)

`at()` method returns an indexed element from an array. 
similar to `[]` but `[]` does not allow getting the last index using `[-1]`, since `[]` is used for both objects and arrays, `obj[-1]` refers to key -1, not last property of object.
`at()` was introduced to solve this problem.

```js
const fruits = ["Bannana", "Orange", "Mango"];

let fruit = fruits.at(2);  // Mango
let fruit = fruits[2];     // Mango
alert( fruits[-1] );   // error
alert( fruits.at(-1) );  // Mango
```

_________________________

# split and join

### str.split(delim)
comma-delimited string of receivers: `John, Pete, Mary`
To get an array of names from this string.

`split()` splits the string into an array by the given delimiter `delim`.
```js
let names = `John, Pete, Mary`;

let arr = names.split(', ');

for (let name of arr) {
	alert( 'A message to ${name}.');
}
```
The `split` method has an optional second numeric argument – a limit on the array length. If it is provided, then the extra elements are ignored.

***Split into letters***
```js
let str = 'test';
alert( str.split('') );  // t, e, s, t
```


### arr.join(glue)

The call [arr.join(glue)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/join) does the reverse to `split`. 
It creates a string of `arr` items joined by `glue` between them.

`join()` method allows joining all array elements into a string similar to `toString` but the separator can be assigned.
```js
const arr = ["Bannana", "Orange", "Mango"];

let str = arr.join(" * ");  // Bannana * Orange * Mango

let str = arr.join(';');  // glue the array into string using string using ;
alert(str);  // Bannana;Orange;Mango
```


### toString()

Converting an Array to String of comma separated values. This is an automatic process when an outputting an array. All JavaScript objects have `toString()` method.
```js
const fruits = ["Bannana", "Orange", "Mango"];

fruits.toString();  // Bannana,Orange,Mango

alert(fruits) // same as above
```


### concat()

`arr.concat` creates a new array that includes values from other arrays and additional items.
```js
arr.cocat(arg1, arg2...)
```
accepts any number of arguments - either arrays or values.

Used to create a new array by merging (concatenating) existing arrays and returns a new array without changing the old ones.
```js
const myGirls = ["Cel", "Lon"];
const myBoys = ["Em", "Lin"];
const myPets = ["cat", 'Dog'];

const myChildren = myGirls.concat(myBoys);
const family = myGirls.concat(myBoys, myPets);

const myKids = myGirls.concat("daisy");
```
It can take strings also as arguments.
Normally, it only copies elements from arrays. Other objects, even if they look like arrays, are added as a whole.


### arr.reverse()

The method [arr.reverse](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/reverse) reverses the order of elements in `arr`.
It also returns the array after the reversal.
```js
let arr = [1, 2, 3, 4, 5];
arr.reverse();

alert( arr );  // 5, 4, 3, 2, 1
```


_____________

# Extracting parts of array

### slice()
```js
arr.slice([start], [end])
```

`slice` returns a new array copying to it all the elements from `start` to `end` (not including `end` but up to end). 
Doesn't remove any element from original. makes a sub array.
Both start and end can be negative, in that case position from the array end is assumed.
When end index is not given, all elements after the start index is taken.
```js
const fruits = ["Bannana", "Orange", "Lemon", "Apple", "Mango"]

// copy from index 1 upto index 3, i.e 1,2
const citrus = fruits.slice(1,3);   // [Orange, Lemon]

// copy from index 2 till the end, including end
const citrus = fruits.slice(2);  //  [Lemon, apple, mango]

// copy from index 2 upto 4,  2,3
console.log([0, 1, 2, 3, 4].slice(2, 4));   // [2, 3]

// copy from index 2 till end
console.log([0, 1, 2, 3, 4].slice(2));  // [2, 3, 4]


let arr = [ "t", "e", "s", "t"]
// copy from -2 till end
aler( arr.slice(-2) );   // s, t

alert( arr.slice(1, 3) );  // e, s
```




______________

# Searching in array

### indexOf() lastIndexOf()    includes()

Usually these methods are used with only one argument, the item to be found.
```js
arr.indexOf(item, from)
```
`indexOf` searches through the array for `item` starting from index `from` to end and returns the ***index*** at which the value was found. Otherwise `-1` if not found.

`lastIndexOf` searches from the end / right to left.
```js
console.log([1, 2, 3, 2, 1].indexOf(2));    // 1

console.log([1, 2, 3, 2, 1].lastIndexOf(2));  // 3

alert ( arr.indexOf(null) );  // -1
```
`indexOf` uses the strict equality `===` for comparison. So, if we look for `false`, it finds exactly `false` and not the zero.

`includes()` is preferred to check existence of item 
```js
arr.includes(item, from)
```
searches through the array for `item` starting from index `from` to end, and returns the ***true*** if found.
It handles `NaN` properly.
```js
const arr = [NaN];

alert( arr.indexOf(NaN) );  // -1
alert( arr.includes(NaN));  // true
```


###  find() findIndex()  findLastIndex()

In an array of objects, to find an object with a specific condition.

```js
let result = arr.find(function(item, index, array) {
// if true is returned, item is returned and iteration is stopped
// for falsy scenario returns undefined
});
```

```js
let users = [
	{id:1, name: "John"},
	{id:2, name: "Pete"},
	{id:3, name: "John"},
];

let user = users.find(item => item.id == 1);

alert(users.name);  // John

alert(users.findIndex(user => user.name == "John"));  // 0

alert(users.findLastIndex(user => user.name == "John"));  // 2
```

`arr.findIndex()` has the same syntax but returns the index where the element was found instead of the element itself.  -1 if noting is found.
`arr.lastIndexOf()` searches from right to left.


__________________


### copyWithin()

[arr.copyWithin(target, start, end)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/copyWithin) – copies its elements from position `start` till position `end` into _itself_, at position `target` (overwrites existing).
```js
arr.copyWithin(target, start, end)
```

Copies array elements to another position in an array by overwriting the existing value.

copies its elements from position `start` till position `end` into itself, at position `target` (overwrites existing).

It cannot add items to an array so does not change the length of the array.
```js
const fruits = ["Bannana", "Orange", "Mango", "Kiwi"];

fruits.copyWithin(2,0);  // copy to index[2], all elements from [0]
// Bannana, Orange, Bannana, Orange

fruits.copyWithin(2,0,2); //copy to index 2, the elements from 0 to 2
```

_______________

[arr.flat(depth)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/flat)/[arr.flatMap(fn)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/flatMap) create a new flat array from a multidimensional array.

### flat(depth)

Creates a new flat array from a multidimensional array.
The flat method creates a new array with sub-array elements concatenated to a specified depth.
```js
const myArray = [ [1,2], [3,4], [5,6] ];

const newArray = myArray.flat();
// 1,2,3,4,5,6
```

### flatMap(fn)

it first maps all elements of an array and then creates a new array by flattening the array.

```js
const myArray = [1,2,3,4,5,6];

const newArray = myArray.flatMap( x => [x, x*10] );
// [1, 10, 2, 20, 3, 30, 4, 40, 5, 50, 6, 60]
```


____


These methods are the most used ones, they cover 99% of use cases. But there are few others:

- [arr.some(fn)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/some) / [arr.every(fn)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/every) check the array.
    The function `fn` is called on each element of the array similar to `map`. If any/all results are `true`, returns `true`, otherwise `false`.
    
    These methods behave sort of like `||` and `&&` operators: if `fn` returns a truthy value, `arr.some()` immediately returns `true` and stops iterating over the rest of items; 
    if `fn` returns a falsy value, `arr.every()` immediately returns `false` and stops iterating over the rest of items as well.
    
- [arr.fill(value, start, end)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/fill) – fills the array with repeating `value` from index `start` to `end`.

[manual](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array).



