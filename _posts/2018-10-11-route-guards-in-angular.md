---
title: "Route Guards in Angular"
permalink: "/2018/10/11/route-guards-in-angular/"
tags: ["angular", "angularcli", "angularjs", "javascript", "javascripttalks", "js"]
layout: "post"
date: "2018-10-11"
---

{% raw %}
We have worked with routing and navigating from one route to another in our previous articles. If you are new to Routing, refer to: [Routing in Angular](https://nishugoel.wordpress.com/2018/10/10/creating-basic-routes-in-angular/)

##### 1 Usages of Route Guards

While navigating from one route to another, there are situations when we do not want an unauthenticated user to access a particular route and that is where we want to keep a check. For example, A user has subscribed to an Angular course on an online platform but he has not subscribed to any other course on the same platform, in that case, the route to the angular course page would work for him but the routes to other course modules should not be accessible by him. This is where **Route Guards** come into play!

So, in simple terms, we use guards to put a check to restrict the user from accessing some of the pages of our site. If the returned value by the guard is true, the user can continue navigating from one route to another, otherwise the process halts.

The return type of a route guard can be of two kinds:

* Promise <Boolean>(synchronous)
* Observable <Boolean> (asynchronous)

Route Guards are of different types, used as per their functionalities. They are:

* CanActivate
* CanActivateChild
* CanDeactivate
* Resolve
* CanLoad

In this blogpost, we will learn how to work with **CanActivate** Route Guard. To begin with, let us import:

> **import {CanActivate} from ‘@angular/router’;**

Next step is to create an Injectable class which will implement our CanActivate() function

```
class RouteGuardDemo implements CanActivate{
       CanActivate(){
                console.log("Guard Implemented");
                return true;
        }
}
```

Since Guard is a service, we need to declare it inside the providers array in the module.

> @NgModule({  
> providers: [  
> RouteGuardDemo  
> ]  
> })

Now to use this guard that we created, we need to use it inside one of the routes. So, suppose we have two components **FirstComponent** and **SecondComponent**, and the user is trying to route from first component to the second component.

```

const routes: Routes = [
  {path:'first', component:FirstComponent, canActivate: [RouteGuardDemo]},
  {path:'second', component:SecondComponent},
];

@NgModule({
  imports: [RouterModule.forRoot(routes)],
  exports: [RouterModule]
})
export class AppRoutingModule { }
```

We added our **RouteGuardDemo** to the list of **CanActivate** guards now. Everytime we try to navigate from FirstComponent, the guard gets implemented and we will get a message in our console as “**Guard Implemented**“.  
Similarly, there are different functionalities for each guard that can be implemented.

Another important thing with guards is that the function parameters. there are certain arguments that need to be passed in the guard function to provide/restrict the access to the user. These are:

* **component: Component**

This is the component that we are using for the route guard.

* **state: RouterStateSnapshot**

This is the RouterState of the next component, if the guard is successfully executed. The URL of the next route that the user is trying to navigate to, can be figured out then from the URL property.

* **route: ActivatedRouteSnapshot**

This is the next route that will activate if the guard returns true value and is successfully passed.

### **Summary**

In this blog post, we learn what are Route Guards and why are they required. We also see how navigation can be controlled using the route guards. Then we look at the different types of Route Guards in Angular and also implement the functionality of one of the route guards from all. There are some parameters that need to be passed to the guard function, which are covered in the last section of the article.
{% endraw %}
