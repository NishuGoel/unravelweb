---
title: "Angular & SPAs"
permalink: "/2019/01/23/angular-spas/"
tags: ["Uncategorized", "angular", "angularcli", "angularjs", "javascript", "singlepageapplications"]
layout: "post"
date: "2019-01-23"
---

{% raw %}
I was scrolling through questions on stackoverflow and saw a lot of people questioning if Angular applications are SPAs (Single-page applications) or what are SPAs. Hope this blog post will contain the information required to understand what this actually means.

To start with, let us try to comprehend the meaning of the term Single-page applications. We have evolved from the time when we used websites involving a number of HTML pages interlinked. However, it reduced to fewer and fewer and then what what came to be used as Single page applications. SPAs can be implemented with smaller number of files whereas this won’t be the same case with the interlinked HTML files. One major plus of using SPAs is that it does not need to download every page every time from the server. It just downloads the index.html and rest happens on the client side.

If we inspect the main page of any of the websites based on SPAs, we will see that the first page to download is the index.html one and there is no need to download all the pages one by one from the server.

![](/assets/img/7c3c2f-66870-1qrmnjdxs84lkzmwkgln_xq.png)

For example, when we inspect the home page of the website of [**ng-India**](http://ng-ind.com/)**,**we see that the page that gets loaded first is the index.html page.

### The concept of SPAs sounds fancy! But how does it work?

You might be wondering that we load very little HTML from the server, with the data that is present at that time. What about the data that is added later. how does that get updated every time in a single page application! To do this, browser needs to change the data into HTML every time. That is a very logical question!

The answer to that can be obtained by comparing these applications to those traditional server-based applications. The rendering of data which used to be done on the server-side has a different approach with SPAs.

With SPAs, the data to HTML transformation is done on the client-side. Yes, you heard it right. The SPA-friendly browsers have something like a template engine running in them which makes the rendering part much faster and easier. Now, the data won’t need to be loaded from the server every time.

### Why do we need Angular for SPA? Or do we not?

The answer to this is No! We do not always need Angular to create SPAs but let us understand why Angular comes into picture then!

When we are putting in a lot of data into one web-page with the aim of creating a single-page application, the program becomes very complex and is not driven by HTML but JavaScript in that case. The code becomes very complex and then to handle such complex functions, Angular jumps in.

Now we will not look at our application as a set of static pages with a lot of data in them, instead, we understand it as a complex program which needs to use all the tools required for a Development project using a typed language like Typescript.

Another very important thing to put light on, here, is that we do not need Angular to create an SPA because the website is an SPA but because the website is a complex program with a lot of code and complex functions in it.

An easy-way of understanding this can be by saying that a non-SPA is actually nothing but a list of many SPAs. Many single-page applications comprise to form a Single-page application.

To summarize, the advantages of using an SPA are:

* Easier to deploy in Production
* Server to serve a minimum of 3 files — single page index.html, a CSS bundle, a JS bundle.
* Faster page refreshes and no full-page refreshes occur.

One major downside of using an SPA is that not all browsers are SPA-friendly as they suffer from indexing a single page application correctly. To solve this problem, browsers use AJAX Crawling or Progressive enhancement which is not in the scope of this blog post.
{% endraw %}
