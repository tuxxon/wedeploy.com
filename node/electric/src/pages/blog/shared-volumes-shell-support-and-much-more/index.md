---
title: "Shared Volumes, Shell Access, and Much More"
description: "We may only be a few months in, but 2018 has been an exciting year for us here at WeDeploy. There are many features we've been working on and today we finally get to share them all with you."
date: "March 26, 2018"
author: "Eduardo Lundgren"
layout: "blog"
---

<article>

{$page.description}

#### Multiple Shared Volumes

Our volumes feature is a simple way to choose what directory of your service you want to be persistent. This kind of persistent file system is essential for many applications and so that's why we are excited to share that now you can declare multiple volumes in each service and seamlessly share them across all your services.

It's as easy as sharing the volume ID between two services like below.

**Service 1**

```application/json
{
  "id": "service1",
  "volumes": {
    "logs": "foo/app/logs",
    "docs": "bar/documents"
  }
}
```

**Service 2**

```application/json
{
  "id": "service2",
  "volumes": {
    "logs": "foo/app/logs"
  }
}
```

**Read more about it in our [Improved Volumes blog post](/blog/big-improvements-to-volumes/).**

#### Shell Access

Command-line tools are fundamental for developer experience and productivity because they deliver speed, control, traceability, scripting and automation capabilities to the developer’s workflow.

In many cases, it's challenging to get full visibility and control in your service. Shell access makes it easy to see whats going on inside your application, look for side effects that would not be easily spotted in the logs or even call functions like data population or report generation that are just meant to be performed once.

<figure>
  <img src="/images/blog/post-25--0.gif" alt="WeDeploy Shell" />
</figure>

Now WeDeploy Shell provides you with secure, command-line access to your service directly from your browser so you can easily manage your service and perform commands just like you were logged into your server.

**Read more about it in our [WeDeploy Shell blog post](/blog/introducing-wedeploy-shell/).**

#### Improved Performance

Performance is something very dear to our hearts. This is why we are happy to share that now we are exclusively using all Solid-State Drive (SSD) storage. This gives you access to the speed and durability of SSD along with the scalability of the cloud.

We know new features are awesome, but at the end of the day we all want to see the numbers. These are the results of our performance comparison between the old and new infrastructure.

<figure>
  <img src="/images/blog/post-26--1.png" alt="Performance" />
</figure>

#### New Code Examples

Seeing live code is one of the most effective ways to show how a new technology works. Because of this, we feel that it is imperative to keep our code demonstrations well maintained and updated.

To accomplish this, we moved all the boilerplates and demos to a new GitHub Repo called [WeDeploy Examples](https://github.com/wedeploy-examples). Our goal is to provide you with more accessible and updated code examples that show how you can easily use WeDeploy.

<figure>
  <img src="/images/blog/post-26--0.png" alt="New Examples Org" />
</figure>

We also moved all branches to their own repo. This improved the exposure to the examples with non-web environments like Android, iOS, and React Native.

**Explore our new [Organization](https://github.com/wedeploy-examples) or see our growing list of examples.**

#### cURL Documentation

We're always looking for ways to be more accessible to any developer using any kind of programming language.

As you may know, we currently have three official SDKs for [JavaScript](/docs/configure/wedeploy-sdks/#2), [Swift (iOS)](/docs/configure/wedeploy-sdks/#3), and [Java (Android)](/docs/configure/wedeploy-sdks/#4). Those libraries are great and can help you work with our services in a much easier way, but we wanted to go back to the basics and introduce cURL docs.

<figure>
  <img src="/images/blog/post-22--1.gif" alt="Shell docs" />
</figure>

If you are using languages like PHP, Python, Ruby, Go or C++, this will be a valuable addition to our docs.

**Check out our new [cURL docs](/docs/).**

---

Haven't tried WeDeploy before and want to get started? [Create a free account](https://console.wedeploy.com/signup) today and start deploying in seconds!

If you need any help or want to give us feedback, please **[join our WeDeploy Community](https://chat.wedeploy.com)**.

</article>
