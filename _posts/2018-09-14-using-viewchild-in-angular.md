---
title: "Using @ViewChild in Angular"
permalink: "/2018/09/14/using-viewchild-in-angular/"
tags: ["angular", "angularcli", "angularjs", "javascript", "javascripttalks", "js"]
layout: "post"
date: "2018-09-14"
---

{% raw %}
A ViewChild is a component, directive, or element as a part of a template. If we want to access a child component, directive, DOM element inside the parent component, we use the decorator @ViewChild() in Angular.

To understand this, suppose we have two components, a child and a parent one. Since the child component can be located inside the parent component, it can accessed as @ViewChild.

```typescript
export class AppComponent implements OnInit, AfterViewInit {
    message: any;
    @ViewChild(ChildComponent) chviewChild: ChildComponent;
 
    ngAfterViewInit() {
        console.log(this.chviewChild);
    }
 
    ngOnInit() {
        this.message = 'Hello World !';
    }
}
```

In the above code, we imported @ViewChild decorator and then imported the lifecycle hook AfterViewInit and implemented it. Now, to change the property value, we can make use of the viewchild we just create like:

> ngAfterViewInit(){  
> this.chviewChild.message = ‘Changed value of View Child’  
> }

This will output the value **Changed value of View Child,** but will throw an error saying “**Expression has changed after it was last checked**”.

![](/assets/img/755e7d-c6dea-18zrcnmxoi3fo4vgqbiqlka.jpeg)

To handle this error, we use Change detection using ***ChangeDetectorRef***

```typescript
constructor(private cd: ChangeDetectorRef) {}
 
ngAfterViewInit() {
    console.log(this.chviewChild);
    this.chviewChild.message = 'Changed value of View Child';
    this.cd.detectChanges();
}
```

Here, we have imported ***ChangeDetectorRef***from ‘@angular/core’ and injected it to the constructor. We have also called the method ***detectChanges()***.

This was for one child element located inside the component template, but what in the case when we have multiple references to the child element?  
That is when @ViewChildren comes into play.

```typescript
export class AppComponent implements OnInit {
    messages: any;
    ngOnInit() {
        this.messages = this.getMessage(); 
    }
    getMessage() {
        return [
            'Hi',
            'Hello',
            'How are you?'
        ];
    }
}
```

Modifying the template,

```typescript
@Component({
    selector: 'app-root',
    template: `
  <div>
  <app-child *ngFor="let i of messages" [message]='i'></app-child
  </div>`
})
```

Finally, marking the reference of ViewChildren with type QueryList,

```typescript
@ViewChildren(ChildComponent) chviewChildren: QueryList<ChildComponent>;
ngAfterViewInit() {
    console.log(this.chviewChildren);
}
```

Now, we can update the value of the message property using Viewchildren inside the ngAfterViewinit() life cycle hook like this:

> **this.chviewChildren.forEach((item) => {item.message = ‘Updated Value’;});**

Let us look at the final code now:

```
import { Component, Input, OnInit, ViewChild, AfterViewInit, ChangeDetectorRef, ViewChildren } from "@angular/core";
import { ChildComponent } from "./child.component";
import { QueryList } from "@angular/core";

@Component({
  selector: 'app-root',
  template:`
  <app-child *ngFor = 'let i of message' [message] = 'i'></app-child>
  `
})
export class AppComponent implements OnInit, AfterViewInit{
  constructor(private cd: ChangeDetectorRef){}
  ngAfterViewInit() {
    console.log(this.chviewChildren);
    this.chviewChildren.forEach((item) =>{item.message = "Updated Value"; });
    this.cd.detectChanges();
  }
  message: any;
  @ViewChildren(ChildComponent) chviewChildren: QueryList<ChildComponent>;
  
  ngOnInit(){
    this.message = this.getMessage();
  }
  getMessage(){
    return[
      'Hi',
      'Hello',
      'How are you?
    ];
  }
}
```

This gives us the output as:

![11.JPG](/assets/img/8ad462-11.jpg)
{% endraw %}
