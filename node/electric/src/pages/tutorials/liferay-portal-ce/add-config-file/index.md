---
title: "Add Config File"
description: "In this section, you'll learn how to deploy a Liferay Portal CE instance on WeDeploy."
buttonTitle: "I added the config files"
tutorialTitle: "Getting started with Liferay Portal CE"
parentId: "liferay-portal-ce"
layout: "tutorial"
time: 40
weight: 3
---

#### Add Config File

Every service folder must have a `wedeploy.json` file that configures it, so let's add one file inside the sample project you just downloaded.

1. Open the `liferay-portal-ce-tutorial` folder in a code editor
2. Create a new file named `wedeploy.json`.
3. In that file, paste this code:

```application/json
{
  "id": "liferay",
  "image": "wedeploy/liferay-portal-ce:7.1.0-b3-1.0",
  "memory": 4096,
  "cpu": 3,
  "healthCheck": {
    "url": "localhost:8080",
    "startPeriod": 120,
    "retries": 30
  }
}
```