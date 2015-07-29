---
layout: post
comments: true
title: How to create wifi hotspot in access-point mode on Ubuntu 14.04
---

In our office we had only wired internet connection, I wanted wifi connection for internet access to my mobile phone. I have tried WiFi hotspot created using Ubuntu's pre-installed network manager, but it was not working properly.
I have searched a lot to get one good WiFi hotspot solution that is working in Ubuntu 14.04.
The solution was to create a WiFi Hotspot in access-point mode. For which we need a network card which supports access-point mode.

> This solution works only with, WiFi/Network cards supports access-point(AP) mode.

To check whether your network card supports access-point mode or not, use the following command

```sh
    $ sudo apt-get install iw
    $ iw list
```
Look for  `AP` entry under supported interface section, If it is present you can proceed.

Ubuntu's pre-installed Network Manager doesn't support AP mode, So we are using the KDE’s connection editor which supports the AP mode. You can install it uing

```sh
  $ sudo apt-get install plasma-nm
```
Once it is installed You can start it by 

```sh
  $ kde-nm-connection-editor	
```
After opening it, click `Add` Button and choose `Wirless(shared)`, Now in the wireless tab set an SSID and choose `Access Point` mode.
Now set the password in the `Wireless Security` tab and Click OK.
Now your WiFi Hotspot will be visible to all other devices.

