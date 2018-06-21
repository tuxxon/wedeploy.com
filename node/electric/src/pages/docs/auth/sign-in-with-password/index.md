---
title: "Sign-in With Password"
description: "Let your users authenticate using their emails and passwords."
headerTitle: "Auth"
layout: "guide"
weight: 3
---

### {$page.title}

###### {$page.description}

<aside>

If you are unfamiliar with our API, please visit the [WeDeploy SDK's](/docs/configure/wedeploy-sdks/) page first to learn how to install and configure it.

</aside>

<article id="1">

## Authenticate

To sign in using email and password, call this method:

```javascript
WeDeploy
  .auth('https://<serviceID>-<projectID>.wedeploy.io')
  .signInWithEmailAndPassword("user@domain.com", "password")
  .then(function(user) {
    // User is signed in.
  })
  .catch(function(err) {
    // User is not signed in.
  });
```
```swift
WeDeploy
  .auth('https://<serviceID>-<projectID>.wedeploy.io')
  .signInWith(username: "user@domain.com", password: "password")
  .then { auth -> Void in
    // User is signed in.
  }
  .catch { err in
    // User is not signed in.
  }
```
```text/x-java
WeDeploy
  .auth("<auth-url>")
  .signIn("user@domain.com", "password")
  .execute();
```
```text/x-sh
curl -X "POST" "https://<serviceID>-<projectID>.wedeploy.io/oauth/token" \
     -H 'Content-Type: application/json' \
     -d $'{
        "grant_type": "password",
        "username": "user@domain.com",
        "password": "password"
      }'
```

</article>

## What's next?

Now we're ready to start enabling other [login providers like Facebook](/docs/auth/sign-in-with-facebook/).
