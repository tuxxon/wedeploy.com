---
title: "Persistent Storage"
description: "WeDeploy Volumes provide a way to add a persistent storage to your application."
headerTitle: "Configure"
layout: "guide"
weight: 4
---

### {$page.title}

###### {$page.description}

<article id="1">

## Introduction

For many applications, it is necessary to be able to write and access a persistent file system so that your files can keep their state even after re-deployment or restarting your service. We make this possible with **Volumes**.

To create, or mount, a volume, you specify an `id` and a path. The `id` is a unique name that allows multiple services to read and write from that same volume, and the path is the directory in your application code that you want to be persistent.

```application/json
{
  "id": "app",
  "volumes": {
    "photos": "/photos",
    "logs": "/db/logs"
  }
}
```

</article>

<article id="2">

## Sharing between Services

Each volume (or file system drive), is mounted with a unique `id` that can be accessed by any service in that project. For example, if you create service1 and deploy with a volume declared as `photos`, you can access that same volume with service2 by declaring the same volume `id`.

In this scenario, this is how the services would connect to the volume via their `wedeploy.json` [configuration](/docs/configure/the-wedeployjson/):

**service1**

```application/json
{
  "id": "service1",
  "volumes": {
    "photos": "/photos"
  }
}
```

**service2**

```application/json
{
  "id": "service2",
  "volumes": {
    "photos": "/myapp/photos"
  }
}
```

In this example, the `photos` volume will be shared and both services can access the files within that volume by the declared paths. We only accept absolute paths and not relative ones.

</article>

<article id="3">

## Deleting Stored Files

Because volumes can be shared between services, the only way to fully destroy the contents of your volumes is to delete the project they belong to. This also means that deleting services that contain volumes will not remove the volume contents.

</article>

## What's next?

Learn more about [Environments](/docs/configure/environments/).