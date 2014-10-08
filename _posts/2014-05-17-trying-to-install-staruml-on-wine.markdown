---
layout: post
title: Error While Installing StarUML on Wine
date: 2014-05-07 20:35:55
categories: wine starUML OOP Development
---

Problem :
Trying to install StarUML

{% highlight bash %}
C:\Program Files\StarUML\Pgmr101.ocx
> |
> | Unable to register the DLL/OCX: LoadLibrary failed; code 126.
> | Module not found.
{% endhighlight %}



Solution:
wget http://kegel.com/wine/winetricks
sh winetricks vcrun6 msxml4







