---
layout: post
title: How to list all IPs OR Hosts in the connected network
---

Last week when I started working with my Raspberry Pi, I was looking for a tool to find the Pi's IP, Normally we used to login to the modem for details of connected hosts.  But I wanted to list all hosts and their IPs in the connected network very quickly without logging into modem. 
Then I found a command-line tool called [nmap](http://en.wikipedia.org/wiki/Nmap) for listing all hosts connected to the local network.
[nmap](http://en.wikipedia.org/wiki/Nmap) is a security scanner used to discover hosts and services on a computer network.

###How to use nmap to list all Hosts connected to the local network###

first you have to check whether nmap is installed or not. by typing the following command

```sh
	$ nmap --version
```

If nmap is not installed, install it by typing

```sh
	$ sudo apt-get install nmap
```
Now type the following command to list all hosts

```sh
	$ nmap -sn 192.168.1.0/24
```

Which gives you a list like this

```
	$ nmap -sn 192.168.1.0/24

	Starting Nmap 6.40 ( http://nmap.org ) at 2014-12-28 16:55 IST
	Nmap scan report for 192.168.1.1
	Host is up (0.0028s latency).
	Nmap scan report for 192.168.1.2
	Host is up (0.0063s latency).
	Nmap scan report for 192.168.1.3
	Host is up (0.049s latency).
	Nmap scan report for 192.168.1.4
	Host is up (0.0030s latency).
	Nmap scan report for 192.168.1.5
	Host is up (0.00019s latency).
	Nmap done: 256 IP addresses (5 hosts up) scanned in 4.09 seconds
```
Here the option `-sn` stands for Ping scan, and `192.168.1.0/24` is the subnet change this with details of your network.
