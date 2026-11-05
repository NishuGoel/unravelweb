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

```
import {Component, provide} from '@angular/core';
import {bootstrap} from '@angular/platform-browser-dynamic';
import {Store, createStore, StoreEnhancer} from 'redux';
import {indexReducer} from './index-reducer';
```

In the above stated import statements, we have imported class ***Store*** and ***createStore*** which is a creator function inside ***Redux***. We have also imported a new class ***StoreEnhancer***and ***indexReducer*** from *index-reducer.ts* file that we will create.

Let us now create our AppState as:

```
export interface AppState{
  index: number;
};
```

To define our reducer now that we need to integrate our Angular app with Redux,

```
 import { INCREMENT, DECREMENT } from './index-action-creators';
 let initialState: AppState = {index: 0 };
 
 export const indexReducer: Reducer<AppState> =(state: AppState = initialState, action Action): AppState => {
 switch(action.type){
  case INCREMENT: return Object.assign({}, state, { counter: state.counter +1});
  case DECREMENT: return Object.assign({}, state, { counter: state.counter -1});
  default:
  return state;
 
 }
 };
```

Here, we have our AppState as initialState, setting the counter to zero and two constants INCREMENT and DECREMENT exported by our action creators.

Now, defining our action creators,

```
import {Action, ActionCreator} from 'redux';

export const INCREMENT: string = 'INCREMENT';
export const increment: ActionCreator<Action> = () => ({type: INCREMENT});

export const DECREMENT: string = 'DECREMENT';
export const decrement: ActionCreator<Action> = () => ({type: DECREMENT});
```

Here, action creator functions return the type **ActionCreator<Action>**. **ActionCreator** is a generic class in Redux which is used to define functions that create actions.

Finally, creating the Store,

```
let store: Store<AppState> = createStore<AppState>(indexReducer);
```

Now that we have fully set up our Redux, let us go to our **IndexComponent** and provide it with the store that we create inside Redux.  
Another thing to make sure of here is that since store is created using Redux, we need to make it accessible everywhere inside our application, and to do that we use dependency injection (DI), using the provide function.

Since we have already created our store and do not want Angular to create it, we will use ***useValue*** instance of the **provide** function like this:

> provide(API\_URL, { useValue: ‘…’ });

Bootstrapping our app now,

> bootstrap( indexApp, [  
> provide(AppStore, useValue:  store}),  
> ])

Let us have  a look at our **IndexComponent** now:

```
@Component({
  selector: 'index-component',
  template: `
    <p>The index value is {{index}}</p>
    <p> <button (click) = "increment()"> Increment </button>
    <button (click) = "increment()"> Increment </button> </p>
    
    export class IndexComponent{
    index: number;
    
    
    constructor(@Inject(AppStore) private store: Store<AppState>){
      store.subscribe(() => this.readState());
      this.readState();
      }
      readState(){
      let state: AppState = this.store.getState() as AppState;
      this.index =state.index;
      }
      increment(){
        this.store.dispatch(IndexActions.increment());
      }
      decrement(){
        this.store.dispatch(IndexActions.decrement());
      }
    }
  
  `
```

We can create more complex angular components with Redux.
{% endraw %}
