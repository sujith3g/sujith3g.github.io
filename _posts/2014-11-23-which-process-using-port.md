---
layout: post
title: How to find which process is using a particular port on Ubuntu
---


There are situations in which we will get this error  message.

```sh

 the port is already in use 

 ```


This occurs when we are trying to install or execute something, and after some searching I found the following commands, to find the process which uses a particular port. I am adding the commands to kill that (if required), most of the time I do so.  

So open a terminal window by pressing ``` ctrl + alt + t ``` .

These are the commands to find which process is using port ``` 3000 ```

```sh
	
	sudo netstat -tulpn | grep 3000

```

This may ask you for administrator password. It gave me this output.

```sh
	
	sg@sg-pc:~$ sudo netstat -tulpn | grep 3000
	
	tcp        0      0 0.0.0.0:3000            0.0.0.0:*               LISTEN      19911/node

```

A node server script is running with PID 19911, to kill that I use ```sh $ sudo kill 19911 ```.

So port ``` 3000 ``` on my system is free now :)