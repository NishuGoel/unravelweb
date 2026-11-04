---
title: "travel ??= stay/work/play at home"
permalink: "/travel-stay-work-play-at-home/"
tags: ["Articles", "Code", "JavaScript", "Node.js", "Programming", "community", "covid", "javascript", "javascripttalks"]
layout: "post"
date: "2021-05-29"
---

{% raw %}
know what I mean?

nope, not another rant post.  
not to do with staying productive working from home.  
also not about travel nostalgia.

yeah enough mystery, right? **So in this post, I’ll**`briefly`**share a tip about the usage of logical operators in Javascript**and updated ways to use them in 2021.

quite unrelated to the title, ya? It’s actually not. you’ ll see why.

# TLDR; Using logical operators with assignment :

> 1) &&=
>
> 2) ||=
>
> 3) ??=

the blog post title?

![](/assets/img/de6342-1_wO1HpwEuwO1DMEym7fnuNw.png)

=======================================

## Basic most way of using logical operators in Javascript

![](/assets/img/df4741-1_CFjE6k8qYyJmsuYKM3uNhg.png)
![](/assets/img/194475-1__F_YUqN6u6ddtKYHqGm4gA.png)

Now, let’s make it simpler.

![](/assets/img/dab697-1_ncPQTz6Xmlp6ggLAvWhHug.png)

all simple so far?  
but did you know we could also assign using logical operators? let’s see.

![](/assets/img/f50973-1_XF6JWRuxldkFfxH64a-QqQ.png)

This is similar to how we have been using the numeric operators `+=` :-

![](/assets/img/1bff71-1_JeorrVRPUQDZ2dT1E9epPA.png)

let’s see some more examples of assignments using logical operators.

## Using && operator

![](/assets/img/be9137-1_btKv9BSpVMrbe0iUNlri1w.png)
![](/assets/img/7b683d-1_uy5GYBrJwqqOzIlmYugrZg.png)

with `&&` operator, it prints the right hand side if ‘val’ is truthy, LHS otherwise.

## Using nullish coalescing operator

The nullish coalescing operator specifically checks for null or undefined, so if a variable is null or undefined, return an alternative, else the value in the variable.

***non-assignment usage***

![](/assets/img/9f0d20-1_AAD0YawRvJxeFr3ihwJn3g.png)
![](/assets/img/505a72-1_nMOmy0RcRbczHbdUlyaJJA.png)

***with-assignment usage***

![](/assets/img/ebb8f6-1_aoWG68-qDYUJQgWd5NC0mg.png)
![](/assets/img/b5f668-1_tToskuWAZUWdeUlgJHTfxA.png)
![](/assets/img/1168d9-1_iJmBvYnM_Lz6v7PM14a-Hg.png)

there we go with a small but helpful enhancement in this javascript feature.

oh also, remember?

![](/assets/img/da03e1-1_wO1HpwEuwO1DMEym7fnuNw.png)

Goodbye! 🙂
{% endraw %}
