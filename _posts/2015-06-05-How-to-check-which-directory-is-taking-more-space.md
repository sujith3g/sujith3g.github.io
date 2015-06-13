---
layout: post
title: How to check which directory is taking more disk space in linux
---

Yesterday when I logged in to my server, I noticed that about 90% of the disk space used. Normally I use ssh to access my server from home.
So I wanted a tool/method to find the directory which is using more disk space, that too from terminal. After some googling I found the following command which will list the top largest directories

To list top 10 largest directories in the current directory

```sh
	$ du -ks * | sort -nr | head -n10
```  

In the above commands we are using three linux command line utilities:

*    [`du`](https://en.wikipedia.org/wiki/Du_(Unix)), Disk usage utility
*    [`sort`](https://en.wikipedia.org/wiki/Sort_(Unix)), Sorting program in unix.
*    [`head`](https://en.wikipedia.org/wiki/Head_(Unix)), head is a program on Unix and Unix-like systems used to display the beginning of a text file or piped data.

first `du` command is used for finding the size of each file/directory, then piped the output to `sort`, afterwards the sorted data is passed to `head`. 

Options used with [`du`](https://en.wikipedia.org/wiki/Du_(Unix))

```
    k: show sizes as multiples of 1024 bytes, not 512-byte
    s: report only the sum of the usage in the current directory, 
    not for each file
```
Options used with [`sort`](https://en.wikipedia.org/wiki/Sort_(Unix))

```
   n: used to perform numeric value based sorting
   r: used to reverse the sort order
```
Options used with [`head`](https://en.wikipedia.org/wiki/Head_(Unix))

```
   n: used to specify the number of lines to be printed 
```
 The output for the above command will look like this

 ```
41752	Mac Format - March 2015 {bk}.pdf
23892	nmap-6.49BETA1.dmg
4976	Malare Ninne -SongspkFree.Com.mp3
1064	demo login fb.apk
776	indian_patent.sql
240	IntelHAXM_1.0.8.mpkg
164	DocketingDB - Latest.csv
48	Capture.PNG
40	12453385.pdf
24	11245371.pdf
 ```
This method is  not that easy, there is a handy tool for doing the same thing. That is [`ncdu`](http://linux.die.net/man/1/ncdu) (NCurses Disk Usage), which is a curses-based version of `du`, and provides a fast way to see what directories are using your disk space. 

You can install [`ncdu`](http://linux.die.net/man/1/ncdu) on your ubuntu machine using **apt**

```sh
    $ sudo apt-get install ncdu
```
For **mac** users

```sh
    $ brew install ncdu
```
Sample output from [`ncdu`](http://linux.die.net/man/1/ncdu)

```sh
- /home/server ----------------------------------------------------------
   10.3GiB [##########] /Desktop
    9.9GiB [######### ] /.local
    5.3GiB [#####     ] /.meteor
  622.1MiB [          ] /.cache
  616.3MiB [          ] /clex
  197.2MiB [          ] /purple_line
  188.3MiB [          ] /Downloads
  147.9MiB [          ] /.config
  146.6MiB [          ] /.npm
  106.4MiB [          ] /.meteorite
   83.2MiB [          ] /back_up
   43.8MiB [          ] /mongo_db
   19.2MiB [          ] /.node-gyp
   18.9MiB [          ] /mrt
    1.7MiB [          ] /.thunderbird
```

