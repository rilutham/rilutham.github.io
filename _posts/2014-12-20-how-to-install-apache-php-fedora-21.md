---
layout: post
title:  Install Apache - PHP - Maria DB on Fedora 21
date:   2014-12-20 21:00
categories: fedora apache python maria mysql 
tags: []
excerpt: "Guide in installing web server on Fedora 21."
comments: true
---

Hi Developers! This is the ingredients before you cooking, isn’t it? I made the recipe for you.

## Apache

Install Apache:

{% highlight bash %}
$ sudo yum install httpd
{% endhighlight %}

Start Apache service:

{% highlight bash %}
$ sudo systemctl start httpd.service

# Start Apache when fedora boot
$ sudo systemctl enable httpd.service
{% endhighlight %}

Go to `localhost` in your favorite page to check whether the Apache is run or not. To make the Fedora Test Page go away, commenting out the lines in `/etc/httpd/conf.d/welcome.conf`. Apache configuration file is in `/etc/httpd/conf/httpd.conf`.

## PHP

Install PHP:

{% highlight bash %}
$ sudo yum install php php-common
{% endhighlight %}

Install PHP module:

{% highlight bash %}
$ sudo yum install php-pecl-apcu php-cli php-pear php-pdo php-mysqlnd php-pgsql php-pecl-mongo php-sqlite php-pecl-memcache php-pecl-memcached php-gd php-mbstring php-mcrypt php-xml
{% endhighlight %}

## Maria DB

Why am I choose Maria DB than MySQL? Check this out [Replace MySQL with MariaDB](http://fedoraproject.org/wiki/Features/ReplaceMySQLwithMariaDB). Install Maria DB:

{% highlight bash %}
$ sudo yum install mariadb mariadb-server
{% endhighlight %}

Start Maria DB service:

{% highlight bash %}
$ sudo systemctl start mariadb.service

# Start Maria DB when fedora boot
$ sudo systemctl enable mariadb.service
{% endhighlight %}

Configure Maria DB server:

{% highlight bash %}
$ sudo mysql_secure_installation

# And follow the instruction.
{% endhighlight %}

And if you a big fan of `phpMyAdmin`, go ahead install it:

{% highlight bash %}
$ sudo yum install phpMyAdmin
{% endhighlight %}

Happy coding :)