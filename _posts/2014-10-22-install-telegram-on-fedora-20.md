---
layout: post
title:  Install Telegram on Fedora 20/21/22
date:   2014-10-22 12:44
modified: 2015-07-10
categories: messenger tool fedora
tags: [telegram, messenger, secure, private, fedora]
excerpt: "A few simple steps to install Telegram on Fedora 20."
comments: true
---

I can't says anything more about [Telegram](https://telegram.org/), it was absolutely amazing. It is a secure, fast, private, and powerful messenger [^1]. Moreover, it can be accessed from multiple devices (Mobile, Desktop, and Web), the thing that makes me adore it. I decided to install it on my Fedora 20 machine and only requires a few simple steps.

[^1]: <https://www.techinasia.com/10-best-secure-messaging-apps>

This instruction works well on all GNU/Linux distributions.
{: .notice}

* Download Telegram for Linux [here](https://desktop.telegram.org/) (32 bit or 64 bit depends on your machine).
* Extract file to `/opt` directory.

{% highlight bash %}
$ sudo tar xvf tsetup.0.6.4.tar.xz -C /opt
Telegram/
Telegram/Updater
Telegram/Telegram
{% endhighlight %}

### Create executable file

{% highlight bash %}
$ sudo ln -s /opt/Telegram/Telegram /usr/bin/telegram
{% endhighlight %}

Now, you can execute `telegram` on your favorite shell/ terminal.

### Create menu shortcut

* Download Telegram icon.

{% highlight bash %}
$ sudo wget https://telegram.org/img/t_logo.png -O /opt/Telegram/icon.png
{% endhighlight %}

* Add the following script to `/usr/share/applications/telegram.desktop` file.

{% highlight bash %}
$ sudo nano /usr/share/applications/telegram.desktop

[Desktop Entry]
Version=0.6.4
Name=Telegram
GenericName=Telegram
Comment=Private and Secure Messenger
Exec=telegram
Icon=/opt/Telegram/icon.png
Terminal=false
Type=Application
StartupNotify=true
Categories=Network;WebBrowser;
Keywords=chat;messenger;internet;
{% endhighlight %}

Check Application Menu > Internet > Telegram , find your friend and start private and secure conversation.

<figure>
	<img src="/images/posts/telegram-on-fedora-20.jpg" alt="Telegram on Fedora 20">
	<figcaption>Telegram on Fedora 20.</figcaption>
</figure>
