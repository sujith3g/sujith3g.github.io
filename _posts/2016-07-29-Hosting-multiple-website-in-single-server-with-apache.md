---
layout: post
comments: true
title: How to host multiple website on a single server with Apache
---


If you are a web developer using Apache web server for hosting, then this is for you.
You might have faced scenarios where you have to host multiple websites in the same server. For instance if you want to host `example.com` and `sujith.com` in a server.
In Apache, we can use virtual hosts to do this.

I am assuming that you have already installed Apache webserver.

As a first step, keep the content of sites in `/var/www/example.com/html`, `/var/www/sujith.com/html` locations.

Now we have to create a virtual hosts file for both the sites in `/etc/apache2/sites-available/` directory.

### for first domain

Create the virtual host file from `000-default.conf`.

`$ sudo cp /etc/apache2/sites-available/000-default.conf /etc/apache2/sites-available/example.com.conf`

Open the created file in your favorite text editor

`$ sudo nano /etc/apache2/sites-available/example.com.conf`

Next you have to modify the default configuration like this:

```
 <VirtualHost *:80>
    ServerAdmin admin@example.com
    ServerName example.com
    ServerAlias www.example.com
    DocumentRoot /var/www/example.com/html
    ErrorLog ${APACHE_LOG_DIR}/example.error.log
    CustomLog ${APACHE_LOG_DIR}/example.access.log combined
</VirtualHost> 

```

### for second domain

Create the virtual host file from `000-default.conf`.

`$ sudo cp /etc/apache2/sites-available/000-default.conf /etc/apache2/sites-available/sujith.com.conf`

Open the created file in your favorite text editor.

`$ sudo nano /etc/apache2/sites-available/sujith.com.conf`

Next you have to modify the default configuration like this:

```
 <VirtualHost *:80>
    ServerAdmin admin@sujith.com
    ServerName sujith.com
    ServerAlias www.sujith.com
    DocumentRoot /var/www/sujith.com/html
    ErrorLog ${APACHE_LOG_DIR}/sujith.error.log
    CustomLog ${APACHE_LOG_DIR}/sujith.access.log combined
</VirtualHost> 

```
Now enable the sites

`$ sudo a2ensite example.com.conf`
`$ sudo a2ensite sujith.com.conf`

Once the sites are enabled, you have to map both `sujith.com` and `example.com` to the IP of this server in DNS settings of the domains.

You can also test this by manually adding an entry like this to `/etc/hosts`

```
  127.0.0.1 sujith.com
  127.0.0.1 example.com
  ## use server's IP address if you are testing from any other system.
```

Now you can test this by visiting `http://example.com` and `http://sujith.com`.
