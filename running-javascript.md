---
layout: default
title: Running Javascript
description: Press Control-Shift-I in your browser.
---

The biggest reason to use JavaScript is that it works in every web browser. There's nothing to install, so it's easy to get started and to show your work to other people. And there are basic development tools built into all the major desktop browsers.

**Control-Shift-I** (or sometimes F12) will bring up the developer tools.

The Elements tab will show you the HTML code for the page, and when you
mouse over an element it will highlight it on the page (if it's on-screen). You can also get here by right-clicking on the page and choosing Inspect (Inspect Element on Firefox).

If you double-click on things in the Elements view you can mess with the text. To the right of the HTML pane there will be a pane with more tabs. If you choose the Styles tab it will show the CSS that applies to the current element. By double-clicking here you can mess with the colors and sizes and such. This won't get saved anywhere, but it can be fun to experiment with, and is sometimes a good way to debug your layouts and styling.

Anyway. On to JavaScript. If you choose the Console tab at the top of the Developer Tools pane, you'll get a JavaScript command-line. So if you type `alert("AAaaaaaah!");` and hit enter/return, a dialog box will pop up with your message. If you type `document.body.append("Blah blah blah");` it will add text onto the end of the page. Though if you're on a web page it might show up anywhere, or not at all, since CSS can lay things out in various orders. On Google's home page it usually shows up on the very top left.
