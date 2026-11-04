---
title: "Creating your first Angular project"
permalink: "/2018/10/17/creating-your-first-angular-project/"
tags: ["angular", "angularcli", "angularjs", "javascript", "javascripttalks", "js"]
layout: "post"
date: "2018-10-17"
---

{% raw %}
In this blog post, we will see how to create a new project and start working with all the concepts in Angular.

Some of the pre-requisites to begin with are:  
– Installed Node.js and Node Package Manager (NPM)  
– Installed Angular CLI  
– Visual Studio Code

Step 1 is to go to the command prompt and create a new Angular project. Make sure that you are inside the directory where you want to create this new project. The command used to create a new project is

> **ng new *project-name***

In this command, we instruct Angular CLI to create a new project using the new keyword and provide it with the name of the project. And then when we press **Enter,**various operations will start running on the terminal.

![ng](/assets/img/31e848-ng-e1539773088183.png)

![ng (1)](/assets/img/eac01c-ng-11.png)

CLI just created a new angular project for us with all the required modules and components.  
Let us go to Visual Studio Code and see what has been done for us by CLI. To go to VS Code from the command prompt, we use:

> ***code .***

Inside VS Code now, we see CLI has create the component file and the app module for us. It looks like this:

![ng](/assets/img/2bc6e1-ng1.png)

Now, let us create a very simple program where in we want to display some text on the browser. Let us go to the HTML file of our AppComponent.

![ng](/assets/img/156ac0-ng2.png)

Inside the **app.component.ts**,

![ng](/assets/img/6a42d0-ng3.png)

The **app.module.ts** looks like this:

![ng](/assets/img/41506b-ng4.png)

Now that we have created our program, let us go and compile it.

To compile an Angular project, we go to the terminal and use the command:

> **ng serve**

![ng](/assets/img/f317ba-ng5.png)

We could compile our program successfully. CLI also displays the port no. which will be used on the browser.

In our case, the port is **localhost:4200**

![ng](/assets/img/840027-ng6.png)

We can also change the port no. in case the port that we are trying to access is already in use. To do that, we use the command:

> **ng serve –port portno**

![ng](/assets/img/2f8f05-ng7.png)

Now, let us try to access this port on the browser,

![nfg](/assets/img/95f0e0-nfg.png)

And we have successfully created our first program.
{% endraw %}
