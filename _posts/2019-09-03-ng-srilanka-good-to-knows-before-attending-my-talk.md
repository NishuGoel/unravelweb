---
title: "ng-Srilanka: Good to knows before attending my talk"
permalink: "/2019/09/03/ng-srilanka-good-to-knows-before-attending-my-talk/"
tags: ["Uncategorized", "angular", "angular2", "javascript"]
layout: "post"
date: "2019-09-03"
---

{% raw %}
Hey everyone!

In around 10 days from today, I will be speaking at ng-Srilanka, the first ever Angular conference of SriLanka. I will be speaking on the topic “Creating Libraries in Angular” on 14th September, 2019, along with some other great speakers.

The purpose of this blog post is to make sure you are well-versed with the very basic concepts of Angular before attending the talk. This would make it easier for you and myself to dive deeper into the topic and discuss the internal working of the files and packages when creating libraries in Angular.

### I will be listing down some of the important concepts to know before learning how to create libraries.

* Basic building blocks of Angular  
  – Components  
  – Modules  
  – Services
* Angular CLI commands syntax  
  – ng generate component *<component-name> OR* ng g c *<component-name>  
  –* ng generate module *<module-name> OR* ng g m *<module-name>  
  –* ng generate service *<service-name>* *OR* ng g s *<service-name>*

> **Similarly,ng generate library *<library-name>***

* Understanding the structure of package.json

A basic example:sample-package.json

Read about each one of these here: <https://nodesource.com/blog/the-basics-of-package-json-in-node-js-and-npm/>

* Understanding semantic versioning

> <https://semver.org>

* npm commands  
  – npm install  
  – npm lint  
  – npm build  
  – npm test  
  – npm link  
  – npm pack, etc.
* And most importantly, the Angular documentation for the overview of Libraries here: <https://angular.io/guide/libraries>

Before Angular 6, The CLI did not have support for creating a library using the command and the files needed to be created manually and implemented using ng-packagr, a project on npm and Github, which allows libraries to be built and packaged using a single command.

See the blog post below to understand the manual creation of a library: <https://medium.com/swlh/angular-library-with-ng-packagr-13f20ed202bd>

With an idea of all these terms and concepts, you are good to go and I hope to talk about the topic in the most convenient and easy manner.

*See you all!*

*Mark the date! 14th Sep*  
*Check the speakers, talk topics, schedule etc. here : ng-srilanka.com*
{% endraw %}
