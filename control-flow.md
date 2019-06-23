---
title: Code Structures
description: Functions, Conditionals and loops.
---

Functions
---------

A **function** is a block of code which may take inputs and may return a single output (though that output may be an array or object).

To call a function, follow it with parentheses containing a comma-separated list of inputs:

```javascript
let result = action(input1, input2)
```

The `function` keyword defines a function.

```javascript
function name(inputName1, inputName2) {
	code
	code
	code
	return output
}
```

If you don't return a value, the result will be the special JavaScript value `undefined`.

A function is a type of value, so you can assign them to variables. `let name = function() { ... }` is (nearly) identical to `function name() { ... }`.

You may also pass them as arguments to other functions. You might do this to bind an action to an *event* such as a mouse click on a particular link or button. You might provide a comparison function to sort a list, or a condition function to filter out a certain subset of a list.

-----


Conditional Statements
----------------------

I *think* conditional statements are fairly straightforward.

```javascript
if(condition) {
	doThis()
	andThis()
} else if(other condition) {
	doThings()
} else {
	somethingElse()
}
```

You can leave out any of these parts.


Counted Loops
-------------

Counted loops are the most common type. They are used when you know in advance how many times you want to repeat an action. So if you want to do something for each element of a list, use a counted loop.

Unfortunately JavaScript copied its counted loop syntax from the C programming language. So while it is very flexible, it is also more complex and error-prone than counted loops from more modern languages.

```javascript
for(setup; keepLooping; update) {
	code to be repeated
}
```

It starts by running the `setup` code.  Then each time through, it:

* Checks `keepLooping` to see if it should exit the loop.
* Runs the `code to be repeated`.
* Runs the `update` code to update the loop variables.

As you can see, this is pretty vague and could do almost anything. The usual patterns for looping over an array (forward and backward) look like this:

```javascript
// Forward (0 to list.length - 1):
for(let i=0; i<list.length; ++i) {
	do something with list[i]
}

// Backward (list.length - 1 down to 0):
for(let i=list.length-1; i>=0; --i) {
	do something with list[i]
}
```

It's traditional to use `i` for loop indices (plus `j` and `k` for nested loops). The single-character name is easy to type and signals that there's nothing particularly meaningful about this value. But if the loop variable *does* have a meaning (e.g. how many pets do these people have?) you may want to give it a more descriptive name.



Looping Through Objects
-----------------------

Looping through objects is like a counted loop, but JavaScript has a special structure for it.

```javascript
for(let name in object) {
	do something with object[name]
}
```

But JavaScript objects can inherit properties from other objects. When libraries define their own data types, they will often attach functions to objects this way (so a graphical object might know how to draw or rotate or move itself). The `for..in` loop will find these inherited properties. So you usually want to add an extra check to exclude them:

```javascript
for(let name in object) {
	if(object.hasOwnProperty(name)) {
		do something with object[name]
	}
}
```


Conditional Loops
-----------------

The other type of loop is a conditional loop. You use these user input, or data streaming over the network, or other places where you can recognize the end of the data but don't know in advance how long it will be.

JavaScript has two (similar) ways of writing these: one with the condition at the beginning of the loop, and one with it at the end. The first is **far** more common: it's relatively rare to want your loop to execute at least once even if there is no data.

```javascript
while(condition) {
	do this
}

do {
	these things
} while(condition)
```


Exiting Loops Early
-------------------

Sometimes you want to break out of a loop early. Maybe you're searching for the first matching element in a list (though JavaScript has helper functions for this) or something similar. To do this you use a `break` statement. It immediately exits the smallest enclosing loop. This is not necessarily the smallest scope: it ignores `if` statements (as it must, since a `break` is always conditional or it would just stop the loop the first time through).

In some languages, `break` takes an optional number and lets you break out of two or more nested loops. JavaScript doesn't do this.

I want to mention a common pattern with counted loops which some people refer to as a 'loop-and-a-half'. Let's say you were letting the user type in commands. You read a line, process it, and then wait for another. But if the user types &ldquo;quit&rdquo; you want to stop. The obvious way to do this has some duplicated code:

```javascript
let command = readInput()
while(command !== 'quit') {
	perform(command)
	command = readInput()
}
```

If the `readInput` code needed to change, you'd have to change it in two places. That leaves a chance for bugs to creep in. A loop-and-a-half avoids this by writing, "loop forever, but break if we get a quit command."

```javascript
while(true) {
	let command = readInput()
	if(command === 'quit') break
	perform(command)
}
```

Note that I didn't use curly-brackets with the `if` statement. The control-flow structures actually take a single statement, so if you just need one you can leave out the brackets. But you almost always need several, so the brackets allow us to group them together into a single block.

There are various code-style conventions around this: you'll have to decide what works for you. Some people put in the brackets even if they don't need them. I usually leave them out if I can fit the whole thing one one line, as above. But if I put the command on a separate line, I always use brackets even if there's only one:

```javascript
if(command === 'quit') {
	break
}
```
