---
title: "Deployment"
description: "There are many ways to deploy your app based on the needs of your workflow."
headerTitle: "Configure"
layout: "guide"
weight: 2
---

### {$page.title}

###### {$page.description}

<article id="1">

## CLI

The CLI is one of the most powerful interfaces of WeDeploy. It allows you to manage your apps right from your terminal. There are two ways to deploy project from the CLI:

##### Local Source Code

![instant deployment](/images/blog/post-12--instant-deployment.gif)

By simply running the deploy command while inside the directly containing your source code, you can immediately start uploading your project files to WeDeploy.

```xml
we deploy
```

Once that command is finished, WeDeploy will start building and deploying your application. In the end, you'll be able to see it online in any browser.

##### Public GitHub Repo

If you don't have your code locally, you can provide the path (`org/repo`) to a public GitHub repo and we will deploy it.

```xml
we deploy wedeploy-examples/hosting-example
```

This will create a one-time deployment of that repo. If you want to make further changes, you need to clone the repo and deploy to those services again.

</article>

<article id="2">

## GitHub Integration

Especially for collaborative projects, you may want the site to always reflect the changes you commit to a source code repo. You push, we deploy, and it's live!

All you need to do is link a GitHub branch to a WeDeploy project and then every time you push changes to that branch, it will automatically trigger a new deployment.

![Connect to GitHub](/images/docs/getting-started/static-deployment-github.gif)

Once it's connected it will immediately start building and deploying your application. In the end, you'll be able to see it online in any browser.

</article>

<article id="3">

## Git URL

If you want to deploy from GitHub but not initiate the continuous integration feature, you can just deploy from a git URL.

![Deploy with Git URL](/images/docs/getting-started/deploy-with-git.gif)

This will create a one-time deployment of that repo. If you want to make further changes, you need to setup a GitHub integration or clone the repo and deploy it again using the CLI.

</article>

<article id="4">

## Deploy Button

You can deploy without touching a single line of code or running a command in your terminal. With the deploy button, all you do is click and follow the UI on our Web Console to deploy an app in a few seconds.


![Deploy Button](/images/docs/getting-started/deploy-button.gif)

All you need is a WeDeploy account and you deploy from anywhere! Go ahead, click the button below to try it out!

<a href="https://console.wedeploy.com/deploy?repo=https://github.com/wedeploy-examples/hosting-example" target="_blank">
  <img class="deploy-button" src="https://cdn.wedeploy.com/images/deploy.svg" alt="Deploy" style="width: 197px;" >
</a>

Behind the scenes, we are displaying an SVG image and wrapping it in a link element. The `href` for the link element contains a parameter which is the URL to your Git repo.

This is very helpful when you want your users to easily deploy your project from your website or GitHub readme. Here is the code you will need to add the button to your `html` or markdown files.

##### Markdown

```
[![Deploy](https://cdn.wedeploy.com/images/deploy.svg)](https://github.com/user/repo)
```

##### HTML

```
<a href="https://console.wedeploy.com/deploy?repo=https://github.com/user/repo" target="_blank">
  <img class="deploy-button" src="https://cdn.wedeploy.com/images/deploy.svg" alt="Deploy" style="width: 197px;" >
</a>
```

You can grab either of these code snippets and just update the repo parameter to the URL of your repo.

<aside>

The Deploy Button works with **[GitHub](https://github.com)**, **[GitLab](https://about.gitlab.com/)** and **[Bitbucket](https://bitbucket.org/)** repositories.

</aside>

</article>

## What's next?

Learn more about [Health Checks](/docs/configure/health-checks/).