---
title: "Big Improvements To Volumes"
description: "Our volumes feature is a simple way to choose what directory of your service you want to be persistent. This kind of persistent file system is very important for many applications and so that's why we are excited to share some big improvements we've made to our volumes."
date: "March 24, 2018"
author: "Thiago Moreira"
layout: "blog"
---

<article>

{$page.description}

#### What Are Volumes?

Before talking about the new features, it is important to remember how WeDeploy Volumes function. When you deploy your service, we host all your application files inside of your container and keep these files in a dynamic state so if you redeploy or restart your container, all those files will be replaced with new ones.

When you declare a volume path, you are telling us that you want all the application files inside that path to remain persistent (unchanging during a restart or redeploy).

Below is an example of a `wedeploy.json` with the old volume parameter.

```application/json
{
  "id": "service1",
  "volume": "bar/app/documents"
}
```

#### Multiple Volumes

One limitation with the old volume system was that you could only declare one volume per service. Today that changes with the capability to add multiple volumes to a service. This allows you to setup separate volumes for different assets or purposes.

Here is an example of the new multiple volume syntax.

```application/json
{
  "id": "service",
  "volumes": {
    "logs": "/foo/app/logs",
    "docs": "/bar/documents"
  }
}
```

As you can see, it is now necessary to add an `id` along with the path variable.

#### Shared Volumes

We received lots of feedback from you about the need for services to share the same file system. Whether it was to scrub application logs or share documents and files, we knew this would be an important feature to develop.

Now it's easy to call the same volume `id` in multiple services in order to share it. This is how it would look with two services sharing the same volume.

**Service 1**

```application/json
{
  "id": "service1",
  "volumes": {
    "logs": "/foo/app/logs",
    "docs": "/bar/documents"
  }
}
```

**Service 2**

```application/json
{
  "id": "service2",
  "volumes": {
    "logs": "/foo/app/logs"
  }
}
```

As you can see from above, by declaring the same volume `id` in both services, they can access the same files from that volume.

If you are just getting started with volumes, check this [code example](https://github.com/wedeploy-examples/volumes-example), or if you want to see a real application demo of the shared volume concept, take a look at this [example](https://forsale.wedeploy.io) (or the [source code](https://github.com/wedeploy-examples/forsale-example)).


#### Performant Volumes

While working on this big exciting improvements to the volumes, we also took the opportunity to improve the volume performance. A lot!

Now they are 5x faster than before! Take a look below to see the difference in speeds between the old and new volumes.

<figure>
  <img src="/images/blog/post-27--0.png">
</figure>

#### Backwards Compatibility

As of today, the new volumes are ready to be used in your `wedeploy.json` but both the old (`volume`) and new (`volumes`) properties will be accepted.

We strongly encourage you to begin using the new `volumes` property because in a few months we will discontinue support for the previous version.

---

We are excited about these new volume features and how they can help you develop amazing applications even faster than before.

**If you have any questions, check our [volume documentation](/docs/configure/the-wedeployjson/#volumes) or join our [Slack Community](https://chat.wedeploy.com).**

</article>
