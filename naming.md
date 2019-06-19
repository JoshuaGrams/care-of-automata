---
title: Choosing Names
description: That which we call a rose... yeah right.
---

Choosing good names is hard. It's an art rather than a science. And good names can make your code much easier to manage.

On the other hand, you can get along with mediocre or even bad names. It will just slow you down a bit. So don't stress about it. And avoid turning the hunt for the perfect name into a form of procrastination (this is really easy to do...ask me how I know).

There are some rules of thumb. I'm going to have to do my homework and get back to this section because I know there are a bunch of rules I try to follow, but I seem to have internalized and forgotten most of them.

-----

**Consistency** is probably the biggest thing. If you have lists, do you name them in the singular so you it reads `element[5]`, or in the plural so you know it's a collection of things?

And it's not just for names. If you have a bunch of functions with similar inputs, try to pick an order and stick with it. Stuff like that.

It doesn't matter what conventions you choose. But if you mix up different ones, you'll have trouble remembering which name is which way. A good programmer's text editor or IDE (Integrated Development Environment) will auto-complete names for you, which can help a lot, but even then...consistency is good.

-----

In general, use **nouns** for data, **verbs** for functions.


-----

Put the data type in the name? This is controversial because it's often badly used, so you'll have to make up your own mind about it. There's no point saying that a variable holds a number or a string or a list: the programming language will figure that out for you. But putting units can sometimes be useful, so you can immediately see when you're trying to add inches to miles, or pixels to grid units.
