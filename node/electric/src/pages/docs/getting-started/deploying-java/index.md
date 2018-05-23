---
title: "Deploying Java"
description: "Launch a Java application in few seconds."
headerTitle: "Getting Started"
layout: "guide"
weight: 7
---

### {$page.title}

###### {$page.description}

<article id="1">

## Introduction

[Java](https://www.oracle.com/java/) is a concurrent, class-based, object-oriented language expressly designed for use in the distributed environment of the web. It is normally compiled to the binary format defined in the JVM Specification.

Deploy a Java site now with just the click of a button!

<a href="https://console.wedeploy.com/deploy?repo=https://github.com/wedeploy-examples/java-example" target="_blank">
  <img style="width:197px;" src="https://cdn.wedeploy.com/images/deploy.svg">
</a>

To learn more, you can also follow our **[step by step Tutorial](/tutorials/java/)** or look through the **[example source code](https://github.com/wedeploy-examples/java-example)**.

</article>

<article id="3">

## Configuring

<aside>

All WeDeploy projects use similar a [configuration file](/docs/configure/the-wedeployjson/) to prepare your projects for deployment.

</aside>

Below is an examples of a `wedeploy.json` for the Java container. The `id` for your services are uniquely determined by you.

```application/json
{
  "id": "myservice",
  "memory": 2048
}
```

You need to place a `wedeploy.json` wherever you have a `build.gradle`.

```xml
myservice
├── build.gradle
└── wedeploy.json
```

##### Port

The default port exposed for Java services is `8080` ([learn more about using ports](/docs/configure/the-wedeployjson/#port)).

##### Versions

When deploying Java services, we use these versions to automatically build your services.

**Maven**

- Maven version `3.5.2`
- JDK version `8`

**Gradle**

- Gradle version `4.5`
- JDK version `8`

</article>
