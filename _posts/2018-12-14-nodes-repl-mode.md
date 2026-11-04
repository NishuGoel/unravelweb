---
title: "Node’s REPL Mode"
permalink: "/2018/12/14/nodes-repl-mode/"
tags: ["Node.js", "angular", "angularcli", "angularjs", "javascript", "javascripttalks", "node", "nodejs"]
layout: "post"
date: "2018-12-14"
---

{% raw %}
When working with node, if we type in node command with an executable script for it, the node starts a **REPL** session. But, What is a REPL session? REPL is Read-Eval-Print-Loop implementation provided by the REPL module which exists both as a standalone program as well as a includible one in other applications. It is very useful to debug the JavaScript codes.

**REPL** stands for:

**R** – Read  
**E** – Evaluate  
**P** – Print  
**L** – Loop

REPL proves to be a very convenient way of testing JavaScript and Node commands. To check, type in any function, say Math.random() in the REPL session, now node will do 4 tasks:

1. Read the line,
2. Evaluate it,
3. Print the output, and
4. Wait for further lines.

One important thing to notice is that to get an output, we didn’t actually need a print statement. REPL did it all.   
There are times when there is output of a statement at all, in that case, Node print ***undefined***.

For example, if you type any JavaScript Statement on the node, like say,

> var a = 5;

This is just a statement and not a JavaScript expression which will have some output, so in such a case, Node will print *undefined*.

Now let us take a boolean expression of JavaScript, say

> 5 == ‘5’

The REPL session will print ***true*** since according to JavaScript rules, these two, when compared are equal and hence print output as true.

Also, in the node, we need to type multiple lines of code sometimes, so, to do that, here is the syntax:

> function f-name() {  
> …return something;  
> …}  
>   
> f-name()

The minute a statement seems to contain a curly brace at the end of it, REPL understands that it is not the end of the statement and there is more to come and this is how it considers multiple lines of code until the closing curly brace comes in.  And then we can simply call the function and REPL displays the output.

Some of the REPL commands are:

Use **Ctrl + C** to terminate the current command  
Use **Ctrl + D** to terminate the Node REPL  
Use **.break** to exit from multi-line expression.  
Use **.save *filename*** to save the current Node REPL session to a file.

To come out of a Node.js REPL session, use **Ctrl + C** twice.
{% endraw %}
