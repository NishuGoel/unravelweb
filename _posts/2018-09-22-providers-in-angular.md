---
title: "Providers in Angular"
permalink: "/2018/09/22/providers-in-angular/"
tags: ["angular"]
layout: "post"
date: "2018-09-22"
---

{% raw %}
We have learnt the concept of Services and Dependency injection in our previous article. Read here: [Understanding Services and Dependency injection](https://nishugoel.wordpress.com/2018/08/24/understanding-services-and-dependency-injection/)

When we inject a service, the Angular injector needs to look at the Service providers to create an instance of that particular service.  The provider determines which instance of the service should be injected at the runtime in the component, module, pipe or directive.

To understand, let us create a service first.

```typescript
import {Injectable} from '@angular/core';

@Injectable()
export class HelloService{
    sayHello(msg: String){
        console.log(msg);
    }

}
```

Inside the component,

```typescript
import { Component } from '@angular/core';
import {HelloService} from './hello.service';


@Component({
  selector: 'app-root',
  template:`
  <input [(ngModel)]='msg' type='text'/>
  <button (click)='apserv()'>Apply Service</button>
  
  `,
  providers: [HelloService]
})
export class AppComponent {
  constructor(private hservice: HelloService){}
  msg: String;
  apserv(){
    this.hservice.sayHello(this.msg);
  }
}
```

Here, we imported the service, injected it and used it inside the component to log the hello message. Also, we provided the injected service inside the providers array. Let us look at the output.

![1](/assets/img/309860-11.png)

After applying the service,

![2](/assets/img/8ea2f9-2.png)

A providers therefore, determines that how the object of a particular token is created.

**TYPES OF PROVIDERS**

1. Type Provider
2. Class Provider
3. Value Provider
4. Existing Provider
5. Factory ProviderThe syntax for using providers is :

> providers: [{  
> provide: HelloService, useClass: HelloService  
> }]

The provide property here is used for locating the dependency value and registering the dependency. On the other hand, the second parameter  has 4 different values:

1. useClass
2. useExisting
3. useValue
4. useFactory

### **useExisting**

This is used to avoid creating two instances of the same Service. Inside the new service,

```typescript
import {Injectable} from '@angular/core';

@Injectable()
export class NewService{
    sayHello(msg: String){
        console.log("Here is the message: " +msg);
        document.write("New Service executed")
    }

} 
```

To use **useExisting inside the component now,**

```typescript
import { Component } from '@angular/core';
import {FormsModule} from '@angular/forms';
import {HelloService} from './hello.service';
import {NewService} from './new.service';


@Component({
  selector: 'app-root',
  template:` 
  <input [(ngModel)]='msg' type='text'/>
  <button class = 'btn btn-success' (click)='apserv()'>Apply Service</button>
  
  `,
  providers: [NewService, {provide: HelloService, useExisting: NewService}]
})
export class AppComponent {
  constructor(private hservice: HelloService){}
  msg: String;
  apserv(){
    this.hservice.sayHello(this.msg);
  }
}
```

![3](/assets/img/603095-3.png)

## **useValue**

When we do not want to create an instance but pass the object directly, we use **useValue****.**

```typescript
import { Component } from '@angular/core';
import {FormsModule} from '@angular/forms';
import {HelloService} from './hello.service';
import {NewService} from './new.service';


@Component({
  selector: 'app-root',
  template:` 
  <input [(ngModel)]='msg' type='text'/>
  <button class = 'btn btn-success' (click)='apserv()'>Apply Service</button>
  
  `,

  providers: [
        {
            provide: HelloService, useValue: {
                sayHello: function (msg) {
                    console.log('using useValue');
                    document.write("using useValue");
                }
            }
        }]


})

export class AppComponent {
  constructor(private hservice: HelloService){}
  msg: String;
  apserv(){
    this.hservice.sayHello(this.msg);
  }
}
```

Output:

![4](/assets/img/0a2a67-4.png)

### **useFactory**

When the information about our dependency is dynamic, that is when **useFactory** comes into play.

```typescript
import { Component } from '@angular/core';
import {FormsModule} from '@angular/forms';
import {HelloService} from './hello.service';
import {NewService} from './new.service';


@Component({
  selector: 'app-root',
  template:` 
  <input [(ngModel)]='msg' type='text'/>
  <button class = 'btn btn-success' (click)='apserv()'>Apply Service</button>
  
  `,
  //providers: [NewService, {provide: HelloService, useExisting: NewService}]
  providers: [
        {
            provide: HelloService, useFactory: () => {
                let i = 0;
                if (i === 0)
                    return new HelloService();
                 else
                    return new NewService();
            }
        }
    ]
})
export class AppComponent {
  constructor(private hservice: HelloService){}
  msg: String;
  apserv(){
    this.hservice.sayHello(this.msg);
  }
}
```

Here, when the value of i equals 0, the output comes from the first service, i.e., HelloService, in any other case, the output comes from the second service, i.e., NewService.

To see the working of what we just created , go to my project here on Stackblitz (<https://angular-9bljze.stackblitz.io>) and try yourself!
{% endraw %}
