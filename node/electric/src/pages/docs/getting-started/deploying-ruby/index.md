---
title: "Deploying Ruby"
description: "Launch a Ruby application in few seconds."
headerTitle: "Getting Started"
layout: "guide"
weight: 6
---

### {$page.title}

###### {$page.description}

<article id="1">

## Introduction

[Ruby](https://www.ruby-lang.org) is a dynamic, open source programming language with a focus on simplicity and productivity. It has an elegant syntax that is natural to read and easy to write.

Deploy a Ruby site now with just the click of a button!

<a href="https://console.wedeploy.com/deploy?repo=https://github.com/wedeploy-examples/ruby-example" target="_blank">
  <img style="width:197px;" src="https://cdn.wedeploy.com/images/deploy.svg">
</a>

To learn more, you can also follow our **[step by step Tutorial](/tutorials/ruby/)** or look through the **[example source code](https://github.com/wedeploy-examples/ruby-example)**.

</article>

<article id="2">

## Configuring

<aside>

All WeDeploy projects use similar a [configuration file](/docs/configure/the-wedeployjson/) to prepare your projects for deployment.

</aside>

Below is an example of a `wedeploy.json` for a Ruby container. The `id` for your services are uniquely determined by you.

```application/json
{
  "id": "myservice"
}
```

You need to place a `wedeploy.json` wherever you have a `Gemfile`.

```xml
myservice
├── Gemfile
└── wedeploy.json
```

##### Port

The default port exposed for Ruby services is `80` ([learn more about using ports](/docs/configure/the-wedeployjson/#port)).

##### Version

We use Ruby version `2.3` when auto-detecting your Ruby deployment.

</article>

## What's next?

Learn more about [deploying Java](/docs/getting-started/deploying-java/).