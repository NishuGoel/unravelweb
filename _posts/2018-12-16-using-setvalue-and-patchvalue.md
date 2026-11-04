---
title: "Using setValue and patchValue"
permalink: "/2018/12/16/using-setvalue-and-patchvalue/"
tags: ["angular", "angularcli", "angularjs", "javascript", "javascripttalks", "node", "nodejs"]
layout: "post"
date: "2018-12-16"
---

{% raw %}
In this blog post, we will see that when building Reactive Forms, if we need to update the input elements on the form from our component class, we use **setValue** and **patchValue**.

If you are new to Reactive Forms, I would recommend you to go through this article : [Reactive (Model-Driven) Forms](https://nishugoel.wordpress.com/2018/10/17/angular-model-driven-reactive-forms/)

We use **setvalue** to set the value of every form control on the form. For example, here we have three form control in our form model. And now because we want to update the value of each one of these, we use setValue.

https://gist.github.com/NishuGoel/1a9560e14952e58ae56f0446ad0b3de1

However, if we only want to set the subset of the values, we then use **patchValue**. In this example, we set only of the three values.

https://gist.github.com/NishuGoel/2f2bc061482279b1ea22de793d8e84f8

Let us try our hands on it now!

In the component template, Let us take a button to check the data like this:

https://gist.github.com/NishuGoel/2f4e81a846bc2fde5b7c9b62f3c96360

Now let us take this method inside the component.ts file.

https://gist.github.com/NishuGoel/932a0c47a2c6121415063bd04606c8e2

Now when we check this in the browser, it populates the data in the browser as:

> Value {“name”: “Wilson”, “city”: “Bangalore”, “email”: “wilsondcousta@gmail.com”}

In case, in the **checkData()** method, we do not set the value of name and email and set it just for the city, like this:

> this.myForm.setValue({  
>        city: ‘Gurgaon’  
> })

In this case, the console throws an error like:

![](/assets/img/697352-error.png)

To solve this, simple solution!  
We use patchValue, since we are making a change to only a subset of the form element and not all the elements of the form.

In place of the above code, we will write:

> *this.myForm.patchValue({*  
> *city: ‘Gurgaon’*  
> *})*

And then, it works well.
{% endraw %}
