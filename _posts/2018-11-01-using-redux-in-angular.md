---
title: "Using Redux in Angular"
permalink: "/2018/11/01/using-redux-in-angular/"
tags: ["angular", "angularcli", "angularjs", "bootstrap", "bs", "javascript", "javascripttalks", "js", "redux"]
layout: "post"
date: "2018-11-01"
---

{% raw %}
In this blog post, we will see how to integrate and use **Redux** with **Angular**. Before beginning, let us have a basic understanding of what **Redux** is!

**Redux** is an open-source JavaScript library that can be used with any other view library like React, Angular etc. The best perk of using **Redux** is that in larger applications with a lot of moving parts in it, we can easily maintain performance and testability. **Redux** is also known to provide great developer experience.

To read more about **Redux**, go to its [official documentation](https://redux.js.org/)

![A New Design - Made with PosterMyWall (1)](/assets/img/36afed-a-new-design-made-with-postermywall-1.jpg)

To move further, let us create a simple angular application inside which we want to simply increment or decrement a counter with a button. While creating this app, our major focus will be on the process of integration between Angular and Redux.

Starting with step 1 in the process, we will need to create a top-level app which contains our component displaying the view. At the next level, we need to perform 3 basic steps of Redux:

1. Create a Reducer
2. Define Action Creators
3. Create Stores

a. Create *Store* and inject it using Dependency Injection  
b. Subscribe to the changes made inside the store and displaying them on the browser  
c. Whenever user does activity on it, perform an action on the store.

To set up Redux, we need to import few important classes.

https://gist.github.com/NishuGoel/cfd65f7da0cd2e1418f5e4a4178f16f3

In the above stated import statements, we have imported class ***Store*** and ***createStore*** which is a creator function inside ***Redux***. We have also imported a new class ***StoreEnhancer***and ***indexReducer*** from *index-reducer.ts* file that we will create.

Let us now create our AppState as:

https://gist.github.com/NishuGoel/83426e0aacd29a5096f4c41c294d7927

To define our reducer now that we need to integrate our Angular app with Redux,

https://gist.github.com/NishuGoel/93f3aa25e1faa10011b52008128f2720

Here, we have our AppState as initialState, setting the counter to zero and two constants INCREMENT and DECREMENT exported by our action creators.

Now, defining our action creators,

https://gist.github.com/NishuGoel/e46c14a0c3ade1ccdb198f6286604fcb

Here, action creator functions return the type **ActionCreator<Action>**. **ActionCreator** is a generic class in Redux which is used to define functions that create actions.

Finally, creating the Store,

https://gist.github.com/NishuGoel/8f0d5de6f133febe09032a4c1c9f63e9

Now that we have fully set up our Redux, let us go to our **IndexComponent** and provide it with the store that we create inside Redux.  
Another thing to make sure of here is that since store is created using Redux, we need to make it accessible everywhere inside our application, and to do that we use dependency injection (DI), using the provide function.

Since we have already created our store and do not want Angular to create it, we will use ***useValue*** instance of the **provide** function like this:

> provide(API\_URL, { useValue: ‘…’ });

Bootstrapping our app now,

> bootstrap( indexApp, [  
> provide(AppStore, useValue:  store}),  
> ])

Let us have  a look at our **IndexComponent** now:

https://gist.github.com/NishuGoel/bcfe5a06d8b16bebdf49a23eedacdb8a

We can create more complex angular components with Redux.
{% endraw %}
