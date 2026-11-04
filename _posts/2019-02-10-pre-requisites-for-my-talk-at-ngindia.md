---
title: "Pre-requisites for my talk at #ngIndia"
permalink: "/2019/02/10/pre-requisites-for-my-talk-at-ngindia/"
tags: ["Speaking", "angular", "angularcli", "angularjs", "community", "javascript", "ngIndia"]
layout: "post"
date: "2019-02-10"
---

{% raw %}
Hello lovely people!

With just 13 days left for the Angular conference of India — #ngIndia, here I have put down some of the **must-knows**before you come to attend my talk on the topic “**HostBinding() & HostListener()**” in Angular.

[ngIndia](http://ng-ind.com/)is happening on February 23, 2019 in Fortuna Excalibur, Gurgaon, India. Check the conference website [**ng-ind.com**](http://ng-ind.com/)for details.

When you look at the agenda of the conference, you’ll see that all the topics require you to have the knowledge of the basic concepts of Angular. And therefore, to grab the most out of this one-day conference, you definitely need to do some homework.

Hereby, making things a little easier for you.   
 The topic that my talk is based on requires the basic knowledge of what are components, how are directives used in Angular, different types of directives, applications of Directives, can we create custom directives and most importantly, some of the terminology related to the topic because we definitely do not want to go to google every time a random heavy word is thrown into air.

Starting off with a light and ‘relevant-to-the-topic’ introduction to what components are.

A component is a basic building block of an Angular application. Components are technically directives only, with the difference being that these are the subsets of directives which always have a template of their own. The decorator @Component() defines a class as a component and defines it functioning accordingly.  
 In simple terms, it serves as a controller for user interface. It is made up of some typescript code, HTML, and CSS.

A component body looks like:

```
import { Component } from '@angular/core';

@Component({
    selector: 'appchild',
    template: `<h2>Hi {{message}}</h2>`
})
export class ChildComponent{

}
```

But, What are directives?

When we were talking about components, we used it relatively to Directives. So what directives really are! Angular builds applications with the help of directives as the major building blocks. Components are largely directives with a template. A directive modifies the DOM to change its appearance, behaviour or the layout of the elements. Directives use @Directive() decorator to mark a class as a directive and define its functionality accordingly.

Directives in Angular are of 3 types:

– Components

– Attribute Directives

– Structure Directives

Component Directives, like we defined earlier are the directives that have a template associated with them. These are also known as Self-contained directives.

Attribute Directives are the directives that change the behavior or appearance of a component, element like the font style, background color etc. Some of the built-in directives in Angular are:

* ng-bind
* ng-model
* ng-init etc.

Structural Directives, however, are used to modify the layout of the DOM elements by showing or hiding or say adding or removing the DOM elements. These are like the conditional statements.

The most commonly used structural directives are \*ngIf and \*ngFor.

One simple example of using \*ngIf is here:

```
@Component({
  selector: 'app-root',
  template: `<h2>Welcome</h2>
  <p *ngIf="show">Show</p>
  `
})

export class Component{
  public show = true;
}
```

Directives are very useful because they extend the power of an application by binding the HTML element to the application data. The most common application of directives is DOM transformation. You can do almost any task with the help of directives.  
They provide us a re-usable HTML component, a re-usable HTML behavior.

As a whole, we can do almost anything with a directive in Angular. Apart from the built-in directives that we have, we also have the liberty to create our own custom directives.  
Custom directives help us define our own functionality for the DOM elements. This is the most relevant topic for understanding HostBinding() and HostListener().

In this blog post, we’ll quickly see how to create a custom attribute directive and how it is relevant to the topic, then moving on to look at the important terminology.

To create a custom attribute directive in Angular, we’ll create a class and decorate it with the decorator @Directive(). This will be the **step 1** towards creating our custom directive.

```
import { Directive} from "@angular/core";

@Directive({
    selector: '[app-ch-color]'
})
export class bgDirective{
    constructor(){}
}
```

**Step 2**is to inject the services required for our directive. Services is a vast concept in itself, but for now to understand, we use services for component communication between two components which are not related to or dependent on each other.

```
import { Directive, ElementRef, Renderer } from "@angular/core";

@Directive({
    selector: '[app-ch-color]'
})
export class bgDirective{
    constructor(private el: ElementRef, private renderer: Renderer){
        this.changeColor('red');
    }
    changeColor(color: string){
        this.renderer.setElementStyle(this.el.nativeElement, 'color', color); 
    }
}
```

More than half of our work to create a custom directive is done here. Next step i.e. **step 3** is to register your very own directive inside the module.

```
import { BrowserModule } from '@angular/platform-browser';
import { NgModule } from '@angular/core';

import { AppComponent } from './app.component';
import { DemoDirectiveDirective } from './demo-directive.directive';

@NgModule({
  declarations: [
    AppComponent,
    DemoDirectiveDirective
  ],
  imports: [
    BrowserModule
  ],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule { }
```

**Step 4** is to go on, use the directive 😊.

```
<div app-ch-color>
  Hello Lovely people!!!
</div>
<div>
  What say now?(No Custom Attribute applied)
</div>
```

This directive that we created here, simply changes the appearance of your DOM element. I have attached the Stackblitz code of creating a custom directive in Angular here, so that you can go and play around, and COME PREPARED FOR THE TALK.



<iframe class="wp-embedded-content" data-secret="avOKUbgcOq" height="400" sandbox="allow-scripts" security="restricted" src="https://stackblitz.com/edit/custom-directive-demo?embed=1#?secret=avOKUbgcOq" title="custom-directive-demo - StackBlitz" width="745"></iframe>



However, we can always change the functionality or apply the directive only when a particular event is raised. We can also change only a specific property of the host element. We can instruct Angular to change the appearance only when the user clicks on the element or change only a particular property when the user hover over the element. To do these add-ons to our custom directives, we use HostBinding() and HostListener() and this is what the talk will be about.

---

Before we think we are ready to learn what’s next, let us take a quick look on the terminology important for us to understand better.

We recently used a word, Host Element when talking about applying custom directives specifically. A host element is that HTML element which we apply our custom directive to.  
 So suppose in the above case,

**If***[app-ch-color]***is your directive, the host element will be this***div* **on which you have applied this directive.**

Services are injected when we need our components to communicate with each other. There are different ways of component communication like using Input(), Output(), but when two components do not depend on each other for their working and are totally independent, we need services.

HostListener() as the name suggests, is used when we want to capture the event of our Host Element and work as the event directs to.

HostBinding(), on the other hand, is used when the property of the Host Element needs to be captured and made changed to.
{% endraw %}
