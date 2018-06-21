---
title: "Feature Overview"
description: "This is an overview of the features that make WeDeploy the easiest way to deploy and scale applications."
headerTitle: "Getting Started"
layout: "guide"
weight: 2
---

### {$page.title}

###### {$page.description}

<article id="1">

## Deployment Types

Every developer and team has a different process for deployment. With WeDeploy you have the flexibility of initiating your project deployments in multiple different ways depending on your process needs.

* **[CLI](/docs/configure/deployment/#1)**: Deploy local source code or public GitHub repos from the comfort of your terminal
* **[GitHub Integration](/docs/configure/deployment/#2)**: Continuous deployment on every change pushed to your specific repo branch
* **[Git URL](/docs/configure/deployment/#3)**: Simply paste the URL to a GitHub, GitLab or Bitbucket repo and we'll deploy it
* **[Deploy Button](/docs/configure/deployment/#4)**: Quick, one time deployments with the click of a button from your website or source code readme

No matter how you choose to deploy, WeDeploy tries to determine what language your project uses based on the file structure. We scan your directory in order to install dependencies, compile the code, and run the application.

Our automatic code detection comes with a number of pre-configured recipes for projects that contain Docker, Node.js, Ruby, or Java files.

</article>

<article id="2">

## Zero-Downtime Deployments

Whenever a new deployment is triggered, you don't want your application to go offline until the new version is 100% ready. What you want is to minimize user interruption.

With WeDeploy you can push updates and restart your services with zero downtime.

We also wait until your **[Health Checks](/docs/configure/health-checks)** have successfully passed before switching your containers. If the health check does not pass, we will rollback to your previous deployment.

</article>

<article id="3">

## HTTPS Certificates

Every project you deploy and every service you install will automatically be given a HTTPS certificate. This means your application will safely communicate with your users without you having to configure anything.

WeDeploy also makes sure that those HTTPS certificates are valid by renewing them from time to time. That way you can always trust that your application will be secured.

</article>

<article id="4">

## Self Healing

Mission-critical services require health monitoring, self-healing, and fault tolerance both for themselves and the platform and infrastructure they run on. WeDeploy gives you multiple layers of protection.

To achieve self-healing, WeDeploy services are continually monitored via their **[health check](/docs/configure/health-checks)**. If we notice the health check fail, then we will automatically replace your service with a new one until your service is healthy.

</article>

<article id="5">

## Global DNS

We know how tedious it is to setup your domains. That's why we have a reliable and scalable DNS solution.

You can point your domains directly to our nameservers and we will automatically configure everything for you.

WeDeploy provides a DNS service across 7 different countries, including Australia, Germany, France, Netherlands, Singapore, United Kingdom, United States. Our goal is to ensure that you always have low-latency resulting in a great experience for your users and your business.

</article>

<article id="6">

## Elastic Scalability

WeDeploy gives you the power to easily scale your services up and down with a single line of code.

You can change the number of service instances at any time and we will distribute your sites traffic smoothly to each instance using our Load Balancer.

</article>

<article id="7">

## Intuitive User Interfaces

WeDeploy offers two interfaces to make it easy to monitor and manage the projects and their services.

The **[WeDeploy Console](/docs/configure/web-console/)** lets you monitor resource allocation, check application health, and more with intuitive browser-based navigation, real-time graphs, and interactive debugging tools.

The **[WeDeploy Command-line Interface (CLI)](/docs/configure/command-line/)** provides you control from the comfort of a terminal. It’s powerful, yet easily scriptable, with handy commands to interact with your projects.

</article>

<article id="8">

## Logs and Metrics

Debugging issues and checking activity in your application is critical. We provide you with powerful and transparent logs that you can access from the Web Console or the CLI.

Also, we collect data on your CPU, Memory, Transfer, and service health to give you a beautiful graphical visualization of each service's performance.

</article>

<article id="9">

## Persistent Storage Volumes

Because we replace the service containers on every new deployment, it is important to have persistent storage for files and assets that you need to preserve through deployments and restarts.

To accomplish this, we provide a feature called **[Volumes](/docs/configure/persistent-storage/)**. These Volumes are accessible by any services in their project and can be easily mounted through your service's [configuration file](/docs/configure/the-wedeployjson/).

</article>

## What's next?

Learn more about [static hosting](/docs/getting-started/deploying-static-hosting/).