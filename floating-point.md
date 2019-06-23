---
title: Floating-point numbers
description: 0.1 + 0.9 &ne; 1.0
---

The catch with floating-point numbers is that they're stored in a sort of binary scientific notation: with a big string of digits (about 15 decimal digits worth) and then a power of two that tells how big or small the number is (multiplying the digits by 2 or 1/2, 4 or 1/4, ... 1024 or 1/1024, etc.).

So you know how some fractions can't be represented exactly in decimal? Like 1/3 is 0.3333...? And if you add 1/3 and 2/3 you might get 0.9999... instead of 1?

That problem is even worse in floating-point numbers because numbers that are fine in decimal might go on forever when stored in binary. For instance, decimal 0.1 is binary 0.00011&nbsp;0011&nbsp;0011...

What this means for you is that if you write fractions and do math on them you can't expect them to add up exactly. Specifically dollars and cents will come out funny sometimes. Whole numbers with 15 digits or less (whether positive or negative) will always come out exactly. If you run into trouble when working with money, you can try storing it as cents instead of as dollars, and rounding your results to the nearest whole cent.

-----

More subtly, you will lose some precision when you add or subtract a very big and a very small number. This might never cause you problems, but the error will sometimes be big enough to matter when you're checking to see if a result is zero.

So feel free to skip this part, but I'm a math geek, so I have to try to explain it.

Let's say we can store only four decimal digits.  Now let's add a large number: 1234, and a small one: 5.678. These would be stored as something like 1.234e3 (shift the decimal point three places right) and 5.678e0 (leave the decimal point alone).

To add them, we have to line them up where they belong, making the exact result 1,239.678. But we can only keep the top four digits: 1239. Since the numbers only overlapped in the very bottom digit of the result, we lost the other three. We wouldn't be able to tell the difference between adding 5.9 and adding 5.2.

With 15 digits to work with, this is usually not too much of a problem. But as I said, sometimes if you're trying to check whether something is near zero, the error will be noticeable.
