---
title: "Add Bootstrap to your Angular CLI Project"
permalink: "/2018/08/24/add-bootstrap-to-your-angular-cli-project/"
tags: ["angular", "angularcli", "angularjs", "bootstrap", "bs", "javascript", "javascripttalks", "js"]
layout: "post"
date: "2018-08-24"
---

{% raw %}
This article will help us understand the usage of bootstrap framework within Angular. To understand a little about bootstrap, Bootstrap is the most popular HTML, CSS, and JavaScript framework for web front-end development. It’s great for developing responsive, mobile-first web sites.

![](/assets/img/61c882-d090f-1lfe5hawdcbyi-ysky2uifq.jpeg)

Bootstrap in Angular

**Step 1. Create a new Angular Project**So, to apply bootstrap to your angular project, the very first step is to create an angular project using ng new.

> $ ng new bs\_ang

**Step 2. Install Bootstrap**To add bootstrap to an angular project, there are different ways:  
— Adding Bootstrap from CDN  
— Adding Boostrap via NPM

### **From CDN**

The CSS and JS files of bootstrap can be directly accessed from a CDN (Content Delivery Network). The CDN links for Bootstrap can be found at <http://getbootstrap.com/getting-started/>

In the **index.html**, insert <link> element *(It will appear like given in the picture below)*to get the Bootstrap CSS file after the <head> tag.

![](/assets/img/2fb2b7-e4e6f-1ipdl3h3q9-o-xwue6mb5yw.jpeg)

Your index.html must look like this now.

```html
[<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8">
  <title>Pract</title>
  <base href="/">
  <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css" integrity="sha3-BVYiiSIFeK1dGmJRAkycuHAHRg32OmUcww7on3RYdg4Va+PmSTsz/K68vbdEjh4u" crossorigin="anonymous">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <link rel="icon" type="image/x-icon" href="favicon.ico">
</head>
<body>
  <app-root></app-root>
</body>
</html>
```

### Now, to use this bootstrap inside one of our components, lets take this example.

In our app.component.html,i.e.,

```html
<div>
    <button> Hey </button>
    <h1>Welcome to Angular</h1>
    <table>
        <tr>
            <td> No bootstrap</td>
        </tr>
    </table>
</div>
```

The result shows as follows if bootstrap framework is not applied.

![](/assets/img/ee9be3-b3b5c-1d39p6mv0562zx8mmoiarkq.png)

Without bootstrap

However, when you apply the bootstrap framework in your app.component.html, i.e.,

```html
<div class = 'jumbotron'>
    <button class = 'btn btn-info'> Hey </button>
    <h1>Welcome to Angular</h1>
    <table class = 'table'>
        <tr>
            <td> With bootstrap</td>
        </tr>
    </table>
</div>
```

it appears like:

![](/assets/img/f5a58c-69a38-1fdxhwvzuo9o2j-iirdhjq.jpeg)

With Bootstrap

> **Look at the difference in the presentation with Bootstrap applied to Angular!**

### **Via NPM**

> Use $npm install boostrap@3

After installing, find the bootstrap CSS file here: [*node\_modules/bootstrap/dist/css/bootstrap.min.css*](http://node_modules/bootstrap/dist/css/bootstrap.min.css)and add it to the <link> element in the index.html

And then, apply bootstrap to any component as we did earlier.

> We can also change the bootstrap theme from websites like **Bootswatch**, (<https://bootswatch.com/>) by simply copying the URL of a particular theme and pasting it in the **index.html**
{% endraw %}
