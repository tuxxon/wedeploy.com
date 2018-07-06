---
title: "Hiding Your Service from Public Access"
description: "There are many situations where a service is only used inside a project. In these cases, you may not want these services to be accessible from guests. Now you can hide any service you want by adding a new field to your wedeploy.json"
date: "Jul 2, 2018"
author: "Albertinin Mourato"
image: "images/blog/post-5--0.png"
layout: "blog"
---

<article>

{$page.description}

### Don't expose what should not be exposed

Imagine you have an application which requires a bunch of different services (database, server, etc...) to make it work. These complementary services might not be important for users or accessible for anyone. Now, you can make it unacessible by adding the new field `public` to your `wedeploy.json`.

### Marking Your Service Unreachable from Public

You can easily hide your service by doing the following:

```application/json
{
    "id": "myservice",
    "public": false
}
```

</article>