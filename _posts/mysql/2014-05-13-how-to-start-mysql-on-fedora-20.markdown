---
layout: post
title:  "How to start mysql server : Failed to issue method call: No such file or directory"
date:   2014-05-07 20:35:55
categories: database fedora
---

Problem :
cannot start mysql server on Fedora / Unable to start mysql on startup with the following command:
{% highlight Bash shell scripts %}
systemctl enable mysqld.service
{% endhighlight %}

Solution:
systemctl enable mariadb.service







