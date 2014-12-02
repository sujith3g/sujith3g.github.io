---
layout: post
title: Running Background process in remote server using ssh
---

If you are handling remote server using ssh, You may require this. Last week I was trying to run my meteor application on the server using ssh. I started the meteor app on the server using ssh, But when I logged out from the ssh console, the meteor app stopped. I wanted a solution to run a background process in the server. So that the process I started won't exit even If I logged out from the ssh console. The following commands worked.

First I started the process(for me its my meteor app) as background process using `&` at the end of command as shown below

```sh
	$ meteor -p 4040 &
```
Then I got the output with the processId, like this

```sh
	$ meteor -p &
	[1] 11436
```
which shows two things `[1]` is the job-number for the background job and the `11436` is the pID for that particular job

