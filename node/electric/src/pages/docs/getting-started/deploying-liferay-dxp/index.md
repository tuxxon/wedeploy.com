---
title: "Deploying Liferay DXP"
description: "Launch a Liferay DXP Trial application in few seconds."
headerTitle: "Getting Started"
layout: "guide"
weight: 8
---

### {$page.title}

###### {$page.description}

<article id="1">

## Introduction

[Liferay DXP](https://www.liferay.com/digital-experience-platform) provides an architecture for companies to digitize business operations, deliver connected customer experiences, and gather actionable customer insight, with the ultimate goal of providing better customer experiences for their clients.

We give you a free 15 day trial period to test and develop your DXP instance.

Deploy a Liferay DXP stack site now with just the click of a button!

<a href="https://console.wedeploy.com/deploy?repo=https://github.com/wedeploy-examples/liferay-dxp-example" target="_blank">
  <img style="width:197px;" src="https://cdn.wedeploy.com/images/deploy.svg">
</a>

To learn more, you can also follow our **[step by step Tutorial](/tutorials/liferay-dxp/)** or look through the **[example source code](https://github.com/wedeploy-examples/liferay-dxp-example)**.

</article>

<article id="2">

## Configuring

<aside>

All WeDeploy projects use similar a [configuration file](/docs/configure/the-wedeployjson/) to prepare your projects for deployment.

</aside>

Below is an example of a `wedeploy.json` for a Liferay DXP service. The `id` for your services are uniquely determined by you.

```application/json
{
  "id": "myservice",
  "image": "wedeploy/liferay:@site.version.image.liferay@",
  "volume": "/opt/liferay/data",
  "memory": 4096,
  "cpu": 3
}
```

</article>

<article id="3">

## Hot Deployment

Liferay DXP's hot deploy mechanism allows you to install themes, portlets, OSGi modules, and even a license by simply including WAR, JAR, and XML files into a `deploy` folder.

For example, if you wanted to deploy a custom JAR file, this is how your directory could look like:

```xml
myservice
├── deploy
│   └── com.liferay.wedeploy.samples.portlet-1.0.0.jar
└── wedeploy.json
```

Under the hood, those files will be copied into the `$LIFERAY_HOME/deploy` folder and automatically deployed on startup.

<aside>

###### <span class="icon-16-star"></span> Pro Tip

You can provide your own activation key to your Liferay DXP instance on WeDeploy. Simply put your license or activation key inside the deploy folder with the name `license.xml`. If this file exists, we will use your license instead of starting a 30-day DXP trial.

</aside>

</article>

<article id="4">

## OSGi Configurations

OSGi framework allows you to configure OSGi modules by simply including `.cfg` and `.config` files into an `osgi-configs` folder.

For example, if you wanted to deploy a configuration for the Elasticsearch OSGi bundle, this is how your directory could look like:

```xml
myservice
├── osgi-configs
│   └── com.liferay.portal.search.elasticsearch.configuration.ElasticsearchConfiguration.config
└── wedeploy.json
```

Under the hood, those files will be copied into the `$LIFERAY_HOME/osgi/configs` folder and automatically applied on startup.

</article>

<article id="5">

## Liferay DXP Configuration

Liferay DXP can be configured using a properties file named `portal-ext.properties` and located in portal's classpath. WeDeploy allows you to deploy a portal-ext.properties to your Liferay DXP service simply including it next to the wedeploy.json file.

For example, if you wanted to deploy the configuration for your Liferay DXP, this is how your directory could look like:

```xml
myservice
├── portal-ext.properties
└── wedeploy.json
```

Under the hood, that file will be copied into the `$LIFERAY_HOME` folder and automatically applied on startup.

<aside>

###### <span class="icon-16-star"></span> Pro Tip

In order for Liferay DXP to work properly on WeDeploy, you need two properties to be set in your custom portal-ext.properties file:

```properties
web.server.protocol=https
redirect.url.security.mode=domain
```

Otherwise, Liferay DXP won't calculate the URLs properly under our load balancer with HTTPS protocol enabled.

</aside>

</article>

<article id="6">

## Shared Libraries

Sometimes you want to make visible several Java libraries to both Tomcat internal classes and to all web applications. This is the case for JDBC drivers, and portlet or servlet API's, as example. For this reason Liferay DXP adds the `lib/ext` directory to Tomcat's **Common** classloader, and puts there several libraries for common use. WeDeploy allows you to upload your shared libraries to your Liferay DXP service simply including them into a `shared-libs` directory present next to the wedeploy.json file.

For example, if you wanted to add an Oracle JDBC driver to your Liferay DXP instance, this is how your directory could look like:

```xml
myservice
├── shared-libs
│   └── ojdbc6.jar
└── wedeploy.json
```

Under the hood, those files will be copied into the `$CATALINA_HOME/lib/ext` folder and automatically loaded on startup.

</article>

## What's next?

Learn more about [configuring your wedeploy.json](/docs/configure/the-wedeployjson/).
