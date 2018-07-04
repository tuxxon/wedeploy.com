---
title: "Deploying Liferay Portal CE"
description: "Launch a Liferay Portal CE application in few seconds."
headerTitle: "Deploy"
layout: "guide"
weight: 9
---

### Liferay Portal CE

###### {$page.description}

<article id="1">

## Introduction

[Liferay Portal CE](https://community.liferay.com/-/portal) provides an architecture for companies to digitize business operations, deliver connected customer experiences, and gather actionable customer insight, with the ultimate goal of providing better customer experiences for their clients.

</article>

<article id="2">

## Try it yourself

Want to see the process of deploying Liferay Portal CE step by step?

<div class="guide-btn-cta">
  <a class="btn btn-accent btn-lg" href="/tutorials/liferay-portal-ce/" target="_blank">
    <span class="icon-16-external"></span>Try the tutorial
  </a>
</div>

<div class="guide-aux-cta">
	or see a <a href="https://github.com/wedeploy-examples/liferay-portal-ce-example" target="_blank">source code example</a>.
</div>

</article>

<article id="3">

## Configuring

<aside>

All WeDeploy projects use similar configuration files to prepare your projects for deployment. Learn more on our page about <strong><a href="/docs/deploy/getting-started/">Getting Started with Deploying</a></strong>.

</aside>

Below is an example of a `wedeploy.json` for a Liferay Portal CE service. The `id` for your services are uniquely determined by you.

```application/json
{
  "id": "myservice",
  "image": "wedeploy/liferay:@site.version.image.liferayce@",
  "volume": "/opt/liferay/data",
  "memory": 4096,
  "cpu": 3
}
```

</article>

<article id="4">

## Hot Deployment

Liferay Portal CE's hot deploy mechanism allows you to install themes, portlets, OSGi modules, and even a license by simply including WAR, JAR, and XML files into a `deploy` folder.

For example, if you wanted to deploy a custom JAR file, this is how your directory could look like:

```xml
myservice
├── deploy
│   └── com.liferay.wedeploy.samples.portlet-1.0.0.jar
└── wedeploy.json
```

Under the hood, those files will be copied into the `$LIFERAY_HOME/deploy` folder and automatically deployed on startup.

</article>

<article id="5">

## OSGi configurations

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

<article id="6">

## Liferay Portal CE Configuration

Liferay Portal CE can be configured using a properties file named `portal-ext.properties` and located in portal's classpath. WeDeploy allows you to deploy a portal-ext.properties to your Liferay Portal CE service simply including it next to the wedeploy.json file.

For example, if you wanted to deploy the configuration for your Liferay Portal CE, this is how your directory could look like:

```xml
myservice
├── portal-ext.properties
└── wedeploy.json
```

Under the hood, that file will be copied into the `$LIFERAY_HOME` folder and automatically applied on startup.

<aside>

###### <span class="icon-16-star"></span> Pro Tip

In order for Liferay Portal CE to work properly on WeDeploy, you need two properties to be set in your custom portal-ext.properties file:

```properties
web.server.protocol=https
redirect.url.security.mode=domain
```

Otherwise, Liferay Portal CE won't calculate the URLs properly under our load balancer with HTTPS protocol enabled.

</aside>

</article>

<article id="7">

## Shared libraries

Sometimes you want to make visible several Java libraries to both Tomcat internal classes and to all web applications. This is the case for JDBC drivers, and portlet or servlet API's, as example. For this reason Liferay DXP adds the `lib/ext` directory to Tomcat's **Common** classloader, and puts there several libraries for common use. WeDeploy allows you to upload your shared libraries to your Liferay DXP service simply including them into a `shared-libs` directory present next to the wedeploy.json file.

For example, if you wanted to add an Oracle JDBC driver to your Liferay Portal CE instance, this is how your directory could look like:

```xml
myservice
├── shared-libs
│   └── ojdbc6.jar
└── wedeploy.json
```

Under the hood, those files will be copied into the `$CATALINA_HOME/lib/ext` folder and automatically loaded on startup.

</article>

## What's next?

Now you can start building your Liferay Portal CE application.
