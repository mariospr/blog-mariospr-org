---
title: Installing a VNC server on a maemo Internet Tablet
date: '2008-04-17T11:14:54+00:00'
slug: installing-a-vnc-server-on-a-maemo-internet-tablet
categories:
- GNOME
- Maemo
- Meetings and conferences
- Planet GNOME
- Planet GPUL
- Planet Igalia
- Planet Maemo
- Vagalume
wp_id: 24
---

Today, I'm going to give a talk about <a title="Vagalume at igalia.com" href="http://vagalume.igalia.com">Vagalume</a> in the <em>"<a target="_blank" title="VIII Jornadas de Software Libre de GPUL 2008" href="http://gpul.grupos.udc.es/MaKaC/conferenceDisplay.py?confId=11">VIII Jornadas de Software Libre de GPUL 2008</a>"</em>, since <a title="Berto's blog" href="https://blogs.igalia.com/berto">Berto</a> finally won't be able to be there, as it was initially planned, so I'll be charged with the responsibility of telling the people how cool <a title="Vagalume at igalia.com" href="http://vagalume.igalia.com">Vagalume</a>, <a target="_blank" title="maemo.org" href="http://www.maemo.org">Maemo</a> and <a target="_blank" title="The GNOME project" href="http://www.gnome.org">GNOME</a> are in only 30 minutes... quite a big challenge for me, since I seldom can speak in a concise, short and effective way without going on and on.

So, yesterday I spent some time looking for an easy and effective way for showing people attending to the talk how cool this cute device (my <em><a title="Nokia N810" target="_blank" href="http://en.wikipedia.org/wiki/N810">N810</a></em>) is... and thinking about the past I remembered when Andres gave a talk/workshop about the Maemo development platform, where he used an <a title="Virtual Network Computing" href="http://en.wikipedia.org/wiki/VNC">VNC</a> server installed in the device to show the <em><a title="Nokia N810" target="_blank" href="http://en.wikipedia.org/wiki/N810">N810</a></em> "screen" to everyone in the room, just using an <a title="Virtual Network Computing" href="http://en.wikipedia.org/wiki/VNC">VNC</a> client in the laptop connected to the proyector.

IIRC, <a title="Andres' blog" href="https://blogs.igalia.com/agomez">Andrés</a> compiled the <a title="Virtual Network Computing" href="http://en.wikipedia.org/wiki/VNC">VNC</a> server for the device to get it working, but yesterday I found a much easier way to get it working, so here you are the receipt (I use too much this word in my blog, perhaps I should consider to become a cook... ):
<ul>
	<li>Download the pre-compiled .deb package for your device from <a target="_blank" title="Mike Saunby's web" href="http://mike.saunby.googlepages.com/x11vncfornokia7702">this web</a>.</li>
	<li>Copy the .deb file to your device and install it following <strong>one of the following methods</strong>:</li>
<ul>
	<li>Install it with the Application installer from the Control Panel (<a title="Nokia N770" target="_blank" href="http://en.wikipedia.org/wiki/N770"><em>N770</em></a>).</li>
	<li>Install it with the Application Manager from the 'Settings' Menu (<em><a title="Nokia N800" target="_blank" href="http://en.wikipedia.org/wiki/N800">N800</a> / <a title="Nokia N810" target="_blank" href="http://en.wikipedia.org/wiki/N810">N810</a></em>). It's <strong>required </strong>to have the <strong>red-pill mode enabled</strong>. To know how to enable this "peculiar" mode, <a target="_blank" title="Application Manager: Activating the Red-Pill mode" href="http://maemo.org/community/wiki/ApplicationManagerRedPillMode">check this out</a>.</li>
	<li>Open a <strong>root terminal</strong> in the device with a remote ssh connection and install it this way:</li>
<blockquote>dpkg -i x11vnc_0.9.3-1_armel.deb</blockquote>
</ul>
	<li>Configure it to use a password with the default username available in the device ('<em>user</em>'):</li>
<ul>
	<li>Make sure you are running the terminal as <em>'user'</em>, by executing the command:</li>
<blockquote>su user</blockquote>
</ul>
<ul>
	<li>Create a VNC password (recommended):</li>
<blockquote>x11vnc -storepasswd</blockquote>
<ul>
	<li>This will store your password (encrypted) under <em>/home/user/.vnc/passwd</em></li>
</ul>
</ul>
	<li>Start the server:</li>
<ul>
	<li>Not using the password: from <em>Menu -&gt; Extras</em>, click on <em>x11vnc</em>.</li>
	<li>Using the password (recommended):</li>
<ul>
	<li>Open a terminal for <em>'user'</em></li>
	<li>Execute the command:</li>
<blockquote>x11vnc --usepw</blockquote>
</ul>
</ul>
	<li>Connect to server (already running on the device, at <em>port 5900</em>):</li>
<ul>
	<li>Using any VNC client connect to your device's IP, using the following credentials if you started the server with <em>--usepw</em>:</li>
<ul>
	<li>Username: <em>user</em></li>
	<li>Password: (whatever you've set with <em>--storepasswd</em>)</li>
</ul>
</ul>
</ul>
Of course, there are lots of options you can pass to <em>x11vnc</em> (see <em>x11vnc --help</em>) but these ones worked fine for me: I have an easy <a title="Virtual Network Computing" href="http://en.wikipedia.org/wiki/VNC">VNC</a> server working with password authentication :-)

And to finish this post, just a last advice: If you think you're going to use always (like me) the <a title="Virtual Network Computing" href="http://en.wikipedia.org/wiki/VNC">VNC</a> server with password authentication, it could be more nice for you to edit the <em>/usr/bin/x11vnc.sh</em> script so it also includes the <em>--usepw</em>. This way, you can always start the <a title="Virtual Network Computing" href="http://en.wikipedia.org/wiki/VNC">VNC</a> server from <em>Menu -&gt; Extras</em>, withouth having to open a terminal for it... although, to be honest, I still prefer a remote terminal for most of the times, because of the output I continously get through it... but hey! that's just a very personal opinion! :-)
