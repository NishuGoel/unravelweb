---
title: "Binding Array to a Table"
permalink: "/2018/08/25/binding-array-to-a-table/"
tags: ["angular", "angularcli", "angularjs", "javascript", "javascripttalks", "js"]
layout: "post"
date: "2018-08-25"
---

{% raw %}
In this article, we will learn how to bind an array to a HTML table.  This means that we want the elements in our array and their attributes to be displayed on the view.

For this, we will mainly use some hard-coded data and structure directives like \*ngIf and \*ngFor.

So, initially, if we have a  component.ts file in our project, it will look like this:

https://gist.github.com/NishuGoel/b5aaa93f2b3949cdb783067f791ca9aa

Now to display these items on the view, we would need to use \*ngFor which is a structure directive.  
So, inside the HTML file app.component.html,

https://gist.github.com/NishuGoel/158a29a5a0cd72f745668fa7834e03b7

This will give result like:

![cc](/assets/img/abb6a6-cc8.jpg)

Now, we want to display the attributes of these elements, so for the sake of convenience let us hard-code the data.

https://gist.github.com/NishuGoel/a8ef5c81835cd6231a7f929e999fa548

And, inside the app.component.html, we display it like:

https://gist.github.com/NishuGoel/6a0bf7252bdfbbd4a80de6aa7c650e78

This will show up the table with all the elements and their attributes as follows:

![cc](/assets/img/19d435-cc9.jpg)

This is how we bind our array to an HTML table. Your turn to try now!
{% endraw %}
