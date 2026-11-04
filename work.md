---
title: "Work"
permalink: "/work/"
layout: "page"
---

{% raw %}
I build products for the web, from the first idea to production, with a soft spot for performance and developer experience. Most of my work today is in TypeScript, React, Svelte and Node.js on AWS, with some Go along the way.

## epilot

<p class="meta">Product Engineer · Cologne, Germany · 2022 – present</p>

[epilot](https://epilot.cloud) is the energy XRM: one platform for energy suppliers, grid operators and solution providers in Germany and Austria to run sales, service and new energy products end to end.

### Blueprints & Marketplace

[Blueprints](https://epilot.cloud/anwendungsbereiche/blueprints/) package a complete use case (schemas, journeys, workflows, automations, templates and more) so customers can install it in minutes instead of building it from scratch.

- Built the platform-level Blueprint Marketplace and the install engine behind it, which resolves dependencies between hundreds of resources and installs them in the right order.
- Sandbox → production sync: customers build in a sandbox and promote changes to production, with drift detection and merge policies for resources that were changed on both sides.
- Visibility and safety around installs: sync history with retries for failed runs, a resource tree that shows how everything in a blueprint fits together, health checks, and protected blueprints that customers can update without breaking their own changes.
- Working on AI-assisted blueprint updates, where an agent plans an update, asks about conflicts and applies it.

### Configuration Hub

- Tools to compare configuration across organisations, take snapshots and restore earlier states.
- An org health dashboard that surfaces broken or risky configuration before customers run into it.
- Fine-grained permissions for configuration management.

### Platform & performance

- Part of the team that set up epilot's micro-frontend architecture. Added brotli compression to every micro-frontend bundle and later audited bundle sizes across the platform.
- [Used the Server-Timing API to bring a > 70% performance improvement](/2024/01/07/how-using-server-timing-api-helped-bring-70-perf-improvement/) and open-sourced [lambda-server-timing](https://www.npmjs.com/package/lambda-server-timing) along the way.
- Search and filtering across entities in epilot360 with React and Elasticsearch, including [Unicode normalisation for umlauts](/2024/02/12/the-u-u-conundrum/) and the noisy-neighbour problem on a shared cluster.
- Moved infrastructure setup to a declarative approach by [running Terraform inside AWS Lambda](/2024/04/01/til-tf-plugin-cache/).

<p class="meta">TypeScript · React · Svelte · Node.js · AWS Lambda · DynamoDB · Elasticsearch · Terraform</p>

## Before epilot

- **Scraping platform.** Frontend in React and TypeScript, services in Go, plus quick Python scripts for scraping.
- **Conversational AI bot.** Angular frontend with a Python backend on AWS.
- **Castrol Fastlane.** A progressive web app built with Angular.
- **Angular web components.** Built framework-agnostic web components in Angular, published them to npm and used them in React apps. Wrote about it [here](/2019/12/12/creating-framework-agnostic-web-components-with-angular/).

## Writing

- **[Web Almanac 2021, JavaScript chapter](https://almanac.httparchive.org/en/2021/javascript)**, HTTP Archive. Author and content lead; six months of digging into how the web uses JavaScript.
- **A Hands-on Guide to Angular**, Educative, 2021.
- **[Step-by-Step Angular Routing](https://www.amazon.com/dp/B07SVHF2SJ)**, BPB Publications, 2019.
- **Angular for Beginners**, Udemy course, 2018.
- 100+ posts on [this blog](/) since 2018.

## Speaking

Talks at performance.now(), Web Directions, WebExpo, ngConf, JSPoland, iJS London, ng-India, ngNepal and DevFests across Europe and India. See [all talks](/speaking/).

## Recognition

- **Google Developer Expert**, Web Technologies and Angular, since 2020. Featured in the [GDE community highlight](https://web.dev/gde-focus-nishu-goel/) on web.dev.
- **Microsoft MVP**, Developer Technologies, since 2020.
- Microsoft Imagine Cup national finalist with an app that brings educational opportunities to local students, especially girls.

## Community

- Volunteered with YIYA, a Ugandan NGO that delivers education to school-aged children through keypad phones and radio: Python scripts, bug fixes and portal issues.
- Mentoring and speaking at local GDG and community events.

## Education

- University of California San Diego, 2018 – 2019.
- Bachelor's degree in Computer Science, 2014 – 2018.
{% endraw %}
