---
layout: post
title:  Unable to Start MySQL on Fedora System Boot
date:   2014-05-07 20:35:55
modified: 2014-10-21 23:13
categories: database fedora
tags: [mysql, mariadb, fedora, apache, php, systemctl]
excerpt: "A binary drop in replacement of MySQL Server."
comments: true
---

This evening, I was updating a set of web development tools on my Fedora 20 machine, including Apache 2.4.9, PHP 5.5.12 and MySQL 5.5.37. After that, I started all the services and enabled them to run on startup. But I cannot enable MySQL service with the following command (as usual):

{% highlight bash %}
# systemctl enable mysqld.service
Failed to issue method call: No such file or directory
{% endhighlight %}

After did some research on this issue, I found that **MariaDB** is a binary drop in replacement of the same MySQL version (on Fedora 20). So that MySQL 5.5 will be compatible with MariaDB 5.5. 

{% highlight bash %}
# mysql --version
mysql  Ver 15.1 Distrib 5.5.37-MariaDB, for Linux (x86_64) using readline 5.1
{% endhighlight %}

To be able to start MySQL server when system boot, you must enable `mariadb.service`.

{% highlight bash %}
# systemctl enable mariadb.service
ln -s '/usr/lib/systemd/system/mariadb.service' '/etc/systemd/system/multi-user.target.wants/mariadb.service'

# systemctl start mariadb.service
{% endhighlight %}




