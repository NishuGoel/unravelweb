---
title: "Working with Hasura in Angular 6"
permalink: "/2018/12/13/working-with-hasura-in-angular-6/"
tags: ["angular", "angularcli", "angularjs", "graphql", "hasura", "javascript", "javascripttalks"]
layout: "post"
date: "2018-12-13"
---

{% raw %}
In this article, we will work with setting up a login application with the Hasura’s GraphQL engine using Angular 6.   
Starting with a small description about GraphQL and Hasura’s GraphQL engine.

**GraphQL**GraphQL is an open source data query and manipulation language, and a runtime for fulfilling queries with existing data. It is designed to build client applications by providing an intuitive and flexible syntax and system for describing their data requirements and interactions.

**Hasura’s GraphQLEngine**The Hasura GraphQL Engine is an extremely lightweight, high-performance product that gives you instant real-time GraphQL APIs on a Postgres database. This can be used to quickly build new applications on Postgres or fast-track the move to GraphQL for existing applications on Postgres.

To start working with these inside an Angular 6 or above application, **Step 1** is to set up Angular for Hasura inside our system. To do that, we need to open the terminal and implement the following commands.

Assuming Angular CLI is already installed globally, use:

> $ ng new hasura-app –routing  
> $ cd hasura-app

If Angular CLI isn’t installed already, install using:

`$ npm install -g @angular/cli`

`And run the application on localhost:4200 using:`

`$ ng serve`

Now, **Step 2** is to set up Apollo Client which helps us build a UI that fetches the data from the GraphQL server. To install Apollo, use:

$ npm install apollo-angular apollo-angular-link-http apollo-client apollo-cache-inmemory graphql-tag graphql

Once done with that, **Step 3** is to set up your Hasura’s engine on Heroku, using the **HASURA\_GRAPHQL\_ACCESS\_KEY**, Creating a Table with all the custom checks and permissions provided.

Now, coming to **Step 4**, we use Auth0 to set up our application that will login to our Angular app.

Create a new application on **Auth0**, set it up as Single Page Application, and give the callback URL as: <http://localhost:4200>

Finally, configuring the Apollo client to interact with Hasura Engine, we create a new GraphQL module. Like this:

```typescript
import { NgModule } from '@angular/core';

import {HttpClient, HttpHeaders, HttpClientModule} from '@angular/common/http';
import {Apollo, ApolloModule} from 'apollo-angular';
import {HttpLink, HttpLinkModule} from 'apollo-angular-link-http';
import {InMemoryCache} from 'apollo-cache-inmemory';
import {stringify} from '@angular/compiler/src/util';


@NgModule({
  exports:[
    HttpClientModule, ApolloModule, HttpLinkModule

  ]
})
export class GraphQLModule {
  constructor(apollo:Apollo, httpLink: HttpLink){
    const uri = 'https://hasura-app.herokuapp.com/vlalphal/graphql';

    const authHeader = new HttpHeaders()
    .set('X-HASURA-ACCESS-KEY', 'secret')
    .set('ContentType', 'application/json')
    .set('Authorisation', `Bearer ${localStorage.getItem('access_token')}`)
    .set('X-Hasura-Role', 'user')
    .set('X-Hasura-User-Id', stringify(localStorage.getItem('userId')))

    console.log(localStorage.getItem('user_id'));
    const http = httpLink.create({uri, headers: authHeader});

    apollo.create({
      link: http,
      cache: new InMemoryCache()
    });
  }
 }
```

We can further organize our application create more components providing queries inside a query.ts file.

By the end, your code should look like this:

```typescript
import { Component, OnInit } from '@angular/core';
import { AuthService } from './auth.service';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent implements OnInit {

  constructor(public auth: AuthService) {
    auth.handleAuthentication();
  }

  ngOnInit() {
    if (localStorage.getItem('isLoggedIn') === 'true') {
      this.auth.renewSession();
    }
  }

}
```

**app.component.html**

```html
<nav class="navbar navbar-default">
  <div class="container-fluid">
    <div class="navbar-header">
      <a class="navbar-brand" href="#">Auth0 - Angular</a>

      <button
        class="btn btn-primary btn-margin"
        routerLink="/">
          Home
      </button>

      <button
        class="btn btn-primary btn-margin"
        *ngIf="!auth.isAuthenticated()"
        (click)="auth.login()">
          Log In
      </button>

      <button
        class="btn btn-primary btn-margin"
        *ngIf="auth.isAuthenticated()"
        (click)="auth.logout()">
          Log Out
      </button>

    </div>
  </div>
</nav>

<main class="container">
  <router-outlet></router-outlet>
</main>
```

**app.component.html**

While injecting the service, **auth.service.ts**,

```typescript
// src/app/auth/auth.service.ts

import { Injectable } from '@angular/core';
import { Router } from '@angular/router';
import { filter } from 'rxjs/operators';
import * as auth0 from 'auth0-js';

@Injectable()
export class AuthService {

  private _idToken: string;
  private _accessToken: string;
  private _expiresAt: number;

  auth0 = new auth0.WebAuth({
    clientID: 'fcesrulTTieGc3TEK0PrOaRQeNrqF12u',
    domain: 'nishugoe.auth0.com',
    responseType: 'code',
    redirectUri: 'http://localhost:4200/callback',
    scope: 'openid'
  });

  constructor(public router: Router) {
    this._idToken = '';
    this._accessToken = '';
    this._expiresAt = 0;
  }

  get accessToken(): string {
    return this._accessToken;
  }

  get idToken(): string {
    return this._idToken;
  }

  public login(): void {
    this.auth0.authorize();
  }

  public handleAuthentication(): void {
    this.auth0.parseHash((err, authResult) => {
      if (authResult && authResult.accessToken && authResult.idToken) {
        window.location.hash = '';
        this.setSession(authResult);
        this.router.navigate(['/home']);
      } else if (err) {
        this.router.navigate(['/home']);
        console.log(err);
      }
    });
  }

  private setSession(authResult): void {
    // Set isLoggedIn flag in localStorage
    localStorage.setItem('isLoggedIn', 'true');
    // Set the time that the access token will expire at
    const expiresAt = (authResult.expiresIn * 1000) + new Date().getTime();
    this._accessToken = authResult.accessToken;
    this._idToken = authResult.idToken;
    this._expiresAt = expiresAt;
  }

  public renewSession(): void {
    this.auth0.checkSession({}, (err, authResult) => {
      if (authResult && authResult.accessToken && authResult.idToken) {
        this.setSession(authResult);
      } else if (err) {
        alert(`Could not get a new token (${err.error}: ${err.error_description}).`);
        this.logout();
      }
    });
  }

  public logout(): void {
    // Remove tokens and expiry time
    this._accessToken = '';
    this._idToken = '';
    this._expiresAt = 0;
    // Remove isLoggedIn flag from localStorage
    localStorage.removeItem('isLoggedIn');
    // Go back to the home route
    this.router.navigate(['/']);
  }

  public isAuthenticated(): boolean {
    // Check whether the current time is past the
    // access token's expiry time
    return new Date().getTime() < this._expiresAt;
  }

}
```
{% endraw %}
