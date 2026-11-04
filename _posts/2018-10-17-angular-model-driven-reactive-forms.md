---
title: "Angular Model-Driven (Reactive) Forms"
permalink: "/2018/10/17/angular-model-driven-reactive-forms/"
tags: ["angular", "angularcli", "angularjs", "community", "javascript", "javascripttalks", "js"]
layout: "post"
date: "2018-10-17"
---

{% raw %}
Forms come handy when handling user-input and enabling user to log in, update information, and other data-entry tasks. These are basically used to capture user input events. In Angular, there are two approaches to handling user inputs.

* Template-Driven Forms
* Reactive Forms

### Template Driven Forms

Template Driven Forms are used to bind the data to the component class using ngModel. We do not need to take the pain of writing code and most of the task is done by Angular itself. There is very less of effort required from the developer to pass information from the component class to the template.

### Reactive forms

However, Reactive forms are synchronous and are usually considered when working with database. We write the code for validation inside the component class and also map the objects to the form controls on the view.

In this article, our focus is to work with Reactive Forms which follow the model-driven approach to work with user input and handle it dynamically.

## GETTING STARTED WITH REACTIVE FORMS

We will create a Form, using FormGroup, FormControl, FormBuilder class etc. The very first step is to import ReactiveFormsModule in the app.module.ts as listed below :

> import { BrowserModule } from ‘@angular/platform-browser’;  
> import { NgModule } from ‘@angular/core’;  
> import {ReactiveFormsModule} from ‘@angular/forms’;  
> import { AppComponent } from ‘./app.component’;
>
> @NgModule({  
> declarations: [  
> AppComponent  
> ],  
> imports: [  
> BrowserModule, ReactiveFormsModule  
> ],  
> providers: [],  
> bootstrap: [AppComponent]  
> })
>
> export class AppModule { }

Continue reading on the [DotNetTricks Blog](https://www.dotnettricks.com/learn/angular/model-driven-reactive-forms-example)
{% endraw %}
