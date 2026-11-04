---
title: "Creating a LitElement"
permalink: "/2019/12/25/creating-a-litelement/"
tags: ["angular", "customElements", "html", "javascript", "polymer", "webcomponents"]
layout: "post"
date: "2019-12-25"
---

{% raw %}
This is a very basic blog post on how to create a simple web component using Polymer [**LitElement**](https://lit-element.polymer-project.org/).

A web component is basically a view with functionality that you can reuse in any frameworks on any web page. Such a web component can then simply be used by just using the element as:

> <my-web-comp></my-web-comp>

inside your web page built in any framework.

Web components work on the four web standards:

* Custom elements
* Shadow DOM
* ES5 Modules
* HTML templates

Dive deeper into web components [**here**](https://developer.mozilla.org/en-US/docs/Web/Web_Components).

Here, we will focus on how to create a web component using Polymer’s [**LitElement**](https://lit-element.polymer-project.org/) which uses lit-html to render the web component or the custom element as nodes in the shadow DOM tree.

### Getting set up

First thing first, we need to install node and npm. If we have that, we proceed to install polymer cli which which help us create a custom element in a polymer project.

To install polymer CLI,

> `npm install -g polymer-cli`

We can run our project and serve it simply like :

> `polymer serve`

Once your project setup is ready, you can start with creating the first lit element.

### Create a Custom Element

The first step here would be to install litElement using npm inside your project.

> `npm install lit-element`

Create a .js file for your web component now. Lets call it `myWebComp.js`

In this file, you would include the lit element from the library you just installed:

```
import { LitElement, html } from 'lit-element';
```

Then create a class for your element extending the LitElement,

```
export class myWebComp extends LitElement {
  render() {
    return html `<div>text here</div>`
  }
}
```

Any element created with **LitElement** should have an implementation of render() function to render your template. This render function should return a Template result of lit-html. To create this template result, we use :

```
return html`<!--template comes here-->    `;
```

### Register the custom element

Now, the next step is to register this custom element with the browser, to do that, we use the customElements DOM API as:

```
customElements.define('my-web-comp', myWebComp);
```

In Typescript, we can avoid explicitly registering the custom element with the browser by using `@customElement` decorator.

```
@customElement('my-web-comp')
export class myWebComp extends LitElement {

  @property()
  compProp = 'hello';

  render(){
    return html`<p>${this.compProp}</p>`;
  }
```

This way, we create our custom element using **LitElement** and register it with the browser.

Now, we are ready to use this as a web component in our different projects. Let us see how:

To use it in any other project of yours locally, you can simply place the path to your custom element and the element in the `.html` file.

```
<html>
<head>
  <script type="module" src="/path/to/my-web-comp.js"></script>
</head>
<body>
  <my-web-comp></my-web-comp>
</body>
</html>
```

To be able to use it in any of you other projects, you can publish it as a package to npm and make it ready-for-use for other projects/developers.

To see how to publish a web component as a package to npm, check the **Publishing to npm** section of [**this blog post**](https://medium.com/angular-in-depth/creating-framework-agnostic-web-components-with-angular-6cc6466d5c06).

### Installing your web component and using in another project

One published to npm, install the component inside your project folder using:

```
npm install @nishugoel/my-web-comp
```

```
<html>
<head>
  <script type="module" src="node_modules/package-name/my-web-comp.js"></script>
</head>
<body>
  <my-web-comp></my-web-comp>
</body>
<html>
```

To use this component inside another web component, you can place it inside the `.js` file of the new web component.

```
import '@nishugoel/my-web-comp/my-web-comp.js';

class NewCustElement extends LitElement{
  render(){
    return html`
      <my-web-comp></my-web-comp>       // Using our custom element inside the implementation of another custom element
    `;
  }
}
customElements.define('new-cust-ele', NewCustElement);
```

If you do not see your web component, it might be because of polyfills. I have written more about the necessary polyfills [**here**](https://medium.com/angular-in-depth/creating-framework-agnostic-web-components-with-angular-6cc6466d5c06).

Thanks for reading!
{% endraw %}
