---
title: Compound Data Types
description: Dictionaries and Lists and Sets, oh my!
---

Objects
-------

An **Object** is JavaScript's dictionary type: it stores data items by name.

You create an array by putting curly brackets `{` `}` around a comma-separated list of `name: value` pairs. [Valid JavaScript names](variables) can be written bare: other names must have quotes (single or double).

```javascript
let PurpleHaze = {
	variety: "carrot",
	color: "purple",
	'days to maturity': 73
};
```

There are two ways to look up the properties of an object.

If you know the name ahead of time, and it's a valid JavaScript name, you can follow the object with a period and then the name.

If it isn't a valid name, or if you're computing the name when your program runs, you follow the object with the name in square brackets.

```javascript
PurpleHaze.color;                // gives "purple"
PurpleHaze['days to maturity'];  // gives 73
let someName = 'variety';
PurpleHaze[someName];            // gives "carrot"
```

You can set object properties (even adding new ones) with either notation at any time:

```javascript
PurpleHaze.color = 'Tyrian purple';
PurpleHaze['inches long'] = 8;
```

One extremely stupid limitation of JavaScript is that object property "names" can only be strings. In any half-decent programming language, you can use any object as a dictionary key. This isn't often necessary, but when you want it, you really want it. Most of these use cases are now handled by the new `Set` data type, but it has been a long time coming.

If you try to use another type of value with the square bracket notation, JavaScript will silently convert it to a string.

```javascript
PurpleHaze[true] = 'are you sure?';
PurpleHaze["true"];  // gives "are you sure?"

PurpleHaze["100"] = "one hundred";
PurpleHaze[100];  // gives "one hundred"
```

You can process all properties of an object with a `for..in` loop:

```javascript
for(a_name in PurpleHaze) {
	console.log(a_name, PurpleHaze[a_name])
}
```


Arrays
------


An **Array** is a list of items. You create an array by enclosing a comma-separated list in square brackets.

```javascript
let array = ['elephant', 'mouse', 3, true];
```

Some languages require that all items in an array have the same type. JavaScript doesn't care. You can even put arrays or objects inside arrays.

But it's a good rule of thumb anyway. If you have a mixed array, your code will have to decide what to do with each item. If there are rules about which types come in which order, you'll have to decide what to do if you get the wrong type. You do want this sometimes. But first ask yourself if there are other ways to accomplish what you're trying to do and if it's really worth the trouble.

You can ask an array for its `length`, or select a single element with a numeric index. You do this just like with objects (in fact, in JavaScript an array is just a special type of object, one that maintains a `length` property). But since numbers aren't valid names, you always have to use the square-bracket notation.

```javascript
array.length;  // gives 4
array[0];      // gives 'elephant'
array[3];      // gives true
```

Note that the indices start at 0. This takes some getting used to, but it's how nearly all programming languages work, so it's best to just learn it.

It may help to think of them not as ordinals (first, second, third item) but as offsets (0 elements from the start). Note that the last element is at the index one less than the length.

Arrays have a bunch of handy functions attached:

* `array.push(value)` adds the value to the end of the array (increasing the length).
* `value = array.pop()` removes the last element of an array and returns it (decreasing the length).

You can also add and remove elements at the start of the array, but since this requires re-numbering all the remaining values, it gets more expensive as the array gets longer. It's usually not a concern, but if you're doing it thousands of times or with arrays thousands of items long, it can add up. So unless you need to add or remove at both ends of an array, consider using push/pop instead.

* `value = array.shift()` "shifts" a value *off* the start of an array.
* `array.unshift(value)` insert a value at the start of an array.

You can copy a piece of an array with `array.slice(begin, end)`. Because indices are really offsets, `end` is the first element to leave out (it is *not* included in the slice). If you leave `end` out, it will choose the entire rest of the array. `slice` also supports a handy shortcut where negative indices count backward from the end of the array. So `array.slice(-2)` will give you the last two elements, and `array.slice(0, -2)` will give you all *but* the last two.


Sets
----

```javascript
let red = {name: 'red', hex: '#f00'}
let orange = {name: 'orange', hex: '#f80'}
let yellow = {name: 'yellow', hex: '#0f0'}
let green = {name: 'green', hex: '#0f0'}

let colors = new Set([red, orange, yellow])

colors.length  // not useful: always gives zero.
colors.size    // gives 3.

colors.add(green)
colors.delete(red)

colors.has(green)  // gives true.
colors.has(red)    // gives false.

colors.clear()  // removes all values, giving an empty set.
```

You still have to be careful with objects: `Set.has()` does not check the properties of the object, it just checks to see if it's "physically" the same object. So if we ask `colors.has({name: 'green', hex: '#0f0'})` we will get `false`.

Think of them as cars from the same assembly line. They may be identical, but they're separate cars. `Set.has()` isn't checking for a red 2019 Toyota Corolla, it's checking for the exact car you put in the set.
