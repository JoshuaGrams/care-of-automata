---
title: Names and Variables
description: Who is "It"?
---

JavaScript names can contain `$`, `_`, letters and numbers, and may not start with a number. They may not contain spaces or any other punctuation.

These days, &ldquo;letters and numbers&rdquo; means Unicode letter and number characters and combining/accent marks, so feel free to write names in your preferred language. If you're making a library for other people to use, and you want it to gain traction outside your language community, you'll probably need to make the public names in English. But otherwise, do whatever you want.

-----

In computer programming, a **variable** is a nickname for a piece of data. So in a game of tag, "it" is a variable. Now this person is "it", now that one. In a murder investigation, "suspects" might be a variable naming a list of people. Some people teach that a variable is a bucket that you can put a piece of data in. This is a very concrete metaphor and may be helpful when you first start, but it doesn't capture some subtleties of variables.

For instance, different variables can refer to the same data. I'm still "Joshua" or "Josh" while I'm a suspect, or while I'm "it".

You can also have different variables with the same name at different times. You probably know other people named Joshua, so when you use the word you may not be referring to me. In the real world you might clarify with a surname or other description, or expect people to understand from the context.

But computers need this explicitly spelled out. And we want each piece of code to have access to as few names as possible, to reduce the chance of bugs. If it can't access a name, it can't accidentally mess up that data. Also, if a variable ends up with a bad value, the fewer pieces of code that access it, the fewer places we have to look at to find the bug.

So variables also have a **scope**, a section of the source code in which they are visible. In JavaScript (and many other languages with similar syntax), scopes are marked by `{` and `}`. These curly brackets mark (nested) sections of code. A variable can't escape into a bigger box than the one it's defined in. So in the following code we have two nested scopes: the function has one, and the `for` loop has another. Note that we can access `emoticons` inside the inner box. It's still inside the outer box, so we can still see it.

```javascript
function animals(count) {
	let emoticons = [
		':~',    // elephant
		'_@/',   // snail
		'><>',   // fish
		'=^.^=', // cat
		'(o.o)'  // owl
	];

	let results = [];  // Start with an empty list.
	for(let i=0; i<count; ++i) {
		// Add a random emoticon to the list.
		let e = Math.floor(emoticons.length * Math.random())
		results.push(emoticons[e])
	}

	// Join them together with double spaces between.
	return results.join('  ');
}

// Error: we can't see `emoticons` because we're not in the function box!
alert(emoticons[3]);
// But note that there could be a *different* `emoticons` variable out here.
```

If you can see multiple variables of the same name, the rule is that you take the most specific one: the one in the smallest scope.

When you set a variable (`name = value`) it will look for an *existing* variable. If it doesn't find one, it will create a *global* variable that's visible everywhere. So you say `let name = value` to **declare** a new variable that exists only in the current scope. If you don't want to set it right away, you can say `let name` which reads strangely but works fine.

JavaScript used to use `var` for variables, but it has some weird quirks that cause problems occasionally. So you'll see `var` a lot in existing code, but you should use `let` for new code.

In more advanced usage, there's also `const name = value` (the initial value is required). Assigning a new value to that name will cause an error. But if the value is a list or a dictionary, the *contents* of that collection may change: it's just that the name always refers to the same container.
