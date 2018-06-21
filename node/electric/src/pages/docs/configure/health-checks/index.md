---
title: "Health Checks"
description: "Health checks are the way we validate the status of your service and enable self-healing."
headerTitle: "Configure"
layout: "guide"
weight: 3
---

### {$page.title}

###### {$page.description}

<article id="1">

## Introduction

**Why do you need Health Checks?**

Health Checks are primarily useful for two things: validating deployment success and enabling accurate service self-healing.

##### Validating Deployment Success

When deploying a service, our default behavior is to make sure the container in the background of your service is up and running. At that point, we will say your deployment was successful. In many cases, this is not enough to truly validate if the deployment was complete and ready.

To add custom checks, you can use our Health Check feature to specify a custom [URL](#2) or [Command](#3) to check before declaring your service is healthy.

##### Accurate Service Self-Healing

Once your service has successfully deployed, it is important that you always know it's health status. We are always running a health check on your service and if we notice the health check fail then we will replace your service with a new one.

This is a powerful self-healing feature, but unless you have accurate Health Checks, we may not know that your service needs to be replaced.

To add custom Health Checks, you can specify a custom [URL](#2) or [Command](#3) to check so we know when to heal your service.

<aside>

All WeDeploy Services (Hosting, Auth, Data and Email) have finely tuned Health Checks so you don't have to ever worry about creating your own for them. For your custom services, you can use the `healthCheck` property in the `wedeploy.json` to set your custom Health Checks.

</aside>

</article>

<article id="2">

## Checking with a URL

If you provide a URL, we will ping that address until we get a `200` response.

Here is an example of the URL approach:

```application/json
{
  "id": "ui",
  "healthCheck": {
    "url": "localhost"
  }
}
```

By putting `localhost` as the health check URL, we will ping the IP of your service. You could also specify a specific path like `localhost/blog/` or a certain port like `localhost:4000`.

</article>

<article id="3">

## Checking with a Command

For more complex health checks, you can add commands to check the uptime of your service.

```application/json
{
  "id": "db",
  "healthCheck": {
    "command": "curl -X GET --silent --fail 'localhost/blog/'"
  }
}
```

</article>

<article id="4">

## Configuring

With both of these approaches, we provide you with other customizable configurations.

- `interval`: How many seconds should pass between health check tries
- `timeout`: How many seconds the health check will try to test
- `startPeriod`: How many seconds the healthCheck should wait after the service is up before testing
- `retries`: How many times the healthCheck will retry before declaring your service as `unhealthy`

When you declare a healthCheck, these are the default configurations that you can change at any time in your `wedeploy.json`:

```application/json
{
  "id": "db",
  "healthCheck": {
    "command": "curl -X GET --silent --fail 'localhost'",
    "interval": 5,
    "timeout": 5,
    "startPeriod": 1,
    "retries": 10
  }
}
```

</article>

## What's next?

Learn more about [persistent storage (Volumes)](/docs/configure/persistent-storage/).