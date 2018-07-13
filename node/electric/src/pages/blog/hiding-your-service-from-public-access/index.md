---
title: "Hiding Your Service from Public Access"
description: "There are many situations where a service is only used inside a project. In these cases, you may not want these services to be accessible by guests. Now you can hide any service you want by adding a new field to your wedeploy.json"
date: "Jul 2, 2018"
author: "Albertinin Mourato"
image: "images/blog/post-5--0.png"
layout: "blog"
---

<article>

{$page.description}

### Don't Expose What Should Not Be Exposed

Imagine you have an application which requires multiple different services (database, server, etc...) to make it work. You may want to provide more security and protection to these complementary services or simply hide them from public access. Now, you are able to choose if you want your service to be public or private by adding the new `public` field to your `wedeploy.json`.

### Marking Your Service as Private

By setting this field to false in your `wedeploy.json` like you see below, we will hide your service from the public. Don't worry, your service is still accessible to other services in your project via its hostname.

```application/json
{
    "id": "myservice",
    "public": false
}
```

</article>