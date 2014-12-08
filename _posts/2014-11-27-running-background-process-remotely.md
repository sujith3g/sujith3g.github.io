---
layout: post
title: Running Background process in remote server using ssh
---

If you are handling remote server using ssh, You may require this. Last week I was trying to run my meteor application on the server using ssh. I started the meteor app on the server using ssh, But when I logged out from the ssh console, the meteor app stopped. I wanted a solution to run a background process in the server. So that the process I started won't exit even If I logged out from the ssh console. The following commands worked.

First I started the process(for me its my meteor app) as background process using `&` at the end of command as shown below

```sh
	$ meteor -p 4040 >> ~/myapp.log &
```
Then I got the output with the processId, like this

```sh
	$ meteor -p 4040 >> ~/myapp.log &
	[1] 11436
```
which shows two things `[1]` is the job-number for the background job and the `11436` is the pID for that particular job

Now use the `$ bg` command to move the job to background, [bg](http://en.wikipedia.org/wiki/Bg_%28Unix%29) resumes the suspended process in the background.

Now use [disown](http://en.wikipedia.org/wiki/Disown_%28Unix%29) command to remove the process from job table, so that the process will be running in the background even we logged out from the ssh console. 

```sh
	$ disown %1

```
The `%1` is the job number to be removed from the job table, which we can get either from the output of the first command or you can use the `$ jobs` command to find the job number. which lists the status of all running jobs with their job number.