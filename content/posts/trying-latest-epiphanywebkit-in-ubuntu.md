---
title: Trying latest epiphany/WebKit in Ubuntu
date: '2010-02-03T23:53:51+00:00'
slug: trying-latest-epiphanywebkit-in-ubuntu
categories:
- Debian
- Epiphany
- GNOME
- Planet GNOME
- Planet GPUL
- Planet Igalia
- Ubuntu
- WebKit
- WebKitGTK
wp_id: 190
---

Even though I'll be stating the obvious for so many ubuntu users/developers reading this post, I'd like to post a quick recipe for those who don't know how to <strong>easily</strong> install the latest version of epiphany with the WebKit backend, as well as all the needed dependencies, without having to mess with compiling the source code (which is not always an easy nor a quick task, by the way).

So here we go
<ol>
	<li>First of all, this only works for Ubuntu Jaunty or Karmic, since there are no PPAs available for previous distros to install Epiphany (WebKit PPAs provided since Hardy).</li>
	<li>Add the PPA’s from the <a title="WebKit team in Launchpad" href="https://launchpad.net/~webkit-team">WebKit Team</a> both for installing latest version of <a title="PPA for WebKit" href="https://launchpad.net/~webkit-team/+archive/ppa">WebKit</a> and <a title="PPA for Epiphany" href="https://launchpad.net/~webkit-team/+archive/epiphany">Epiphany</a>. So, that is, add the following lines to your <code>/etc/apt/sources.list</code>file (replace ‘karmic’ with ‘jaunty’ if needed):
<pre>deb http://ppa.launchpad.net/webkit-team/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/webkit-team/ppa/ubuntu karmic main 

deb http://ppa.launchpad.net/webkit-team/epiphany/ubuntu karmic main
deb-src http://ppa.launchpad.net/webkit-team/epiphany/ubuntu karmic main</pre>
</li>
	<li>Import the GPG key of the repo in APT:
<pre>sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 2D9A3C5B</pre>
</li>
	<li>Update APT packages cache:
<pre>sudo apt-get update</pre>
</li>
	<li>Install the needed packages:
<pre>sudo apt-get install epiphany-browser epiphany-browser-dataepiphany-extensions</pre>
</li>
	<li>Just wait and let APT to do its magic :-)</li>
</ol>
And that's all. After those simple steps you should be enjoying the last version of  this great and amazingly fast browser (2.29.6 at the time of writing this post), which is nowadays under heavy development, continuously getting better, better and even better on <a title="TODO list for Epiphany/WebKit 2.30" href="http://live.gnome.org/Epiphany/WebKit230">its roadmap towards GNOME 2.30</a>.

So, what are you waiting for? Just go ahead and give it a try if you haven't done it yet and make it your default browser ;-). Now you don't have to manually compile all the needed stuff you just don't have any good excuse not to do it.

And don't forget to report any issue you find in the <a title="GNOME bugzilla" href="https://bugzilla.gnome.org/">bugzilla</a>. Remember feedback (and patches, of course) is the best way to help with improving it even more!

Ah! by the way, almost forgot to say that...

<strong>I'm attending FOSDEM</strong>

...as another member of the <a title="Igalia" href="http://www.igalia.com">Igalia</a> gang hanging around there this weekend.

See you there guys!

[<strong>Update 2010/01/04]</strong> As commented by <strong>zerwas</strong>, there's an <strong>even easier way</strong> from <strong>Karmic</strong> on:
<ol>
	<li>Add the PPA's from the <a title="WebKit team in Launchpad" href="https://launchpad.net/~webkit-team">WebKit Team</a> both for installing latest version of <a title="PPA for WebKit" href="https://launchpad.net/~webkit-team/+archive/ppa">WebKit</a> and <a title="PPA for Epiphany" href="https://launchpad.net/~webkit-team/+archive/epiphany">Epiphany</a>:
<pre>sudo add-apt-repository ppa:webkit-team/ppa
sudo add-apt-repository ppa:webkit-team/epiphany</pre>
</li>
	<li>Update APT packages cache:
<pre>sudo apt-get update</pre>
</li>
	<li>Install the needed packages:
<pre>sudo apt-get install epiphany-browser epiphany-browser-dataepiphany-extensions</pre>
</li>
</ol>
