---
layout: post
title: Last.fm Scrobbler for MOC
date: 2014-10-12 17:57:00
categories: multimedia tool
excerpt: "Instructions on how to set up Last.fm scrobbler on MOC player."
tags: [moc, mocp, scrobbler, last.fm, scrobble for mocp, rhythmbox, nightingale, python3]
comments: true
---

Are you a big fan of **[MOC](http://moc.daper.net/)**? - So do I. MOC (music on console) is a console audio player for Linux/ UNIX. Some people are always calling it **`mocp`** which is actually it's binary file name. Like other audio players such as *Rhythmbox* and *Nightingale*, MOC can also scrobbled playing track information to your [Last.fm](http://www.last.fm/) account. Here are an instructions to set up Last.fm scrobbler for MOC :

You need **[`python3`](https://www.python.org/downloads/)** installed on your computer.
{: .notice}

* Create configuration file on `~/.mocpscrob/config` and should look like below:
{% highlight bash %}
$ nano ~/.mocpscrob/config 

[scrobbler]
login=YOUR_LAST.FM_USERNAME
password=YOUR_LAST.FM-PASSWORD
streams=true
hostname=post.audioscrobbler.com
{% endhighlight %}
Replace `login` and `password` value with your Last.fm account. Don't worry, `password` will be replaced with `password_md5` when the following python script run.

* Download `mocp-scrobbler.py` and put this python script to your $PATH.
{% highlight bash %}
# Download `mocp-scrobbler.py`
$ git clone https://github.com/fluxid/mocp-scrobbler.git

# Check your $PATH
$ echo $PATH
/sbin:/bin:/usr/sbin:/usr/bin:/usr/local/git/bin

# Move `mocp-scrobbler.py` to $PATH 
$ sudo mv mocp-scrobbler/mocp-scrobbler.py /usr/bin
{% endhighlight %}

* Run the python script
{% highlight bash %}
$ python3 -d /usr/bin/mocp-scrobbler.py
{% endhighlight %}

Now, run MOC on other Terminal/ Shell, play a music and the Scrobbler works.

<figure>
	<a href="http://www.last.fm/user/rilutham"><img src="/images/posts/mocp-scrobbler.jpg" alt="mocp scrobbler"></a>
	<figcaption>"Now Playing" notification on Last.fm profile.</figcaption>
</figure>

### How to Start Scrobbler with MOC?
If you want to start Scrobbler automatically when MOC is running, you can make a simple custom alias.

* Add an alias to last line of `~/.bashrc` file.
{% highlight bash %}
$ nano ~/.bashrc

...
## alias for last.fm scrobbler on moc
alias mocp='python3 /usr/bin/mocp-scrobbler.py -d; mocp'
{% endhighlight %}

* Run the following command
{% highlight bash %}
$ source ~/.bashrc
{% endhighlight %}

Enjoy and share your favorite track to the world :)