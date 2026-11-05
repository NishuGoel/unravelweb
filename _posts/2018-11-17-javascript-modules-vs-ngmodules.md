---
title: "JavaScript Modules vs. NgModules"
permalink: "/2018/11/17/javascript-modules-vs-ngmodules/"
tags: ["angular", "angularcli", "angularjs", "javascript", "javascripttalks", "js"]
layout: "post"
date: "2018-11-17"
---

{% raw %}
This article explains in short about the difference between the JavaScript modules and NgModules and that how they are used in Angular.

Modules help organize our code and use it in an efficient way. The manner in which the code is organised is different for JavaScript and Angular but the ultimate purpose of a module remains the same.

However, any Angular application that we create depends on both the ways.

A JavaScript Module is a code written in JavaScript which means to organize it and this module comes into action by making use of an export statement like this:

> export class MyComponent {}

An NgModule is the use of a module decorated by the decorator ***@NgModule.***The imports array inside the decorator tells Angular that these modules will be needed for the current scenario. This goes like:

```
@NgModule({
  declarations: [
    AppComponent
  ],
  imports: [ 
    BrowserModule
  ],
  providers: [],
  bootstrap: [AppComponent]
})
```

An NgModule differs from the JS Modules specifically because unlike JS Modules, NgModules do not have their own file. Also they need the presence of the decorator @NgModule and its metadata.

An NgModule has a declarations list wherein it defines all the member classes and it bounds declarable classes.

Some of the frequently use NgModules are BrowserModule, FormsModule, CommonModule etc.
{% endraw %}
