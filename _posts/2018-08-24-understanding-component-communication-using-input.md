---
title: "Understanding Component Communication using @Input()"
permalink: "/2018/08/24/understanding-component-communication-using-input/"
tags: ["angular", "angularcli", "angularjs", "bootstrap", "javascript", "javascripttalks", "js"]
layout: "post"
date: "2018-08-24"
---

{% raw %}
Want your components to share information? Yes, they can!  
Say you have two components, a parent component (PC) and a child component (CC) and you want the data to move from the parent component to the child component or vice versa, you use **COMPONENT COMMUNICATION/INTERACTION.**

There are multiple ways to achieve that. This article focuses on the use of **@Input()**to receive the data from the PC to CC.

![](/assets/img/a02976-6ab4c-1zabcm_xptvwqi5tu5pbrxw.png)

@Input decorator is used to pass data from parent to child component. Now suppose we have created two components:  
***app.component.ts*** and ***child.component.ts***

Here, we have decorated the message property with the @Input() decorator so that value of the message property can be set from the parent component.

https://gist.github.com/NishuGoel/d9d60bffd9ad81c004e24a1d7055a0fe

Now, let us modify the parent component AppComponent to pass data to the child component.

https://gist.github.com/NishuGoel/f4381fbb870074df00b09cc6957b3252

Here we are setting the value of the child component’s property message with the help of parent component. To pass a value to the child component, we need to pass the property inside a square bracket and assign its value to any property of the parent component. We are passing the value of **‘cmessage’**property from the parent component to the ‘**message’** property of the child component.

Taking this example to the next level, there might be a situation where we’d need to intercept the data passed from the parent component. To do this, we need to use getter and setter on the input property.  
We create a property called \_message and using @Input() decorator, create getter and setter for the \_message property.

https://gist.github.com/NishuGoel/718c9b573d9676d65d8123759cecdc2c

In the above example, we need to understand that the behavior of the parent component is not changed when we intercept the message. Now let us take another case where if the parent passes empty value, then the child component displays some default value.

<https://gist.github.com/NishuGoel/586d5da00bbc87ec1a78a6b0e70ca725>

It checks here if the value passed is an empty string. If yes, we assign the default value for message in the child component.

This is one-way communication between components. In the upcoming article, we’ll see component communication both ways.
{% endraw %}
