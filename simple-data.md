---
title: Simple Data Types
description: Numbers, text, true and false.
---

**Numbers** in JavaScript are stored as standard 64-bit floating-point numbers. This means that you can write numbers with the decimal point anywhere and things will [*usually*](floating-point) just work.

You use `+`, `-`, `*`, `/` for the usual arithmetic operations. Note that, as you were shown in school, multiplication and division happen before addition and subtraction, so `7 + 2 * 10` is 27 (not 90).


-----

Text in JavaScript (called **strings** of characters) can be enclosed in single quotes (apostrophes) or double-quotes. I usually use single quotes for most things (because they're less obtrusive) and double-quotes for full sentences (where you might want to put an apostrophe in the text).

Strings must be written on a single line. If you need to put a line break in a string, you can use `\n` ("newline"). If you need to insert the quote character that you're using, you can write `\'` or `\"`.

Modern JavaScript has another form of strings which they call **template literals**. These are enclosed in backtick (grave accent) characters: `` ` ``. They *can* contain line breaks. They also allow you to insert variables or computed values by writing `${code}` (this is called **expression interpolation**). And as you might guess, if you need to insert a backtick, you put a backslash before it.


-----

**True** and **false** are called booleans, after the short-lived 19th-century mathematician George Boole, who did some of the early work on logical operators (AND, OR, NOT, and so on).

Like many other languages, JavaScript uses `&&` for AND, `||` for OR and `!` for NOT. Like the math operators, these have a certain *precedence*. `!` happens before `&&`, which happens before `||`. But you probably won't remember that (I often don't) so use parentheses if you're writing complex conditions.

Conditional operators are `===` and `!==` (equal and not-equal), `<`, `>`, `<=`, `>=` (but not `=<` or `=>`, the `=` must be at the end).

JavaScript also has "approximate" equal and not-equal (`==` and `!=`), but they do a complex type conversion process which sometimes leads to unexpected results, so you're better off using the exact equality operators in the previous paragraph.
