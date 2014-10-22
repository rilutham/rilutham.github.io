---
layout: post
title:  Install Telegram on Fedora 20
date:   2014-10-22 12:44
categories: messenger, tool, fedora
tags: [telegram, messenger, secure, private, fedora]
excerpt: "A few simple steps to install Telegram on Fedora 20."
comments: true
---

I can't says anything more about Telegram, that was absolutely amazing. It is a secure, fast, private, and powerful messenger. Moreover, it can be accessed from multiple devices (Mobile, Desktop, and Web), the thing that makes me adore it. I decided to install it on my Fedora 20 machine and only requires a few simple steps.

* Download Telegram for Linux [here](https://tdesktop.com/) (32 bit or 64 bit depends on your machine).
* Extract file to `/opt` directory.

{% highlight bash %}
$ sudo tar xvf tsetup.0.6.4.tar.xz -C /opt
{% endhighlight %}

### Create executable file

{% highlight bash %}
$ sudo ln -s /opt/Telegram/Telegram /usr/bin/telegram
{% endhighlight %}

### Create menu shortcut

* Download Telegram icon.

{% highlight bash %}
$ sudo wget https://telegram.org/img/t_logo.png -O /opt/Telegram/icon.png
{% endhighlight %}

* Add the following script to `/usr/share/applications/telegram.desktop` file.

{% highlight bash %}
[Desktop Entry]
Version=0.6.4
Name=Telegram
GenericName=Telegram
Comment=Telegram
Exec=telegram
Icon=/opt/Telegram/icon.png
Terminal=false
Type=Application
StartupNotify=true
Categories=Network;WebBrowser;
Keywords=web;chat;internet;
{% endhighlight %}
