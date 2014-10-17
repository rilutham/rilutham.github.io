---
layout: post
title: Error While Installing StarUML on Wine
date: 2014-05-07 20:35:55
categories: oop tool
excerpt: "A tips to fix error while installing StarUML on Wine."
tags: [StarUML, Wine, ArgoUML, starUML on Wine, Wine on Fedora 20, DLL/OCX, kegel, winetricks, vcrun6, msxml4]
comments: true
---

[StarUML](http://staruml.io/) is a powerful open source UML modeling tool. Unfortunately, it's only available for Mac OS and Windows. But that's not a big deal for me and all GNU/Linux users who want to keep using StarUML (although there are many alternative software such as [ArgoUML](http://argouml.tigris.org/) ). Thanks to [Wine](https://www.winehq.org/) which allow applications designed for Windows to run on Unix-like OS. 

### Problem
This evening, I tried to install StarUML on Wine (on my [Fedora](http://fedoraproject.org/) 20 machine) and I found the following error:

{% highlight bat %}
C:\Program Files\StarUML\Pgmr101.ocx
> |
> | Unable to register the DLL/OCX: LoadLibrary failed; code 126.
> | Module not found.
{% endhighlight %}

### How to Fix?
Open your favorite shell, install **winetricks** and some wine prerequisites packages :

{% highlight bash %}
# wget http://kegel.com/wine/winetricks

# sh winetricks vcrun6 msxml4
{% endhighlight %}

Hope this helps :) 