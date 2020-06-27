---
layout: post
comments: true
title: How to enable password authentication in MongoDB 3.x
---

Create one admin user in the special db `admin` like this:

```sh

  $ mongo
  > use admin
  > db.createUser({user:"root-username",pwd:"root-password", roles:[{role:"root",db:"admin"}]})
  > exit

```

Now open `/ect/mongod.conf` in your favorite text editor and enable authentication by adding this to it:

```sh

security:
   authorization: enabled

```

Now restart your mongodb `sudo service mongod restart`.
