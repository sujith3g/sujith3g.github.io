---
layout: post
comments: true
title: How to test cordova-specific feature in a meteor package using Tinytest on Android device.
---

Last week I have created a [meteor](http://meteor.com/) package which had some cordova specific feature. Now its time to test the package.
So I was about to use Tinytest for testing the package. Then the problem comes, How to test the cordova-specific feature ?.
I read the Meteor Cordova Phonegap Integration guide from [here](https://github.com/meteor/meteor/wiki/Meteor-Cordova-Phonegap-integration). They mentioned about how to perform tests in an android device [here](https://github.com/meteor/meteor/wiki/Meteor-Cordova-Phonegap-integration#testing). Now I tried the following

```
meteor test-packages --android-device ./
```

Then an android app opened in my android device showing.

> Testing in progress..
> Passed 0 of 0

It never started the tests, the message was showing for longtime. Then after trying all arguments to the `meteor test-packages`, I found the following fix for running tests on android device, especially for testing cordova-specific feature.

```
meteor test-packages --android-device ./ --mobile-server http://192.168.1.4:3000

```

The mobile-server(`--mobile-server http://<host>:<port>`) argument is required for it to work on android device.
