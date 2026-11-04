---
title: "Angular Component Lifecycle Hooks Explained"
permalink: "/2018/11/20/angular-component-lifecycle-hooks-explained/"
tags: ["angular"]
layout: "post"
date: "2018-11-20"
---

{% raw %}
We have worked with Components and Directives in Angular quite a lot now. And if dear Reader, you are new to Components or directives, refer here. When dealing with components or directives, there is a sequence of steps that are performed to build an angular application. These steps range from the process of its initialization to its destruction.

The lifecycle of a component/directive is managed by Angular as it creates, checks, updates, renders, and destroys. To have a view of all these occurrences and respond to these moments, Angular provides lifecycle hooks which give us visibility into these. These lifecycle hooks can be implemented by the interfaces provided in the Angular Core Library. This is the same with components and directives both. Every interface contains different lifecycle hook methods, named with the interface name prefixed with ng. Like the very commonly used lifecycle hook ngOnInit() is named as ng(prefix) and OnInit (interface name).

## Constructor

Whenever working with components, the first step is the calling of the constructor. This happens even before the implementation of any lifecycle hook. Also, if our component has any dependencies, a constructor is where we can inject those.

A simple example of the usage of the constructor would be like:

https://gist.github.com/NishuGoel/ff7cf4f278cd9f56eb501a686868cde4

### **[Read More on the DotNetTricks Blog](https://www.dotnettricks.com/learn/angular/angular-component-lifecycle-hooks-explained)**
{% endraw %}
