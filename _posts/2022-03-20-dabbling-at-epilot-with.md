---
title: "dabbling at epilot with…"
permalink: "/2022/03/20/dabbling-at-epilot-with/"
tags: ["Javascript", "javascript", "job", "react"]
layout: "post"
date: "2022-03-20"
---

{% raw %}
Year 2022 marked an amazing start for me with a new stint with [**epilot GmbH**](https://epilot.cloud/) based out of Cologne, Germany. I joined the team to be working on their micro-frontend architecture, with my primary focus going to be on the performance aspects of the applications.   
Like the first recent addition we did after I started was to add `brotli` [compression](https://github.com/google/brotli) to each of our micro-frontend (MFEs) bundles.

![](https://unravelweb.dev/wp-content/uploads/2022/10/1CvujCz8dT83A8mMzbBNhEA.png)

Let’s look at the tech stack involved.

#### Micro services

The main `epilot` app is built using `microfrontends` with each entity as its own application. There is a `login` application that takes care of the user login state (built using *React + TypeScript*), a `topbar` application that has features like Global search, notifications (*React + TypeScript*), a `sidebar` application that navigates the user to different entities based on user permissions (*Svelte + TypeScript + Tailwind*), and so on.

The component library of the product is based on material UI, built with React.

[**@epilot/base-elements**](https://www.npmjs.com/package/@epilot/base-elements)

Due to the open source experience of many engineers in the team, most of the non-confidential stuff is kept public on GitHub and npm.  
One of the very interesting things I got to do to ramp up was to build a part of the product as a Svelte MFE. With most of the existing MFEs built using react, this was quite interesting and challenging to do.

We use [**single-spa**](http://single-spa.js.org) framework to build our `microfrontends` and use different frameworks per the ease and knowledge of an engineer. To make the development journey easier for a new developer starting up with microfrontends, we have a `mfe-app-generator` package that creates a boilerplate application with the required config.

[**@epilot360/mfe-app-generator**](https://www.npmjs.com/package/@epilot360/mfe-app-generator)

Due to performance reasons, one of the goals was to switch to rollup for bundling all our applications, however, we use `webpack` due to [rollup’s known issues with](https://github.com/aws/aws-sdk-js/issues/1769) `aws-sdk`.

We use serverless microservices architecture exposed via APIs. Most of the backend services are written in TypeScript using AWS lambda functions, APIs, Cloudfront distribution etc. More on that [here](https://docs.epilot.io/docs/architecture/overview).

With Svelte added to our microfrontend stack, we plan to further diversify the frameworks to be used, ensuring to not lose focus on the performance aspect of the application. [Here’s a list of support frameworks by single-spa.](https://single-spa.js.org/docs/ecosystem)

I also plan to share our journey from a high [LCP (largest contentful paint)](https://web.dev/lcp/) to a much reduced one, but I’d keep it for another blog post.

When working with custom implementation and bundling, one of the challenging tasks is to configure your bundler and ensure it is consistent throughout all the applications (MFEs in this case). We have defined a `@epilot360/webpack-config-epilot360` to base one’s webpack config on top of the existing basic config defined.

[**@epilot360/webpack-config-epilot360**](https://www.npmjs.com/package/@epilot360/webpack-config-epilot360)

I will share more on the webpack configuration for microfrontends and cache invalidation strategies in another post but `cache invalidation` is definitely my major ongoing focus area.

#### Epilot SDK

All public epilot services are available through an epilot-sdk (written in JS/TS) that allows developers to interact with epilot APIs. Internally as well, the recommended way to use the services or APIs using directly the SDK instead of going the granular way.

For e.g.,

```
import { getClient } from 'epilot-sdk/entity-client'
```

Want to scratch your itch? Find it here:

[**@epilot/epilot-sdk**](https://www.npmjs.com/package/@epilot/epilot-sdk)

#### Communicating between microfrontends

One of the interesting challenges I recently faced was to communicate between two applications without any shared library. One was the sidebar built using Svelte and another the topbar built with React. Now we usually tend to avoid any such communication between our MFEs but this was a state clear event to happen before a routing change in any of the two MFEs.

I used single-spa’s custom events to do this. The idea was to clear the selected state of an icon in the topbar when an icon in the sidebar was selected, and vice versa.  
To do this, I used the `single-spa:before-routing-event` custom event to check if the active URL in the current application was undefined, we could clear the state, if however, the URL existed, that becomes the active state.   
Checking the URL history without communicating between two applications was not possible due to two separate routers for each application. Svelte app using the `svelte-routing` package where with React, the `react-router` .

![](https://unravelweb.dev/wp-content/uploads/2022/10/1tbIakQdOsZdWqMkEuAr3TA.png)

[Read more about the single spa custom events here](https://single-spa.js.org/docs/api/#custom-events).

Here’s a detailed view of the tech stack used at epilot:

![](https://unravelweb.dev/wp-content/uploads/2022/10/1V7VGeO-iDvUbnYFgC577mQ.png)

<https://docs.epilot.io/techradar/>

I have shared more info on my journey to epilot as a full-stack developer in my Spotify Podcast here:



<iframe src="https://open.spotify.com/embed/episode/2C4KYDkRroA6Uc2QevdhLt?si=ap_yhzZKTuuECCeAc47wCA&amp;utm_source=oembed" title="Spotify Embed: #17 Unravelling The Web w/ Nishu Goel" loading="lazy" style="width:100%;height:152px;border:0;border-radius:12px"></iframe>



Spotify podcast

Interested to know more about how we do things at epilot? Reach out here: [twitter.com/@TheNishuGoel](http://twitter.com/@TheNishuGoel)
{% endraw %}
