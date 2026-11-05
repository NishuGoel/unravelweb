---
title: "Error: Cannot match any routes"
permalink: "/2018/12/07/error-cannot-match-any-routes/"
tags: ["angular", "angularcli", "angularjs", "javascript", "javascripttalks"]
layout: "post"
date: "2018-12-07"
---

{% raw %}
In Angular, when working with routing, we face this error “***Cannot match any routes***” very commonly. This generally occurs when there is a mismatch in the routes specified, or a component which is not present in our routing configuration, or if there is the use of multiple routes in our angular application which is not properly configured. In this blog post, we will see how the third reason brings out this error and how can it be solved.

An angular router is the one that makes an angular application a Single-page application. The Angular router helps in navigation to different components by matching the ***path*** of a particular URL and if it does get matched, the ***component*** gets displayed.

This routing configuration looks like:

```
const routes: Routes = [
{path: 'first', Component: 'FirstComponent'},
{path: 'second', Component: 'SecondComponent},
{path: '**', Component: 'PageNotFoundComponent}

;
```

Now when we say the component has to get displayed, we have not specified where the component needs to get displayed. To specify that, ***RouterOutlet*** comes into play.

When the path URL gets matched, and it looks forward to displaying the corresponding component, it needs to look for a router-outlet component in the template of the component.

***RouterOutlet*** is actually a dynamic component that displays the components mentioned and matched in the routing configuration. The next important step is to bootstrap the router by importing the ***RouterModule*** in the App Module file.

There is always a default outlet in the angular template, which is known as the ***Primary Outlet***. This is called unnamed outlet. When it comes to displaying different components in the different parts of the application, we can use multiple outlets for that.

Yes, in Angular, we can use multiple outlet for different content on different parts of our SPAs (Single page applications). These secondary outlets are known as ***named outlets***.

For example, we want a sidebar and a main body on our application. Now to route to both the parts and the components, we would need multiple outlets.

Now, any other outlet than the primary one is the one that needs a name, and that is the reason it is called a named outlet. This specified name of the outlet also needs to be specified in the routing configuration with the attribute ***outlet***.

> { path: ‘first’, component: FirstComponent, outlet: ‘addr’ }

Now since, both the routes are active at the same time, the router needs some way of differentiating between the two router outlets.

So a major difference is, that whenever the secondary routes are navigated to, they are inside a bracket.

> localhost:4200/home(addrbar: first)

Routing generally occurs independently of the outlets. However, when an ***absolute Redirect*** is used, the router outlets become dependent on one another.
{% endraw %}
