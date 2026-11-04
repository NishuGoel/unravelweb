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

https://gist.github.com/NishuGoel/1f69956630d198bdfd370da673c436d5

We can further organize our application create more components providing queries inside a query.ts file.

By the end, your code should look like this:

https://gist.github.com/NishuGoel/67366047787534cecfbb7f64b467a66d

**app.component.html**

https://gist.github.com/NishuGoel/1363dd2c5b720f3491cb68a68fe747ec

**app.component.html**

While injecting the service, **auth.service.ts**,

https://gist.github.com/NishuGoel/468f53b3ddcedc9b983c4b29cdd593aa
{% endraw %}
