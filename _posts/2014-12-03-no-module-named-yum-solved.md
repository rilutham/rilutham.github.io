---
layout: post
title:  Yum Problem - No module named yum
date:   2014-12-3 18:52
categories: fedora package python 
tags: [python, django, yum, urlgrabber, python-urlgrabber, rpm]
excerpt: "Solving problem importing one of the Python modules required to run yum."
comments: true
---

Today, I accidentally delete python site-packages directory on /usr/lib/python2.7/ when trying to uninstall Django. Oh my God, it causes yum on my fedora 20 machine is not working. When I try to execute `yum update`, `yum clean all` or `yum install [packages]`, it returns the following error.

{% highlight bash %}
$ sudo yum update

There was a problem importing one of the Python modules
required to run yum. The error leading to this problem was:

   No module named yum

Please install a package which provides this module, or
verify that the module is installed correctly.

It's possible that the above module doesn't match the
current version of Python, which is:
Python 2.7.5 (default, Dec  3 2014, 07:36:20) 
[GCC 4.8.3 20140911 (Red Hat 4.8.3-7)]

If you cannot solve this problem yourself, please go to 
the yum faq at:
  http://wiki.linux.duke.edu/YumFaq
{% endhighlight %}

### How to fix?

* Check yum version 
{% highlight bash %}
$ rpm -qa yum
yum-3.4.3-152.fc20.noarch
{% endhighlight %}

* Download yum package depend on the version and machine type (32 or 64 bit) 
{% highlight bash %}
$ wget ftp://rpmfind.net/linux/fedora/linux/updates/20/x86_64/yum-3.4.3-152.fc20.noarch.rpm
{% endhighlight %}

* Upgrade yum package
{% highlight bash %}
$ sudo rpm -Uvh --force yum-3.4.3-152.fc20.noarch.rpm 
{% endhighlight %}

**yum** should work now, but sometime there was a problem with `urlgrabber` when trying to execute yum.
{% highlight bash %}
   No module named urlgrabber
{% endhighlight %}

Do the same way as when we are solve yum problem.

{% highlight bash %}
$ rpm -qa python-urlgrabber
python-urlgrabber-3.9.1-32.fc20.noarch

$ wget ftp://rpmfind.net/linux/fedora/linux/releases/20/Everything/x86_64/os/Packages/p/python-urlgrabber-3.9.1-32.fc20.noarch.rpm

$ sudo rpm -Uvh --force python-urlgrabber-3.9.1-32.fc20.noarch.rpm
{% endhighlight %}

And ... Now you can use yum like a boss.
