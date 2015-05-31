---
layout: post
title: Unable to ping devices connected on LAN in a D-Link Modem
---


I used to connect my Raspberry pi to my modem using USB Wi-Fi Adapter. Then ssh to my pi over Wi-Fi from my Laptop. Yesterday my USB Wi-Fi Adapter is not working. So I took a LAN Cable and connected my Pi to the D-Link Modem.
 Then the problem comes, 

 I'm not able to ssh or even ping to the Pi connected on LAN, from my Laptop which is using Wifi. After connecting my system on LAN Cable, I realised that Devices connected on LAN and Wi-Fi are isolated.

When both Pi and my Laptop are connected on Wi-Fi, there is no issue in ping or ssh. Similarly when both devices are in LAN there is no issue.

But I cannot use my Laptop always on LAN, then I spend a lot of time in all configurations of my D-link Modem(`DSL-2730U`). Finally found this Solution.

1. Log in to the modem configurations page, for me `192.168.1.1`
2. Navigate to `Setup` > `Wireless` > `Wireless Basic`
3. Then uncheck **`Enable MultiAP Isolation`** .
4. Click `Apply` Button and Reboot your modem.

![My screenshot]({{ site.url }}/assets/screenshot1.jpg)

