---
title: "Deploying Docker"
description: "Launch a Docker application in few seconds."
headerTitle: "Getting Started"
layout: "guide"
weight: 5
---

### {$page.title}

###### {$page.description}

<article id="1">

## Introduction

[Docker](https://www.docker.com) is the world’s leading software container platform. Developers use Docker to eliminate “works on my machine” problems when collaborating on code with co-workers. Enterprises use Docker to build agile software and ship new features faster.

Deploy a Docker (WordPress) site now with just the click of a button!

<a href="https://console.wedeploy.com/deploy?repo=https://github.com/wedeploy-examples/wordpress-example" target="_blank">
  <img style="width:197px;" src="https://cdn.wedeploy.com/images/deploy.svg">
</a>

To learn more, you can also follow our **[step by step Tutorial](/tutorials/docker/)** or look through the **[example source code](https://github.com/wedeploy-examples/wordpress-example)**.

</article>

<article id="2">

## Configuring

<aside>

All WeDeploy projects use similar a [configuration file](/docs/configure/the-wedeployjson/) to prepare your projects for deployment.

</aside>

##### Custom Dockerfile

Below is an example of a `wedeploy.json` for a Docker container. The `id` for your services are uniquely determined by you.

```application/json
{
  "id": "myservice"
}
```

You need to place a `wedeploy.json` wherever you have a `Dockerfile`.

If you were deploying a Wordpress site using custom Docker images for a WordPress and a MySQL database, this is what your project could look like:

```xml
myservice
├── db
│   ├── Dockerfile
│   └── wedeploy.json
└── wp
    ├── Dockerfile
    └── wedeploy.json
```

##### Docker Hub

If you just wanted to fetch the WordPress image from Docker Hub, you could simply call it in your `wedeploy.json`.

```application/json
{
  "id": "wp",
  "image": "wordpress",
  "env": {
    "WORDPRESS_DB_HOST": "db",
    "WORDPRESS_DB_USER": "root",
    "WORDPRESS_DB_PASSWORD": "passw0rd",
    "WORDPRESS_DB_NAME": "wordpress"
  }
}
```

<aside>

It is only possible to fetch public images from Docker Hub. To deploy custom images, you need to use the custom Dockerfile approach.

</aside>

</article>

<article id="3">

## Ports

##### Automatic Detection

When deploying a docker image, WeDeploy will look inside the `Dockerfile` to see what ports are exposed. If there is only one, then we will use that one, but if there are multiple ports exposed, we will use the lowest value port.

For example, if you had a `Dockerfile` like this:

```
FROM ubuntu
EXPOSE 3000
EXPOSE 4000
```

We would automatically expose port `3000` for your service so that it can be accessed publicly via your service URL (_service-project.wedeploy.io_).

##### Manual Configuration

To manually configure your port, you can do this by setting the `port` value in your `wedeploy.json`.

```application/json
{
  "id": "myubuntu",
  "port": 4000
}
```

You can also **block all external access** to your container by setting a port in your `wedeploy.json` that is not exposed in your `Dockerfile`.

```application/json
{
  "id": "myubuntu",
  "port": 0
}
```

</article>

## What's next?

Learn more about [deploying Ruby](/docs/getting-started/deploying-ruby/).