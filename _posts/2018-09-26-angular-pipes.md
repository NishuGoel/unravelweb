---
title: "Angular Pipes"
permalink: "/2018/09/26/angular-pipes/"
tags: ["angular"]
layout: "post"
date: "2018-09-26"
---

{% raw %}
Transforming and showing the modified data to the user is what pipes are used for, in Angular. Pipes help to apply fine tune to the data and display value transformation to the user. Pipes can also be thought of, as styles which we apply in the HTML template. A pipe takes in some data as input and returns an output based on the output of transform function evaluation.

![](/assets/img/b18898-angular-pipes1.png)

A simple example of a pipe would be like:

> import {Component } from ‘@angular/core’;
>
> @Component({  
> selector: ‘app-root’,  
> template:  
>              `<h2>Her birth date is {{ birthdate | date }}</h2>`  
> })
>
> export class AppComponent {  
>            birthdate = new Date(1996, 5, 5);  
> }

Read more about Pipes on the [DotNetTricks Blog](https://www.dotnettricks.com/learn/angular/pipes-custom-pipes-example-usages)
{% endraw %}
