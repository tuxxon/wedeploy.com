---
title: "Deploying Node.js"
description: "Launch a Node.js application in few seconds."
headerTitle: "Getting Started"
layout: "guide"
weight: 4
---

### {$page.title}

###### {$page.description}

<article id="1">

## Introduction

[Node.js](https://nodejs.org) is an open-source, cross-platform runtime for developing server-side web applications using JavaScript. It has an event-driven architecture capable of asynchronous I/O.

Deploy a Node.js site now with just the click of a button!

<a href="https://console.wedeploy.com/deploy?repo=https://github.com/wedeploy-examples/nodejs-example" target="_blank">
  <img style="width:197px;" src="https://cdn.wedeploy.com/images/deploy.svg">
</a>

To learn more, you can also follow our **[step by step Tutorial](/tutorials/nodejs/)** or look through the **[example source code](https://github.com/wedeploy-examples/nodejs-example)**.

</article>

<article id="2">

## Configuring

<aside>

All WeDeploy projects use similar a [configuration file](/docs/configure/the-wedeployjson/) to prepare your projects for deployment.

</aside>

Below is an example of a `wedeploy.json` for a Node.js service. The `id` for your services are uniquely determined by you.

```application/json
{
  "id": "myservice"
}
```

In your application files, you need to place the `wedeploy.json` next to your `package.json`.

```xml
myservice
├── index.js
├── package.json
└── wedeploy.json
```

<aside>

###### <span class="icon-16-alert"></span> Attention

Behind the scenes, we run **npm install --unsafe-perm --production** which means that your application will run in production mode. Because of that, make sure your dependencies are
on `“dependencies”` instead of `“devDependencies”` inside your `package.json`, otherwise they will not be installed.

</aside>

</article>

<article id="3">

## Ports

By default, we expose port `80` on Node.js services. If you want to designate a different port to expose (like `3000`), you must do that in the `wedeploy.json` ([learn more about using ports](/docs/configure/the-wedeployjson/#port)).

```application/json
{
  "id": "myservice",
  "port": 3000
}
```

</article>

<article id="4">

## Specifying the Node.js version

By default, the Node.js version will be the current stable version. If you want to designate a different version, you can specify it on the [engines property](https://docs.npmjs.com/files/package.json#engines) inside `package.json`.

You may add a fixed version:

```application/json
"engines": {
  "node": "8.6.0"
}
```

Or you can specify a range:

```application/json
"engines": {
  "node": ">=8.4 <8.6"
}
```

</article>

## What's next?

Learn more about [deploying Docker](/docs/getting-started/deploying-docker/).