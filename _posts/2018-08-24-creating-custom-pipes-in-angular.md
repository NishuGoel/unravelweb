---
title: "Creating Custom Pipes in Angular"
permalink: "/2018/08/24/creating-custom-pipes-in-angular/"
tags: ["angular", "angularcli", "angularjs", "bootstrap", "javascript", "javascripttalks", "js"]
layout: "post"
date: "2018-08-24"
---

{% raw %}
Previously known as Filters in AngularJS, Custom Pipes can be of two types. Pure and impure custom pipe. Pipe takes an input and returns an output based on the output of transform function evaluation.

![](/assets/img/ff8ad1-9f61d-1qsqo4w0i87dk3jrstubcka.png)

Usage of Pipes

Angular has many built-in pipes. In this article, we’ll see how to create a custom one.

**Steps Involved In Creating a Custom Pipe In Angular are:**  
1) Create a Pipe Class and decorate it with the decorator ***@Pipe.***  
2) Supply a ***name***property to be used as template code name.  
3) Register your Pipe in the module under declarations.  
4) Finally, implement ***PipeTransform***and write transformation logic.  
5) Use your pipe in the HTML using **‘|’**, which represents a pipe.  
6) Also, add Custom arguments if you want to.

https://gist.github.com/NishuGoel/a772bdf319b1eb19a551e8c3dfafd11f

Once we are done creating the Pipe class, we go to app.module.ts and register our pipe.Once we are done creating the Pipe class, we go to app.module.ts and register our pipe.

https://gist.github.com/NishuGoel/aaa2edff8956e57eaf6aa68667c19044

To finally put some logic behind the task of our custom pipe, we use PipeTransform.

https://gist.github.com/NishuGoel/0036f43a5a2f475e8a317aead22f2aac

So, to maintain the required contract to adhere to the standard structure, we use transform() method inside PipeTransform.

Now, our motive is to convert some random number to a readable format of megabytes, and to do that, we put logic inside transform() as follows:

https://gist.github.com/NishuGoel/e11e16baec4426e10d2e9d344a62476a

Now to use it in the HTML,

https://gist.github.com/NishuGoel/41986f747f448224772d829c052e6f69

To add a custom argument to your output, simply add the capability of extension to the Transform() method as follows.

https://gist.github.com/NishuGoel/7f383091ea9916928b62d89d78cd796c

We can also add multiple arguments which can be separated using ‘:’  
For example,

> {{ result| pipe:argument1:argument2 }}
{% endraw %}
