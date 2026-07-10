---
title: My Slug, my PS3 and me
date: '2009-01-27T00:04:32+00:00'
slug: my-slug-my-ps3-and-me
categories:
- Debian
- Planet GPUL
- Planet Igalia
- Systems
wp_id: 33
---

<a title="Juan's NSLU2 page" target="_blank" href="https://blogs.igalia.com/jasuarez/nslu2">As Juan</a>, I'm one of the proud owners of a <a target="_blank" title="Linksys NSLU2" href="http://en.wikipedia.org/wiki/NSLU2">Linksys NSLU2</a> (aka <em>Slug</em>) perfectly (and continuously) running the <a target="_blank" title="Debian/NSLU2" href="http://www.nslu2-linux.org/wiki/Debian/HomePage">Debian/NSLU2</a> distribution for more than 6 months, currently featuring the following configuration (both sw and hw), after some slightly changes:
<ol>
	<li>Attached 500Gb 2,5" HD (powered through its USB2.0 connector).</li>
	<li><a target="_blank" title="MediaTomb - Free UPnP Media Server" href="http://mediatomb.cc/">MediaTomb</a> <a title="uPnP" href="http://en.wikipedia.org/wiki/Upnp">uPnP</a> media server, to keep a nice "media center" running always available.</li>
	<li><a title="Samba" target="_blank" href="http://us3.samba.org/samba/">Samba</a> filesharing server (to easily share files with any device connected to the LAN)</li>
	<li><a title="The libtorrent and rtorrent project" target="_blank" href="http://libtorrent.rakshasa.no/"><em>rtorrent</em></a> bitTorrent client, to use the <em>Slug</em> as a dedicated machine always up and ready to download whatever you want.</li>
	<li>The 'screen' command line utility (useful to easily keep the <em>rtorrent</em> app always running and "detachable" ;-)).</li>
	<li><a title="OpenSSH" target="_blank" href="http://www.openssh.com/">OpenSSH</a> server (ssh port forwarded in the router to access the <em>Slug</em> from the Internet), to easily manage my <em>Slug</em> from anywhere in the world.</li>
</ol>
With the exception of the HD (which used to be a 3,5" 120Gb HD since June to December, when I replaced with the 500Gb one), the rest of the configuration was amazingly working with <span style="font-weight: bold">no problems at all for more than </span>6 months, as I previously stated. This, along with the fact that this  device is quite small, noise-and-heat-free (no fans) and only needs 8W (it's the 266Mhz, 'underclocked' version) to work, makes it one of my favourite devices I ever had :-).

But all this was kind of "incomplete" stuff until I got a <a title="Playstation 3" target="_blank" href="http://www.us.playstation.com/PS3"><em>PS3</em></a>, as a present from my girlfriend during last Christmas holidays, which gave it a new dimension to the <em>Slug</em>, since the <em>PS3</em> bundles a nice uPnP client for pictures, audio and video which works perfectly with the MediaTomb server installed in this cute device<span style="font-style: italic">.</span>

The point now is that I no more need to copy the video files I download with my Slug to another device (a desktop PC, a laptop...) to watch them, either in such a device or in the TV (with the help of a multimedia HD)... all I need to do is just:
<ol>
	<li>Have the MediaTomb server continuously running in the <em>Slug</em>, watching (through its <a title="inotify" target="_blank" href="http://en.wikipedia.org/wiki/Inotify"><em>inotify</em></a> feature) to the <em>/storage/videos</em> directory for new videos (I want it to index them whenever I copy new downloaded videos under that path).</li>
	<li>Have the <em>PS3</em> connected to the local network, either through it's wired or wireless interface.</li>
	<li>Move the video files, as soon as they get fully downloaded, from my <em>/storage/downloads</em> path into <em>/storage/videos</em></li>
</ol>
This way, just by the moving the downloaded media files as explained in (3), and waiting a couple of minutes for the <em>MediaTomb</em> to index them, I have that media content available to be directly watched in the TV, which is really cool and very handy, by the way :-)

Of course, you can also do the same with regular pictures or audio files (which is very nice also if you have, like me, the <em>PS3</em> audio output also plugged into a Hi-Fi), but I think you'll agree with me that watching video files seems to be the best way to make the most of the <em>Slug</em>+<em>Ps3</em>+<em>TV</em> combo :-).

And that's all, I think... just to mention I've written this post while I was listening to a nice <a target="_blank" title="Thin Lizzy" href="http://en.wikipedia.org/wiki/Thin_Lizzy">Thin Lizzy</a> album ("<a target="_blank" title="Thin Lizzy: Dedication" href="http://en.wikipedia.org/wiki/Dedication:_The_Very_Best_of_Thin_Lizzy">Dedication</a>") stored in the <em>Slug</em>, through the <em>PS3 </em>and my Hi-Fi equipment. It sounds good, doesn't it? :-)

PS: One of these days I'll post more in detail how to set up the configuration for all the components I'm currently using in my <em>Slug (rtorrent</em>, <em>Samba</em>, <em>MediaTomb</em>...)<em>,</em> just in case someone found it useful.
