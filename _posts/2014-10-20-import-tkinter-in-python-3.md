---
layout: post
title: Import tkinter in Python 3
date: 2014-10-20 15:03
categories: programming tool
excerpt: "There is an overview of installing and importing tkinter on Python 3 for GUI Programming"
tags: [tkinter, tcl/tk, python3]
comments: true
---
Tkinter is a bridge that connects programmers with **[tk](http://www.tcl.tk/)** which is written in Python. Tk provides all the graphical widgets, so that it enables us to develop GUI applications. In other words, Tkinter is a portable GUI toolkit for Python. If you had just migrated from python2 to python3, you might faced some problems when importing Tkinter.

{% highlight bash %}
$ python3

Python 3.3.2 (default, Jun 30 2014, 17:20:03) 
[GCC 4.8.3 20140624 (Red Hat 4.8.3-1)] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> import tkinter
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named 'tkinter'
{% endhighlight %}

### Install tkinter for Python3
In python2, we usually install `tkinter` package and it can immediately imported. But we can not do that in python 3. So, install `python3-tkinter` package to be able to import tkinter.

{% highlight bash %}
# yum install python3-tkinter
{% endhighlight %}

### Check your tkinter support
Enter an interactive Python interpreter in your favorite shell/ Terminal.

{% highlight bash %}
$ python3

Python 3.3.2 (default, Jun 30 2014, 17:20:03) 
[GCC 4.8.3 20140624 (Red Hat 4.8.3-1)] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> import tkinter
>>> tkinter._test()
{% endhighlight %}

If this works, it should pop up a small window with two buttons (Click me! and QUIT) and you're all set. Congratulations!