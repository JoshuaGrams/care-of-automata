---
title: The Design Recipe
description: A step-by-step process for designing a piece of code.
---

The design recipe forces you to work through some of the most common places where fuzzy thinking can creep in. Since bugs are caused by the code doing something unexpected, this helps avoid bugs.

It also helps counter blank-page syndrome by giving you a process to follow. Not sure if you're starting in the right place? Just pick any place and start running through the steps. You'll either end up with some code or with some smaller pieces that you can apply the design recipe to in turn.

If you run into trouble at any step, you may need to back up and re-evaluate. The recipe is designed to make this cheaper by having you do as much work as possible before you start writing code that's expensive to change.

Adapted from [_How to Design Programs_][HtDP] (HtDP), [Figure 1][Fig1].

1. What is the code's purpose?
2. What information comes in? What goes out? How is that data represented?
3. Create some examples of inputs and correct outputs.
4. Take inventory and outline the code.
5. Fill in the rest of the code.
6. Run the code and check it against your examples.

[HtDP]: https://htdp.org/2019-02-24/
[Fig1]: https://htdp.org/2019-02-24/part_preface.html#(counter._(figure._fig~3athe-design-recipe))

TODO: In the remainder of this section, be less ridiculously inconsistent about 1st/2nd person, active/passive voice, etc.

What is the code's purpose?
---------------------------

This one is pretty straightforward. It starts the thinking process. Sometimes writing it down will help you see if it makes sense or not.


What data does the code operate on?
-----------------------------------

HtDP differentiates between information out in the world (e.g. "this creature has nine legs") and the data in the computer which represents that information (i.e. a non-negative whole number representing the number of legs). Ask yourself:

* What information do I need?

* How many different forms does the information take? A vehicle might be a car, or a van, or a bulldozer.

* For each form, how do I represent it? A number? A "string" of text? A list of other data? A dictionary with named entries in a particular structure?

* What about this data is unclear or might need to be explained? Does it have units (pixels, inches, miles)?


Work out some examples
----------------------

How will you know if your code works? You'll need to have some example inputs and correct outputs to go with them.

This may well turn up some examples that your design doesn't handle. Pat yourself on the back for finding these cases before wasting your time writing code that you'd have to fix or throw away, and back up to the previous step.

Ask yourself if you have covered all the forms in your data definitions from the previous step. Have you considered unusual values? What if you get an empty name? Or a negative number? Or an extremely large number?


Take inventory and outline the code
-----------------------------------

Now it's time to think about the overall code structure. Take stock of your inputs and outputs, and any other constants or functions that you know you'll need to use. Ask yourself:

* How can I tell the different forms of data (if any) apart?

* If you're operating on a collection of data, how do you know when to stop?

	* Do you need to do some work for each data element?

	* Do you keep repeating until some condition is true (e.g. you found a match)?

	* Does your data have a complex structure? Do you need to design other functions to process individual parts?


Fill in the rest of your code
-----------------------------

Now that you have worked out the overall structure, you can go back and fill in the details. This should be relatively straightforward. If it isn't, ask yourself whether the difficult parts are complex enough to be pulled out and redesigned as functions of their own.


Check the code against your examples
------------------------------------

Now make sure the code actually works:

* Does it match all your examples?

* Do your examples cover every form?

* Do they check edge cases?

* Do they convince you that your code will work in every case?
