---
layout: post
title: Error While Installing StarUML on Wine
date: 2014-05-07 20:35:55
categories: wine starUML OOP Development
excerpt: "A tips to fix error while installing StarUML on Wine."
---

StarUML is a powerful open source UML modeling tool. Unfortunately, it is only available for Mac OS and Windows. But it's not a big deal for me and all Linux users around the world. Thanks to Wine which allow applications designed for Windows to run on Unix-like OS.

This evening, i tried to install StarUML on Wine (on my Fedora 20 machine) and found the following error:

{% highlight bat %}
C:\Program Files\StarUML\Pgmr101.ocx
> |
> | Unable to register the DLL/OCX: LoadLibrary failed; code 126.
> | Module not found.
{% endhighlight %}

## How to Fix?
Open your favorite shell, install winetricks and some prerequisites packages :

{% highlight bash %}
# wget http://kegel.com/wine/winetricks
# sh winetricks vcrun6 msxml4
{% endhighlight %}

Congratulation and enjoy your UML modeling job :)