---
title: "Double free error?"
permalink: "/double-free-error/"
tags: ["Code", "Programming", "Rust", "Rustlang", "Uncategorized", "tech"]
layout: "post"
date: "2021-01-29"
---

{% raw %}
This is one of the memory safety bugs in Rust, which we will try to understand through a dialogue in this blog post.

```
let s1 = String::from("Hello");
let s2 = s1;
```

![](/assets/img/84b043-1_RZjzj0r4weRyz9yGpm_7fg.png)

```
let s1 = String::from("Hello");  
let s2 = s1;println!("{}", s1);
```

> Error — *use of moved value*`s1`

Do share your understanding.

Thanks!
{% endraw %}
