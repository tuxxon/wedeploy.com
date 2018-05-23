---
title: "Deploying Static Hosting"
description: "Serve static files easily using WeDeploy Hosting."
headerTitle: "Getting Started"
layout: "guide"
weight: 3
---

### {$page.title}

###### {$page.description}

<article id="1">

## Introduction

Our Hosting service allows you to deliver HTML, CSS, JavaScript, or any other static files using powerful static hosting. It's very fast and will save you a lot of time.

Deploy a static site now with just the click of a button!

<a href="https://console.wedeploy.com/deploy?repo=https://github.com/wedeploy-examples/hosting-example" target="_blank">
  <img style="width:197px;" src="https://cdn.wedeploy.com/images/deploy.svg">
</a>

To learn more, you can also follow our **[step by step Tutorial](/tutorials/hosting/)** or look through the **[example source code](https://github.com/wedeploy-examples/hosting-example)**.

</article>

<article id="2">

## Configuring

<aside>

All WeDeploy projects use similar a [configuration file](/docs/configure/the-wedeployjson/) to prepare your projects for deployment.

</aside>

Below is an example of a `wedeploy.json` for a Hosting service.

```application/json
{
  "id": "ui",
  "image": "wedeploy/hosting:@site.version.image.hosting@"
}
```

The `id` for your services are uniquely determined by you.

</article>

<article id="3">

## Custom Web Path

Sometimes you may want to serve a sub folder on your application instead of the root. This is especially helpful if you run a build prior to deploying that outputs all your files into a build folder.

To declare where you want the Hosting service to serve, you can declare a web path in you `wedeploy.json`.

```application/json
{
  "id": "myservice",
  "image": "wedeploy/hosting:@site.version.image.hosting@",
  "env": {
    "WEDEPLOY_WEB_PATH": "./dist"
  }
}
```

The folder specified in `WEDEPLOY_WEB_PATH` will be resolved relative to the folder where the `wedeploy.json` is located.

In the example above, the `WEDEPLOY_WEB_PATH` is specified as `./dist`, so the `dist` folder would need to be next to `wedeploy.json` in the root of that service directory.

```
myapp
  ├── wedeploy.json
  ├── dist
  └── src
```

</article>

<article id="4">

## Custom Error Pages

When people try to access nonexistent pages on your site, WeDeploy will display a 404 error page. This page follows a template that might not fit to your visual needs. The good news is that you can create custom error pages that are consistent with your site's style.

Files put into the special directory `./_error` are mapped as the error files to be served in case of an error. They must take the form of `<errorCode>.html`.

The name of the error directory can also be customized - change the environment variable `WEDEPLOY_WEB_ERROR_PATH` to a path relative to the root directory (wherever your `wedeploy.json` is) and add the errors files there.

For instance, assume your service had the following directory structure:

```
.
├── myerrors
│   └── 404.html
├── index.html
├── assets
│   └── index.css
└── wedeploy.json
```

You can tell WeDeploy to look for error files in `myerrors` by setting the environment variables in your `wedeploy.json` like the following:

```application/json
{
  "id": "myservice",
  "image": "wedeploy/hosting:@site.version.image.hosting@",
  "env": {
    "WEDEPLOY_WEB_ERROR_PATH": "./myerrors"
  }
}
```

</article>

<article id="5">

## Updates

Check for new releases to our Hosting Service on our [Updates page](/updates/services/hosting).

</article>