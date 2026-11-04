---
title: "Understanding Services and Dependency Injection"
permalink: "/2018/08/24/understanding-services-and-dependency-injection/"
tags: ["angular", "angularcli", "angularjs", "javascript", "javascripttalks", "js"]
layout: "post"
date: "2018-08-24"
---

{% raw %}
We’ve all worked with Components and used component communication, but what do we do if we want to share data or logic across components?

> WE BUILD SERVICES.

Let us try to understand what exactly services are.  
So, a service is basically a class, but with a focused purpose. With services, the code becomes easy to test, debug, and reuse.

So the component that needs a service can use it in two ways:  
1) Creating an instance of the service class  
2) Registering the service in the module

If the component needs the services, the component class defines the service as a dependency. The Angular Injector then injects the service. This process is called Dependency Injection. It looks like this:

![](/assets/img/a9e5ef-84809-1fzfwvi4trzy4ram-ennsfq.jpeg)

So, when a class receives the instances of objects that it needs from an external source rather than creating them itself, it is called Dependency Injection.

Steps to build a service:  
1) Create a Service class  
2) Use a decorator to define it  
3) Import it

https://gist.github.com/NishuGoel/d59b48ddfcfbf0d882eb34925ce26718

We have built a service, but remember our service is just a normal class unless we register it in the module.

Angular injects services with root injector(available to all the components) or with specific component injector(available to only that component and its child)

Let us register the service with the root injector like this:

https://gist.github.com/NishuGoel/1803b5df3c4a9b25577ada9db6b6284b

This is how we can access this service from any component or any other service now.  
In case, you want to access this service from only one component, this is how you do this.

In the product.component.ts,

https://gist.github.com/NishuGoel/6ac8d024336e257a501dc8b0c7da82d9

For Injecting the service now, the angular injector uses a constructor to inject an instance of the class. Like this,

https://gist.github.com/NishuGoel/39fd84bc60868bd48c50ab1e20f15261

Now finally to use our service, let us call it.

https://gist.github.com/NishuGoel/f8e9a8f2dfd09b30b1f1f2f77882bc63

And we are done creating our service and injecting it.
{% endraw %}
