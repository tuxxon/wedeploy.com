---
title: "How to Export Your Data from WeDeploy"
description: "As you know WeDeploy is being discontinued. In order to facilitate the process of moving to another cloud provider, we created this guide that goes over different use cases that you might have in order to export your data."
date: "March 17, 2019"
author: "WeDeploy Team"
layout: "blog"
---

<article>

As you know [WeDeploy is being discontinued](/blog/discontinuing-wedeploy/). In order to facilitate the process of moving to another cloud provider, we created this guide that goes over different use cases that you might have in order to export your data.

#### Export Data from WeDeploy Auth and WeDeploy Data

Both WeDeploy Auth and WeDeploy Data share the same core features and can be exported following these steps:

**A) Get the Master Token**

You can do that by going to your project page, clicking on `Settings`, and then copying the `Master Token` value.

<figure>
  <img class="blog-img-shadow" src="/images/blog/post-32--1.png">
</figure>

**B) Find the Collection you want to export**

You can do that by going to the service page, clicking on `Database`, and then looking at the `Collections` dropdown.

<figure>
  <img class="blog-img-shadow" src="/images/blog/post-32--2.png">
</figure>

**C) Make a request to the Collection using your Master Token**

For example, if I have a project named `geolocationsearch`, a service named `db`, and a collection named `places`, I could simply put this URL into the browser.

```
https://db-geolocationsearch.wedeploy.io/places?access_token=afd533a0-005c-487d-8b19-58db6d9f5241
```

Or run a cURL command to export the data as JSON into a local file.

```
curl https://db-geolocationsearch.wedeploy.io/places?access_token=afd533a0-005c-487d-8b19-58db6d9f5241 > data.json
```

If you have a collection with more than 10000 records, you can use [this tool](https://github.com/ipeychev/wedeploy-fetch-data) we created to facilitate the export process.

#### Export Data from Volumes

In order to be able to persist data between services, we introduced the concept of volumes. Quite simply, volumes are designated directories that live outside of the file system where your code runs.

To export your volumes, you need to deploy the following service into each project you need to export.

**A) Deploy Export Service**

1. Create a folder
2. Create a file called `wedeploy.json` in that folder
3. Update the `wedeploy.json` file to include:

```application/json
{
  "id": "volumes",
  "image": "coderaiser/cloudcmd",
  "port": 8000,
  "env": {
    "CLOUDCMD_ROOT": "/",
    "CLOUDCMD_AUTH": "true",
    "CLOUDCMD_ONE_FILE_PANEL": "true",
    "CLOUDCMD_PASSWORD": "passwordofyourchoice",
    "CLOUDCMD_USERNAME": "usernameofyourchoice"
  },
  "volumes": {
    "dbdata": "/wedeploy/volumes/dbdata",
    "mydata": "/wedeploy/volumes/mydata"
  }
}
```

1. Replace `passwordofyourchoice` with a password of your choice
2. Replace `usernameofyourchoice` with a username of your choice
3. Replace `dbdata` and `mydata`, to be the name and path of your real volumes
4. Run `we deploy --project projectofyourchoice` in the folder to deploy it

**B) Download .tar.gz**

1. Run `we open --project projectofyourchoice --service volumes` to open in the browser
2. Enter your username and password to authenticate
3. Right click on `volumes`
4. Click Download

#### Need more help?

Feel free to reach out [via email](mailto:ocvh9014@wedeploy-c8529f632b6e.intercom-mail.com
) or via chat by using the green button on the bottom right corner of your screen.

</article>
